# Authentication

You can authenticate with one of the following options:

* Basic Access Authorization
* Session ID (Cookie)
* API Key (API Token)

## Basic Auth / Plain text

```python
TODO
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://your.server.name/node/api/users/current" \
  -H "Content-Type: application/json" \
  -X GET \
  -u "your_login:your_password"
```

```javascript
TODO
```

> Make sure to replace `your_login:your_password` with your credentials.

Pretend your login is `your_login` and the password is `your_password`. You can use basic auth in every request.

## Basic Auth / Base64

```python
TODO
```

```shell
TODO
```

```javascript
TODO
```

> Make sure to replace `your_login:your_password` with your credentials.

TODO

## Create new Session

```python
TODO
```

```shell
# Create session id:
curl "https://your.server.name/node/api/users/session" \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{"login": "your_login", "password": "your_password"}'
  
# Use session id in reqests:
TODO
  
# Create session id and save it to cookies.txt file:
curl "https://your.server.name/node/api/users/session" \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{"login": "your_login", "password": "your_password"}' \
  --cookie-jar cookies.txt

# Use session id previously saved to cookies.txt file:
curl "https://your.server.name/node/api/users/current" \
  -H "Content-Type: application/json" \
  -X GET \
  --cookie cookies.txt
```

```javascript
TODO
```

> The above command returns your session id like this:

```json
"7b9d2b27-a47d-4bbe-a2f7-2c63bf356db0"
```

Creates a new Session, which is later used to authenticate other API requests. In case of successful Session creation, a Set-Cookie header is returned, which sets proper cookie with session ID. The method returns a newly-created session ID.

### HTTP Request

`POST /node/api/users/session`

## Delete current Session

> To logout use this code:

```python
TODO
```

```shell
curl "https://your.server.name/node/api/users/session" \
  -H "Content-Type: application/json" \
  -X DELETE
```

```javascript
TODO
```

> Success response:

```json
TODO
```

Deletes current Session (performs logout).

### HTTP Request

`DELETE /node/api/users/session`

## Create Authentication Token

```python
TODO
```

```shell
# Create authentication token:
curl "https://your.server.name/node/api/users/5716a3296c2356651eab0814/auth-token" \
  -H "Content-Type: application/json" \
  -X POST

# Use authentication token:
curl "https://your.server.name/node/api/users/current?api-token= 32925106-8c56-41d1-8713-410f203e8ce0" \
  -H "Content-Type: application/json" \
  -X GET
```

```javascript
TODO
```

> The above command returns your session id like this:

```json
32925106-8c56-41d1-8713-410f203e8ce0
```

Creates and returns an Authentication Token, which can be further used to authenticate a given User without providing a password.

### HTTP Request

`POST /node/api/users/{id}/auth-token`

`Permission: manage-users`

### Parameters

Parameter | Description
:-------- | :----------
id | The ID of the user to generate auth-token for.

## Delete Authentication Token

```python
TODO
```

```shell
curl "https://your.server.name/node/api/users/5716a3296c2356651eab0814/auth-token" \
  -H "Content-Type: application/json" \
  -X DELETE
```

```javascript
TODO
```

> Success response:

```json
TODO
```

Deletes Authentication Token of a given User. All further requests with existing Authentication Token will be rejected.

### HTTP Request

`DELETE /node/api/users/{id}/auth-token`

`Permission: manage-users`

### Parameters

Parameter | Description
:-------- | :----------
id | The ID of the user to delete auth-token for.
