# Ad Click Aggregator

# Overview

Design Ad Click Aggregator System that will be used to display Ads on a website or an app. System should track Ads
performance based on ad clicks.

# Functional requirements

* TBD

# Non-functional requirements

* Traffic
    * TBD
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
* Availability - 99.9%
* Latency - <300ms
* Data consistency - eventual
* Client types - Browser, Mobile

# APIs

* TBD

# High Level Design

TBD

# Author

Dominik Cebula

* https://dominikcebula.com/
* https://blog.dominikcebula.com/
* https://www.udemy.com/user/dominik-cebula/
