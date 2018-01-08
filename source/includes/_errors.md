# Errors

Cerego uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your Bearer token is wrong.
403 | Forbidden -- The resource you requested is not available given your permissions.
404 | Not Found -- The specified resource could not be found.
410 | Gone -- The resource requested has been removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many resources! Slow down!
500 | Internal Server Error -- We had a problem with our server. If the problem persists, please email us at <support@cerego.com>.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
