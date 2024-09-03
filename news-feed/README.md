# News Feed

# Overview

Design a news feed system.

# Functional requirements

* User can publish a post
* User can see posts published by friends that he/she follows
* User sees posts sorted in a reverse chronological order
* User can publish text, videos and images
* User can have up to 500 friends

# Non-functional requirements

* Traffic
  * 10 million daily active users
* Storage
  * Read to write ration - 10:1
  * Assumption - 30% of users are daily publishers
  * Number of posts created each day - 3 million
* Availability - 99.9%
* Latency - <300ms
* Data consistency - eventual
* Client types - Browser, Mobile

# APIs

* Create a post - `POST /api/v1/me/feed` with `auth_token` request header and with request body:

```json
{
  "title": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
  "body": "In mattis magna ac orci facilisis, quis egestas lorem mollis. Nullam facilisis sagittis eleifend.",
  "media": [
    {
      "type": "IMAGE",
      "upload-id": "0241b7c0-6dc3-787e-87c6-68165e593c3a"
    },
    {
      "type": "VIDEO",
      "upload-id": "0821b7c0-a08b-7dd4-a4f2-e1a8cb0c6680"
    }
  ]
}
```

* Retrieve news feed - `GET /api/v1/me/feed` with `auth_token` request header and with response body:

```json
[
  {
    "post_id": "7236704789428441088",
    "creation_date": "2024-09-03T12:01:43+00:00",
    "title": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "body": "In mattis magna ac orci facilisis, quis egestas lorem mollis. Nullam facilisis sagittis eleifend.",
    "media": [
      {
        "type": "IMAGE",
        "upload-id": "0241b7c0-6dc3-787e-87c6-68165e593c3a"
      },
      {
        "type": "VIDEO",
        "upload-id": "0821b7c0-a08b-7dd4-a4f2-e1a8cb0c6680"
      }
    ]
  }
]
```

# Entities

TBD

# High Level Design

TBD

# Deep dives

TBD

# Author

Dominik Cebula

* https://dominikcebula.com/
* https://blog.dominikcebula.com/
* https://www.udemy.com/user/dominik-cebula/
