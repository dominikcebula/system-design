# Video Sharing Platform

# Overview

Design a video sharing platform like YouTube.

# Functional requirements

* Video upload
* Video playback
* Ability to change video quality playback
* Support for different resolutions
  * 360p
  * 480p
  * 720p
  * 1080p
  * 4k
* Support for different clients
  * Web Browser
  * Mobile
  * Tablets
  * Smart TVs
* Ability to upload videos of up to 1GB

# Non-functional requirements

* Traffic
  * Number of daily active users - 5 million
  * Average daily time spend on the product - 30 minutes
  * Average user watches 5 videos per day
  * 10% of users upload 1 video per day
  * Average video size - 300 MB
* Storage
    * DB
        * TBD
    * Media
        * TBD
* Availability - 99.9%
* Latency - <300ms
* Data consistency - eventual
* Client types - Browser, Mobile, Tablet, Smart TVs

# APIs

* TBD

* Upload Video
    * start upload - `POST /api/v1/media/videos`, response will contain `200 OK` with `location` header pointing to the
      place were data should be uploaded
    * upload file chunks - `POST /api/v1/media/videos/0821b7c0-a08b-7dd4-a4f2-e1a8cb0c6680`
    * finalize upload - `POST /api/v1/media/images/0821b7c0-a08b-7dd4-a4f2-e1a8cb0c6680/finalize`

# High Level Design

TBD

# Author

Dominik Cebula

* https://dominikcebula.com/
* https://blog.dominikcebula.com/
* https://www.udemy.com/user/dominik-cebula/
