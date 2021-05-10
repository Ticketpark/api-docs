---
title: Webhooks
nav_order: 10
has_children: false
---
# Webhooks

By using webhooks, Ticketpark will actively inform your application if certain events take place. You can then react and fetch the required data from the API for further processing.

Please contact [support@ticketpark.ch](mailto:support@ticketpark.ch) to store your webhook urls.

The following webhook events are available:

## New booking
If  a new booking is created and confirmed, the following message will be sent to your webhook url:

```
{
    "type": "new-booking",
    "payload": {
        "booking_pid": [pid-of-booking]
    }
}
```

You can then fetch booking details [as described here](/api-docs/cookbook/read-booking.html).


## New payment
If  a new payment is created and confirmed, the following message will be sent to your webhook url:

```
{
    "type": "new-payment",
    "payload": {
        "booking_pid": [pid-of-booking],
        "payment_pid": [pid-of-payment],
        "payment_method": [pid-of-payment-method],
        "currency": [pid-of-currency],
        "amount": [amount]
    }
}
```