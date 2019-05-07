# <a name="mixing-color-and-depth-data"></a><span data-ttu-id="346d1-101">색과 농도 데이터가 혼합</span><span class="sxs-lookup"><span data-stu-id="346d1-101">Mixing Color and Depth Data</span></span>

<span data-ttu-id="346d1-102">색 카메라 및 깊이 카메라에서 받아야 하는 리소스를 다른 형태와 규모 있습니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-102">The resources you get from the color camera and the depth camera have different shapes and sizes!</span></span> <span data-ttu-id="346d1-103">둘을 결합 하려는 경우 서로 맞게 수행할 수 있는 작업의 수가입니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-103">If you want to combine the two, there's a number of things you can do to align them to each other.</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="346d1-104">**콘텐츠:**</span><span class="sxs-lookup"><span data-stu-id="346d1-104">**Contents:**</span></span>  
[<span data-ttu-id="346d1-105">구성 및 설정</span><span class="sxs-lookup"><span data-stu-id="346d1-105">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="346d1-106">데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="346d1-106">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="346d1-107">데이터 변환</span><span class="sxs-lookup"><span data-stu-id="346d1-107">Transforming Data</span></span>](#Transforming-Data)  
[<span data-ttu-id="346d1-108">지점 클라우드에서 메시 만들기</span><span class="sxs-lookup"><span data-stu-id="346d1-108">Creating a Mesh From the Point Cloud</span></span>](#Creating-a-Mesh-From-the-Point-Cloud)  
[<span data-ttu-id="346d1-109">깊이 색에서 이미지 만들기</span><span class="sxs-lookup"><span data-stu-id="346d1-109">Creating an Image From Depth and Color</span></span>](#Creating-an-Image-From-Depth-and-Color)  
[<span data-ttu-id="346d1-110">정리</span><span class="sxs-lookup"><span data-stu-id="346d1-110">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="346d1-111">전체 소스</span><span class="sxs-lookup"><span data-stu-id="346d1-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="346d1-112">**사용 하 여 함수는 다음과 같습니다.**</span><span class="sxs-lookup"><span data-stu-id="346d1-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_calibration()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-calibration)  
[`k4a_transformation_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-create)  
[`k4a_image_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-create)  
[`k4a_transformation_depth_image_to_color_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-color-camera)  
[`k4a_transformation_color_image_to_depth_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-color-image-to-depth-camera)  
[`k4a_transformation_depth_image_to_point_cloud()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-point-cloud)  

## <a name="configuration-and-setup"></a><span data-ttu-id="346d1-113">구성 및 설정</span><span class="sxs-lookup"><span data-stu-id="346d1-113">Configuration and Setup</span></span>

<span data-ttu-id="346d1-114">원했습니다 거의 모든 구성, 여기서 사용할 수 있지만 우리가 작성할 수 있습니다 압축 되지 않은 데이터 파일에 있으므로 더 작은 해상도을 집중적 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-114">While we could use just about any configuration we wanted here, we're sticking to smaller resolutions since we'll be writing uncompressed data to file.</span></span> <span data-ttu-id="346d1-115">읽기에 문서를 확인 합니다 [색 카메라]() 하 고 [깊이 카메라]() 구성에 대 한 자세한 내용은!</span><span class="sxs-lookup"><span data-stu-id="346d1-115">Check the documents on reading from the [color camera]() and [depth camera]() for more information about configurations!</span></span>

<span data-ttu-id="346d1-116">하나의 추가 요소가 `synchronized_images_only` 옵션.</span><span class="sxs-lookup"><span data-stu-id="346d1-116">One additional element here is the `synchronized_images_only` option!</span></span> <span data-ttu-id="346d1-117">로 설정 `true` 지정만 색이 모두는 캡처 <i>고</i> 깊이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-117">Setting it to `true` specifies that we only want captures that have both color <i>and</i> depth populated.</span></span> <span data-ttu-id="346d1-118">첫 번째 몇에서 캡처에서는 사용 하지 않으면이 `k4a_device_get_capture` 부족 하거나, 또는 이미지 색 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-118">If we don't use this, the first few captures from `k4a_device_get_capture` may lack either depth, or color images.</span></span>

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

<span data-ttu-id="346d1-119">이 구성 정보를 만들었으므로 이제 해당 모든 변환 함수에 전달 되는 보정 개체를 설정 해야 했습니다!</span><span class="sxs-lookup"><span data-stu-id="346d1-119">Now that we have our configuration information, we need to set up a calibration object that will be passed into all of our transformation functions!</span></span> <span data-ttu-id="346d1-120">이 개체와 깊이 공간 및 visa 간에 색 카메라 공간 좌표로 변환 하는 데 사용 된 미리 계산 된 리소스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-120">This object contains precalculated resources used for transforming coordinates to and from color camera space to depth space and visa versa.</span></span> <span data-ttu-id="346d1-121">하나를 수행 하는 것은 매우 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-121">Making one is pretty simple:</span></span>

```C
k4a_calibration_t calibration;
k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration);
k4a_transformation_t transform = k4a_transformation_create(&calibration);
```

## <a name="getting-data"></a><span data-ttu-id="346d1-122">데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="346d1-122">Getting Data</span></span>

<span data-ttu-id="346d1-123">이제 이미지를 색 및 깊이 이미지를 가져오는 데 필요한!</span><span class="sxs-lookup"><span data-stu-id="346d1-123">Now we need to acquire both a color image, and a depth image!</span></span> <span data-ttu-id="346d1-124">단일 프레임 및 관련 데이터를 여기 수집 됩니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-124">So here's grabbing a single frame and the relevant data from it.</span></span> <span data-ttu-id="346d1-125">사용자 이미지 중 하나를 들어오는 경우 다시 null 확인을 사용해 `synchronized_images_only` 구성에서!</span><span class="sxs-lookup"><span data-stu-id="346d1-125">If one of your images is coming back null, ensure you used `synchronized_images_only` in your configuration!</span></span>

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

## <a name="transforming-data"></a><span data-ttu-id="346d1-126">데이터 변환</span><span class="sxs-lookup"><span data-stu-id="346d1-126">Transforming Data</span></span>

<span data-ttu-id="346d1-127">`k4a_transform_` 함수 간 공간 하나 카메라에서에서 이미지 데이터를 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-127">The `k4a_transform_` functions will transform your image data from one camera space to another!</span></span> <span data-ttu-id="346d1-128">상호 연결할 수 있습니다 색 및 깊이 정보 함께 쉽게 하므로 왜곡 및 대상 카메라 공간으로 확인 되는 이미지 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-128">Resulting images will match the distortion and resolution of the target camera space, so you can correlate color and depth information together easily.</span></span>

<span data-ttu-id="346d1-129">예를 들어!</span><span class="sxs-lookup"><span data-stu-id="346d1-129">For example!</span></span> <span data-ttu-id="346d1-130">많은 경우 각 색 픽셀에 대 한 해당 깊이 사용 하 여 카메라에서 컬러 이미지가 좋습니다!</span><span class="sxs-lookup"><span data-stu-id="346d1-130">Quite often, you might want a color image from the camera, with a corresponding depth for each color pixel!</span></span> <span data-ttu-id="346d1-131">이 위해 색 카메라 공간으로 깊이 데이터를 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-131">For this, you would transform the depth data into color camera space.</span></span>

<span data-ttu-id="346d1-132">또는 다음 깊이 카메라에서 3D 지점 데이터의 클라우드를 만들고 각 점 색 인지 알고 있어야 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-132">Alternatively, you might want to create a cloud of 3D point data from the depth camera, and know what color each point is.</span></span> <span data-ttu-id="346d1-133">이 위해 point cloud, 깊이 데이터를 변환 하 고 깊이 카메라 공간에 컬러 이미지를 변환할 수 했습니다!</span><span class="sxs-lookup"><span data-stu-id="346d1-133">For this, we can transform the depth data into a point cloud, and transform the color image into depth camera space!</span></span> <span data-ttu-id="346d1-134">그런 다음 XYZ 값의 버퍼 및 색의 해당 버퍼를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-134">Then you'll have a buffer of XYZ values, and a corresponding buffer of colors.</span></span>

### <a name="depth-data-in-color-space"></a><span data-ttu-id="346d1-135">색 공간에서 깊이 데이터</span><span class="sxs-lookup"><span data-stu-id="346d1-135">Depth Data in Color Space</span></span>

<span data-ttu-id="346d1-136">이 색 카메라의 출력에 맞게 깊이 데이터 변환.</span><span class="sxs-lookup"><span data-stu-id="346d1-136">This transforms depth data to match the color camera's output!</span></span> <span data-ttu-id="346d1-137">결과 버퍼 색 이미지에서 각 픽셀의 깊이 16 비트 값을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-137">The resulting buffer will have a 16 bit depth value for each pixel in the color image.</span></span>
 
```C
k4a_image_t depth_color_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_DEPTH16, 
    color_w, color_h, color_w * sizeof(uint16_t), 
    &depth_color_space))
k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

uint16_t *depth_data = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_color_space));
```

### <a name="creating-a-point-cloud"></a><span data-ttu-id="346d1-138">지점 클라우드 만들기</span><span class="sxs-lookup"><span data-stu-id="346d1-138">Creating a Point Cloud</span></span>

<span data-ttu-id="346d1-139">점 클라우드 이미지 리소스에도 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-139">Point clouds are also stored in image resources!</span></span> <span data-ttu-id="346d1-140">형식의 이미지를 만들겠습니다. 이때 `K4A_IMAGE_FORMAT_CUSTOM`point cloud 이미지인 정확히 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-140">Here, we create an image of format `K4A_IMAGE_FORMAT_CUSTOM`, since a point cloud is not exactly an image.</span></span> <span data-ttu-id="346d1-141">각 이미지의 '픽셀' 3로 구성 됩니다 `int16_t` x y Z 좌표를 나타내는 값을 따라서도 지정 올바른 크기에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-141">Each 'pixel' in the image will be composed of 3 `int16_t` values representing XYZ coordinates, so we also specify the correct size for that.</span></span>

```C
k4a_image_t point_cloud_xyz;
k4a_image_create(
    K4A_IMAGE_FORMAT_CUSTOM, 
    depth_w, depth_h, depth_w * 3 * sizeof(int16_t), 
    &point_cloud_xyz);
k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

int16_t *xyz_data = reinterpret_cast<int16_t*>(k4a_image_get_buffer(point_cloud_xyz))
```

### <a name="color-data-in-depth-space"></a><span data-ttu-id="346d1-142">색 공간의 데이터를 깊이</span><span class="sxs-lookup"><span data-stu-id="346d1-142">Color Data in Depth Space</span></span>

<span data-ttu-id="346d1-143">이 변환 출력 깊이를 일치 하도록 색 데이터!</span><span class="sxs-lookup"><span data-stu-id="346d1-143">This transforms color data to match the output from the depth camera!</span></span> <span data-ttu-id="346d1-144">결과 버퍼의 각 색상 값 깊이 이미지의 값과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-144">Each color value from the resulting buffer will correspond with a value from the depth image.</span></span>

```C
k4a_image_t color_depth_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_COLOR_BGRA32, 
    depth_w, depth_h, depth_w * sizeof(uint32_t), 
    &color_depth_space);
k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

uint8_t *color_data = static_cast<uint8_t*>(k4a_image_get_buffer(color_depth_space));
```

## <a name="creating-a-mesh-from-the-point-cloud"></a><span data-ttu-id="346d1-145">지점 클라우드에서 메시 만들기</span><span class="sxs-lookup"><span data-stu-id="346d1-145">Creating a Mesh From the Point Cloud</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="346d1-146">지점 클라우드 데이터를 좀 더 친숙 한 형식으로 변환 하 여 시작 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-146">We'll start by converting the point cloud data into a format that's a little more familiar.</span></span> <span data-ttu-id="346d1-147">미터, 밀리미터를 변환 하 고 부동 소수점 수를 위로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-147">We'll convert it from millimeters to meters, and move it over to floats.</span></span>

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

<span data-ttu-id="346d1-148">이제 상위 일부 글꼴 정보를 사용 하 여 이러한 꼭 짓이 점 연결에서는 했습니다!</span><span class="sxs-lookup"><span data-stu-id="346d1-148">Now we'll stitch up these vertices with some face information!</span></span> <span data-ttu-id="346d1-149">표 형태로 배치 된 모든 항목 이므로 각 셀의 모퉁이 연결 하는 간단한 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-149">Since everything is laid out as a grid, this is a straightforward process of linking up the corners of each cell.</span></span> <span data-ttu-id="346d1-150">여기서 보여드린 것만 추가 빈 데이터를 포함 하는 모든 얼굴을 건너뛰는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-150">The only additional thing we're doing here is skipping any face that contains empty data.</span></span> <span data-ttu-id="346d1-151">Kinect 지점 클라우드에서 지점에 대 한 깊이 데이터를 찾을 수 없습니다, 하는 경우 < 0,0,0 >에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-151">If the Kinect couldn't find depth data for a point in the point cloud, it places it at <0,0,0>!</span></span> <span data-ttu-id="346d1-152">인덱스 목록에 추가 하는 경우 hedgehog 상당히으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-152">It turns into quite the hedgehog if you add those to the index list.</span></span>

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

<span data-ttu-id="346d1-153">그런 다음 파일에만이 정보를 작성할 수 했습니다!</span><span class="sxs-lookup"><span data-stu-id="346d1-153">Then we can just write this information to file!</span></span> <span data-ttu-id="346d1-154">사용 되지 않는 색을 제거 하지 것 또는 위치 때문에 지금까지 만든 버퍼에만 전달할 수 있으므로 인덱스를 만드는 복잡성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-154">We aren't removing unused colors or positions due to added complexity in creating indices, so we can just pass in the buffers we've created so far.</span></span>

```C
// Write geometry data to a .PLY, and clean up
ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, indices.size() / 4, &indices[0]);
free(vertex_positions);
```

## <a name="creating-an-image-from-depth-and-color"></a><span data-ttu-id="346d1-155">깊이 색에서 이미지 만들기</span><span class="sxs-lookup"><span data-stu-id="346d1-155">Creating an Image From Depth and Color</span></span>

![](img/ColorandDepthSmall.png)

<span data-ttu-id="346d1-156">색을 손쉽게 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="346d1-156">With colors, this is much easier to do!</span></span> <span data-ttu-id="346d1-157">여기에서 간단한 페이드 거리 검정으로 작업을 수행 하지만 모든 종류의 사진 관리 도구에서 마스크로 사용 하기 위해 알파 채널의 깊이 저장 하거나 특정 깊이 범위 아웃 클리핑와 같은 흥미로운 작업을 수행할 수 있습니다!</span><span class="sxs-lookup"><span data-stu-id="346d1-157">Here, we'll do a simple fade to black in the distance, but you could do all sorts of interesting things, like clipping out certain depth ranges, or storing depth in the alpha channel for use as a mask in a photo manipulation tool!</span></span>

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

## <a name="cleaning-up"></a><span data-ttu-id="346d1-158">정리</span><span class="sxs-lookup"><span data-stu-id="346d1-158">Cleaning Up</span></span>

<span data-ttu-id="346d1-159">항상 릴리스 모두 완료 되 면:) 및</span><span class="sxs-lookup"><span data-stu-id="346d1-159">And as always, release everything when you're finished :)</span></span>

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

# <a name="full-source"></a><span data-ttu-id="346d1-160">전체 소스</span><span class="sxs-lookup"><span data-stu-id="346d1-160">Full Source</span></span>

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

## <a name="next-lab---accessing-the-imuusingimumd"></a><span data-ttu-id="346d1-161">다음 랩- [는 IMU 액세스](UsingIMU.md)</span><span class="sxs-lookup"><span data-stu-id="346d1-161">Next Lab - [Accessing the IMU](UsingIMU.md)</span></span>