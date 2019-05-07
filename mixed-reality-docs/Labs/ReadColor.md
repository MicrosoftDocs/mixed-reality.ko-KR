# <a name="reading-rgb-data"></a><span data-ttu-id="04de0-101">RGB 데이터 읽기</span><span class="sxs-lookup"><span data-stu-id="04de0-101">Reading RGB Data</span></span>

<span data-ttu-id="04de0-102">**내용**</span><span class="sxs-lookup"><span data-stu-id="04de0-102">**Contents**</span></span>  
[<span data-ttu-id="04de0-103">장치 구성</span><span class="sxs-lookup"><span data-stu-id="04de0-103">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="04de0-104">색 프레임 가져오기</span><span class="sxs-lookup"><span data-stu-id="04de0-104">Getting a Color Frame</span></span>](#Getting-a-Color-Frame)  
[<span data-ttu-id="04de0-105">정리</span><span class="sxs-lookup"><span data-stu-id="04de0-105">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="04de0-106">전체 소스</span><span class="sxs-lookup"><span data-stu-id="04de0-106">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="04de0-107">**사용 하 여 함수는 다음과 같습니다.**</span><span class="sxs-lookup"><span data-stu-id="04de0-107">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a><span data-ttu-id="04de0-108">장치 구성</span><span class="sxs-lookup"><span data-stu-id="04de0-108">Configuring the Device</span></span>

<span data-ttu-id="04de0-109">한 후 [열려는 k4a 장치](), 색 데이터를 가져오는 데이 카메라를 설정 해야 했습니다!</span><span class="sxs-lookup"><span data-stu-id="04de0-109">After [opening a k4a device](), we'll need to set up the cameras to grab color data!</span></span> <span data-ttu-id="04de0-110">경우는 많은 옵션 여기 에서도 통해 서</span><span class="sxs-lookup"><span data-stu-id="04de0-110">There's a lot of options here as well, so we'll go through them.</span></span> <span data-ttu-id="04de0-111">모양을 실제로 기본 색 카메라 시작의 간단한 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-111">Here's a quick example of what it looks like to start up a really basic color camera.</span></span>

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="04de0-112">`color_format` 이미지 버퍼에 저장 하 여 색 정보 원하는 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-112">The `color_format` allows us to say how we want our color information stored in the image buffer!</span></span> <span data-ttu-id="04de0-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` 파랑, 녹색, 빨강 및 알파 각각 8 비트가으로 저장, 픽셀당 32 비트는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` would be 32 bits per pixel, stored as 8 bits each for Blue, Green, Red, and Alpha.</span></span> <span data-ttu-id="04de0-114">해당 편의상 인해 예제에서이 형식을 사용 하 여 하 있지만 concious 메모리 사용량이 수 하려는 다른 형식 탁월한 선택 될 수 있습니다!</span><span class="sxs-lookup"><span data-stu-id="04de0-114">We use this format in the examples due to its convenience, but if you want to be concious of memory usage, other formats may be superior choices!</span></span>

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|<span data-ttu-id="04de0-115">색 데이터 됩니다 [동작 JPEG 형식](https://en.wikipedia.org/wiki/Motion_JPEG)</span><span class="sxs-lookup"><span data-stu-id="04de0-115">Color data will be in [Motion JPEG format](https://en.wikipedia.org/wiki/Motion_JPEG)</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|<span data-ttu-id="04de0-116">[YUV](https://en.wikipedia.org/wiki/YUV) 색 공간 4:2:0 형식, NV12 720p 해상도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-116">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:0 format, NV12, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|<span data-ttu-id="04de0-117">[YUV](https://en.wikipedia.org/wiki/YUV) 색 공간 4:2:2 형식으로 YUY2 720p 해상도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-117">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:2 format, YUY2, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|<span data-ttu-id="04de0-118">알파, 빨강, 녹색, 파란색으로, 픽셀당 32 비트 원시 색 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="04de0-118">Raw color data, 32 bits per pixel, ordered as Blue, Green, Red, Alpha</span></span>|

<span data-ttu-id="04de0-119">작성 하는 동안 사용자가 직접 YUV 변환의 않을 쉽지만 빠르고 강력한 라이브러리 YUV 변환에서 확인할 수 있습니다 [libyuv](https://chromium.googlesource.com/libyuv/libyuv/)합니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-119">While writing your own YUV conversion may be easy enough, a fast, robust library for YUV conversion can be found at [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span></span>

<span data-ttu-id="04de0-120">`color_resolution` 몇 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-120">The `color_resolution` also has a couple of options!</span></span>

|`color_resolution`|<span data-ttu-id="04de0-121">해결 방법</span><span class="sxs-lookup"><span data-stu-id="04de0-121">resolution</span></span>|<span data-ttu-id="04de0-122">측면</span><span class="sxs-lookup"><span data-stu-id="04de0-122">aspect</span></span>|<span data-ttu-id="04de0-123">보기 필드</span><span class="sxs-lookup"><span data-stu-id="04de0-123">field of view</span></span>| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | <span data-ttu-id="04de0-124">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="04de0-124">1280 x 720</span></span>  | <span data-ttu-id="04de0-125">16:9</span><span class="sxs-lookup"><span data-stu-id="04de0-125">16:9</span></span> | <span data-ttu-id="04de0-126">90x59</span><span class="sxs-lookup"><span data-stu-id="04de0-126">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1080P` | <span data-ttu-id="04de0-127">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="04de0-127">1920 x 1080</span></span> | <span data-ttu-id="04de0-128">16:9</span><span class="sxs-lookup"><span data-stu-id="04de0-128">16:9</span></span> | <span data-ttu-id="04de0-129">90x59</span><span class="sxs-lookup"><span data-stu-id="04de0-129">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1440P` | <span data-ttu-id="04de0-130">2560 x 1440</span><span class="sxs-lookup"><span data-stu-id="04de0-130">2560 x 1440</span></span> | <span data-ttu-id="04de0-131">16:9</span><span class="sxs-lookup"><span data-stu-id="04de0-131">16:9</span></span> | <span data-ttu-id="04de0-132">90x59</span><span class="sxs-lookup"><span data-stu-id="04de0-132">90x59</span></span>
|`K4A_COLOR_RESOLUTION_2160P` | <span data-ttu-id="04de0-133">3840 x 2160</span><span class="sxs-lookup"><span data-stu-id="04de0-133">3840 x 2160</span></span> | <span data-ttu-id="04de0-134">16:9</span><span class="sxs-lookup"><span data-stu-id="04de0-134">16:9</span></span> | <span data-ttu-id="04de0-135">90x59</span><span class="sxs-lookup"><span data-stu-id="04de0-135">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1536P` | <span data-ttu-id="04de0-136">2048 x 1536</span><span class="sxs-lookup"><span data-stu-id="04de0-136">2048 x 1536</span></span> | <span data-ttu-id="04de0-137">4:3</span><span class="sxs-lookup"><span data-stu-id="04de0-137">4:3</span></span>  | <span data-ttu-id="04de0-138">90x74.3</span><span class="sxs-lookup"><span data-stu-id="04de0-138">90x74.3</span></span> 
|`K4A_COLOR_RESOLUTION_3072P` | <span data-ttu-id="04de0-139">4096 x 3072</span><span class="sxs-lookup"><span data-stu-id="04de0-139">4096 x 3072</span></span> | <span data-ttu-id="04de0-140">4:3</span><span class="sxs-lookup"><span data-stu-id="04de0-140">4:3</span></span>  | <span data-ttu-id="04de0-141">90x74.3</span><span class="sxs-lookup"><span data-stu-id="04de0-141">90x74.3</span></span> | <span data-ttu-id="04de0-142">최대 프레임 속도가 15입니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-142">Max framerate 15.</span></span>

<span data-ttu-id="04de0-143">물론는 `camera_fps` 도 합니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-143">And of course, the `camera_fps` as well.</span></span>

|<span data-ttu-id="04de0-144">camera_fps</span><span class="sxs-lookup"><span data-stu-id="04de0-144">camera_fps</span></span>||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a><span data-ttu-id="04de0-145">색 프레임 가져오기</span><span class="sxs-lookup"><span data-stu-id="04de0-145">Getting a Color Frame</span></span>

<span data-ttu-id="04de0-146">색 프레임 및 깊이 프레임에 대 한 데이터를 가져오는 매우 유사한 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-146">Getting data for a color frame and a depth frame is a very similar process!</span></span> <span data-ttu-id="04de0-147">먼저 장치에서 캡처를 얻게 하 고 색 이미지에서 추출한 다음 해당 이미지에서 원시 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-147">First we get a capture from the device, then we extract the color image from it, and then we pull the raw data out of that image.</span></span>

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

<span data-ttu-id="04de0-148">이제 저장 된 데이터 `colorDataBRGA` 는 구성에서 지정 하는 형식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="04de0-148">The data now stored in `colorDataBRGA` is dependant on the format we indicated in configuration.</span></span> <span data-ttu-id="04de0-149">묻는 것 이므로 `K4A_IMAGE_FORMAT_COLOR_BGRA32`, 배열에에서 저장 된 BGRA 32 비트 색 값의 전체 했습니다 order!</span><span class="sxs-lookup"><span data-stu-id="04de0-149">Since we asked for `K4A_IMAGE_FORMAT_COLOR_BGRA32`, we have an array full of 32 bit color values stored in BGRA order!</span></span>

<span data-ttu-id="04de0-150">이 경우.tga 파일 저장 색 주문 BGR 이미!</span><span class="sxs-lookup"><span data-stu-id="04de0-150">In this case, .tga files store colors in BGR order already!</span></span> <span data-ttu-id="04de0-151">및 이미지 데이터를 그대로 전달할 수 있으며 저장 함수를 이러한 인수를 사용 하 여 알파 채널을 건너뛸 수, 있으므로!</span><span class="sxs-lookup"><span data-stu-id="04de0-151">And since our saving function can skip the alpha channel with these arguments, we can just pass the image data as is!</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="04de0-152">정리</span><span class="sxs-lookup"><span data-stu-id="04de0-152">Cleaning Up</span></span>

<span data-ttu-id="04de0-153">하 고 항상으로 완료 되 면 리소스를 해제 하려면!</span><span class="sxs-lookup"><span data-stu-id="04de0-153">And as always, remember to release your resources when you're done with them!</span></span>
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a><span data-ttu-id="04de0-154">전체 소스</span><span class="sxs-lookup"><span data-stu-id="04de0-154">Full Source</span></span>

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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a><span data-ttu-id="04de0-155">다음 랩- [색과 농도 데이터가 혼합](MixDepthAndRGB.md)</span><span class="sxs-lookup"><span data-stu-id="04de0-155">Next Lab - [Mixing Color and Depth Data](MixDepthAndRGB.md)</span></span>