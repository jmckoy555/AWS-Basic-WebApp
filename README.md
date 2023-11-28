# AWS Web App
Using AWS to build a static web application that displays text based on a custom input provided by the user. Using the below architecture we created an application using the following AWS Services:
* AWS Amplify - Deployment of code base
* Amazon API Gateway - Creation and deployment of API used.
* AWS Lambda - Creation of Lambda functions to trigger API calls, DynamoDB data entries, and response to the user webpage
* AWS IAM - Creation of roles and policies attached to Lambda and DynamoDB
![Tut43](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/0e4e3493-22cc-4f46-a41c-52c24b9e72b0)

1) Create the web app. In this portion we use VS Code as a text editor to code our static website to start and delpoy the code file in AWS Amplify giving us
   the ablity to test in a development env and deploy new versions easily.
![Tut1](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/dfabcc1c-2b2f-4221-b35f-b1e296355427)
![Tut3](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/86eb867b-0e6e-44ad-b201-5358b09ffaeb)
![Tut4](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/bcdffd11-9155-4f1e-af6f-d5ea8dbaa29d)
![Tut5](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/45b825a6-bb49-42f4-b533-2bdf6f20e7d1)

2) Here we build our serverless Lambda function in Python and test our function. This function will be used later to add functionality to our web app.
![Tut7](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/6c5c57c6-6807-4773-8fdb-e8507aeab808)
![Tut8](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/1af28d5e-25c5-4751-91e6-887f36d22ba2)

** We created a function in Python and have deployed these changes. Now we configure our test to take in certain test parameters to make sure our function works correctly.
** This function takes the first and last name given to it and returns it to as a JSON object.
![Tut10](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/d930608c-3a4f-45f2-bc69-e163680d2e3e)
![Tut11](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/c2fef890-88d6-4043-ad19-86fd5d5b3853)
Note: This test returns the same name in the JSON object that was given in the test parameters.
![Tut12](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/68c57074-ec41-4635-a592-07151091f92a)

3) Now we use Amazon API gateway to create a RESTful API that will allow us to make calls to the Lambda function from a user's web browser.
![Tut14](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/2032e1d1-d0da-417c-ac91-2fc637fa0320)
   - Create a new API
     ![Tut15](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/a21fc852-9e63-491d-bcd2-a89e05bc58c0)
   - Define HTTP methods on the API 
      ![Tut17](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/da335313-d310-493f-8410-42f811c1f8d0)
   - Test and validate our API's response method is in line with what our Lambda function does
     ![Tut24](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/ef2464a5-4937-4dbe-8766-2e5f3b94e63e)
     ![Tut23](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/f3243ebd-abbd-416a-bdad-d3ef844dcd63)
4) Create a DynamoDB table to persist data. We also use AWS IAM to give our Lambda function permission to write to our DynamoDB table.
   - Create our table. ** Note the ARN (Amazon Resource Name). This will be needed to give our Lambda function proper permissions.
    ![Tut26](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/f1a9eb5f-bad4-4aff-9c4c-eca16eb6a29a)
   ![Tut27](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/b730f73f-2b1d-4ab1-9588-50166508add4)
- Change the IAM permissions to our HelloWorldFunction and attaching inline policies for DynamoDB access.
![tut29](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/de23dfa5-f94b-47ed-a78b-860aad4b6bb7)
![Tut32](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/bfd03ad6-1a29-4698-9145-f03c815dd76d)
![Tut33](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/615aea12-f735-4147-8748-2755be60272b)
- Now we update our Lambda function using Python to write to our DynamoDB table and test the changes.
  ![tut31](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/4ffa87ab-f0b7-4ddc-8ba6-2f59de92a9f2)
  ![Tut34](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/c93492fe-7e98-4a86-adef-967ce282ec46)

5) Here we update our static website to invoke the REST API we created. This will give us the ability to display text
   based on what the user inputs.
   - Updated code in VS code with our API call that will be uploaded to AWS Amplify
  ![tut37](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/c36b9d4a-d7f5-42b4-a6b4-1146b6750d5e)
   - Test newly deployed changes. The user should be able to type in their name and a in browser alert should pop up
     with a message and the user input.
![tut38](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/f8b0617e-af94-4a04-9613-5eaec796cbf8)
![Tut40](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/437df671-cd7d-4093-a63d-dd0ffeaacd20)
![Tut41](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/18d1b65c-074e-4874-a0a8-7913fce53005)
![Tut42](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/db862e33-2649-42b2-bef2-0ebeab589a52)


We now have a working web application that makes a call to our API, which triggers the AWS Lambda function. The Lambda function writes to our DynamoDB database and returns a message to the client via the API gateway.
![Tut43](https://github.com/jmckoy555/AWS-Basic-WebApp/assets/72049114/22a4f02e-79b8-4f9c-b95c-82cc73789646)


