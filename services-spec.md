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

Common Response References: **`400-ad`** |  **`500-ie`** 


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

Common Response References: **`400-ad`** |  **`500-ie`** | **`403-ip`**

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

---


`PUT` `/services/:id` - update exists service

**Request**

```js
PUT {baseUrl}/services/126
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

Updated `200`

Common Response References: **`400-ad`** |  **`500-ie`** | **`403-ip`**

```json
{
    "status" : 201,
    "message" : "Service updated",
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

Not Found `404`

Service by {id} not found

```json
{
    "status": 403,
    "message": "Service by id = 1 not found",
}
```

---



`DELETE` `/services/:id` - delete exists service

**Request**

```js
DELETE {baseUrl}/services/126
X-Client-Access: {client-access-key}
Authorization: Bearer {token}
```


**Responses**

Common Response References: **`400-ad`** |  **`500-ie`**

Deleted `200`

```json
{
    "status" : 201,
    "message" : "Service deleted",
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

Not Found `404`

Service by {id} not found

```json
{
    "status": 403,
    "message": "Service by id = 1 not found",
}
```
