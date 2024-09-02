# Notification System

# Overview

Design a notification system that will support Mobile Push, E-Mail and SMS.

# Core Use Cases

* Notifications can be sent via:
    * Mobile Push
        * Android
        * iOS
    * E-Mail
    * SMS
* User signs up for notifications
* User can opt out from receiving notifications on a selected device
* Notification can be sent to the user

# Non-functional requirements

* Traffic
    * 10 million mobile push notifications
    * 5 million e-mails
    * 1 million SMS

# APIs

* Signup for notifications - request `POST /api/v1/notifications/singup` with body:

```json
{
  "channels": [
    {
      "channelType": "SMS",
      "phoneNumber": "123123123"
    },
    {
      "channelType": "E_MAIL",
      "emailAddress": "user@mail.com"
    },
    {
      "channelType": "MOBILE_PUSH",
      "device_id": "483737234",
      "device_token": "SJ48S3FH496S3R"
    }
  ]
}
```

* Send notification

# Entities

TBD

# Microservices

* TBD

# High Level Design

TBD

# Deep dives

TBD

# Author

Dominik Cebula

* https://dominikcebula.com/
* https://blog.dominikcebula.com/
* https://www.udemy.com/user/dominik-cebula/
