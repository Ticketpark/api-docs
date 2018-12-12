---
parent: Cookbook
nav_order: 1
title: Create a new booking
---
# How to create a new booking

This is the basic workflow how to create a new booking over the api.

## 1. Create a customer

If you don't have an existing customer you want to use, create a new one.

```
POST https://api.ticketpark.ch/persons/
```

```json
{
    "salutation": "m",
    "firstname": "Tom",
    "lastname": "Tomson",
    "email": "tom@tomsons.com",
    "address": {
        "country": "CH",
        "address1": "Testweg 10",
        "address2": "",
        "zip": "3000",
        "city": "Bern"
    }
}
```

Hint
{: .label }
In the response look for the `Location` header field to get the newly created pid.

---

## 2. Create a booking

Create a booking and add the customer to it.

```
POST https://api.ticketpark.ch/bookings/
```

```json
{
    "customer": "{pid of person from request 1}"
}
```

---

## 3. Reserve two tickets

Add some tickets to the booking. Note how in this example we create two tickets with just one request.

A tickets is defined by
* a price
* a show
* a sector or a seat

In this example we assume you already have your event set up and you know the pids of your prices, shows and sectors.

```
POST https://api.ticketpark.ch/tickets/
```

```json
[
{
    "booking": "{pid of booking from request 2}",
    "show": "{pid of a show}",
    "price": "{pid of a price}",
    "sector": "{pid of a sector}"
},
{
    "booking": "{pid of booking from request 2}",
    "show": "{pid of a show}",
    "price": "{pid of a price}",
    "sector": "{pid of a sector}"
}
]
```

---

## 4. Confirm booking

Every booking needs to be confirmed. Tickets of unconfirmed bookings will be released again after 30 minutes.

```
PATCH https://api.ticketpark.ch/bookings/{pid of booking from request 2}
```

```json
{
    "confirmation": true
}
```

---

## 5. Send confirmation email

Optionally, you can send the confirmation mail for the booking you just created.

```
POST https://api.ticketpark.ch/email/send
```

```json
{
    "booking": "{pid of booking from request 2}",
    "type": "confirmation"
}
```

