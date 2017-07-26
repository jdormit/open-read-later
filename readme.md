# Open Library
> An open specification for URL read-later lists

The Open Library specification defines a single-file data format for storing read-later lists of URLs. The goal of the specification is to provide a common storage mechanism to store read-later lists, and one that is human-readable (and human-editable), can easily be stored locally, transferred to a different machine, synchronized between machines, or encrypted if desired.

A common format prevents vendor lock-in by allowing users to migrate their lists between apps without friction. It also has to the potential to encourage an ecosystem of intercompatible read-later list apps and addons, allowing users to choose the apps that best meet their needs (or to easily create on that does).

## The data format
Open Library data files are plain text. Here's an example file:

```
title: Dev Docs
url: https://devdocs.io
tags: tools, programming
---
title: A Taste of Rust
url: http://evanmiller.org/a-taste-of-rust.html
tags: programming, rust
---
title: WHATWG Example Webpage
url: http://example.com
```
