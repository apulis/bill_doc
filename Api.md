<!-- Generator: Widdershins v4.0.1 -->

<h1 id="bill-api">Bill API v0.1.0</h1>

## Meta Data

- Usage Type

  | name | desc |
  | ------- | ------- |
  | cpu | The usage of CPU, unit m |
  | mem | The usage of memory, unit Mi |
  | gpu | The usage of GPU, unit number |
  | npu | The usage of NPU, unit number |

<h1 id="bill-api">Bill API v0.1.0</h1>

<!-- > Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu. -->

<h1 id="bill-api-bills">Bills</h1>

## Get Bill List

<a id="opIdGet Bill List"></a>

`GET /api/Bills`

<h3>Code samples</h3>

```shell
curl -X GET /api/Bills \
  -H 'Accept: text/plain'

```

<h3 id="get-bill-list-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|userId|query|string(uuid)|false|User Id|
|type|query|string|false|Usage Type like cpu, mem, gpu, npu etc.|

<h3 id="get-bill-list-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the bill list|Inline|

<h3 id="get-bill-list-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[BillItem](#schemabillitem)]|false|none|none|
|» id|string(uuid)|false|none|Bill Id|
|» startTime|string(date-time)|false|none|Start time, utc format|
|» endTime|string(date-time)|false|none|End time, utc format|
|» jobId|string¦null|false|none|Job Id|
|» jobName|string¦null|false|none|Job name|
|» userId|string(uuid)|false|none|User Id|
|» username|string¦null|false|none|Username|
|» vcName|string¦null|false|none|The name of virtual cluster|
|» type|string¦null|false|none|Usage type, cpu, mem, gpu, npu|
|» node|string¦null|false|none|The IP of the node where job runs on|
|» device|string¦null|false|none|Device model|
|» quota|number(double)|false|none|Device quota, CPU unit - m, Memory unit - Mi, GPU/NPU unit - number|
|» usage|number(double)|false|none|Sum of the resource usage, using hour as unit|
|» fee|number(double)|false|none|Fee|
|» isRunning|boolean|false|none|Whether the job is still running|

<aside class="success">
This operation does not require authentication now
</aside>

<h1 id="bill-api-ratios">Ratios</h1>

## Get Ratio List

<a id="opIdGet Ratio List"></a>

`GET /api/Ratios`

<h3>Code samples</h3>

```shell
curl -X GET /api/Ratios \
  -H 'Accept: text/plain'

```

<h3 id="get-ratio-list-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|

<h3 id="get-ratio-list-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[RatioInfo](#schemaratioinfo)]|false|none|none|
|» key|string¦null|false|none|Metrics or usage Type|
|» value|number(double)|false|none|The ratio value|

<aside class="success">
This operation does not require authentication now
</aside>

## Create Ratio

<a id="opIdCreate Ratio"></a>

`POST /api/Ratios`

<h3>Code samples</h3>

```shell
curl -X POST /api/Ratios \
  -H 'Content-Type: application/json'

```

> Body parameter

```json
{
  "type": "object",
  "properties": {
    "key": {
      "type": "string",
      "description": "Metrics or usage Type",
      "nullable": true
    },
    "value": {
      "type": "number",
      "description": "The ratio value",
      "format": "double"
    }
  },
  "additionalProperties": false
}
```

<h3 id="create-ratio-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[RatioInfo](#schemaratioinfo)|false|The ratio form|

<h3 id="create-ratio-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|

<aside class="success">
This operation does not require authentication now
</aside>

## Delete Ratio

<a id="opIdDelete Ratio"></a>

`DELETE /api/Ratios/{key}`

<h3>Code samples</h3>

```shell
curl -X DELETE /api/Ratios/{key} \
  -H 'Accept: text/plain'

```

<h3 id="delete-ratio-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|key|path|string|true|Metrics or usage Type|

<h3 id="delete-ratio-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|string|

<aside class="success">
This operation does not require authentication now
</aside>

<h1 id="bill-api-usages">Usages</h1>

## Get Usage List

<a id="opIdGet Usage List"></a>

`GET /api/Usages`

<h3>Code samples</h3>

```shell
curl -X GET /api/Usages \
  -H 'Accept: text/plain'

```

<h3 id="get-usage-list-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|userId|query|string(uuid)|false|User Id|
|type|query|string|false|Usage Type like cpu, mem, gpu, npu etc.|

<h3 id="get-usage-list-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the usage list|Inline|

<h3 id="get-usage-list-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[UsageItem](#schemausageitem)]|false|none|none|
|» id|string(uuid)|false|none|Usage Id|
|» startTime|string(date-time)|false|none|Start time, utc format|
|» endTime|string(date-time)|false|none|End time, utc format|
|» jobId|string¦null|false|none|Job Id|
|» jobName|string¦null|false|none|Job Name|
|» userId|string(uuid)|false|none|User Id|
|» username|string¦null|false|none|Username|
|» vcName|string¦null|false|none|The name of virtual cluster|
|» type|string¦null|false|none|Usage Type, cpu, mem, gpu, npu|
|» node|string¦null|false|none|The IP of the node where job runs on|
|» device|string¦null|false|none|Device model|
|» quota|number(double)|false|none|Device quota, CPU unit - m, Memory unit - Mi, GPU/NPU unit - number|
|» usage|number(double)|false|none|Sum of the resource usage, using hour as unit|
|» isRunning|boolean|false|none|Whether the job is still running|

<aside class="success">
This operation does not require authentication now
</aside>

<h1 id="bill-api-users">Users</h1>

## Get User List

<a id="opIdGet User List"></a>

`GET /api/Users`

<h3>Code samples</h3>

```shell
curl -X GET /api/Users \
  -H 'Accept: text/plain'

```

<h3 id="get-user-list-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the user list|Inline|

<h3 id="get-user-list-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[UserItem](#schemauseritem)]|false|none|none|
|» id|string(uuid)|false|none|none|
|» userName|string¦null|false|none|none|

<aside class="success">
This operation does not require authentication now
</aside>

# Schemas

<h2 id="tocS_BillItem">BillItem</h2>
<!-- backwards compatibility -->
<a id="schemabillitem"></a>
<a id="schema_BillItem"></a>
<a id="tocSbillitem"></a>
<a id="tocsbillitem"></a>

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Bill Id",
      "format": "uuid"
    },
    "startTime": {
      "type": "string",
      "description": "Start time, utc format",
      "format": "date-time"
    },
    "endTime": {
      "type": "string",
      "description": "End time, utc format",
      "format": "date-time"
    },
    "jobId": {
      "type": "string",
      "description": "Job Id",
      "nullable": true
    },
    "jobName": {
      "type": "string",
      "description": "Job name",
      "nullable": true
    },
    "userId": {
      "type": "string",
      "description": "User Id",
      "format": "uuid"
    },
    "username": {
      "type": "string",
      "description": "Username",
      "nullable": true
    },
    "vcName": {
      "type": "string",
      "description": "The name of virtual cluster",
      "nullable": true
    },
    "type": {
      "type": "string",
      "description": "Usage type, cpu, mem, gpu, npu",
      "nullable": true
    },
    "node": {
      "type": "string",
      "description": "The IP of the node where job runs on",
      "nullable": true
    },
    "device": {
      "type": "string",
      "description": "Device model",
      "nullable": true
    },
    "quota": {
      "type": "number",
      "description": "Device quota, CPU unit - m, Memory unit - Mi, GPU/NPU unit - number",
      "format": "double"
    },
    "usage": {
      "type": "number",
      "description": "Sum of the resource usage, using hour as unit",
      "format": "double"
    },
    "fee": {
      "type": "number",
      "description": "Fee",
      "format": "double"
    },
    "isRunning": {
      "type": "boolean",
      "description": "Whether the job is still running"
    }
  },
  "additionalProperties": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|Bill Id|
|startTime|string(date-time)|false|none|Start time, utc format|
|endTime|string(date-time)|false|none|End time, utc format|
|jobId|string¦null|false|none|Job Id|
|jobName|string¦null|false|none|Job name|
|userId|string(uuid)|false|none|User Id|
|username|string¦null|false|none|Username|
|vcName|string¦null|false|none|The name of virtual cluster|
|type|string¦null|false|none|Usage type, cpu, mem, gpu, npu|
|node|string¦null|false|none|The IP of the node where job runs on|
|device|string¦null|false|none|Device model|
|quota|number(double)|false|none|Device quota, CPU unit - m, Memory unit - Mi, GPU/NPU unit - number|
|usage|number(double)|false|none|Sum of the resource usage, using hour as unit|
|fee|number(double)|false|none|Fee|
|isRunning|boolean|false|none|Whether the job is still running|

<h2 id="tocS_RatioInfo">RatioInfo</h2>
<!-- backwards compatibility -->
<a id="schemaratioinfo"></a>
<a id="schema_RatioInfo"></a>
<a id="tocSratioinfo"></a>
<a id="tocsratioinfo"></a>

```json
{
  "type": "object",
  "properties": {
    "key": {
      "type": "string",
      "description": "Metrics or usage Type",
      "nullable": true
    },
    "value": {
      "type": "number",
      "description": "The ratio value",
      "format": "double"
    }
  },
  "additionalProperties": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|string¦null|false|none|Metrics or usage Type|
|value|number(double)|false|none|The ratio value|

<h2 id="tocS_UsageItem">UsageItem</h2>
<!-- backwards compatibility -->
<a id="schemausageitem"></a>
<a id="schema_UsageItem"></a>
<a id="tocSusageitem"></a>
<a id="tocsusageitem"></a>

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Usage Id",
      "format": "uuid"
    },
    "startTime": {
      "type": "string",
      "description": "Start time, utc format",
      "format": "date-time"
    },
    "endTime": {
      "type": "string",
      "description": "End time, utc format",
      "format": "date-time"
    },
    "jobId": {
      "type": "string",
      "description": "Job Id",
      "nullable": true
    },
    "jobName": {
      "type": "string",
      "description": "Job Name",
      "nullable": true
    },
    "userId": {
      "type": "string",
      "description": "User Id",
      "format": "uuid"
    },
    "username": {
      "type": "string",
      "description": "Username",
      "nullable": true
    },
    "vcName": {
      "type": "string",
      "description": "The name of virtual cluster",
      "nullable": true
    },
    "type": {
      "type": "string",
      "description": "Usage Type, cpu, mem, gpu, npu",
      "nullable": true
    },
    "node": {
      "type": "string",
      "description": "The IP of the node where job runs on",
      "nullable": true
    },
    "device": {
      "type": "string",
      "description": "Device model",
      "nullable": true
    },
    "quota": {
      "type": "number",
      "description": "Device quota, CPU unit - m, Memory unit - Mi, GPU/NPU unit - number",
      "format": "double"
    },
    "usage": {
      "type": "number",
      "description": "Sum of the resource usage, using hour as unit",
      "format": "double"
    },
    "isRunning": {
      "type": "boolean",
      "description": "Whether the job is still running"
    }
  },
  "additionalProperties": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|Usage Id|
|startTime|string(date-time)|false|none|Start time, utc format|
|endTime|string(date-time)|false|none|End time, utc format|
|jobId|string¦null|false|none|Job Id|
|jobName|string¦null|false|none|Job Name|
|userId|string(uuid)|false|none|User Id|
|username|string¦null|false|none|Username|
|vcName|string¦null|false|none|The name of virtual cluster|
|type|string¦null|false|none|Usage Type, cpu, mem, gpu, npu|
|node|string¦null|false|none|The IP of the node where job runs on|
|device|string¦null|false|none|Device model|
|quota|number(double)|false|none|Device quota, CPU unit - m, Memory unit - Mi, GPU/NPU unit - number|
|usage|number(double)|false|none|Sum of the resource usage, using hour as unit|
|isRunning|boolean|false|none|Whether the job is still running|

<h2 id="tocS_UserItem">UserItem</h2>
<!-- backwards compatibility -->
<a id="schemauseritem"></a>
<a id="schema_UserItem"></a>
<a id="tocSuseritem"></a>
<a id="tocsuseritem"></a>

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "format": "uuid"
    },
    "userName": {
      "type": "string",
      "nullable": true
    }
  },
  "additionalProperties": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|userName|string¦null|false|none|none|

