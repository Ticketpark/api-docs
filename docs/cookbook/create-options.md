---
parent: Cookbook
nav_order: 11
title: Add options to booking process
---
# How to add options to a booking process

There are two ways how to add additional options to a booking process:

* *Ticket options*, which apply to a single ticket. This is often the best choice. Use this for things which  may differ
per person whithin a booking, like selecting a meal, attending a workshop, etc.


* *Options*, which apply to a booking as a whole. Use this for things which all persons within a booking have in common,
like reservation of a parking space or ordering additional merchandise.


## How to create ticket options


### 1. Create a ticket option group

```
POST https://api.ticketpark.ch/ticketoptiongroups/
```

```json
{
    "event": "{pid of your event}",
    "name": "Your dinner selection",
    "required": true // or false
}
```


---
### 2. Create ticket options


```
POST https://api.ticketpark.ch/ticketoptions/
```

```json
{
    "ticket_option_group": "{pid of your ticket option group}",
    "name": "Main course with meat",
    "price": 20 // A price is optional. Ticketpark fees may apply.
}
```

You can add as many ticket options to a ticket option group as you want. The ticket buyer will be able to select 1 per group.

This can also be used for simple yes/no questions. Imagine a ticket option group with name `Do you need an audio guide?` and the according ticket options `Yes` and `No`.

---
### 3. Add limitations for ticket options

Optionally, you can define the maximum available quantity per ticket options.

```
POST https://api.ticketpark.ch/ticketoptionlimitations/
```

```json
{
    "ticket_options": ["{pid of your ticket option}"], //note that this is a list – see below for more information
    "limitation": 50,
    "scope": "show" // define whether the limitation applies per "show" or per "event" (as a total over all shows)
}
```

By providing multiple `ticket_options` you can create a combined limitation. For example, let's say you sell meal in
a restaurant to enjoy before your theater perfomance. There are 100 seats in the restaurant, but you let people choose
whether they want a vegetarian meal or one with meat. In this case, set a ticket option limitation of 100 per show and
add both ticket options to it.


---
## How to create options

As most often ticket options is the better choice, the possibilities of options are more limited.

```
POST https://api.ticketpark.ch/options/
```

```json
{
    "event": "{pid of your event}",
    "name": "Would you like to reserve a parking space?",
    "items_per_booking": 1 // optional value to set maximum number per booking, if set to 1 the choice will become a yes/no selection
    "limitation": 50 // optional, the maximum available quantity of this option
}
```
