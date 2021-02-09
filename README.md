# API Doc version 0.1.0

## Meta Data

- Metrics/Usage Type

  | name | desc |
  | ------- | ------- |
  | cpu_percent | The usage percent of CPU |
  | mem_byte | The usage bytes of memory |
  | mem_percent | The usage percent of memory |
  | gpu_percent | The usage percent GPU |
  | gpu_mem_percent | The memory usage percent of GPU |
  | npu_percent | The usage percent NPU |
  | npu_mem_percent | The memory usage percent of NPU |


## Bills

- Get bill list

  **GET** /api/Bills

  Request:
  
  | key | from | required | type | desc |
  | ------- | ------- | ------- | ------- | ------- |
  | user | query | N | string | The username |
  | type | query | N | string |  Usage Type like cpu_percent, mem_percent etc. | 
  
  Response:
  
  | name | type | desc |
  | ------- | ------- | ------- |
  | id | uuid | Bill Id |
  | startTime | datetime | Start time, utc format |
  | endTime | datetime | End time, utc format |
  | jobId | uuid | Job Id |
  | jobName | string | Job Name |
  | username | string | Username |
  | vcName | string | The name of virtual cluster |
  | type | string | Metrics or usage Type |
  | node | string | The IP of the node where job runs on |
  | device | string | Device model |
  | deviceId | string | Device Id, like GPU Id or NPU Id |
  | usage | double | Usage between start time and end time |
  | fee | double | Fee between start time and end time |
   
  Example:
  
  /api/Bills?user=admin&type=cpu_percent
  
  ```
  [
    {
        "id":"cad0fbbf-039c-4761-b188-2d2d41fe542a",
        "startTime":"2021-02-09T08:00:00",
        "endTime":"2021-02-09T08:59:59",
        "jobId":"6ab46d21-a0ab-4515-981c-f1f2420017d0",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"cpu_percent",
        "node":"192.168.1.212",
        "device":"Intel(R) Core(TM) i7-9700 CPU @ 3.00GHz",
        "deviceId":null,
        "usage":0.7749166666666668,
        "fee":7.749166666666668
    },
    {
        "id":"6c222247-f48c-495e-96e5-3e34690fb40d",
        "startTime":"2021-02-09T07:00:00",
        "endTime":"2021-02-09T07:59:59",
        "jobId":"6ab46d21-a0ab-4515-981c-f1f2420017d0",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"cpu_percent",
        "node":"192.168.1.212",
        "device":"Intel(R) Core(TM) i7-9700 CPU @ 3.00GHz",
        "deviceId":null,
        "usage":0.7663333333333335,
        "fee":7.663333333333336
    }
  ]
  ```
  
  /api/Bills
  ```
  [
  {
        "id":"aa50adb9-7712-405b-a544-af0179d4b783",
        "startTime":"2021-02-06T04:00:00",
        "endTime":"2021-02-06T04:59:59",
        "jobId":"f62d8712-c25d-4d82-a575-f523765aad5a",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"cpu_percent",
        "node":"192.168.1.212",
        "device":"Intel(R) Core(TM) i7-9700 CPU @ 3.00GHz",
        "deviceId":null,
        "usage":0.6886363636363637,
        "fee":6.886363636363637
    },
    {
        "id":"349811ad-1bd4-4e28-8b2d-b29b4ab57d80",
        "startTime":"2021-02-06T04:00:00",
        "endTime":"2021-02-06T04:59:59",
        "jobId":"e710f8a0-bd77-49aa-aa41-c1a4a4cb2715",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"gpu_mem_percent",
        "node":"192.168.1.212",
        "device":"GeForce RTX 2070",
        "deviceId":"GPU-47ceca12-1ca0-c019-34e2-97cbd6f2e41e",
        "usage":74.30468554247057,
        "fee":3715.234277123528
    },
    {
        "id":"88fb0aca-591a-4556-8a83-abb5a490f6d8",
        "startTime":"2021-02-06T04:00:00",
        "endTime":"2021-02-06T04:59:59",
        "jobId":"2854838b-d1ed-407b-8b21-4dc059f9fbc1",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"gpu_mem_percent",
        "node":"192.168.1.212",
        "device":"GeForce RTX 2070",
        "deviceId":"GPU-47ceca12-1ca0-c019-34e2-97cbd6f2e41e",
        "usage":66.04860937108494,
        "fee":3302.430468554247
    },
    {
        "id":"4b421f88-aa4b-4d3e-8fca-ad158f73e3f1",
        "startTime":"2021-02-06T04:00:00",
        "endTime":"2021-02-06T04:59:59",
        "jobId":"e710f8a0-bd77-49aa-aa41-c1a4a4cb2715",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"gpu_percent",
        "node":"192.168.1.212",
        "device":"GeForce RTX 2070",
        "deviceId":"GPU-47ceca12-1ca0-c019-34e2-97cbd6f2e41e",
        "usage":17.5,
        "fee":1750
    },
    {
        "id":"89c54027-d7bf-4d6f-b1a8-2f15dd8f5213",
        "startTime":"2021-02-06T04:00:00",
        "endTime":"2021-02-06T04:59:59",
        "jobId":"2854838b-d1ed-407b-8b21-4dc059f9fbc1",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"gpu_percent",
        "node":"192.168.1.212",
        "device":"GeForce RTX 2070",
        "deviceId":"GPU-47ceca12-1ca0-c019-34e2-97cbd6f2e41e",
        "usage":20.666666666666668,
        "fee":2066.666666666667
    },
    {
        "id":"a05c6575-1eac-4374-9007-0c473abb5bbf",
        "startTime":"2021-02-06T04:00:00",
        "endTime":"2021-02-06T04:59:59",
        "jobId":"f62d8712-c25d-4d82-a575-f523765aad5a",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"mem_byte",
        "node":"192.168.1.212",
        "device":"Unknown",
        "deviceId":null,
        "usage":163308562.6181818,
        "fee":0
    },
    {
        "id":"8dc82d93-5b9c-4960-ba3d-6067878479b9",
        "startTime":"2021-02-06T04:00:00",
        "endTime":"2021-02-06T04:59:59",
        "jobId":"7b22c0ad-dd9d-49a8-9b9a-e158eec5297e",
        "jobName":"",
        "username":"admin",
        "vcName":"platform",
        "type":"mem_byte",
        "node":"192.168.1.212",
        "device":"Unknown",
        "deviceId":null,
        "usage":60483541.40160001,
        "fee":0
    }
  ]
  ```
