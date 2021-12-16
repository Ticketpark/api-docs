---
parent: Cookbook
nav_order: 50
title: Protection concept
---
# Protection concept

This is how to set [protection concept data](https://headwayapp.co/ticketpark-changelog/schutzkonzept-einfach-selbst-definieren-169591) over the api:


## Facemask, health certificate and social distancing

A protection concept defining whether a facemask or a health certificate is required and whether social distancing on seating charts should apply
is created whenever you add a new event.


### Defining protection concept settings when creating an event

You can set values when creating a new event:

```
POST https://api.ticketpark.ch/events/
```

```json
{
    "host": "{pid of your host}",
    "name": "My Fair Lady",
    "allow_digital_dispatch": true,
    "currency": "CHF",
    "protection_concept": {
        "facemask_required": true,
        "enable_social_distancing": true,
        "health_certificate_mode": '3G' // accepts '3G', '2G', '2GPLUS' and NULL
    }
}
```

### Updating protection concept settings of an event

You can also update the protection concept data of your event:

```
PATCH https://api.ticketpark.ch/events/{pid-of-your-event}
```

```json
{
    "protection_concept": {
        "facemask_required": true,
        "enable_social_distancing": true
    }
}
```


Heads up
{: .label .label-red}
With `enable_social_distancing` on, you still need to define the social distancing state per show when creating the over the API:


```
POST https://api.ticketpark.ch/shows/
```

```json
{
    "enable_social_distancing": true
    // all other show properties
}
```


## Contact tracing

Contact tracing data is collected with `Annotations`, which are text fields attached to single tickets.
In order to ask for contact tracing data, you can use exiting annotation templates which contain all required settings:

### Creating a contact tracing annotation

 ```
 POST https://api.ticketpark.ch/annotations/
 ```
 
 ```json
 {
     "event": "{pid of your event}",
     "based_on_annotation_template": "contact_tracing_name"
 }
 ```


These templates are available:

* `contact_tracing_name`
* `contact_tracing_phone`
* `contact_tracing_email`
* `contact_tracing_zip`
* `contact_tracing_city`
* `contact_tracing_birthday`


### Updating a contact tracing annotation

Use normal [PATCH functionality](../getting-started/basic-requests.html) on annotation endpoints to update an
existing contact tracing annotation.
