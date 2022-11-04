---
title : "AMI API"
description : "Artificial Machine Intelligence (AMI API)"
lead: "Artificial Machine Intelligence (AMI API)"
date : 2022-10-23T00:00:00+00:00
lastmod : 2022-10-23T00:00:00+00:00
draft : false
mermaid : false
menu:
  docs:
    parent: "Woodcord"
weight : 14
toc: true
---

[GitHub Repository](https://github.com/WonkyMic/ami-api)

{{< alert icon="💡" context="info" text="Interface documentation is out of date. Check Repository for latest." />}}

## Store Message
**Given** the AMI API, **when** invoked with a Message Body, **then** store the content **and** return a Message ID.

### Endpoint
`POST` | `/ami/message`

### Request
```
curl https://wonky-api.web.app/ami/message
```

### Response
```
{
    "id": "1231"
}
```

## Get Reply
**Given** the AMI API, **when** invoked with a Message Body, **then** return *Instant Reploy*

### Endpoint
`GET` | `/ami/message/<id>`

### Request
```
curl https://wonky-api.web.app/ami/message/<id>
```

### Response
```
{
    "reply": "lorem ipsum"
}
```

## Store Feedback
**Given** the AMI API, **when** invoked with Message Feedback, **then** store the feedback by Message ID.

### Endpoint
`POST` | `/ami/message/<id>/feedback`

### Request
```
curl https://wonky-api.web.app/ami/message/<id>/feedback
```

### Response
```
{
    "id": "1231"
}
```

## Development
WIP