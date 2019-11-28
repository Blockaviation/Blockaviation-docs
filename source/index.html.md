---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  #- ruby
  #- python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>


includes:
  - errors

search: true
---

# Introduction

Welcome to the <b>Blockaviation API!</b> You can use our API to access the Blockaviation API endpoints, which can allow you to search, retrieve authenticated aircraft records for your application.

We have language bindings in Shell and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

For this beta version of the API we are focusing on search and retrieval of only:

<b>1)</b> EASA Form one's & FAA Form 8130-3

<b>2)</b> Engineering orders associated to specific airworthiness directives

# Authentication

> To authorize, use this code:

<!-- ```ruby
require 'blockav'

api = Blockav::APIClient.authorize!('PrepareForTakeOff')
```

```python
import blockav

api = blockav.authorize('PrepareForTakeOff')
``` -->

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: PrepareForTakeOff"
```

```javascript
const blockav = require('blockaviation');

let api = blockav.authorize('PrepareForTakeOff');
```

> Make sure to replace `PrepareForTakeOff` with your API key.

Blockaviation uses API keys to allow access to the API. You can register a new Blockaviation API key at our [developer portal](http://example.com/developers).

Blockaviation expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: PrepareForTakeOff`

<aside class="notice">
You must replace <code>PrepareForTakeOff</code> with your personal API key.
</aside>




# Get a Specific Record

## EASA Form one, FAA 8130-3




<!-- ```ruby
require 'blockav'

api = Blockav::APIClient.authorize!('PrepareForTakeOff')
api.records.get(2)
```

```python
import blockav

api = blockav.authorize('PrepareForTakeOff')
api.records.get(2)
``` -->

```shell
curl "http://example.com/api/records/2"
  -H "Authorization: PrepareForTakeOff"
```

```javascript
const blockav = require('blockaviation');

let api = blockav.authorize('PrepareForTakeOff');
let max = api.records.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "partNumber": "157T9300",
  "manufacturerCode": "81485",
  "airlineSerialNumber": "000344",
  "lifeLimitPartIndicator": true
}
```

This endpoint retrieves a component specific record.



<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/componentrecords/<parameter>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the record to retrieve
PartNumber | Manufacturer Full Length Part Number
ManufacturerCode | Manufacturers Code
AirlineSerialNumber | Airline Part Serial Number
LifeLimitedPartIndicator | Indicates whether component is a LLP
TimeControlledComponentIndicator| Indicates whether component is time controlled
SerialNumber | Part serial number
PartDescription | Component part description
AuthorizedReleaseCertificateNumber | ID of most recent Authorized Release Certificate Number



## Airworthiness Directives




<!-- ```ruby
require 'blockav'

api = Blockav::APIClient.authorize!('PrepareForTakeOff')
api.records.get(2)
```

```python
import blockav

api = blockav.authorize('PrepareForTakeOff')
api.records.get(2)
``` -->

```shell
curl "http://example.com/api/records/2"
  -H "Authorization: PrepareForTakeOff"
```

```javascript
const blockav = require('blockaviation');

let api = blockav.authorize('PrepareForTakeOff');
let max = api.records.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "partNumber": "157T9300",
  "manufacturerCode": "81485",
  "airlineSerialNumber": "000344",
  "lifeLimitPartIndicator": true
}
```

This endpoint retrieves a component Engineering orders relating to Airworthiness directives.



<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/componentrecords/<parameter>`

### URL Parameters

Parameter | Description
--------- | -----------
AD_Num | AD issuing authority number
AD_Title | Subject matter or intent of the AD
EffectiveDate | Date on which the AD takes affect
ProductType | Aviation product type the AD refers to
AD_Status | Current status of compliance of the AD
AMOC_Flag| Indicates if the AD has been complied with using AMOC
MethodOfCompliance | Information relating to the Method Of Compliance
