<!-- loioc6b49c938e974e93ae5f1b17d6eb8479 -->

# 401 Unauthorized or 403 Forbidden



<a name="loioc6b49c938e974e93ae5f1b17d6eb8479__section_fpd_5hr_v2c"/>

## Symptom

When you try to reach a service, you get ***401 Unauthorized*** or ***403 Forbidden*** in response.



<a name="loioc6b49c938e974e93ae5f1b17d6eb8479__section_rks_whr_v2c"/>

## Cause

The error ***401 Unauthorized*** occurs when you try to access a Service that requires authentication, and the appropriate credentials were not provided or were incorrect. You get the error ***403 Forbidden*** when you try to access a Service or perform an action for which you lack permission.



<a name="loioc6b49c938e974e93ae5f1b17d6eb8479__section_sbh_zhr_v2c"/>

## Solution

Make sure that you are using an active JSON Web Token \(JWT\) with proper scopes.

1.  Decode the JWT.
2.  Check the validity and scopes of the JWT:

    ```
    {
       "sub": ********,
       "scp": "test",
       "aud": ********,
       "iss": ******,
       "exp": 1697120462,
       "iat": ******,
       "jti": ******,
    }
    ```

3.  [Generate a new JWT](https://kyma-project.io/#/api-gateway/user/tutorials/01-50-expose-and-secure-a-workload/01-51-get-jwt) if needed.

