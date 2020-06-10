---
parent: Cookbook
nav_order: 1
title: Create a new event
---
# How to create a new event

This is the basic workflow how to create a new event over the api.


## 1. Create a venue

If you don't have a venue yet, create one.

```
POST https://api.ticketpark.ch/venues/
```

```json
{
	"host": "{pid of your host}",
	"name": "Hallenstadion",
	"city": "Zürich"
}
```

Hint
{: .label }
In the response look for the `Location` header field to get the newly created pid.


Then add sectors to your venue.

```
POST https://api.ticketpark.ch/sectors/
```

```json
[
{
	"host": "{pid of venue from above}",
	"name": "Tribune A",
	"price_category": 1,
	"capacity": 1000
},
{
  	"host": "{pid of venue from above}",
  	"name": "Tribune B",
  	"price_category": 2,
  	"capacity": 500
}
]
```

---
## 2. Create an event


```
POST https://api.ticketpark.ch/events/
```

```json
{
	"host": "{pid of your host}",
	"name": "My Fair Lady",
	"allow_digital_dispatch": true,
	"currency": "CHF"
}
```


---
## 3. Create shows

Add one or multiple show to your event.


```
POST https://api.ticketpark.ch/shows/
```

```json
{
	"event": "{pid of event from above}",
	"venue": "{pid of venue from above}",
	"start": "2020-06-01 12:00:00"
}
```


---
## 3. Create prices

Add one or multiple prices to your event.


```
POST https://api.ticketpark.ch/prices/
```

```json
[
{
	"event": "{pid of event from above}",
	"name": "Normal price",
	"price_category": 1,
	"price": 50
},
{
	"event": "{pid of event from above}",
	"name": "Children",
	"price_category": 1,
	"price": 40
},
{
  	"event": "{pid of event from above}",
	"name": "Normal price",
  	"price_category": 2,
  	"price": 20
},
 {
   	"event": "{pid of event from above}",
 	"name": "Children",
   	"price_category": 2,
   	"price": 10
 }
]
```