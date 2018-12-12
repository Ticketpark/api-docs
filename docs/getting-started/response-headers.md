---
parent: Getting started
title: Reading response header
nav_order: 3
---
# Reading response headers

## Status codes

|Status|Meaning|
|:-----|:------|
**200**   | All went well.
**204**   | All went well, but there is no data to be returned (because you did a POST, PATCH or DELETE).
**403**   | You are not authorized to perform the requested action.
**404**   | We could not find what you were looking for. Either the url or some pid you sent is invalid.
**409**   | The data you submitted could not be handled. Probably you sent some invalid payload
**500**   | Something went wrong on the server side. Sorry, our fault!


## Response header fields

|Field|Meaning|
|:-----|:------|
Location | The url to access the records you created or edited. This is where you'll find newly created pids.
X-Count | The number of records be returned by a GET request. If you use pagination, this number contains the total of records, not only the ones on your current page.