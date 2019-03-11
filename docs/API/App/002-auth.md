# `AUTH` App API

Except for the `add-user` and `activate-device` endpoints, all API calls should be called with `accessToken` as _bearer_ token retrieved upon device activation.

The token **must be postfixed with a dot, a idempotency integer, a dot and the sha256 hash of the concatenated values of the accessToken, uniqueDeviceIdentifier and the idempotency integer**.

```
curl --request POST \
  --url http://localhost:3001/api/v1/app/ping \
  --header 'authorization: Bearer e916cccb-f8a7-4848-9bf9-c958dcf9534f.123.9a76639d581d36b038bb785ef4fbd7700137490dd2125abeba04de76546ad9e4' \
  --header 'content-type: application/json' \
  --data '{}'
```

- For each call, the _idempotency_ integer should be highter than the last used sent idempotency integer.
- The `uniqueDeviceIdentifier` is the identifier used when the device was activated.
- A valid bearer token can be computed like this (pseudocode):  

  ```
  {accessToken}.{idempotencyInt}.sha256({accessToken}{uniqueDeviceIdentifier}{idempotencyInt})
  ```

You can always call the `ping` endpoint to check if your token is (still) valid.

###### `<` Response `POST`: `/api/v1/app/ping`

Error codes:

 - `800`: No auth 'bearer' present or header incomplete
 - `801`: Invalid or expired access token
 - `802`: Invalid bearer signature

```
{
  "error": {
    "reference": "56a4a5e5-80a5-4296-9c1b-85a6582045d7",
    "code": 801
  }
}
```

Success:

```
{
  "pong": true,
  "auth": {
    "user": { ... },
    "device": { ... },
    "call": { ... }
  }
}
```

#### Logging

All API calls with auth enabled will return a `X-Call-Ref` response header with the unique response logging id.
