# REST API design for an issue tracker


## Bug

### View all bugs
GET: `/v1/bugs`
```
GET request URL = /v1/bugs

response = [
    {
        "id": 1,
        "title": "Authentication service",
        "body": "It doesn't authenticate users who login through Google.",
        "status": "unresolved",
        "assignedUser": null
    },
    {
        "id": 2,
        "title": "Database model",
        "body": "Add tax field to customer orders.",
        "status": "resolved",
        "assignedUser": {
            "id": 1,
            "name": "Rutvik Patel",
            "email": "fake_user@email.com"
        }
    }
]
```

### View a specific bug
GET: `/v1/bugs/{id}`
```
GET request URL = /v1/bugs/1

response = {
    "id": 1,
    "title": "Authentication service",
    "body": "It doesn't authenticate users who login through Google.",
    "status": "unresolved",
    "assignedUser": null
}
```

### View all bugs marked as "resolved"
GET: `/v1/bugs?status={resolved/unresolved}`
```
GET request URL = /v1/bugs?status=resolved

response = [
    {
        "id": 2,
        "title": "Database model",
        "body": "Add tax field to customer orders.",
        "status": "resolved",
        "assignedUser": {
            "id": 1,
            "name": "Rutvik Patel",
            "email": "fake_user@email.com"
        }
    }
]
```

### Create a bug
POST: `/v1/bugs`
```
POST request URL = /v1/bugs
POST request payload = {
    "title": "Code Pipeline Malfunctioning",
    "body": "Test job is failing regarless of passing all test cases."
}

response = {
    "id": 3,
    "title": "Code Pipeline Malfunctioning",
    "body": "Test job is failing regarless of passing all test cases.",
    "status": "unresolved",
    "assignedUser": null
}
```

### Edit a bug
PATCH: `/v1/bugs/{id}`
```
PATCH request URL = /v1/bugs/1
PATCH request payload = {
    "title": "Google authentication service"
}

response = {
    "id": 1,
    "title": "Google authentication service",
    "body": "It doesn't authenticate users who login through Google.",
    "status": "unresolved",
    "assignedUser": null
},
```

### Mark a bug as "resolved" and "unresolved"
PATCH: `/v1/bugs/{id}`
```
PATCH request URL = /v1/bugs/1
PATCH request payload = {
    "status": "resolved"
}

response = {
    "id": 1,
    "title": "Google authentication service",
    "body": "It doesn't authenticate users who login through Google.",
    "status": "resolved",
    "assignedUser": null
},
```
```
PATCH request URL = /v1/bugs/1
PATCH request payload = {
    "status": "unresolved"
}

response = {
    "id": 1,
    "title": "Google authentication service",
    "body": "It doesn't authenticate users who login through Google.",
    "status": "unresolved",
    "assignedUser": null
},
```

### Assign the bug to a user which is identified by its ID.
PATCH: `/v1/bugs/{id}`
```
PATCH request URL = /v1/bugs/1
PATCH request payload = {
    "assignedUserId": 2
}

response = {
    "id": 1
    "title": "Google authentication service"
    "body": "It doesn't authenticate users who login through Google."
    "status": "unresolved",
    "assignedUser": {
        "id": 2,
        "name": "Jake Jigs",
        "email": "fake_user2@email.com"
    }
},
```

### Delete a bug
DELETE: `/v1/bugs/{id}`
```
DELETE request URL = /v1/bugs/1

response = Status Codes only
```



## Comment

### Create a comment on a bug
POST: `/v1/comments`
```
POST request URL = /v1/comments
POST request payload = {
    "title": "Good Catch",
    "body": "I was running into same issues but I thought i was just me.",
    "bugId": 1
    "userId": 3
}

response = {
    "id": 1,
    "title": "Good Catch",
    "body": "I was running into same issue but I thought it was just me.",
    "bugId": 1
    "user": {
        "id": 3,
        "name": "Greg Lopez",
        "email": "fake_user3@email.com"
    }
}
```

### Delete a comment from a bug
DELETE: `/v1/comments/{id}`
```
DELETE request URL = /v1/comments/1

response = Status Codes only
```




## Status Codes for HTTP methods 

### GET:
    - 200 (Okay) : Successful
    - 404 (Not Found) : Resource cannot be found
    - 204 (No Content) : Request was fulfilled but there is no data for the respose body

### POST:
    - 201 (Created) : Successfuly reated a new resource
    - 400 (Bad Request): Client sent invalid data into the request payload

### PATCH:
    - 200 (Okay) : Successfuly modified a resource
    - 400 (Bad Request) : Bad data in the request payload
    - 409 (Conflict) : Data is good, but the changes can't be applied to the resource.

### DELETE:
    - 204 (No Content) : Successfuly deleted a resource
    - 404 (Not Found) : Resource doesn't exist or can't be found

___