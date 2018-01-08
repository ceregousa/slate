# Authentication

Cerego utilizes Bearer tokens to authenticate API calls. 

To easily acquire your Bearer token please log into your [Cerego](https://cerego.com/) account (that has permission for the calls you wish to make) and then [click here.](https://cerego.com/configuration)

On the configuration page you will be able to get your Bearer token that you will need to use for API calls.

Cerego expects the Bearer token to be included in all API requests to the server in a header. The header should look like:

`Authorization: Bearer cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U`

<aside class="notice">
You must replace <code>cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U</code> with your personal Bearer token.
</aside>

<aside class="warning">Please be aware that Cerego does NOT currently use OAuth2. It is not possible to perform API calls on an individual user level.</aside>
