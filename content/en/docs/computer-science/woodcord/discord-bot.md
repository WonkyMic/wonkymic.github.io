---
title : "Discord Bot"
description : "Interact with Discord servers to facilitate a conversation."
lead: "Interact with Discord servers to facilitate a conversation."
date : 2022-10-23T00:00:00+00:00
lastmod : 2022-10-23T00:00:00+00:00
draft : false
mermaid : true
menu:
  docs:
    parent: "Woodcord"
weight : 13
toc: true
---

{{< alert icon="💡" context="info" text="This page contains Mermaid. It's recommended to view in light mode." />}}


|Commands|Description|
|:---|:---|
|`!listauthors`|List AMI Authors|
|`!amihealth`|Liveness check evaluating AMI API|
|`!test`|Woodcord Bot liveness check|

## Store Conversation
**Given** the Woodcord Bot, **when** a Discord Message Event is recieved, **then** store the conversation using the AMI API.
{{< mermaid class="bg-light text-center" >}}
sequenceDiagram
    participant D as Discord
    participant W as Woodcord
    participant AMI as AMI API
    D ->> W: Message Event
    W ->> AMI: Store Message Data
    AMI ->> W: Reply with Message ID
{{< /mermaid >}}

## Get AMI response
**Given** the Woodcord Bot with AMI Message ID, **when** responding to Discord Message Event, **then** get the *AMI Instant Reply*
{{< mermaid class="bg-light text-center" >}}
sequenceDiagram
    participant D as Discord
    participant W as Woodcord
    participant AMI as AMI API
    W ->> AMI: Get Reply by Message ID
    AMI ->> W: AMI Instant Reply
    W ->> D: Reply to Message Event
{{< /mermaid >}}

## Store Feedback
**Given** the Woodcord Bot, **when** a Discord Emoji Event with  is recieved, **then** store conversation feedback using the AMI API
{{< mermaid class="bg-light text-center" >}}
sequenceDiagram
    participant D as Discord
    participant W as Woodcord
    participant AMI as AMI API
    D ->> W: Message Feedback Event
    W ->> AMI: Store Feedback by Message ID
{{< /mermaid >}}

## Development
### Discord Library
|Library|Language|Notes|
|:---|:---|:---|
|~~[Discord4J](https://docs.discord4j.com/)~~|`Java`|Too much Java, not enough Kotlin|
|~~[DiscordKt](https://discordkt.github.io/)~~|`Kotlin`|Too small of a project, lacking documentation|
|~~[Diskord](https://github.com/JesseCorbett/Diskord)~~|`Kotlin`|Poor exception handling.|
|[Serenity](https://docs.rs/serenity/latest/serenity/)|`Rust`|Current implementation|