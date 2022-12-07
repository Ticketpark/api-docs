---
parent: Getting started
title: Response headers
nav_order: 3
title: Response header
---
## Status codes

|Status|Meaning|
|:-----|:------|
**200**   | All went well (GET)
**201**   | All went well, but there is no data to be returned (POST, PATCH).
**204**   | All went well, but there is no data to be returned (DELETE).
**403**   | You are not authorized to perform the requested action.
**404**   | We could not find what you were looking for. Either the url or some pid you sent is invalid.
**409**   | The data you submitted could not be handled. Probably you sent some invalid payload
**500**   | Something went wrong on the server side. Sorry, our fault!


## Response header fields

|Field|Meaning|
|:-----|:------|
location | The url to access the records you created or edited. This is where you'll find newly created pids.
x-count | The number of records be returned by a GET request. If you use pagination, this number contains the total of records, not only the ones on your current page.
