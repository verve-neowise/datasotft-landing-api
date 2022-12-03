# Datasoft Landing API Specification

> Base api url must be start with `/api/v1`

## Services

Model

```js
id: number
title: string
images: string[]
desc: string
content: string
```


`GET` `/services` - Get all services

**Request**
```js
GET {baseUrl}/services
X-Client-Access: {client-access-key}
```

**Responses**

Success `200`

```json
{
    "status" : 200,
    "message" : "Retrive all services",
    "services": [
        {
            "id": 125,
            "title": "Service Title",
            "images": [
                "https://datasoft.uz/files/service-image.png",
                "https://datasoft.uz/files/service-image.png"
            ],
            "desc": "Service Description",
            "content": "Service Content"
        }    
    ]
}
```

Access denied `400`

When access key not provided

```json
{
    "status": 400,
    "message": "Access denied"
}
```

Internal Error `500`

```json
{
    "status": 500,
    "message": "Internal Error"
}
```

`POST` `/services` - create new Service

**Request**

```js
POST {baseUrl}/services
Content-Type: multipart/form-data; boundary=MyBoundary
X-Client-Access: {client-access-key}
Authorization: Bearer {token}

{
 "title": "Service Title",
 "desc": "Service Description",
 "content": "Service Content"
}

Upload multiple images "upload"
```


**Responses**

Created `201`

```json
{
    "status" : 201,
    "message" : "Service created",
    "service": {
        "id": 126,
        "title": "Service Title",
        "images": [
            "https://datasoft.uz/files/service-image.png",
            "https://datasoft.uz/files/service-image.png"
        ],
        "desc": "Service Description",
        "content": "Service Content"
    }    
}
```


Access denied `400`

When access key not provided

```json
{
    "status": 400,
    "message": "Access denied"
}
```

Not Authorized `401`

When user access token not provided

```json
{
    "status": 401,
    "message": "Missing or incorrect access token"
}
```

Bad Request `403`

API rend error when body or images fields incorrect or expected

```json
{
    "status": 403,
    "message": "Invalid parameters",
    "errors" : [
        "image files not provided",
        "title must be not empty",
        "content not provided"
    ]
}
```

Internal Error `500`

```json
{
    "status": 500,
    "message": "Internal Error"
}
```