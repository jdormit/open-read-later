# Open Library
> An open specification for URL read-later lists

Open Library is a specification for defining, accessing, and modifying lists of links (sometimes called "read-later" lists). The goal of the specification is to provide consistent data structures and access mechanisms for creating, modifying, and querying such lists.

## Why a specification instead of an app?
Many read-later list apps exist. I used [Pocket](https://getpocket.com) for a long time. However, many of these apps are proprietary, and all of them require the user to store their lists on the app's server. Link lists cannot easily be migrated to another app. An additional frustration, particularly with Pocket, is that the app made it difficult to read the links in their original form, opting instead to render the links within the app. These problems result in significant lock-in and raise privacy concerns.

By defining a specification rather than creating another app, I hope to create a situation in which users can choose from many apps to store link libraries and easily migrate their data between apps. The specification also allows for many back-end services - this means that a user could, say, store their link library in dropbox for convenience or in an encrypted file to mitigate privacy concerns and feel confident that their preferred read-later app could work with any back-end service they choose.
