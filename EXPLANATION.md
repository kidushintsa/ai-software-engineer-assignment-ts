# Bug Explanation

## 1. What was the bug?

`HttpClient` only refreshed the token when it was `null` or when an `OAuth2Token` instance was expired. If the token was a plain object (e.g. `{ accessToken, expiresAt }`), it was truthy but not an `OAuth2Token` instance, so the refresh logic was skipped.

## 2. Why did it happen?

The condition relied on `instanceof OAuth2Token`. Plain objects with the same fields were not considered invalid, so the refresh condition did not trigger.

## 3. Why does the fix solve it?

The condition now refreshes the token when it is **not an instance of `OAuth2Token`** or when it has expired. This ensures invalid token states are replaced with a proper `OAuth2Token`.

## 4. Remaining edge case

Tests do not cover a case where a plain object token has a valid future expiration time but is still not an `OAuth2Token` instance.
