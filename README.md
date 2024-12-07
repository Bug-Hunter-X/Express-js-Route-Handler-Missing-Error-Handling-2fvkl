# Express.js Route Handler Missing Error Handling

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  Specifically, the `/users/:id` route doesn't handle cases where `req.params.id` is not a valid number or if no user with that ID exists. 

## Bug

The `bug.js` file contains the faulty code.  The route handler attempts to parse `req.params.id` as an integer and uses it to find a user in the `users` array. If `req.params.id` is not a valid number, `parseInt(userId)` will return `NaN`, leading to an error or unexpected behavior when trying to compare it to the numerical `user.id` in the array.  Similarly, if no user matches the provided ID, it fails to send an appropriate response and does not handle the case gracefully.

## Solution

The `bugSolution.js` file provides a corrected version of the route handler.  It includes comprehensive error handling:

- It checks if `req.params.id` can be parsed as an integer. If not, it sends a 400 Bad Request response.
- It checks if a user with the matching ID exists. If not, it sends a 404 Not Found response.

This improved error handling ensures the application remains robust and user-friendly.