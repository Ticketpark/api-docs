---
parent: Getting started
nav_order: 5
title: Pagination
---
In GET requests which return multiple records it is recommended to use pagination.

In order to do this you add two query parameters:

|Parameter|Explanation|
|:--------|:----------|
|page|The page you want to fetch (starting at 0)|
|maxResults|The number of results to be returned per page|

## Example

```
GET https://api.ticketpark.ch/bookings/?page=2&maxResults=10
```

This request would return bookings number 21-30 from all the bookings you can access.

Hint
{: .label }
Look for the `X-Count`  header field in the response to know how many records are available in total. Then you can calculate your maximum page number.