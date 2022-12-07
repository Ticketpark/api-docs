---
parent: Getting started
nav_order: 6
---
## Basics

Filters can be added with a `filters` query parameters to GET requests which return multiple records.

**Example: Find all `things` named `Hugo`:**

```
GET http://api.ticketpark/things/?filters[name]=Hugo
```

---

## Advanced filter parameters

|Parameter|Usage|Allowed values|
|:-----|:------|:------|
|`filters[_logic]`|When using multiple filters, the logic decides, whether the result must match all filters or just one of them|`AND` (default), `OR`
|`filters[_comp]`|The comparison made on the value|`eq` (equal, default), `gt` (greater than), `gte` (greater than or equal), `lt` (lower than), `lte` (lower than or equal), `neq` (not equal), `isNull`, `isNotNull`
|`filters[_value]`|The value the comparison is made against|

---

## Filter examples

**Find all entities with confirmation = true**
```
GET http://api.ticketpark/things/?filters[confirmation]=1
```

**Find all entities with confirmation = true and name == "Hugo"**
```
GET http://api.ticketpark/things/?filters[confirmation]=1&filters[name]=Hugo
```

**Find all entities which have changed sind date x**
```
GET http://api.ticketpark/things/?filters[updated][_comp]=gt&filters[updated][_value]=2014-01-01 00:00:00
```

**Find all entities which have changed sind date x OR have name == "Hugo"**
```
GET http://api.ticketpark/things/?filters[_logic]=OR&filters[updated][_comp]=gt&filters[updated][_value]=2014-01-01 00:00:00&filters[name]=Hugo
```

**Find all entites matching all of the following criterias:**
- confirmed = true
- name is "Johnson" oder "Tomson"
- updated in year 2014

```
GET http://api.ticketpark/things/?filters[confirmation]=1&filters[name][_logic]=OR&filters[name][0]=Johnson&filters[name][1]=Tomson&filters[updated][0][_comp]=gt&filters[updated][0][_value]=2014-01-01 00:00:00&filters[updated][1][_comp]=lt&filters[updated][1][_value]=2014-12-31 23:59:59
```

**Find all bookings by customer name**
```
GET http://api.ticketpark/bookings/?filters[customer][lastname]=Reinhard
```

**Also works with pids: Find all tickets of booking XY which are for show ZZ**
```
http://api.ticketpark/bookings/XY/tickets/?filters[show]=ZZ
```