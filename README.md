# Restful-Booker API Tests

Postman tests for [Restful-Booker](https://restful-booker.herokuapp.com/apidoc/index.html), covering authentication, booking management, and negative scenarios.

## Run

1. Import [API Testing.postman_collection.json](API%20Testing.postman_collection.json) into Postman.
2. Open the Collection Runner and run the entire collection in its saved order, starting with **Auth**.
3. Review the assertions and responses, then save the run results.

No environment file or manual variable setup is required. The collection generates a token and booking ID, then reuses them to update, verify, and delete that booking. A final GET confirms deletion with a 404 response.

## Coverage

- Status codes, JSON schemas, and booking field values.
- Invalid credentials and missing required booking fields.
- Invalid-token updates and deletions, plus retrieval after deletion.

If a run stops after creating a booking, delete that booking using its generated ID and token.

## Known Finding

In the recorded run, `Create_negative` returned **500 Internal Server Error** for missing required fields. Its assertion expects **400**, so the check failed. The expected 400 is the validation expectation used by the test.
