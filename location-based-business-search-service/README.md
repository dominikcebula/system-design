# Location Based Business Search Service

# Overview

Design Location Based Business Search Service like Yelp or Google Places.

# Functional requirements

* User can search for businesses based on keywords and selected location
    * Location can be:
        * a city
        * a city with radius
        * a city district
        * a city district with radius
        * current user location with radius
* User can see details on a selected business
* Business owners can add, update, delete a business
* Business changes made by business owners can appear in search results with a delay

# Non-functional requirements

* Traffic
    * 100 million daily active users
    * Average user makes 5 queries per day
    * Number of queries per day = $`5 * 100*10^6 = 500 million`$
    * Number of queries per second = $`500*10^6 / 86400 = 5787`$
* Storage
    * 200 million registered businesses
    * Number of bytes for single business
* Availability - 99.9%
* Latency <300ms
* Data consistency
    * eventual
* Client types - Browser, Mobile App

# Entity

* Business
    * Title
    * Description
    * Phone Number
    * E-Mail
    * Website
    * Address
    * Opening and Closing Hours
        * Monday
        * Tuesday
        * Wednesday
        * Thursday
        * Friday
        * Saturday
        * Sunday

# APIs

* TBD

# High Level Design

TBD

# Author

Dominik Cebula

* https://dominikcebula.com/
* https://blog.dominikcebula.com/
* https://www.udemy.com/user/dominik-cebula/
