---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>


includes:
  - errors

search: true
---

# Introduction

Welcome to the <b>Blockaviation API!</b> You can use our API to access the Blockaviation API endpoints, which can allow you to search, retrieve authenticated aircraft records for your application.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```ruby
require 'blockav'

api = Blockav::APIClient.authorize!('meowmeowmeow')
```

```python
import blockav

api = blockav.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const blockav = require('blockav');

let api = blockav.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Blockaviation uses API keys to allow access to the API. You can register a new Blockav API key at our [developer portal](http://example.com/developers).

Blockaviation expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Records

## Get All Records

```ruby
require 'blockav'

api = Blockav::APIClient.authorize!('meowmeowmeow')
api.records.get
```

```python
import blockav

api = blockav.authorize('meowmeowmeow')
api.records.get()
```

```shell
curl "http://example.com/api/records"
  -H "Authorization: meowmeowmeow"
```

```javascript
const blockav = require('blockav');

let api = blockav.authorize('meowmeowmeow');
let records = api.records.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "partNumber": "143T6300",
    "manufacturerCode": "81205",
    "airlineSerialNumber": "000984",
    "lifeLimitPartIndicator": true
  },
  {
    "id": 2,
    "partNumber": "157T9300",
    "manufacturerCode": "81485",
    "airlineSerialNumber": "000344",
    "lifeLimitPartIndicator": true
  }
]
```

This endpoint retrieves all Records.

### HTTP Request

`GET http://example.com/api/records`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include records that have already been adopted.

<aside class="success">
Remember — a happy record is an authenticated record!
</aside>

## Get a Specific Record

```ruby
require 'blockav'

api = Blockav::APIClient.authorize!('meowmeowmeow')
api.records.get(2)
```

```python
import blockav

api = blockav.authorize('meowmeowmeow')
api.records.get(2)
```

```shell
curl "http://example.com/api/records/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const blockav = require('blockav');

let api = blockav.authorize('meowmeowmeow');
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

This endpoint retrieves a specific record.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/records/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the record to retrieve

## Delete a Specific Record

```ruby
require 'blockav'

api = Blockav::APIClient.authorize!('meowmeowmeow')
api.records.delete(2)
```

```python
import blockav

api = blockav.authorize('meowmeowmeow')
api.records.delete(2)
```

```shell
curl "http://example.com/api/records/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const blockav = require('blockav');

let api = blockav.authorize('meowmeowmeow');
let max = api.records.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific record.

### HTTP Request

`DELETE http://example.com/records/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the record to delete
