# URL Shortener

# Core Use Cases

* Given a long url, service generates a short url for it
* Given a short url, service redirects a user to short url

Example:
Given URL https://www.amazon.com/Design-Patterns-Distilled-Dominik-Cebula-ebook/dp/B0C91X1GT8 service generates a short
url https://go.io/11PVWGSpX6

## Out of scope

* Short URLs management
* URL analytics

# Non-functional requirements

* Traffic
    * 100 million URLs generated each day
    * read-to-write ratio: 10:1
* Availability - 99.9%
* Latency - <300ms
* Data consistency - strong
* Data durability - 99.999%
* Client types - Browser, Mobile

# APIs

TBD

# Entities

TBD

# Microservices

TBD

# High Level Design

TBD

# Author

Dominik Cebula

* https://dominikcebula.com/
* https://blog.dominikcebula.com/
* https://www.udemy.com/user/dominik-cebula/
