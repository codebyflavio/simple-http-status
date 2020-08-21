# simple-http-status

## Why

Heavily inspired by [Django Rest Framework](https://www.django-rest-framework.org/api-guide/status-codes)

Using bare status codes in your responses isn't recommended. This package includes a set of named constants that you can use to make your code more obvious and readable.

## Getting started

```js
yarn add simple-http-status
```

## Usage

```ts
import { Status } from 'simple-http-status';

app.get('/', (req, res, next) => {
  res.status(Status.HTTP_200_OK).send('Hello world');
});
```

### Informational - 1xx

This class of status code indicates a provisional response.

```js
HTTP_100_CONTINUE;
HTTP_101_SWITCHING_PROTOCOLS;
```

### Successful - 2xx

This class of status code indicates that the client's request was successfully received, understood, and accepted.

```js
HTTP_200_OK;
HTTP_201_CREATED;
HTTP_202_ACCEPTED;
HTTP_203_NON_AUTHORITATIVE_INFORMATION;
HTTP_204_NO_CONTENT;
HTTP_205_RESET_CONTENT;
HTTP_206_PARTIAL_CONTENT;
HTTP_207_MULTI_STATUS;
HTTP_208_ALREADY_REPORTED;
HTTP_226_IM_USED;
```

### Redirection - 3xx

This class of status code indicates that further action needs to be taken by the user agent in order to fulfill the request.

```js
HTTP_300_MULTIPLE_CHOICES;
HTTP_301_MOVED_PERMANENTLY;
HTTP_302_FOUND;
HTTP_303_SEE_OTHER;
HTTP_304_NOT_MODIFIED;
HTTP_305_USE_PROXY;
HTTP_306_RESERVED;
HTTP_307_TEMPORARY_REDIRECT;
HTTP_308_PERMANENT_REDIRECT;
```

### Client Error - 4xx

The 4xx class of status code is intended for cases in which the client seems to have erred. Except when responding to a HEAD request, the server SHOULD include an entity containing an explanation of the error situation, and whether it is a temporary or permanent condition.

```js
HTTP_400_BAD_REQUEST;
HTTP_401_UNAUTHORIZED;
HTTP_402_PAYMENT_REQUIRED;
HTTP_403_FORBIDDEN;
HTTP_404_NOT_FOUND;
HTTP_405_METHOD_NOT_ALLOWED;
HTTP_406_NOT_ACCEPTABLE;
HTTP_407_PROXY_AUTHENTICATION_REQUIRED;
HTTP_408_REQUEST_TIMEOUT;
HTTP_409_CONFLICT;
HTTP_410_GONE;
HTTP_411_LENGTH_REQUIRED;
HTTP_412_PRECONDITION_FAILED;
HTTP_413_REQUEST_ENTITY_TOO_LARGE;
HTTP_414_REQUEST_URI_TOO_LONG;
HTTP_415_UNSUPPORTED_MEDIA_TYPE;
HTTP_416_REQUESTED_RANGE_NOT_SATISFIABLE;
HTTP_417_EXPECTATION_FAILED;
HTTP_422_UNPROCESSABLE_ENTITY;
HTTP_423_LOCKED;
HTTP_424_FAILED_DEPENDENCY;
HTTP_426_UPGRADE_REQUIRED;
HTTP_428_PRECONDITION_REQUIRED;
HTTP_429_TOO_MANY_REQUESTS;
HTTP_431_REQUEST_HEADER_FIELDS_TOO_LARGE;
HTTP_451_UNAVAILABLE_FOR_LEGAL_REASONS;
```

### Server Error - 5xx

Response status codes beginning with the digit "5" indicate cases in which the server is aware that it has erred or is incapable of performing the request. Except when responding to a HEAD request, the server SHOULD include an entity containing an explanation of the error situation, and whether it is a temporary or permanent condition.

```js
HTTP_500_INTERNAL_SERVER_ERROR;
HTTP_501_NOT_IMPLEMENTED;
HTTP_502_BAD_GATEWAY;
HTTP_503_SERVICE_UNAVAILABLE;
HTTP_504_GATEWAY_TIMEOUT;
HTTP_505_HTTP_VERSION_NOT_SUPPORTED;
HTTP_506_VARIANT_ALSO_NEGOTIATES;
HTTP_507_INSUFFICIENT_STORAGE;
HTTP_508_LOOP_DETECTED;
HTTP_509_BANDWIDTH_LIMIT_EXCEEDED;
HTTP_510_NOT_EXTENDED;
HTTP_511_NETWORK_AUTHENTICATION_REQUIRED;
```

### Helper functions

The following helper functions are available for identifying the category of the response code.

```js
import {
  isInformational,
  isSuccess,
  isRedirect,
  isClientError,
  isServerError,
} from 'simple-http-status';

isInformational(); // 1xx
isSuccess(); // 2xx
isRedirect(); // 3xx
isClientError(); // 4xx
isServerError(); // 5xx
```

### Others

For convenience this module also exports a [Method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) typescript enum:

```ts
export enum Method {
  GET = 'GET',
  HEAD = 'HEAD',
  POST = 'POST',
  PUT = 'PUT',
  DELETE = 'DELETE',
  CONNECT = 'CONNECT',
  OPTIONS = 'OPTIONS',
  TRACE = 'TRACE',
  PATCH = 'PATCH',
}
```
