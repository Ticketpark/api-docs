---
parent: Cookbook
nav_order: 30
title: Read data of bookings
---
# How to read data of bookings

This is the basic workflow how to read data of bookings over the api.

## 1. Get a single booking

To read the most common data of a booking, you can fetch it with one request like this:

```
POST https://api.ticketpark.ch/bookings/[booking-pid]?properties[customer]=true&properties[tickets]=true
```

You will get a response like this (simplified example):

```json
{
  "pid": 293233446073,
  "pid_readable": "2932-3344-6073",
  "confirmation": true,
  "delivery_method": "digital",
  "tickets": [
    {
      "confirmation": true,
      "seat_string": "Sector A, Row 12, Seat 3",
      "denormalized_host_name": "My Event Agency",
      "denormalized_event_name": "Shakespeare Day",
      "denormalized_show_start": "2019-08-11T12:00:00+0200",
      "denormalized_venue_name": "Cellar Theatre",
      "denormalized_sector_name": "A",
      "denormalized_price_name": "Normalpreis",
      "denormalized_price_including_vat": "25.00",
      "denormalized_currency_pid": "CHF",
      "pid": "6445cdbe3e9509e8",
      "code": "6445CDBE3E9509E8",
    },
    {
      "confirmation": true,
      "seat_string": "Sector A, Row 12, Seat 4",
      "denormalized_host_name": "My Event Agency",
      "denormalized_event_name": "Shakespeare Day",
      "denormalized_show_start": "2019-08-11T12:00:00+0200",
      "denormalized_venue_name": "Cellar Theatre",
      "denormalized_sector_name": "A",
      "denormalized_price_name": "Normalpreis",
      "denormalized_price_including_vat": "25.00",
      "denormalized_currency_pid": "CHF",
      "pid": "6445cdbe3e9509e9",
      "code": "6445CDBE3E9509E9",
    }
  ],
  "customer": {
    "pid": "8CB96870-68AC-4296-BEC2-F0F04B29D4F0",
    "salutation": "m",
    "firstname": "Manuel",
    "lastname": "Reinhard",
    "company": "Ticketpark",
    "email": "tech@ticketpark.ch",
    "newsletter": true,
    "mailing": true,
    "locale": "de",
    "address": {
      "pid": "1A64A213-AF6C-462C-B5ED-6A0D1967B9CE",
      "address1": "Birkenweg 61",
      "zip": "3013",
      "city": "Bern",
      "country": "CH",
    },
  }
}
```

Hint
{: .label }
Ticketpark can notify you per call to a webhook url whenever a new booking has been created. [Get in touch with our team](mailto:support@ticketpark.ch) for more information.

---

## 2. Get a collection of bookings

You can fetch all bookings of a show, event or even host by getting a collection of bookings. Example:

```
GET https://api.ticketpark.ch/events/[event-pid]/bookings/?properties[customer]=true&properties[tickets]=true&maxResults=10&page=0
```

You will get a response containing a collection of results like above.
