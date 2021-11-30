# Test Plan

## Unit Testing

We currently are using unit tests written in Postman to send requests to our music service/recommendation service. The responses we receive back from the services are then tested to ensure we are getting the right output from the input we put in. We currently have two test collection, one for music service and the other for recommendation service. Within these collections show the requests that are labeled with the test case we are checking for. We include a route to hit the API endpoint we have within our service, any parameters we need to pass in or body if needed in the request. The tests run automatically when we receive the response to check that the response is what we were expecting. Some examples of this would be checking for the appropriate status code, response body attributes, list lengths, etc.…  Before running the test collection we need to make sure we import the testing environment. We currently have two enviornments, again one for the music service and one for the recommendation service. The environment contains environment variables needed to run the test collections appropriately. Within our CI/CD plan we explain with more detail how we automate our testing. Specific to the unit tests the unit tests are run whenever a developer opens a pull request to merge code into the main branch. We currently use GitHub for source control and the main branch is the source code to our services. By running the tests automatically on checking in the code we have the following benefits:

- Fast & free to run so we are making sure the test cases are constantly being checked against the code.
- We check in more accurate and efficient code.
- Spot problems earlier so it's less expensive to fix.
- Automated testing schedule to align with our CI plan.

## Integration Testing

We currently support integration testing by testing the connection between our UI to our services. With having two separate services and UI we need to make sure we can send requests and get responses appropriately.

## UI Testing

For the UI we are utilizing Selenium to do automated browser tests. The reason being is to increase confidence in the UI we are delivering to our end user despite already having unit and integration tests on our services. This can also lead to fewer production problems and lower level of costs when problems are caught early.
