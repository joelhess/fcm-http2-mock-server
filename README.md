# FCM Mock Server (docker)

Simple HTTP/2 based FCM mock for testing server applications.

Forked from: (https://github.com/rslota/fcm-http2-mock-server)

## Quick start

There is an atomatic build setup on my Docker Hub, so you can run this docker simply with:
```bash
docker run joelhess/fcm-http2-mock-server
```

## API

The docker exposes one port - 443. Beside, of course, `FCM` API, there are some simple controll enpoints:
* **POST** */reset* - resets state of the mock
* **POST** */error-tokens* - by sending `JSON` list of objects you can set `HTTP` *error code* and *error reason* that should be returned for given *device token*. The objects should have the following fields: `device_token`, `status`, `reason`

The body of the post should be: 
```json
[
	{"device_token":"abcdefg", "status":200, "reason":"InvalidRegistration"},
	{"device_token":"abcdsdfefg", "status":200, "reason":"InvalidRegistration"}
]
```

* **GET** */activity* - returns (as `JSON`) history of `FCM` API calls to this mock
