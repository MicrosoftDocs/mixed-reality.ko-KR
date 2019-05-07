# <a name="mixing-color-and-depth-data"></a>색과 농도 데이터가 혼합

색 카메라 및 깊이 카메라에서 받아야 하는 리소스를 다른 형태와 규모 있습니다. 둘을 결합 하려는 경우 서로 맞게 수행할 수 있는 작업의 수가입니다.

![](img/ColorandDepthMeshSmall.png)

**콘텐츠:**  
[구성 및 설정](#Configuration-and-Setup)  
[데이터 가져오기](#Getting-Data)  
[데이터 변환](#Transforming-Data)  
[지점 클라우드에서 메시 만들기](#Creating-a-Mesh-From-the-Point-Cloud)  
[깊이 색에서 이미지 만들기](#Creating-an-Image-From-Depth-and-Color)  
[정리](#Cleaning-Up)  
[전체 소스](#Full-Source)  

**사용 하 여 함수는 다음과 같습니다.**  
[`k4a_device_get_calibration()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-calibration)  
[`k4a_transformation_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-create)  
[`k4a_image_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-create)  
[`k4a_transformation_depth_image_to_color_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-color-camera)  
[`k4a_transformation_color_image_to_depth_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-color-image-to-depth-camera)  
[`k4a_transformation_depth_image_to_point_cloud()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-point-cloud)  

## <a name="configuration-and-setup"></a>구성 및 설정

원했습니다 거의 모든 구성, 여기서 사용할 수 있지만 우리가 작성할 수 있습니다 압축 되지 않은 데이터 파일에 있으므로 더 작은 해상도을 집중적 하는 것입니다. 읽기에 문서를 확인 합니다 [색 카메라]() 하 고 [깊이 카메라]() 구성에 대 한 자세한 내용은!

하나의 추가 요소가 `synchronized_images_only` 옵션. 로 설정 `true` 지정만 색이 모두는 캡처 <i>고</i> 깊이 채워집니다. 첫 번째 몇에서 캡처에서는 사용 하지 않으면이 `k4a_device_get_capture` 부족 하거나, 또는 이미지 색 수 있습니다.

```C
// Configure the Kinect to open a stream of 512x512 wide field of view
// 16 bit depth data + 1280x720 BRGA color at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;
config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
config.synchronized_images_only = true;

k4a_device_start_cameras(device, &config);
```

이 구성 정보를 만들었으므로 이제 해당 모든 변환 함수에 전달 되는 보정 개체를 설정 해야 했습니다! 이 개체와 깊이 공간 및 visa 간에 색 카메라 공간 좌표로 변환 하는 데 사용 된 미리 계산 된 리소스를 포함 합니다. 하나를 수행 하는 것은 매우 간단 합니다.

```C
k4a_calibration_t calibration;
k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration);
k4a_transformation_t transform = k4a_transformation_create(&calibration);
```

## <a name="getting-data"></a>데이터 가져오기

이제 이미지를 색 및 깊이 이미지를 가져오는 데 필요한! 단일 프레임 및 관련 데이터를 여기 수집 됩니다. 사용자 이미지 중 하나를 들어오는 경우 다시 null 확인을 사용해 `synchronized_images_only` 구성에서!

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Grab image data from the Kinect
k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
int32_t color_w = k4a_image_get_width_pixels (raw_colors);
int32_t color_h = k4a_image_get_height_pixels(raw_colors);
printf("Captured depth image, %dx%d\n", depth_w, depth_h);
printf("Captured rgb image, %dx%d\n", color_w, color_h);
```

## <a name="transforming-data"></a>데이터 변환

`k4a_transform_` 함수 간 공간 하나 카메라에서에서 이미지 데이터를 변환 됩니다. 상호 연결할 수 있습니다 색 및 깊이 정보 함께 쉽게 하므로 왜곡 및 대상 카메라 공간으로 확인 되는 이미지 일치 합니다.

예를 들어! 많은 경우 각 색 픽셀에 대 한 해당 깊이 사용 하 여 카메라에서 컬러 이미지가 좋습니다! 이 위해 색 카메라 공간으로 깊이 데이터를 변환 합니다.

또는 다음 깊이 카메라에서 3D 지점 데이터의 클라우드를 만들고 각 점 색 인지 알고 있어야 하는 것이 좋습니다. 이 위해 point cloud, 깊이 데이터를 변환 하 고 깊이 카메라 공간에 컬러 이미지를 변환할 수 했습니다! 그런 다음 XYZ 값의 버퍼 및 색의 해당 버퍼를 해야 합니다.

### <a name="depth-data-in-color-space"></a>색 공간에서 깊이 데이터

이 색 카메라의 출력에 맞게 깊이 데이터 변환. 결과 버퍼 색 이미지에서 각 픽셀의 깊이 16 비트 값을 갖게 됩니다.
 
```C
k4a_image_t depth_color_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_DEPTH16, 
    color_w, color_h, color_w * sizeof(uint16_t), 
    &depth_color_space))
k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

uint16_t *depth_data = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_color_space));
```

### <a name="creating-a-point-cloud"></a>지점 클라우드 만들기

점 클라우드 이미지 리소스에도 저장 됩니다. 형식의 이미지를 만들겠습니다. 이때 `K4A_IMAGE_FORMAT_CUSTOM`point cloud 이미지인 정확히 때문입니다. 각 이미지의 '픽셀' 3로 구성 됩니다 `int16_t` x y Z 좌표를 나타내는 값을 따라서도 지정 올바른 크기에 대 한 합니다.

```C
k4a_image_t point_cloud_xyz;
k4a_image_create(
    K4A_IMAGE_FORMAT_CUSTOM, 
    depth_w, depth_h, depth_w * 3 * sizeof(int16_t), 
    &point_cloud_xyz);
k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

int16_t *xyz_data = reinterpret_cast<int16_t*>(k4a_image_get_buffer(point_cloud_xyz))
```

### <a name="color-data-in-depth-space"></a>색 공간의 데이터를 깊이

이 변환 출력 깊이를 일치 하도록 색 데이터! 결과 버퍼의 각 색상 값 깊이 이미지의 값과 일치 합니다.

```C
k4a_image_t color_depth_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_COLOR_BGRA32, 
    depth_w, depth_h, depth_w * sizeof(uint32_t), 
    &color_depth_space);
k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

uint8_t *color_data = static_cast<uint8_t*>(k4a_image_get_buffer(color_depth_space));
```

## <a name="creating-a-mesh-from-the-point-cloud"></a>지점 클라우드에서 메시 만들기

![](img/ColorandDepthMeshSmall.png)

지점 클라우드 데이터를 좀 더 친숙 한 형식으로 변환 하 여 시작 하겠습니다. 미터, 밀리미터를 변환 하 고 부동 소수점 수를 위로 이동 됩니다.

```C
// Convert the point cloud from millimeters to meters
float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
for (int32_t i = 0; i < depth_w*depth_h; i++)
{
    vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
    vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
    vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
}
```

이제 상위 일부 글꼴 정보를 사용 하 여 이러한 꼭 짓이 점 연결에서는 했습니다! 표 형태로 배치 된 모든 항목 이므로 각 셀의 모퉁이 연결 하는 간단한 프로세스입니다. 여기서 보여드린 것만 추가 빈 데이터를 포함 하는 모든 얼굴을 건너뛰는 중입니다. Kinect 지점 클라우드에서 지점에 대 한 깊이 데이터를 찾을 수 없습니다, 하는 경우 < 0,0,0 >에 넣습니다. 인덱스 목록에 추가 하는 경우 hedgehog 상당히으로 바뀝니다.

```C
// Make mesh faces as quads across the image. Skip the 
// face if any part of its data is empty.
vector<uint32_t> indices;
for (int32_t y = 0; y < depth_h; y++)
{
    for (int32_t x = 0; x < depth_w; x++)
    {
        int32_t row1 = x +       y * depth_w;
        int32_t row2 = x + (y + 1) * depth_w;

        // If all corners of this quad have depth data
        if (xyz_data[ row1      * 3 + 1] != 0 && 
            xyz_data[(row1 + 1) * 3 + 1] != 0 && 
            xyz_data[ row2      * 3 + 1] != 0 && 
            xyz_data[(row2 + 1) * 3 + 1] != 0)
        {
            // ..then add indices for this quad
            indices.push_back(row2);
            indices.push_back(row2+1);
            indices.push_back(row1+1);
            indices.push_back(row1);
        }
    }
}
```

그런 다음 파일에만이 정보를 작성할 수 했습니다! 사용 되지 않는 색을 제거 하지 것 또는 위치 때문에 지금까지 만든 버퍼에만 전달할 수 있으므로 인덱스를 만드는 복잡성을 추가 합니다.

```C
// Write geometry data to a .PLY, and clean up
ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, indices.size() / 4, &indices[0]);
free(vertex_positions);
```

## <a name="creating-an-image-from-depth-and-color"></a>깊이 색에서 이미지 만들기

![](img/ColorandDepthSmall.png)

색을 손쉽게 수행 됩니다. 여기에서 간단한 페이드 거리 검정으로 작업을 수행 하지만 모든 종류의 사진 관리 도구에서 마스크로 사용 하기 위해 알파 채널의 깊이 저장 하거나 특정 깊이 범위 아웃 클리핑와 같은 흥미로운 작업을 수행할 수 있습니다!

```C
// Create an RGB image where we fade color values to black as they recede into the distance
uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
for (int32_t i = 0; i < color_w*color_h; i++)
{
    // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
    float depth = 1 - depth_data[i]/4000.0f;
    depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

    // Fade this pixel, and assign it to our new buffer
    mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
    mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
    mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
}
// Write the image to file
tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
free(mixed_colors);
```

## <a name="cleaning-up"></a>정리

항상 릴리스 모두 완료 되 면:) 및

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(point_cloud_xyz);
k4a_image_release(depth_color_space);
k4a_image_release(color_depth_space);
k4a_image_release(raw_colors);
k4a_image_release(raw_depth);
k4a_capture_release(capture);
k4a_transformation_destroy(transform);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>전체 소스

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

#include <vector>
using namespace std;

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices);
void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 512x512 wide field of view
    // 16 bit depth data + 1280x720 BRGA color at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;
    config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
    config.synchronized_images_only = true;
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
        printf("Failed to start cameras!\n");

    // Prep data for transforming depth information to color camera space
    k4a_calibration_t calibration;
    if (K4A_FAILED(k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration)))
        printf("Failed to get calibration!\n");
    k4a_transformation_t transform = k4a_transformation_create(&calibration);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    if (K4A_FAILED(k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE)))
        printf("Failed to capture image!\n");

    // Grab image data from the Kinect
    k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
    k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
    int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
    int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
    int32_t color_w = k4a_image_get_width_pixels (raw_colors);
    int32_t color_h = k4a_image_get_height_pixels(raw_colors);
    printf("Captured depth image, %dx%d\n", depth_w, depth_h);
    printf("Captured rgb image, %dx%d\n", color_w, color_h);

    // Transform the raw depth data into color camera space
    k4a_image_t depth_color_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_DEPTH16, color_w, color_h, color_w * sizeof(uint16_t), &depth_color_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

    // Get the point cloud
    k4a_image_t point_cloud_xyz;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_CUSTOM, depth_w, depth_h, depth_w * 3 * sizeof(int16_t), &point_cloud_xyz)))
        printf("Failed to create a point cloud image resource!\n");
    k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

    // Transform the raw color data into depth camera space
    k4a_image_t color_depth_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_COLOR_BGRA32, depth_w, depth_h, depth_w * sizeof(uint32_t), &color_depth_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

    // Get access to the raw color and point cloud data.
    uint8_t  *raw_color_data = static_cast     <uint8_t  *>(k4a_image_get_buffer(raw_colors));
    uint8_t  *color_data     = static_cast     <uint8_t  *>(k4a_image_get_buffer(color_depth_space));
    uint16_t *depth_data     = reinterpret_cast<uint16_t *>(k4a_image_get_buffer(depth_color_space));
    int16_t  *xyz_data       = reinterpret_cast<int16_t  *>(k4a_image_get_buffer(point_cloud_xyz));

    // Turn the point cloud into a mesh, and write it to file!

    // Convert the point cloud from millimeters to meters
    float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
    for (int32_t i = 0; i < depth_w*depth_h; i++)
    {
        vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
        vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
        vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
    }

    // Make mesh faces as quads across the image. Skip the
    // face if any part of its data is empty.
    vector<uint32_t> indices;
    for (int32_t y = 0; y < depth_h; y++)
    {
        for (int32_t x = 0; x < depth_w; x++)
        {
            int32_t row1 = x +       y * depth_w;
            int32_t row2 = x + (y + 1) * depth_w;

            // If all corners of this quad have depth data
            if (xyz_data[ row1      * 3 + 1] != 0 && 
                xyz_data[(row1 + 1) * 3 + 1] != 0 && 
                xyz_data[ row2      * 3 + 1] != 0 && 
                xyz_data[(row2 + 1) * 3 + 1] != 0)
            {
                // ..then add indices for this quad
                indices.push_back(row2);
                indices.push_back(row2+1);
                indices.push_back(row1+1);
                indices.push_back(row1);
            }
        }
    }

    // Write geometry data to a .PLY, and clean up
    ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, static_cast<uint32_t>(indices.size()) / 4, &indices[0]);
    free(vertex_positions);
    
    // Create an RGB image where we fade color values to black as they recede into the distance
    uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
    for (int32_t i = 0; i < color_w*color_h; i++)
    {
        // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
        float depth = 1 - depth_data[i]/4000.0f;
        depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

        // Fade this pixel, and assign it to our new buffer
        mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
        mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
        mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
    }
    // Write the image to file
    tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
    free(mixed_colors);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(point_cloud_xyz);
    k4a_image_release(depth_color_space);
    k4a_image_release(color_depth_space);
    k4a_image_release(raw_colors);
    k4a_image_release(raw_depth);
    k4a_capture_release(capture);
    k4a_transformation_destroy(transform);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices)
{
    FILE *fp = nullptr;
    fopen_s(&fp, filename, "w");

    // Write the .PLY header information
    fprintf(fp, "ply\nformat ascii 1.0\n");
    fprintf(fp, "element vertex %d\nproperty float x\nproperty float y\nproperty float z\nproperty uchar red\nproperty uchar green\nproperty uchar blue\n", vertex_count);
    fprintf(fp, "element face %d\nproperty list uchar int vertex_index\n", index_quad_count);
    fprintf(fp, "end_header\n");

    // Write each vertex with color information!
    for (uint32_t i = 0; i < vertex_count; i++)
    {
        fprintf(fp, "%g %g %g %d %d %d\n", 
            vertex_positions[i*3    ],
            vertex_positions[i*3 + 1],
            vertex_positions[i*3 + 2], 
            vertex_colors_bgra[i*4 + 2], 
            vertex_colors_bgra[i*4 + 1], 
            vertex_colors_bgra[i*4    ]);
    }

    // Write faces as quads.
    for (size_t i = 0; i < index_quad_count; i++)
    {
        fprintf(fp, "4 %d %d %d %d\n", quad_indices[i*4], quad_indices[i*4 + 1], quad_indices[i*4 + 2], quad_indices[i*4 + 3]);
    }
    fclose(fp);
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width%256, (uint8_t)(width/256), height%256, (uint8_t)(height/256), file_channels*8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---accessing-the-imuusingimumd"></a>다음 랩- [는 IMU 액세스](UsingIMU.md)