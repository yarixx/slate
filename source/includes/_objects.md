# Objects

## Get all Objects

```python
TODO
```

```shell
curl "https://your.server.name/node/api/objects?fields=id,name,state_id,class_id,properties" \
  -H "Content-Type: application/json" \
  -X GET
```

```javascript
TODO
```

> Success response:

```json
[
  {
    "id": "5867948233835d9661c56dc8",
    "name": "Object name",
    "class_id": 3,
    "state_id": 5,
      "properties": Array[1][
        {
          "name": "SN",
          "value": "-",
          "type_id": 1,
          "id": "5b9f422abefad26ed2013437"
        }
      ]
  },
  ...
]
```

Retrieves a list of all Objects in the system. By default Objects are returned without their Properties. You can optionally get Properties with `properties` option.

### HTTP Request

`GET /node/api/objects`

`Permission: objectPermissions`

### Options

Option | Type | Description
:----- | :--- | :----------
fields *`optional`* | list | Comma-separated list of Object fields to return.

## Get Object by ID

```python
TODO
```

```shell
curl "https://your.server.name/node/api/objects/5867948233835d9661c56dc8 \
  -H "Content-Type: application/json" \
  -X GET
```

```javascript
TODO
```

> Success response:

```json
{
  "id": "5867948233835d9661c56dc8",
  "name": "Child object 1",
  "class_id": 4,
  "state_id": 3,
  "parent_id": "58eb553d0c90a26391d6a041",
  "child_ids": ["57f4be0e747280c143641a8e", "57f4be0e747280c143641c60", ...],
  "properties": [
    {
      "id": "57f4be0e747280c143641d60",
      "name": "Description",
      "type_id": 1,
      "value": "Some description"
    },
    ...
  ],
  ...
}
```

Retrieves a single Object by ID. By default an Object is returned with full contents.

### HTTP Request

`GET /node/api/objects/{id}`

`Permission: objectPermissions`

Parameter | Type | Description
:-------- | :--- | :----------
id *`required`* | string | The ID of the object.

### Options

Option | Type | Description
:----- | :--- | :----------
fields *`optional`* | list | Comma-separated list of Object fields to return.

## Delete Object by ID

```python
TODO
```

```shell
curl "https://your.server.name/node/api/objects/5867948233835d9661c56dc8 \
  -H "Content-Type: application/json" \
  -X DELETE
```

```javascript
TODO
```

> Success response:

```json
TODO
```

Deletes a given Object and its child Objects.

### HTTP Request

`GET /node/api/objects/{id}`

`Permission: objectPermissions + (delete-objects | manage-objects)`

Parameter | Type | Description
:-------- | :--- | :----------
id *`required`* | string | The ID of the object.
