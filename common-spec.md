# Common APIs Specification

All endpoints must be return response as template

```ts
{
    // operation status code
    "status": 200,
    // message about operation
    "message": string,
    // any data (name of data is optional) than returned from endpoint (optional)
    "<data>": any
}
```

### All endpoints can be returned error response like:
---
Access denied `400`

Reference: **`400-ad`**

When access key not provided

```json
{
    "status": 400,
    "message": "Access denied"
}
```
---
Internal Error `500`

Reference: **`500-ie`**

```json
{
    "status": 500,
    "message": "Internal Error"
}
```

### All mutation operations like POST, PUT, PATCH, DELETE can be returned error response like below, if some body parameters is invalid

---

Invalid Parameters `403`

API rend error when body or images fields incorrect or expected

Reference: **`403-ip`**

```json
{
    "status": 403,
    "message": "Invalid parameters",
    "errors" : [
        "first parameter error",
        "second parameter error"
    ]
}
```

