---
parent: Cookbook
nav_order: 3
title: Add translations
---
# How to add translations

In `POST` and `PATCH` requests you can use the special `_translations` key to add or edit translations for specific fields.


```json
{
    "_translations": {
        "de": {
            "name": "Mein Event",
            "description": "Eine Beschreibung"
        },
        "en": {
            "name": "My event",
            "description": "Some description"
        }
    }
}
```


`de` will be treated as default locale and be used for the default value of the fields outside of translations.