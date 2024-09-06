# Location Based Business Search Service

# Overview

Design Location Based Business Search Service like Yelp or Google Places.

# Functional requirements

* User can search for businesses based on keywords and selected location
    * Location can be:
        * current user location with radius
        * a city
        * a city with radius
        * a city district
        * a city district with radius
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
    * Businesses
        * 200 million registered businesses
        * Number of bytes for single business registration
            * Max - $`4780B`$
            * Avg = $`693B`$
        * Storage for business registrations (avg) = $`200*10^6 * 693 /1024/1024/1024 = 129GB`$
    * Cities
        * Number of bytes for single city registration
            * Max - $`121B`$
            * Avg = $`46B`$
        * Number of cities in US - $`19495`$
        * Storage for cities registrations (avg) = $`19495 * 46 /1024 = 875KB`$
    * Cities Districts
        * Number of bytes for single city district registration
            * Max - $`125B`$
            * Avg = $`55B`$
        * Estimated Number of city districts in US - $`19495 * 3 = 58485`$
        * Storage for city districts registrations (avg) = $`58485 * 55 /1024/1024 = 3MB`$
* Availability - 99.9%
* Latency <300ms
* Data consistency - eventual
* Client types - Browser, Mobile App

# Entity

* Business - max=4780, avg=693
    * ID - 16 bytes
    * Title - 100 bytes
    * Description - 2000 bytes
    * Phone Number - 16 bytes
    * E-Mail - 320 bytes
    * Website - 2048 bytes
    * Street Name - 85 bytes
    * BuildingNumber - 16 bytes
    * ApartmentNumber - 16 bytes
    * Zip Code - 10 bytes
    * State - 85 bytes
    * City ID - 4 bytes
    * City District ID - 4 bytes
    * Geolocation (latitude, longitude) - `geography(POINT, 4326)` - 32 bytes
    * Opening and Closing Hours - $`7 * 2 * 2 = 28 bytes`$
        * Monday
        * Tuesday
        * Wednesday
        * Thursday
        * Friday
        * Saturday
        * Sunday

* City - max=121, avg=46
    * ID - 4 bytes
    * Name - 85 bytes
    * Geolocation (latitude, longitude) - `geography(POINT, 4326)` - 32 bytes

* City District - max=125, avg=55
    * ID - 4 bytes
    * City ID - 4 bytes
    * Name - 85 bytes
    * Geolocation (latitude, longitude) - `geography(POINT, 4326)` - 32 bytes

* Indexes
    * Business Geolocation - R-Tree Spatial Index
    * City Name
    * City Geolocation - R-Tree Spatial Index
    * City District Name
    * City District Geolocation - R-Tree Spatial Index

# APIs

* Search for business
    * by geolocation - `GET /api/v1/search?keywords=...&latitude=...&longitude&=...&radius=...`
    * by named location - `GET /api/v1/search?keywords=...&location=...&locationType=...&radius=...`

responds with `200 OK` and response body:

```json
{
  "total": "10",
  "businesses": [
    {
      ...
    }
  ]
}
```

* Get Business Details for a user - `GET /api/v1/businesses/:businessId`

* Business Management operations for a business owner
    * Create - `POST /api/v1/management/businesses`
    * Read - `GET /api/v1/management/businesses/:businessId`
    * Update - `PUT /api/v1/management/businesses/:businessId`
    * Delete - `DELETE /api/v1/management/businesses/:businessId`

# High Level Design

![diagram.png](diagram.png)

# Deep Dives

## DB Scaling

Taking into account:

* GB-level storage requirements
* large amount of reads
* small amount of writes

decision was made to use read replicas and indexes for scalability while keeping a single database.

Other approaches, listed below were not used because of added complexity without added benefits taking into account
storage requirements:

* Data Sharding
* Multiple different dedicated databases

## Search by Geo Location

Design assumes usage of dedicated geospatial search index which can be achieved by using for example PostgreSQL &
PostGIS.

When searching by current user location and radius, location should be encoded using PostGIS Point, and then search
should be executed against businesses table by including condition on distance from each found business.

PostGIS Indexing should be applied for all Geolocations for PostgreSQL to use R-Tree Spatial Index to speed-up search by
location and distance.

## Search by City Name or City District Name with radius

When searching by city name or city district name with radius, first geolocation of specific city or city district will
need to be found. This operation will be fast by using indexing on top of name column in city and city district tables.

Having geolocation found, businesses should be queried by using distance condition based on city or city district
geolocation and each business. Operation will use R-Tree Spatial Index on both city / city district and
business location.

# Author

Dominik Cebula

* https://dominikcebula.com/
* https://blog.dominikcebula.com/
* https://www.udemy.com/user/dominik-cebula/
