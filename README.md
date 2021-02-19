# Bill

## Introduction

- The collectors will collect the metrics of a job in every 30 seconds, including:

  - Memory Usage
  - CPU Usage
  - GPU Usage
  - NPU Usage

- The calculator will calculate the usage in every hour. The fomula is `Usage = (SUM(metrics value) / metrics count) * use time`, and the use time usually equals to 1 excepts:

  - The job start time > the start time of an hour
  - The job end time < the end time of an hour
 
- The usage multiplying the ratio turn out to be the fee

## API Description
[API Document](Api.md)

## Bill Sample

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
