---
parent: Getting started
nav_order: 2
---
# Basic requests

## GET
Use GET to fetch exisiting records.

You can get single records:<br>
`GET https://api.ticketpark.ch/events/{eventPid}`

Or you can get multiple records at once:<br>
`GET https://api.ticketpark.ch/events/`

**Heads up:**  Fetching multiple records may return a lot of data. You will probably want to use pagination and/or filters.

## POST
Use POST to create new records.

You can create single records:

```
POST https://api.ticketpark.ch/events/
{"name": "My party", "currency": "CHF"}
```

Or you can create multiple records at once:

```
POST https://api.ticketpark.ch/events/
[
{"name": "My party", "currency": "CHF"},
{"name": "My concert", "currency": "CHF"}
]
```

## PATCH
Use PATCH to edit existing records.

You can edit single records:

```
PATCH https://api.ticketpark.ch/events/{eventPid}
{"name": "My renamed party"}
```

Or you can edit multiple records at once:

```
PATCH https://api.ticketpark.ch/events/
[
{"pid": "{eventPid}", "name": "My renamed party"},
{"pid": "{eventPid}", "name": "My renamed concert"}
]
```

## DELETE
Use DELETE to remove records.

`DELETE https://api.ticketpark.ch/events/{eventPid}`

**Heads up:** Deleting a record over the API is very powerful. All related child records will also get deleted.