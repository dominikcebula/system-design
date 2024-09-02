# URL Shortener

# Core Use Cases

* Given a long url, service generates a short url for it
* Given a short url, service redirects a user to short url

Example:
Given URL https://www.amazon.com/Design-Patterns-Distilled-Dominik-Cebula-ebook/dp/B0C91X1GT8 service generates a short
url https://url.com/11PVWGSpX6

## Out of scope

* Short URLs management
* URL analytics
* AuthN and AuthZ

# Non-functional requirements

* Traffic
    * 100 million URLs generated each day
    * read-to-write ratio: 10:1
  * Write operations per second = `100 * 10^6 / 86400 = 1157`
  * Read operations per second = `1157 * 10 = 11570`
* Storage
  * Average DB Entry Size [B] = Avg Long Url + Avg Short Url + ID = `83 + 10 + 8 = 101`
  * DB Size After 1 Year [TB] = `1 * 365 * 100*10^6 * 101 / 1024 / 1024 / 1024 / 1024 = 3.35`
  * DB Size After 2 Year [TB] = `2 * 365 * 100*10^6 * 101 / 1024 / 1024 / 1024 / 1024 = 6.7`
  * DB Size After 5 Year [TB] = `5 * 365 * 100*10^6 * 101 / 1024 / 1024 / 1024 / 1024 = 16.75`
  * DB Size After 10 Year [TB] = `10 * 365 * 100*10^6 * 101 / 1024 / 1024 / 1024 / 1024 = 33.5`
* Availability - 99.9%
* Latency - <300ms
* Data consistency - strong
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
