# <a name="reading-depth-data"></a>깊이 데이터 읽기

장치에서 깊이 데이터를 읽을 필요 합니까? 쉬워요!

**내용**  
[장치 구성](#Configuring-the-Device)  
[메트로 깊이 데이터](#Acessing-Depth-Data)  
[정리](#Cleaning-Up)  
[전체 소스](#Full-Source)  

**사용 하 여 함수는 다음과 같습니다.**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a>장치 구성

이후에 [인터페이스를 열고]() Azure Kinect DK 장치로 카메라 깊이 데이터 캡처를 구성 해야 합니다. 하나의 항목이 실제로 깊이 구성할 때 알아야 할 것을 `depth_mode`!

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

여기서는 `depth_mode` 몇 가지 선택할 수 있습니다. 응용 프로그램의 컨텍스트에 따라 다양 한 형식의 깊이 데이터 요청 수 있습니다.

깊이 데이터에서 시간이 제한 알고리즘을 실행 중인 있습니다? 적은 양의 데이터에 적용할 이므로 2X2BINNED 모드를 선택할 수 있습니다. 확인 하는 보다 훨씬 란 직접 out 주변에 닫기 란 대신 미리? 좁은 시야를 사용 하 여 NFOV 모드를 사용 하 여!
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | description |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|와이드 각도 보기 (120x120) 단순 깊이 (0.25-2.21 m), 높은 데이터 확인 (1024 x 1024)입니다. 15을 최대 프레임 속도 있습니다.|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|와이드 각도 보기 (120x120) 단순 깊이 (0.25-2.88 m), 낮은 데이터 확인 (512 x 512).|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|좁은 각도 보기 (75 x 65) 먼 깊이 (0.5-3.86 m), 높은 데이터 확인 (640 x 576)입니다.|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|좁은 각도 보기 (75 x 65) 먼 깊이 (0.5-5.46 m), 낮은 데이터 확인 (320 x 288)입니다.|
|`K4A_DEPTH_MODE_PASSIVE_IR`|원시 IR 카메라 (1024x1024)에서 피드|
||깊이 반사 개체에 따라 지정 된 범위 외부에서 제공 됩니다.|

## <a name="acessing-depth-data"></a>메트로 깊이 데이터

![](img/Depth.png)

장치에서 프레임을 캡처하려면 우리가 하는 경우 사용할 수 있습니다 `k4a_capture_get_depth_image` 및 `k4a_image_get_buffer` 깊이 원시 데이터를 가져옵니다.

```C
// Capture a frame
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the depth data and information from the current capture
k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
int32_t width  = k4a_image_get_width_pixels (depth_image);
int32_t height = k4a_image_get_height_pixels(depth_image);
```

자세한 내용은 (밀리미터 단위)를에서 나타내는 부호 없는 16 비트 정수의 배열로 제공 됩니다. 배열 수준 값을 특정 픽셀에 없는 경우 0을 유지 됩니다.

이 예에서는 방금 농도 데이터가 회색조 이미지를 변환 하 고 파일에 저장!

```C
// Write this depth capture to an image file

// Allocate memory for an 8-bit grayscale image
uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

// Convert each depth value to a shade of gray!
for (int32_t i = 0; i < width*height; i++)
{
    // Make a gray from the depth, white up close, black at 3 meters in the distance
    float depth_gray = 1-(depth_buffer[i] / 3000.0f);
    // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
    depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

    file_color[i] = static_cast<uint8_t>(depth_gray * 255);
}
tga_write("outDepth.tga", width, height, file_color, 1, 3);
free(file_color);
```

## <a name="cleaning-up"></a>정리

종료 및 할당 했거나 놓은 모든 릴리스를 잊지 말고 하세요! 상호 및 다른 프레임을 잡기 전에 완료 후 프레임 캡처를 해제 해야 해야 합니다.

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>전체 소스

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 1024x1024 wide FOV at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_5;
    config.depth_mode = K4A_DEPTH_MODE_WFOV_UNBINNED;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the depth data and information from the current capture
    k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
    uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
    int32_t width  = k4a_image_get_width_pixels (depth_image);
    int32_t height = k4a_image_get_height_pixels(depth_image);
    printf("Captured depth image, %dx%d\n", width, height);

    // Write this depth capture to an image file

    // Allocate memory for an 8-bit grayscale image
    uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

    // Convert each depth value to a shade of gray!
    for (int32_t i = 0; i < width*height; i++)
    {
        // Make a gray from the depth, white up close, black at 3 meters in the distance
        float depth_gray = 1-(depth_buffer[i] / 3000.0f);
        // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
        depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

        file_color[i] = static_cast<uint8_t>(depth_gray * 255);
    }
    tga_write("outDepth.tga", width, height, file_color, 1, 3);
    free(file_color);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(depth_image);
    k4a_capture_release(capture);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width % 256, (uint8_t)(width / 256), height % 256, (uint8_t)(height / 256), file_channels * 8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---reading-rgb-datareadcolormd"></a>다음 랩- [RGB 데이터 읽기](ReadColor.md)