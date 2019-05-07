# <a name="reading-depth-data"></a><span data-ttu-id="c7ee4-101">깊이 데이터 읽기</span><span class="sxs-lookup"><span data-stu-id="c7ee4-101">Reading Depth Data</span></span>

<span data-ttu-id="c7ee4-102">장치에서 깊이 데이터를 읽을 필요 합니까?</span><span class="sxs-lookup"><span data-stu-id="c7ee4-102">Need to read depth data from the device?</span></span> <span data-ttu-id="c7ee4-103">쉬워요!</span><span class="sxs-lookup"><span data-stu-id="c7ee4-103">It's easy!</span></span>

<span data-ttu-id="c7ee4-104">**내용**</span><span class="sxs-lookup"><span data-stu-id="c7ee4-104">**Contents**</span></span>  
[<span data-ttu-id="c7ee4-105">장치 구성</span><span class="sxs-lookup"><span data-stu-id="c7ee4-105">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="c7ee4-106">메트로 깊이 데이터</span><span class="sxs-lookup"><span data-stu-id="c7ee4-106">Acessing Depth Data</span></span>](#Acessing-Depth-Data)  
[<span data-ttu-id="c7ee4-107">정리</span><span class="sxs-lookup"><span data-stu-id="c7ee4-107">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="c7ee4-108">전체 소스</span><span class="sxs-lookup"><span data-stu-id="c7ee4-108">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="c7ee4-109">**사용 하 여 함수는 다음과 같습니다.**</span><span class="sxs-lookup"><span data-stu-id="c7ee4-109">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a><span data-ttu-id="c7ee4-110">장치 구성</span><span class="sxs-lookup"><span data-stu-id="c7ee4-110">Configuring the Device</span></span>

<span data-ttu-id="c7ee4-111">이후에 [인터페이스를 열고]() Azure Kinect DK 장치로 카메라 깊이 데이터 캡처를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-111">After [opening an interface]() to the Azure Kinect DK device, you'll need to configure the camera for capturing depth data.</span></span> <span data-ttu-id="c7ee4-112">하나의 항목이 실제로 깊이 구성할 때 알아야 할 것을 `depth_mode`!</span><span class="sxs-lookup"><span data-stu-id="c7ee4-112">There's only one item you really need to know about when configuring depth, and that's the `depth_mode`!</span></span>

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="c7ee4-113">여기서는 `depth_mode` 몇 가지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-113">Here the `depth_mode` has a couple choices!</span></span> <span data-ttu-id="c7ee4-114">응용 프로그램의 컨텍스트에 따라 다양 한 형식의 깊이 데이터 요청 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-114">Depending on the context of our application, we can request our depth data in different formats.</span></span>

<span data-ttu-id="c7ee4-115">깊이 데이터에서 시간이 제한 알고리즘을 실행 중인 있습니다?</span><span class="sxs-lookup"><span data-stu-id="c7ee4-115">Are you running time constrained algorithms on the depth data?</span></span> <span data-ttu-id="c7ee4-116">적은 양의 데이터에 적용할 이므로 2X2BINNED 모드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-116">Maybe pick a 2X2BINNED mode so there's less data to operate on!</span></span> <span data-ttu-id="c7ee4-117">확인 하는 보다 훨씬 란 직접 out 주변에 닫기 란 대신 미리?</span><span class="sxs-lookup"><span data-stu-id="c7ee4-117">Do you care more about what's far out directly ahead, rather than what's close and in the periphery?</span></span> <span data-ttu-id="c7ee4-118">좁은 시야를 사용 하 여 NFOV 모드를 사용 하 여!</span><span class="sxs-lookup"><span data-stu-id="c7ee4-118">Use a narrow field of view with the NFOV modes!</span></span>
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | <span data-ttu-id="c7ee4-119">description</span><span class="sxs-lookup"><span data-stu-id="c7ee4-119">description</span></span> |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|<span data-ttu-id="c7ee4-120">와이드 각도 보기 (120x120) 단순 깊이 (0.25-2.21 m), 높은 데이터 확인 (1024 x 1024)입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-120">Wide angle view (120x120), shallow depth (0.25-2.21m), high data resolution (1024x1024).</span></span> <span data-ttu-id="c7ee4-121">15을 최대 프레임 속도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-121">Has a maximum framerate of 15.</span></span>|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|<span data-ttu-id="c7ee4-122">와이드 각도 보기 (120x120) 단순 깊이 (0.25-2.88 m), 낮은 데이터 확인 (512 x 512).</span><span class="sxs-lookup"><span data-stu-id="c7ee4-122">Wide angle view (120x120), shallow depth (0.25-2.88m), low data resolution (512x512).</span></span>|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|<span data-ttu-id="c7ee4-123">좁은 각도 보기 (75 x 65) 먼 깊이 (0.5-3.86 m), 높은 데이터 확인 (640 x 576)입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-123">Narrow angle view (75x65), far depth (0.5-3.86m), high data resolution (640x576).</span></span>|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|<span data-ttu-id="c7ee4-124">좁은 각도 보기 (75 x 65) 먼 깊이 (0.5-5.46 m), 낮은 데이터 확인 (320 x 288)입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-124">Narrow angle view (75x65), far depth (0.5-5.46m), low data resolution (320x288).</span></span>|
|`K4A_DEPTH_MODE_PASSIVE_IR`|<span data-ttu-id="c7ee4-125">원시 IR 카메라 (1024x1024)에서 피드</span><span class="sxs-lookup"><span data-stu-id="c7ee4-125">Raw feed from the IR camera (1024x1024)</span></span>|
||<span data-ttu-id="c7ee4-126">깊이 반사 개체에 따라 지정 된 범위 외부에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-126">Depth will be provided outside of indicated range depending on object reflectivity.</span></span>|

## <a name="acessing-depth-data"></a><span data-ttu-id="c7ee4-127">메트로 깊이 데이터</span><span class="sxs-lookup"><span data-stu-id="c7ee4-127">Acessing Depth Data</span></span>

![](img/Depth.png)

<span data-ttu-id="c7ee4-128">장치에서 프레임을 캡처하려면 우리가 하는 경우 사용할 수 있습니다 `k4a_capture_get_depth_image` 및 `k4a_image_get_buffer` 깊이 원시 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-128">When we capture a frame from the device, we can use `k4a_capture_get_depth_image` and `k4a_image_get_buffer` to get the raw depth data!</span></span>

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

<span data-ttu-id="c7ee4-129">자세한 내용은 (밀리미터 단위)를에서 나타내는 부호 없는 16 비트 정수의 배열로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-129">Depth information is provided as an array of unsigned 16 bit integers, representing millimeters from the camera.</span></span> <span data-ttu-id="c7ee4-130">배열 수준 값을 특정 픽셀에 없는 경우 0을 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-130">The array will hold a zero if the depth value isn't present for a particular pixel.</span></span>

<span data-ttu-id="c7ee4-131">이 예에서는 방금 농도 데이터가 회색조 이미지를 변환 하 고 파일에 저장!</span><span class="sxs-lookup"><span data-stu-id="c7ee4-131">In this example, we'll just convert the depth data into a grayscale image, and save it to file!</span></span>

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

## <a name="cleaning-up"></a><span data-ttu-id="c7ee4-132">정리</span><span class="sxs-lookup"><span data-stu-id="c7ee4-132">Cleaning Up</span></span>

<span data-ttu-id="c7ee4-133">종료 및 할당 했거나 놓은 모든 릴리스를 잊지 말고 하세요!</span><span class="sxs-lookup"><span data-stu-id="c7ee4-133">Remember to shut down and release everything you've allocated or grabbed!</span></span> <span data-ttu-id="c7ee4-134">상호 및 다른 프레임을 잡기 전에 완료 후 프레임 캡처를 해제 해야 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ee4-134">Remember that frame captures should be freed after you're finished with them and before grabbing another frame.</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="c7ee4-135">전체 소스</span><span class="sxs-lookup"><span data-stu-id="c7ee4-135">Full Source</span></span>

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

## <a name="next-lab---reading-rgb-datareadcolormd"></a><span data-ttu-id="c7ee4-136">다음 랩- [RGB 데이터 읽기](ReadColor.md)</span><span class="sxs-lookup"><span data-stu-id="c7ee4-136">Next Lab - [Reading RGB Data](ReadColor.md)</span></span>