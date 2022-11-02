---
title : "System Design"
description : "Facilitate Discord conversations using cloud enabled distributed architecture."
lead: "Facilitate Discord conversations using cloud enabled distributed architecture."
date : 2022-10-23T00:00:00+00:00
lastmod : 2022-10-23T00:00:00+00:00
draft : false
mermaid : true
menu:
  docs:
    parent: "Woodcord"
weight : 12
toc: true
---

- Natural Language Processing to label conversations by subject.
- Respond with helpful information.
- Categorize severity.

{{< alert icon="💡" context="info" text="This page contains Mermaid. It's recommended to view in light mode." />}}

{{< mermaid class="bg-light text-center" >}}
sequenceDiagram
    actor Bob
    participant D as Woodcord
    participant API as AMI API
    participant DB as Database
    participant LM as Learning Module
    Bob ->> D: Post Message
    D ->> API: Store Message / Search for Reply
    DB ->> API: Common Reply
    API ->> D : Reply 
    D ->> Bob: Reply
    Bob ->> D: Reply Feedback (emoji)
    API ->> DB: Store Fedback by Message Id
    DB ->> LM: Execute NLP
    LM ->> DB: Store Updated Response List
{{< /mermaid >}}