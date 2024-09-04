# Video Sharing Platform

# Overview

Design a video sharing platform like YouTube.

# Functional requirements

* TBD

# Non-functional requirements

* Traffic
    * TBD
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
