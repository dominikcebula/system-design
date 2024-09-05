# Ad Click Aggregator

# Overview

Design Ad Click Aggregator System that will be used to display Ads on a website or an app. System should track Ads
performance based on ad clicks.

# Functional requirements

* User is redirected to an advertiser website after clicking on an Ad
* Advertiser can query Ads performance by checking click metrics
* Ads performance and click metrics have 1 minute granularity
* Protection against clicking an Ad multiple times that would skew Ad analytics, only first click on an Ad is recorded
  for a given user

## Out of scope

* Ad serving and placement in a website or an app
* Cross Device Tracking
* Conversion tracking
* Demographic profiling

# Non-functional requirements

* Traffic
  * 10 million Ads at any given time
  * 10k Ads clicks per second
* Storage
    * DB
        * TBD
* Availability - 99.9%
* Latency
  * Ad placement <300ms
  * Analytics Queries <1000ms
* Data consistency
  * strong
  * analytics as realtime as possible
* Client types - Browser, Mobile App

# APIs

* TBD

# High Level Design

TBD

# Author

Dominik Cebula

* https://dominikcebula.com/
* https://blog.dominikcebula.com/
* https://www.udemy.com/user/dominik-cebula/
