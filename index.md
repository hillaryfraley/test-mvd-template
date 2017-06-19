---
layout: home
---

<h2>Template Instructions</h2>

This template is a fill-in-the-blank framework for developing basic API documentation. The idea is to replace all of the [prompts in brackets] with content that's specific to your API. When you've replaced all the bracketed prompts, you'll have the essentials documented sufficiently to help people use your API.

If something in this template doesn't make sense for your API, delete it! And likewise, make sure to add any sections you need based on your API's particulars. We hope our suggestions in this template will spark more ideas about documenting features of your API to help users consume it.

The template is written in [Markdown](https://daringfireball.net/projects/markdown/). Some options for publishing are listed at the bottom of the template.]

If you're interested in ideas for moving beyond basic API documentation, check out [this article](link to API doc checklist article).

# [Name of API] API Documentation

Welcome to the documentation for [name of API]! [Name of API] is a [type - RESTful, SOAP, platform-based] API that you can use to:

* [Brief example use case - 1 sentence]
* [Brief example use case - 1 sentence]
* ...

[Name of API] uses [protocol for requests, such as HTTP protocols `GET`, `POST`, `PUT`, and `DELETE`]. Responses are returned in [language] format. [Other items to mention about requests and responses, if applicable: whether users can specify the response language using the `ACCEPT` header.]

To access [name of API], you'll need [describe access requirements, which might include an account with your product, an authentication token, username/password, or other credentials].

The base URL is [your API's base URL]. Each user is limited to [number] requests per second. If you exceed this rate limit, [explain what happens if rate limit is exceeded---for example, will users see an error response?].

## Authentication

[Details in this section will vary based on your authentication method, but make sure to explain these things:

* If your API requires an authentication token or key, how do users get one?
* If authentication tokens or keys expire, what's the expiration interval? How do users refresh expired tokens or keys?
* How do users pass authentication information to your API? For example, do they use an Authorization header?

The prompts in this section assume that users will need an authentication token and the token should be kept private.]

You'll need to include an [authentication token] with all of your requests to [name of API]. Anyone with your [authentication token] can access your data through our API, so keep your [authentication token] private. Don't share it with other users, and make sure to remove it from any code samples.

To get your [authentication token], [explain how to get the token---for example, contact Customer Support, send a call with your username and password to the API, or go to your account at our website].

[Authentication tokens] expire [list expiration interval - for example, every 2 weeks or after 1 year]. If your [authentication token] expires, [explain how to refresh - for example, contact Customer Support or go to your customer account and click "Refresh Token"].

To pass your authentication information with your API requests, [explain how to pass authentication token---for example, use the authorization header in cURL].

## Workflows

[In *Workflows*, describe the optimal or assumed workflows for a few things users can accomplish with your API. Think about the most common and highest-impact outcomes. Each workflow should walk users through a brief explanation, any prerequisites, and the steps involved in completing the outcome with your API, including the reasons users must take each step and the API call required to finish the step.

Here's an example workflow for an API that allows you to retrieve and update timesheet records.

### Example Workflow: Add a description to explain overtime on employee's timesheet

You asked an employee, Meghan, to work 2 hours of overtime last Thursday. To make sure Payroll approves Meghan's timesheet with the extra 2 hours, you need to add a description.

To complete this outcome, you need Meghan's employee ID number and your authentication token for the API.

1. First, retrieve the record for Meghan's timesheet for last Thursday. Send a request to the `GET` https://api.payrollrecord.com/timesheet endpoint. Your request must include Meghan's employee ID number and the date as query parameters. Here's the complete request in cURL:

``` curl
curl --request GET \
  --url 'https://api.payrollrecord.com/timesheet?employee={employee ID number}&date=2017-05-25' \
  --header 'authorization: {your authentication token}'
```

2. The JSON object in the response will include a unique ID for the timesheet for last Thursday, `timesheet_ID`. Note this ID---you will use it in the next request.

3. Send a request to the `PUT` https://api.payrollrecord.com/timesheet endpoint. Your request must include the `timesheet_ID` as a query parameter and the description you want to add in the request body. Here's the complete request in cURL:

``` curl
curl --request PUT \
  --url 'https://api.payrollrecord.com/timesheet?timesheet_id={timesheet ID number}' \
  --header 'authorization: {your authentication token}' \
  --header 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  --form 'description=Employee worked 2 hours of overtime to complete data entry. Overtime approved by {your name}.'
```

Now, if you send another request for Meghan's timesheet for May 25, 2017 (like you did in Step 1), you will see the description you added at the end of the JSON object in the response.]


## Code Samples

[In *Code Samples*, provide a few complete code samples or snippets that users can copy and paste for common use cases. The idea is that your code samples will help users understand how to write their own code for your API.

You can start with cURL command line code samples, but you should also add code samples in other languages to address common needs, such as JavaScript for web browser code and Java and Swift for mobile developers.]


## Reference

[The *Reference* includes all the information users need to know to use your endpoints. That means you'll repeat the information below for each endpoint in your API.]

### [Description of what the endpoint does, such as "Retrieve a record" or "Delete a user"]

#### HTTP Method and URL

[`GET`, `PUT`, `POST`, or `DELETE` and URL---for example, `GET` https://api.payrollrecord.com/timesheet]

#### Parameters

[Table that lists all query and path parameters for the endpoint]

Name | Type | Description | Required
---- | ---- | ----------- | --------
[Name of parameter] | [query or path] | [Brief description of parameter's function - what does it do?] | [Required or Optional]
[Name of parameter] | [query or path] | [Brief description of parameter's function - what does it do?] | [Required or Optional]
[Name of parameter] | [query or path] | [Brief description of parameter's function - what does it do?] | [Required or Optional]
...

#### Example Request

[Code or pseudocode sample of a complete request for this endpoint, including header and body, followed by a table that lists each element in the example request]

Element | Type | Description | Required
------- | ---- | ----------- | --------
[Element as it appears in request] | [array, object, string, integer, or float] | [Brief description of what information the element represents, including default and valid values] | [Required or Optional]
[Element as it appears in request] | [array, object, string, integer, or float] | [Brief description of what information the element represents, including default and valid values] | [Required or Optional]
[Element as it appears in request] | [array, object, string, integer, or float] | [Brief description of what information the element represents, including default and valid values] | [Required or Optional]
...

#### Example Response

[Code or pseudocode sample of a complete response for this endpoint, followed by a table that lists each element in the example response]

Element | Type | Description
------- | ---- | -----------
[Element as it appears in response] | [array, object, string, integer, or float] | [Brief description of what information the element represents]
[Element as it appears in response] | [array, object, string, integer, or float] | [Brief description of what information the element represents]
[Element as it appears in response] | [array, object, string, integer, or float] | [Brief description of what information the element represents]
...

#### Error and Status Codes

[Table that lists all possible error and status codes for this endpoint]

Code | Message | Meaning
---- | ------- | -------
[HTTP code, such as "404"] | [Message for code, such as "Not Found"] | [Brief description of what the code means within your API, such as "We couldn't complete your request right now"]
[HTTP code, such as "404"] | [Message for code, such as "Not Found"] | [Brief description of what the code means within your API, such as "We couldn't complete your request right now"]
[HTTP code, such as "404"] | [Message for code, such as "Not Found"] | [Brief description of what the code means within your API, such as "We couldn't complete your request right now"]
...


## Publishing Options

Here are some options for publishing Markdown source files as HTML:

* [Jekyll](https://jekyllrb.com)
* [Hugo](https://gohugo.io)
* [MkDocs](http://www.mkdocs.org)
* [MDwiki](http://dynalon.github.io/mdwiki/#!index.md)

