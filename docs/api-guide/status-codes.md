# Status Codes

Flask API includes a set of named constants that you can use to make more code more obvious and readable.

    from flask_api import status

    ...

	@app.route('/empty-view/')
    def empty_view(self):
        content = {'please move along': 'nothing to see here'}
        return content, status.HTTP_404_NOT_FOUND

The full set of HTTP status codes included in the `status` module is listed below.

The module also includes a set of helper functions for testing if a status code is in a given range.

    from flask_api import status
	import unittest
	
	...

	class ExampleTestCase(unittest.TestCase):
        def test_success(self):
            with app.test_client() as client:
                response = client.get('/')
	            self.assertTrue(status.is_success(response.status_code))

For more information on proper usage of HTTP status codes see [RFC 2616][rfc2616]
and [RFC 6585][rfc6585].

## Informational - 1xx

This class of status code indicates a provisional response.  There are no 1xx status codes used in REST framework by default.

    HTTP_100_CONTINUE
    HTTP_101_SWITCHING_PROTOCOLS

## Successful - 2xx

This class of status code indicates that the client's request was successfully received, understood, and accepted.

    HTTP_200_OK
    HTTP_201_CREATED
    HTTP_202_ACCEPTED
    HTTP_203_NON_AUTHORITATIVE_INFORMATION
    HTTP_204_NO_CONTENT
    HTTP_205_RESET_CONTENT
    HTTP_206_PARTIAL_CONTENT

## Redirection - 3xx 

This class of status code indicates that further action needs to be taken by the user agent in order to fulfill the request.

    HTTP_300_MULTIPLE_CHOICES
    HTTP_301_MOVED_PERMANENTLY
    HTTP_302_FOUND
    HTTP_303_SEE_OTHER
    HTTP_304_NOT_MODIFIED
    HTTP_305_USE_PROXY
    HTTP_306_RESERVED
    HTTP_307_TEMPORARY_REDIRECT

## Client Error - 4xx

The 4xx class of status code is intended for cases in which the client seems to have erred.  Except when responding to a HEAD request, the server SHOULD include an entity containing an explanation of the error situation, and whether it is a temporary or permanent condition.

    HTTP_400_BAD_REQUEST
    HTTP_401_UNAUTHORIZED
    HTTP_402_PAYMENT_REQUIRED
    HTTP_403_FORBIDDEN
    HTTP_404_NOT_FOUND
    HTTP_405_METHOD_NOT_ALLOWED
    HTTP_406_NOT_ACCEPTABLE
    HTTP_407_PROXY_AUTHENTICATION_REQUIRED
    HTTP_408_REQUEST_TIMEOUT
    HTTP_409_CONFLICT
    HTTP_410_GONE
    HTTP_411_LENGTH_REQUIRED
    HTTP_412_PRECONDITION_FAILED
    HTTP_413_REQUEST_ENTITY_TOO_LARGE
    HTTP_414_REQUEST_URI_TOO_LONG
    HTTP_415_UNSUPPORTED_MEDIA_TYPE
    HTTP_416_REQUESTED_RANGE_NOT_SATISFIABLE
    HTTP_417_EXPECTATION_FAILED
    HTTP_428_PRECONDITION_REQUIRED
    HTTP_429_TOO_MANY_REQUESTS
    HTTP_431_REQUEST_HEADER_FIELDS_TOO_LARGE

## Server Error - 5xx

Response status codes beginning with the digit "5" indicate cases in which the server is aware that it has erred or is incapable of performing the request.  Except when responding to a HEAD request, the server SHOULD include an entity containing an explanation of the error situation, and whether it is a temporary or permanent condition.

    HTTP_500_INTERNAL_SERVER_ERROR
    HTTP_501_NOT_IMPLEMENTED
    HTTP_502_BAD_GATEWAY
    HTTP_503_SERVICE_UNAVAILABLE
    HTTP_504_GATEWAY_TIMEOUT
    HTTP_505_HTTP_VERSION_NOT_SUPPORTED
    HTTP_511_NETWORK_AUTHENTICATION_REQUIRED

## Helper functions

The following helper functions are available for identifying the category of the response code.

    is_informational()  # 1xx
    is_success()        #??2xx
    is_redirect()       # 3xx
    is_client_error()   # 4xx
    is_server_error()   # 5xx

[rfc2616]: http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html
[rfc6585]: http://tools.ietf.org/html/rfc6585
