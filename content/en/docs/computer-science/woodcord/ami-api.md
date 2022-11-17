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

|Resource|Reference|
|:---|:---|
|Repository|[https://github.com/WonkyMic/ami-api](https://github.com/WonkyMic/ami-api)|
|Host|http://localhost:8080|
|Database|[https://www.cockroachlabs.com/](https://www.cockroachlabs.com/)|



## Author

### Store
**Given** Author information, **when** storing in DB,  **then** return AMI Author ID.

<details>
    <summary>Request</summary>

`POST` | `/ami/author`

|Name|Type|Description|
|:---|:---|:---|
|`Alias`|String|Platform Alias|
|`Platform`|String|Platform name|
|`PlatformAliasId`|uint64|Platform specific author identifier|

#### Response
|Http Status|Body|
|:---|:---|
|201|`<Author Response>`|
|302|Author already exists|

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Author Identifier|
|`Alias`|String|Platform Alias|
|`Platform`|String|Platform name|
|`PlatformAliasId`|uint64|Platform specific author identifier|

#### Validation Rules
- Author must not already exist by PlatformAliasId.

</details>

### Delete
**Given** AMI Author ID, **when** delete API is invoked, **then** delete the Author.

<details>
    <summary>Request</summary>

`DELETE` | `/ami/author/<id>`

#### Response
|Http Status|Body|
|:---|:---|
|`200`|`Author Deleted`|

#### Validation Rules
- Deletes Reactions for Author
- Deletes Messages by Author as well as the related message reactions

</details>

### Search
**Given** Platform Alias ID, **then** return associated author information.

<details>
    <summary>Request</summary>

`GET` | `/ami/author/search`


#### Query Parameters
|Name|Type|Description|
|:---|:---|:---|
|`platformAliasId`|String|Platform specific author identifier|

#### Response
|Http Status|Body|
|:---|:---|
|`200`|`<Author>`|

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Author Identifier|
|`Alias`|String|Platform Alias|
|`Platform`|String|Platform name|
|`PlatformAliasId`|uint64|Platform specific author identifier|

</details>

### Retrieve
**Given** AMI Author ID, **then** return associated author information.

<details>
    <summary>Request</summary>

`GET` | `/ami/author/<id>`

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Author Identifier|

#### Response
|Http Status|Body|
|:---|:---|
|`200`|`<Author>`|

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Author Identifier|
|`Alias`|String|Platform Alias|
|`Platform`|String|Platform name|
|`PlatformAliasId`|uint64|Platform specific author identifier|

</details>

### Retrieve List
**Given** the AMI API, **when** the Get Author endpoint is invoked, **then** return Author list.

<details>
    <summary>Request</summary>

`GET` | `/ami/author/`

#### Response
|Http Status|Body|
|:---|:---|
|`200`|`List<Author>`|

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Author Identifier|
|`Alias`|String|Platform Alias|
|`Platform`|String|Platform name|
|`PlatformAliasId`|uint64|Platform specific author identifier|

</details>

### Retrieve Reactions
**Given** an Author ID, **then** retrieve the list of associated reactions.

<details>
    <summary>Request</summary>

`GET` | `/ami/author/<id>/reactions`

#### Response
|Http Status|Body|
|:---|:---|
|`200`|`List<Reaction>`|

|Name|Type|Description|
|:---|:---|:---|
|`MessageId`|String|Message Identifier|
|`AuthorId`|String|Author Identifier|
|`Reaction`|uint64|Reaction Integer|

</details>

## Message

### Store 
**Given** the AMI API, **when** invoked with a Message Body, **then** store the content **and** return a Message ID.

<details>
    <summary>Request</summary>

`POST` | `/ami/message`

|Name|Type|Description|
|:---|:---|:---|
|`AuthorId`|String|Identifier used by Platform|
|`Content`|String|Message Content|
|`Platform`|String|Platform name|

#### Response
|Http Status|Body|
|:---|:---|
|`201`|`<Message>`|
|`400`|Bad Request|

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Message Identifier|
|`AuthorId`|UUID|Identifier used by Platform|
|`Content`|String|Message Content|
|`Platform`|String|Platform name|

#### Validation Rules
- Author must exist.
</details>

### Delete
**Given** message ID, **when** invoking the delete AMI API, **then** delete the related message.

<details>
    <summary>Request</summary>

`DELETE` | `/ami/message/<id>`

#### Response

|Http Status|Body|
|:---|:---|
|`200`|`Message Deleted`|

</details>

### Retrieve
**Given** the AMI API, **when** invoked with a Message ID, **then** return the associated message content

<details>
    <summary>Request</summary>

`GET` | `/ami/message/<id>`

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Message Identifier|

#### Response
|Http Status|Body|
|:---|:---|
|`200`|`<Message>`|

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Message Identifier|
|`AuthorId`|UUID|Identifier used by Platform|
|`Content`|String|Message Content|
|`Platform`|String|Platform name|

</details>

### Retrieve List
**Given** the AMI API, **when** the Get endpoint is invoked, **then** return a message list.

<details>
    <summary>Request</summary>

`GET` | `/ami/message/`

#### Response
|Http Status|Body|
|:---|:---|
|`200`|`List<Message>`|

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Message Identifier|
|`AuthorId`|UUID|Identifier used by Platform|
|`Content`|String|Message Content|
|`Platform`|String|Platform name|

</details>

### Retrieve Reactions
**Given** a message ID, **then** retrieve the list of associated reactions.

<details>
    <summary>Request</summary>

`GET` | `/ami/message/<id>/reactions`

|Name|Type|Description|
|:---|:---|:---|
|`Id`|UUID|AMI Message Identifier|

#### Response
|Http Status|Body|
|:---|:---|
|`200`|`List<Reaction>`|

|Name|Type|Description|
|:---|:---|:---|
|`MessageId`|String|Message Identifier|
|`AuthorId`|String|Author Identifier|
|`Reaction`|uint64|Reaction Integer|

</details>

## Reaction

### Store
**Given** Author and Message IDs, **when** invoked with a Message Reaction, **then** store the reaction by Message ID.

<details>
    <summary>Request</summary>

`POST` | `/ami/reaction`

|Name|Type|Description|
|:---|:---|:---|
|`MessageId`|String|Message Identifier|
|`AuthorId`|String|Author Identifier|
|`Reaction`|uint64|Reaction Integer|

#### Response

|Name|Type|Description|
|:---|:---|:---|
|`MessageId`|String|Message Identifier|
|`AuthorId`|String|Author Identifier|
|`Reaction`|uint64|Reaction Integer|

#### Validation Rules
- Author must exist.
- Message must exist.
- Reaction relationship must not already exist.

</details>