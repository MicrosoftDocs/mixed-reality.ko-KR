# <a name="setting-up"></a>설정

Azure Kinect DK API를 사용 하 여 시작 할까요? 더 이상 찾지 않으셔도! 이 문서를 얻게 됩니다 및 실행 액세스를 사용 하 여 장치에!

첫째, 다운로드 및 설치 합니다 [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) Github에서.

**내용**  
[헤더](#Headers)  
[Kinect 장치 찾기](#Finding-a-Kinect-Device)  
[이 카메라를 시작합니다.](#Starting-the-Cameras)  
[오류 처리](#Error-Handling)  
[전체 소스](#Full-Source)  

**사용 하 여 함수는 다음과 같습니다.**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>헤더
해야 하는 하나의 헤더만 이며 k4a.h입니다! SDK의 라이브러리를 사용 하 여 선택한 컴파일러 설정 되어 있는지 확인 하 고 폴더를 포함 합니다. k4a.lib k4a.dll 파일과 연결 해야 합니다.
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>Kinect 장치 찾기

![](img/Serial.png)

여러 Azure Kinect DK 장치를 컴퓨터에 연결할 수 있습니다. 찾기 개수를 초과 하 여 먼저 먼저 않거나 전혀 사용 하 여 연결 된 모든 경우는 [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) 함수입니다. 이 함수는 추가 설정 없이 바로 작동 해야 합니다!

```C
uint32_t count = k4a_device_get_installed_count();
```

결정 한 후 있습니다를 실제로 장치를 연결할 컴퓨터를 사용 하 여를 열 수 있습니다 [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)합니다. 인덱스를 제공할 수 있습니다를 열려면 마우스 장치 또는 사용할 수 있습니다 [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) 첫 번째 웹 후크의 합니다.

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
으로 k4a api에서 대부분의 작업을 사용 하 여 무엇 인가 열면도 종료 해야이 사용 하 여 완료 되 면! 종료 하는 경우이를 호출 해야 [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)합니다.

```C
k4a_device_close(device);
```

장치를 열면 우리 모두 유용 하도록 쉽게 테스트를 가능 합니다. 장치의 일련 번호를 읽을 보겠습니다!

```C
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = static_cast<char*>(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

## <a name="starting-the-cameras"></a>이 카메라를 시작합니다.

사용 하 여 카메라를 구성 해야 장치를 연 후에 [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) 개체! 카메라 구성에는 다양 한 옵션을 많이 하 고 고유한 시나리오에 가장 잘 맞는 설정을 선택 해야 합니다.

```C
// Configure a stream of 4096x3072 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config)

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

에 대 한 구성 세부 정보를 __color__ 카메라 [이 문서를 체크 아웃]()!  
에 대 한 구성 세부 정보를 __깊이__ 카메라 [이 문서를 체크 아웃]()!

## <a name="error-handling"></a>오류 처리

간 결함 및 명확성을 위해에서는 인라인 예로의 오류 처리를 표시 하지 않습니다. 그러나 오류 처리는 항상 중요 한! 다양 한 함수는 일반적인 성공/실패 형식을 반환 [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), 또는 같은 구체적인 변형 마샬링과 세부 정보 [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t). 문서를 확인 해야 하거나 어떤 오류 메시지를 보려면 특정 함수의 intellisense에서 참조으로 예상할 수 있습니다!

오류 유형과 함께 이기도 합니다 [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) 하 고 [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) 으로 사용할 수 있는 매크로 합니다. 따라서 k4a 장치를 방금 열 대신 다음과 같이 보호 될 수 있습니다 것:

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>전체 소스

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

int main()
{
    uint32_t count = k4a_device_get_installed_count();
    if (count == 0)
    {
        printf("No k4a devices attached!\n");
        return 0;
    }

    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device)))
    {
        printf("Failed to open k4a device!\n");
        return 0;
    }

    // Get the size of the serial number
    size_t serial_size = 0;
    k4a_device_get_serialnum(device, NULL, &serial_size);

    // Allocate memory for the serial, then acquire it
    char* serial = static_cast<char*>(malloc(serial_size));
    k4a_device_get_serialnum(device, serial, &serial_size);
    printf("Opened device: %s\n", serial);
    free(serial);

    // Configure a stream of 4096x3072 BRGA color data at 15 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_15;
    config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

    // Start the camera with the given configuration
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
    {
        printf("Failed to start cameras!\n");
        k4a_device_close(device);
        return 0;
    }

    // ...Camera capture and application specific code would go here...

    // Shut down the camera when finished with application logic
    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}
```

## <a name="next-lab---reading-depth-datareaddepthmd"></a>다음 랩- [깊이 데이터 읽기](ReadDepth.md)
