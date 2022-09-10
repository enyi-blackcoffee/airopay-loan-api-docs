# airopay-loan-api-docs
This serves as a documentation to explain the various endpoints of the loan application

Each file in the root directory signifies an endpoint to call and how to go about it

- The first part signifies the call to make with "-H" being header property and "-X" being the method/verb
- The second part is a brief description of what the endpoint is all about.
- The body sample for POST requests. With required fields in * and sample data that is expected in each field.
- The body (description) field that explains what is to be expected in each key and how to source the data.
- The response body is the payload to expect in response to the request for the app to make its decisions and pass information to the user.
<br/>
<br/>
<br/>
<br/>

HOW TO USE

Always call the history with the customer's email address and three things could happen
```
1. You will get a (customer) "not found" error

{
    "code": 404,
    "status": "Not Found",
    "message": "Could not find any customer record with the email address",
    "result": []
}
```
this means you have to display blank fields and register for a new loan with the endpoint at the new_loan_request file in the root dir or you simply leave if the customer is not interested in taking a loan.
<br/>
<br/>
<br/>


```
2. You may get a (customer) "not authorised" error

{
    "code": 401,
    "status": "Not Authorized",
    "message": "You are not authorized to view, provide a valid jwtoken header with the request",
    "result": []
}
```
this means you are to present the jwtoken generated or revalidate it using the initial email address and salt provided at registeration.
<br/>
<br/>
<br/>


```
3. You get the standard response about the current loan 

{
    "code": 200,
    "status": "OK",
    "message": "",
    "result": {
      "latest_loan_status": "DISBURSED_AND_ACTIVE",
      "latest_loan_details": {
        "universal_id": "3099006069168228088069108",

          . . .
        },
      }
    }
}
```
At this point, you can now display user screens according to the latest_loan_status constant and other values within the response body. Refere to the history file in the root directory for more information)