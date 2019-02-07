---
parent: Getting started
nav_order: 1
---
# Authentication
The authentication system for the Ticketpark API is based on oAuth 2.0. This means in a nutshell:

* A username/password is required initally to get an access token and a refresh token.
* The access token can be used for multiple requests within a limited time.
* If the access token expires, the refresh token can be used to get a new access token.
* All requests to the API must be made over https.

## Required credentials
Client key and Client secret can be obtained from Ticketpark support.
Username and password are the same you would use to log in to the Ticketpark backend.

---

## Getting an access token
To get your first access token you need to send the username and password along with your client authorization data. This is the only time you need the user’s password. Never save the user’s password in your application, but store the refresh token instead.

### Request

```
POST https://api.ticketpark.ch/oauth/v2/token
```

**Header fields**

|Field         |Type          |Description   |Example
|:-------------|:-------------|:-------------|:-------------
Content-Type   |string	      |Content type which is posted | `application/x-www-form-urlencoded`
Accept	       |string        |Accepted response type | `application/json`
Authorization  |string	      |Basic Authorization based on client key and client secret (see  [examples](https://gist.github.com/brandonmwest/a2632d0a65088a20c00a)) | `Basic NDNfM2F1MGxk...`


**Body fields**

|Field         |Type          |Description   |Example
|:-------------|:-------------|:-------------|:-------------
username	|string	|Username of user	|`john@domain.ch`
password	|string	|Password of user	|`secretabc123`
grant_type	|string	|String 'password'	|`password`


### Response

|Field         |Type          |Description   |Example
|:-------------|:-------------|:-------------|:-------------
access_token   |string	      |Access token	 | `NTIxNzE4N…`
refresh_token  |string	      |Refresh token | `YWUzOTJjNz…`
expires_in	   |int	          |Time in seconds after which the access_token will expire | `600`


---

## Refreshing the access token

### Request

```
POST https://api.ticketpark.ch/oauth/v2/token
```

**Header fields**

|Field         |Type          |Description   |Example
|:-------------|:-------------|:-------------|:-------------
Content-Type   |string	      |Content type which is posted | `application/x-www-form-urlencoded`
Accept	       |string        |Accepted response type | `application/json`
Authorization  |string	      |Basic Authorization based on client key and client secret (see  [examples](https://gist.github.com/brandonmwest/a2632d0a65088a20c00a)) | `Basic NDNfM2F1MGxk...`


**Body fields**

|Field         |Type          |Description   |Example
|:-------------|:-------------|:-------------|:-------------
refresh_token  |string	      |Refresh token	|`YWUzOTJjNz`
grant_type	   |string	      |String 'refresh_token'	|`refresh_token`


### Response

|Field         |Type          |Description   |Example
|:-------------|:-------------|:-------------|:-------------
access_token   |string	      |Access token	 | `NTIxNzE4N…`
refresh_token  |string	      |Refresh token | `YWUzOTJjNz…`
expires_in	   |int	          |Time in seconds after which the access_token will expire | `600`


---

## Using the access token


In [any request](basic-requests.html) provide a valid access token.

**Header fields**

|Field         |Type          |Description   |Example
|:-------------|:-------------|:-------------|:-------------
Content-Type   |string	      |Content type which is posted | `application/json`
Accept	       |string        |Accepted response type | `application/json`
Authorization  |string	      |String 'Bearer' followed by the access token|`Bearer NTIxNzE4N…`