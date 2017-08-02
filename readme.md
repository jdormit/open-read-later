# Open Read-Later
> An open specification for URL read-later lists

The Open Read-Later specification defines a single-file data format for storing read-later lists of URLs. The goal of the specification is to provide a common storage mechanism to store read-later lists, and one that is human-readable (and human-editable), can easily be stored locally, transferred to a different machine, synchronized between machines, or encrypted if desired.

A common format prevents vendor lock-in by allowing users to migrate their lists between apps without friction. It also has to the potential to encourage an ecosystem of intercompatible read-later list apps and addons, allowing users to choose the apps that best meet their needs (or to easily create on that does).

## The data format
Open Read-Later data files are plain text. Here's an example file:

```
title: Dev Docs
url: https://devdocs.io
tags: tools, programming
---
title: A Taste of Rust
url: http://evanmiller.org/a-taste-of-rust.html
tags: programming, rust
---
title: IANA Example Webpage
url: http://example.com
```

The format is quite straightforward. Each link entry consists of a `title` field, a `url` field, and an optional `tags` field. Entries are separated the delimiter `---`.

A field consists of a key followed by a colon, an optional space, then a value. This means that `key:value` and `key: value` are both valid representations of the same field.

Every entry must have the `title` and `url` fields; the `tags` field is optional, and client apps are free to add other optional fields as they see fit. However, clients should not rely on optional fields being present - the only fields that can reliably be counted on are `title` and `url`.
