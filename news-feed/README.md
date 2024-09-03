# News Feed

# Overview

Design a news feed system.

# Functional requirements

* User can publish a post
* User can see posts published by friends that he/she follows
* User sees posts sorted in a reverse chronological order
* User can publish text, videos and images
* User can have up to 5000 friends

# Non-functional requirements

* Traffic
    * 10 million daily active users
    * 30% of users are daily publishers
    * Each user looks at news feed 8 times a day
    * 90% of posts contain an image
    * 10% of posts contain a video
    * Number of posts created each day - $`10*10^6 * 30\% = 3`$ million
    * Number of feed read operations each day - $`8 * 10*10^6 = 80`$ million
    * Number of images uploaded each day - $`3*10^6 * 0.9 = 2.7`$ million
    * Number of videos uploaded each day - $`3*10^6 * 0.1 = 0.3`$ million
    * Number of posts created each second - $`3*10^6 / 86400 = 35`$
    * Number of feed read operations each second - $`80*10^6 / 86400 = 925`$
    * Number of images uploaded each second - $`2.7*10^6 / 86400 = 31.25`$
    * Number of videos uploaded each second - $`0.3*10^6 / 86400 = 3.47`$
* Storage
    * DB
        * DB Single post size (excluding images and videos size) = $`800`$ bytes
        * DB Storage increase each day - $`800 * 3*10^6 / 1024 / 1024 / 1024 = 2.24`$ GB
        * DB Storage increase each yer - $`2.24 * 365 = 817`$ GB
        * DB Storage 1st year - $`1 * 817 / 1024 = 0.79`$ TB
        * DB Storage 2nd year - $`2 * 817 / 1024 = 1.59`$ TB
        * DB Storage 3rd year - $`3 * 817 / 1024 = 2.39`$ TB
        * DB Storage 5th year - $`5 * 817 / 1024 = 3.98`$ TB
        * DB Storage 10th year - $`10 * 817 / 1024 = 7.97`$ TB
    * Media
        * Average Image Size - $`0.5`$ MB
        * Average Video Size - $`24`$ MB
        * Media Storage increase each day = $`((2.7*10^6 * 0.5) + (0.3*10^6 * 24)) / 1024 / 1024 = 8.15`$ TB
        * Media Storage increase each year = $`365 * 8.15 / 1024 = 2.9`$ PB
        * Media Storage 1st year = $`1 * 2.9 = 2.9`$ PB
        * Media Storage 2nd year = $`2 * 2.9 = 5.8`$ PB
        * Media Storage 3rd year = $`3 * 2.9 = 8.7`$ PB
        * Media Storage 5th year = $`5 * 2.9 = 14.5`$ PB
        * Media Storage 10th year = $`10 * 2.9 = 29`$ PB
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
      "media_id": "0241b7c0-6dc3-787e-87c6-68165e593c3a"
    },
    {
      "type": "VIDEO",
      "media_id": "0821b7c0-a08b-7dd4-a4f2-e1a8cb0c6680"
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
        "media_id": "0241b7c0-6dc3-787e-87c6-68165e593c3a"
      },
      {
        "type": "VIDEO",
        "media_id": "0821b7c0-a08b-7dd4-a4f2-e1a8cb0c6680"
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
