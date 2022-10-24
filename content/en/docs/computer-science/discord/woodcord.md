---
title : "Woodcord Kotlin Bot"
description : "A discord bot developed by Little Woodrows enjoyers."
lead: "A discord bot developed by Little Woodrows enjoyers."
date : 2022-10-23T00:00:00+00:00
lastmod : 2022-10-23T00:00:00+00:00
draft : false
mermaid : true
menu:
  docs:
    parent: "discord"
weight : 11
toc: true
---

{{< alert icon="💡" context="info" text="This page contains Mermaid. It's recommended to view in light mode." />}}


## Objective 
Interact with Discord servers using Kotlin.
- Natural Language Processing to label conversations by subject.
- Respond with helpful information.
- Categorize severity.

## Resources
- [Discord4J](https://docs.discord4j.com/)

## Design
### Message Processing
{{< mermaid class="bg-light text-center" >}}
sequenceDiagram
    participant D as Discord
    participant W as Woodcord
    participant AMI as AMI API
    D ->> W: Message Event
    W ->> AMI: Send Message Data
    AMI ->> W: Reply with common response
    W ->> D: Reply
{{< /mermaid >}}

### Artificial Machine Intelligence (AMI)
{{< mermaid class="bg-light text-center" >}}
sequenceDiagram
    actor Bob
    participant API
    participant DB as Database
    participant LM as Learning Module
    Bob ->> API: Post Message
    API ->> DB: Store Message / Search for Reply
    DB ->> API: Common Reply
    API ->> Bob: Reply
    Bob ->> API: Reply Feedback (emoji)
    API ->> DB: Store Fedback by Message Id
    DB ->> LM: Execute NLP
    LM ->> DB: Store Updated Response List
{{< /mermaid >}}