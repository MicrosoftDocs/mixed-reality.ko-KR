# <a name="reading-rgb-data"></a>RGB 데이터 읽기

**내용**  
[장치 구성](#Configuring-the-Device)  
[색 프레임 가져오기](#Getting-a-Color-Frame)  
[정리](#Cleaning-Up)  
[전체 소스](#Full-Source)  

**사용 하 여 함수는 다음과 같습니다.**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a>장치 구성

한 후 [열려는 k4a 장치](), 색 데이터를 가져오는 데이 카메라를 설정 해야 했습니다! 경우는 많은 옵션 여기 에서도 통해 서 모양을 실제로 기본 색 카메라 시작의 간단한 예제는 다음과 같습니다.

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

`color_format` 이미지 버퍼에 저장 하 여 색 정보 원하는 말할 수 있습니다. `K4A_IMAGE_FORMAT_COLOR_BGRA32` 파랑, 녹색, 빨강 및 알파 각각 8 비트가으로 저장, 픽셀당 32 비트는 것입니다. 해당 편의상 인해 예제에서이 형식을 사용 하 여 하 있지만 concious 메모리 사용량이 수 하려는 다른 형식 탁월한 선택 될 수 있습니다!

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|색 데이터 됩니다 [동작 JPEG 형식](https://en.wikipedia.org/wiki/Motion_JPEG)|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|[YUV](https://en.wikipedia.org/wiki/YUV) 색 공간 4:2:0 형식, NV12 720p 해상도로 사용할 수 있습니다.|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|[YUV](https://en.wikipedia.org/wiki/YUV) 색 공간 4:2:2 형식으로 YUY2 720p 해상도로 사용할 수 있습니다.|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|알파, 빨강, 녹색, 파란색으로, 픽셀당 32 비트 원시 색 데이터 정렬|

작성 하는 동안 사용자가 직접 YUV 변환의 않을 쉽지만 빠르고 강력한 라이브러리 YUV 변환에서 확인할 수 있습니다 [libyuv](https://chromium.googlesource.com/libyuv/libyuv/)합니다.

`color_resolution` 몇 가지 옵션이 있습니다.

|`color_resolution`|해결 방법|측면|보기 필드| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | 1280 x 720  | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1080P` | 1920 x 1080 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1440P` | 2560 x 1440 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_2160P` | 3840 x 2160 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1536P` | 2048 x 1536 | 4:3  | 90x74.3 
|`K4A_COLOR_RESOLUTION_3072P` | 4096 x 3072 | 4:3  | 90x74.3 | 최대 프레임 속도가 15입니다.

물론는 `camera_fps` 도 합니다.

|camera_fps||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a>색 프레임 가져오기

색 프레임 및 깊이 프레임에 대 한 데이터를 가져오는 매우 유사한 프로세스입니다. 먼저 장치에서 캡처를 얻게 하 고 색 이미지에서 추출한 다음 해당 이미지에서 원시 데이터를 가져옵니다.

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the color data and information from the current capture
k4a_image_t colors      = k4a_capture_get_color_image(capture);
uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
int width  = k4a_image_get_width_pixels (colors);
int height = k4a_image_get_height_pixels(colors);

// Write this capture to file
tga_write("out.tga", width, height, colorDataBGRA, 4, 3);
```

이제 저장 된 데이터 `colorDataBRGA` 는 구성에서 지정 하는 형식에 따라 달라 집니다. 묻는 것 이므로 `K4A_IMAGE_FORMAT_COLOR_BGRA32`, 배열에에서 저장 된 BGRA 32 비트 색 값의 전체 했습니다 order!

이 경우.tga 파일 저장 색 주문 BGR 이미! 및 이미지 데이터를 그대로 전달할 수 있으며 저장 함수를 이러한 인수를 사용 하 여 알파 채널을 건너뛸 수, 있으므로!

## <a name="cleaning-up"></a>정리

하 고 항상으로 완료 되 면 리소스를 해제 하려면!
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a>전체 소스

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main() {
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure a stream of 1280x720 BRGA data at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the color data and information from the current capture
    k4a_image_t colors      = k4a_capture_get_color_image(capture);
    uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
    int width  = k4a_image_get_width_pixels (colors);
    int height = k4a_image_get_height_pixels(colors);
    printf("Captured RGB image, %dx%d\n", width, height);

    // Write this capture to file
    tga_write("out.tga", width, height, colors_bgra, 4, 3);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(colors);
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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a>다음 랩- [색과 농도 데이터가 혼합](MixDepthAndRGB.md)