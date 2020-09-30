---
parent: Cookbook
nav_order: 40
title: Get ticket count of show
---
# How to read the ticket count of a show

Sometimes you want to get the number of available tickets for a show, for example to display a *sold out* badge on your
website if necessary.


This is how you do it:

## Request

```
GET https://api.ticketpark.ch/shows/{showPid}?properties[capacity]=1
```

## Response

The response will contain a list of capacities of all available ticket allocations.

```json
{
  "capacity": {
    "total": {
      "total": 245,
      "sold": 15,
      "available": 230
    },
    "public": {
      "total": 165,
      "sold": 0,
      "available": 165
    }
  }
}
```


To display that *sold out* badge mentioned above, you want to check `capacity['public']['available']`.
In the example above, there are still 165 tickets publicly available.
