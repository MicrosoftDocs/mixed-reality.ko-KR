# <a name="accessing-the-imu"></a><span data-ttu-id="d42a9-101">IMU 액세스</span><span class="sxs-lookup"><span data-stu-id="d42a9-101">Accessing the IMU</span></span>

<span data-ttu-id="d42a9-102">관성 측정 단위 (IMU)를 포함 하는 azure Kinect DK!</span><span class="sxs-lookup"><span data-stu-id="d42a9-102">Azure Kinect DK contains an Inertial Measurement Unit (IMU)!</span></span> <span data-ttu-id="d42a9-103">이 동작 및 캡처하는 동안 장치의 방향을 결정 하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d42a9-103">This can be useful for helping to determine motion and orientation of the device during capture.</span></span> <span data-ttu-id="d42a9-104">특히 없으면 장치 고정!</span><span class="sxs-lookup"><span data-stu-id="d42a9-104">Especially if you device isn't stationary!</span></span>

<span data-ttu-id="d42a9-105">**콘텐츠:**</span><span class="sxs-lookup"><span data-stu-id="d42a9-105">**Contents:**</span></span>  
[<span data-ttu-id="d42a9-106">구성 및 설정</span><span class="sxs-lookup"><span data-stu-id="d42a9-106">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="d42a9-107">데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="d42a9-107">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="d42a9-108">정리</span><span class="sxs-lookup"><span data-stu-id="d42a9-108">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="d42a9-109">전체 소스</span><span class="sxs-lookup"><span data-stu-id="d42a9-109">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="d42a9-110">**사용 하 여 함수는 다음과 같습니다.**</span><span class="sxs-lookup"><span data-stu-id="d42a9-110">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-imu)  
[`k4a_device_stop_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-imu)  
[`k4a_device_get_imu_sample()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-imu-sample)  

## <a name="configuration-and-setup"></a><span data-ttu-id="d42a9-111">구성 및 설정</span><span class="sxs-lookup"><span data-stu-id="d42a9-111">Configuration and Setup</span></span>

<span data-ttu-id="d42a9-112">여기서의 구성은 매우 간단!</span><span class="sxs-lookup"><span data-stu-id="d42a9-112">Configuration here is pretty simple!</span></span> <span data-ttu-id="d42a9-113">지정 해야 하는 항목이 없는 IMU 장치 구성에서 샘플링 수 있지만 작업을 호출 해야 `k4a_device_start_cameras` 작동 됩니다!</span><span class="sxs-lookup"><span data-stu-id="d42a9-113">There are no items you need to specify the in the device configuration for IMU sampling to work, but you will need to call `k4a_device_start_cameras` before it'll work!</span></span> <span data-ttu-id="d42a9-114">대신 호출 해야 `k4a_device_start_imu` 이 카메라를 시작한 후입니다.</span><span class="sxs-lookup"><span data-stu-id="d42a9-114">Instead, you'll make a call to `k4a_device_start_imu` after starting the cameras.</span></span>

```C
// Cameras need to be 'started' even if all we want is the IMU
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
k4a_device_start_cameras(device, &config);

// Start up the IMU sensors
k4a_device_start_imu(device);
```

## <a name="getting-data"></a><span data-ttu-id="d42a9-115">데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="d42a9-115">Getting Data</span></span>

<span data-ttu-id="d42a9-116">![샘플 앱 이미지 IMU](img/IMU.png "같습니다. 예를 들어 빌드할 내용!")</span><span class="sxs-lookup"><span data-stu-id="d42a9-116">![IMU sample app image](img/IMU.png "Here's what we'll build as an example!")</span></span>

<span data-ttu-id="d42a9-117">IMU는 1.6 kHz의 속도로 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d42a9-117">The IMU provides data at a rate of 1.6kHz!</span></span> <span data-ttu-id="d42a9-118">데이터를 많이 있고 즉만 하려는 경우에 각 깊이/색 프레임 시간은 사용 가능한 기다리는 IMU 샘플의 큐가 있을 것!</span><span class="sxs-lookup"><span data-stu-id="d42a9-118">That's a lot of data, and this means that if you're only looking at it each time a depth/color frame is available, you'll likely have quite a queue of IMU samples waiting for you!</span></span> <span data-ttu-id="d42a9-119">이 데이터는 방향이 또는 위치 하지만 아니라 장치에 현재 적용 된 힘의 측정값을 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d42a9-119">Note that this data is not an orientation or position, but rather, a measure of the force currently applied to the device.</span></span>

<span data-ttu-id="d42a9-120">샘플을 잡고 호출 하 여 큐에서 제거할 수 있습니다 것 `k4a_device_get_imu_sample` 시간 제한은 0 시간 (밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="d42a9-120">We can grab a sample and remove it from the queue by calling `k4a_device_get_imu_sample` with a timeout of 0 milliseconds.</span></span> <span data-ttu-id="d42a9-121">반환 `K4A_WAIT_RESULT_SUCCEEDED` 사용할 수 있는 샘플 붙어 있다면!</span><span class="sxs-lookup"><span data-stu-id="d42a9-121">It'll return `K4A_WAIT_RESULT_SUCCEEDED` as long as it has a sample available!</span></span>

<span data-ttu-id="d42a9-122">현재 큐에 있는 모든 샘플을 구하고 평균 인쇄의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d42a9-122">Here's an example of summing all the samples currently in the queue, and printing the average.</span></span> 

```C
k4a_float3_t gyro_sum  = {0};
k4a_float3_t acc_sum   = {0};
int32_t      sum_count = 0;

// Sum the current queue of IMU samples
k4a_imu_sample_t sample;
while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
{
    gyro_sum.xyz = { 
        gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
        gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
        gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
    acc_sum.xyz = { 
        acc_sum.xyz.x + sample.acc_sample.xyz.x,  
        acc_sum.xyz.y + sample.acc_sample.xyz.y,  
        acc_sum.xyz.z + sample.acc_sample.xyz.z };
    sum_count += 1;
    samples   += 1;
}

// If we got any samples, print out their average!
if (sum_count > 0)
{
    k4a_float3_t gyro_avg = {
        gyro_sum.xyz.x / sum_count,
        gyro_sum.xyz.y / sum_count,
        gyro_sum.xyz.z / sum_count };
    k4a_float3_t acc_avg = {
        acc_sum.xyz.x / sum_count,
        acc_sum.xyz.y / sum_count,
        acc_sum.xyz.z / sum_count };

    printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
    printf("<%6.2f, %6.2f, %6.2f>", acc_avg.xyz.x, acc_avg.xyz.y, acc_avg.xyz.z);

    // Write backspaces so we'll overwrite this line next time
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
}
```

## <a name="cleaning-up"></a><span data-ttu-id="d42a9-123">정리</span><span class="sxs-lookup"><span data-stu-id="d42a9-123">Cleaning Up</span></span>

<span data-ttu-id="d42a9-124">항상 릴리스 모두 완료 되 면:) 및</span><span class="sxs-lookup"><span data-stu-id="d42a9-124">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_device_stop_imu(device);
k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="d42a9-125">전체 소스</span><span class="sxs-lookup"><span data-stu-id="d42a9-125">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Cameras need to be 'started' even if all we want is the IMU
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    k4a_device_start_cameras(device, &config);

    // Start up the IMU sensors
    k4a_device_start_imu(device);

    // Display 10,000 samples as fast as they arrive
    printf("Sampling 10,000 times.\n");
    printf("Gyroscope radians/s:       Accelerometer meters/s^2:\n");
    int32_t samples = 0;
    while (samples < 10000)
    {
        k4a_float3_t gyro_sum  = {0};
        k4a_float3_t accel_sum = {0};
        int32_t      sum_count = 0;

        // Sum the current queue of IMU samples
        k4a_imu_sample_t sample;
        while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
        {
            gyro_sum.xyz = { 
                gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
                gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
                gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
            accel_sum.xyz = { 
                accel_sum.xyz.x + sample.acc_sample.xyz.x,  
                accel_sum.xyz.y + sample.acc_sample.xyz.y,  
                accel_sum.xyz.z + sample.acc_sample.xyz.z };
            sum_count += 1;
            samples   += 1;
        }

        // If we got any samples this loop, print out their average!
        if (sum_count > 0)
        {
            k4a_float3_t gyro_avg = {
                gyro_sum.xyz.x / sum_count,
                gyro_sum.xyz.y / sum_count,
                gyro_sum.xyz.z / sum_count };
            k4a_float3_t accel_avg = {
                accel_sum.xyz.x / sum_count,
                accel_sum.xyz.y / sum_count,
                accel_sum.xyz.z / sum_count };

            printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
            printf("<%6.2f, %6.2f, %6.2f>", accel_avg.xyz.x, accel_avg.xyz.y, accel_avg.xyz.z);

            // Write backspaces so we'll overwrite this line next time
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
        }
    }
    printf("\nShutting down.\n");

    // Release all allocated resources, and shut down the Kinect
    k4a_device_stop_imu(device);
    k4a_device_stop_cameras(device);
    k4a_device_close(device);
}
```