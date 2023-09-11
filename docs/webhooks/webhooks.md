---
title: Webhooks
nav_order: 10
has_children: false
title: Webhooks
---
By using webhooks, Ticketpark will actively inform your application when certain events take place. You can then react and fetch the required data from the API for further processing.

Please contact [support@ticketpark.ch](mailto:support@ticketpark.ch) to store your webhook urls.

The following webhook events are available:

## New booking
When a new booking is created and confirmed, the following message will be sent to your webhook url:

```
{
    "type": "new-booking",
    "payload": {
        "booking_pid": "pid-of-booking"
    }
}
```

You can then fetch booking details [as described here](/api-docs/cookbook/read-booking.html).

## Tickets of booking updated
When tickets within a confirmed booking are updated (e.q. the price or seat is changed) or when new tickets are added to an already confirmed booking, the following message will be sent to your webhook url:


```
{
  "type": "booking-tickets-updated",
  "payload": {
    "booking_pid": "pid-of-booking",
    "ticket_pids": [collection-of-pids-of-updated-tickets]
  }
}

```

## Tickets of booking cancelled
When tickets within a confirmed booking are deleted (without cancelling the rest of the booking), the following message will be sent to your webhook url:


```
{
  "type": "booking-tickets-deleted",
  "payload": {
    "booking_pid": "pid-of-booking",
    "ticket_pids": [collection-of-pids-of-deleted-tickets]
  }
}

```

## Booking cancelled
When a previously confirmed booking gets cancelled, the following message will be sent to your webhook url:


```
{
    "type": "booking-cancelled",
    "payload": {
        "booking_pid": "pid-of-booking"
    }
}

```



## New payment
When a new payment is created and confirmed, the following message will be sent to your webhook url:

```
{
    "type": "new-payment",
    "payload": {
        "booking_pid": "pid-of-booking",
        "payment_pid": "pid-of-payment",
        "payment_method": "pid-of-payment-method",
        "currency": "pid-of-currency",
        "amount": "amount"
    }
}
```

## New person
When a new person is created (via ticket booking process or otherwise), the following message will be sent to your webhook url:

```
{
    "type": "new-person",
    "payload": {
        "person_pid": "pid-of-person"
    }
}
```

## Person updated
When a person is updated (name, address, or contact data), the following message will be sent to your webhook url:

```
{
    "type": "new-updated",
    "payload": {
        "person_pid": "pid-of-person"
    }
}
```