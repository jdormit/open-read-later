# Open Library
> An open specification for URL read-later lists

Open Library is a specification for defining, accessing, and modifying lists of links (sometimes called "read-later" lists). The goal of the specification is to provide consistent data structures and access mechanisms for creating, modifying, and querying such lists.

## Why a specification instead of an app?
Many read-later list apps exist. I used [Pocket](https://getpocket.com) for a long time. However, many of these apps are proprietary, and all of them require the user to store their lists on the app's server. Link lists cannot easily be migrated to another app. An additional frustration, particularly with Pocket, is that the app made it difficult to read the links in their original form, opting instead to render the links within the app. These problems result in significant lock-in and raise privacy concerns.

By defining a specification rather than creating another app, I hope to create a situation in which users can choose from many apps to store link libraries and easily migrate their data between apps. The specification also allows for many back-end services - this means that a user could, say, store their link library in dropbox for convenience or in an encrypted file to mitigate privacy concerns and feel confident that their preferred read-later app could work with any back-end service they choose.

## The specification
The specification defines the data structure in which links should be stored and the mechanisms used to query link lists. Queries are made as HTTP requests. The specification does not define any particular method of displaying lists - it only defines the back end.

### Link data structure
Every link item must have the following fields:
```json
{
  "id": Number
  "title": String,
  "url": String,
  "timestamp": Number,
  "tags": String[]
}
```

The `id` field is an integer that uniquely identifies the link (i.e., two links in the same back end cannot share an `id`).

The `title` and `url` fields are self-explanatory (although it is worth noting that the Open Library specification does not impose any constraints on the title, e.g. it is not required to be the `<title>` element of the link's target).

The `timestamp` is a UNIX timestamp (seconds since January 1, 1970) representing the time when the link was first added to the library.

The `tags` field is a list of arbitrary strings. The specification does not impose any constraints on how these tags are used, nor does it guarantee that the `tags` list is not empty. However, the `tags` field must be present, even if it is an empty list.

### HTTP endpoints
All back end endpoints return JSON unless otherwise noted. Open Library backends must support the following HTTP endpoints:

#### `GET /`
Returns a list of link objects representing every link in the library.

##### Response
```json
{
  [
    {
      "id": Number
      "title": String,
      "url": String,
      "timestamp": Number,
      "tags": String[]
    },
    ...
  ]
}
```

#### `GET /{id}`
Returns the link object identified by `id`.

##### Response
```json
{
  "id": Number
  "title": String,
  "url": String,
  "timestamp": Number,
  "tags": String[]
}
```

## What about multiple users sharing an Open Library back end?
