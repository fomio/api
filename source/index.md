---
title: User Poll API Documentation

language_tabs:
  - code

toc_footers:
  - <a href='#'>Sign Up for a API Key</a>

includes:
  - http_codes

search: true
---

# Introduction

> User Poll

```shell
# Welcome to Fom.io
```
Hassel free User Polls & Surveys in minutes.

This API is in <sup>Beta</sup> phase. We would like you to give it a try. Please [Sign Up](#) here to get an API Key.


# Authentication

> Example Form:

```html
<form action="http://fom.io/s/fd9d" method="POST">
  <input type="hidden" name="utf8" value="β">
  <input type="text" name="name" placeholder="Name">
  <input type="submit" name="submit">
</form>
```


To interact with User Poll API, you will need an API Keys. You can receive the API key by [Signing Up](#) here.

Authentication is done via HTTP Basic authentication. We expect for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token="YOUR-API-KEY`

<aside class="notice">
You must replace `YOUR-API-KEY` with your private API key.
</aside>


# NPS<sup>&reg;</sup> Survey

## Send survey right away


> Example Request

```shell
curl https://api.userpoll.io/v1/send_survey \
      -H 'Authorization: Token token="YOUR-API-KEY"' \
      -H 'Content-Type: application/json' \
      -d '{ "survey_id":"1001", "email":"fake@email.com" }'
```

> <span style="color: #2ecc71">Success Resonse</span>

```json
{
  "status": "success",
  "message": "Email Successfully Sent"
}
```

> <span style="color: #e74c3c">Error Resonse</span>

```json
{
  "status": "error",
  "type": "invalid_params",
  "message": "Invalid Parameter/s",
  "params": {
    "survey_id": "Invalid Survey ID",
    "email": "Invalid Email Address"
  }
}
```

Send NPS<sup>&reg;</sup> right away to your customer.

For Example:-
In case of ecommerce store, sending this survey email could be helpful to get the response from the customer who just received an order.

### HTTP Request

`POST https://api.userpoll.io/send_survey`

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
survey_id | false | Survey you created. `survey_id` is available on your dashboard.
email | true | Your email by default (Used to send a test email). Provide customer email address to send email to customer.

<aside class="success">
  Remember — <code>survey_id</code> and <code>email</code> both are required!
</aside>

## Send survey at certain time


> Example Request

```shell
curl https://api.userpoll.io/v1/send_survey \
      -H 'Authorization: Token token="YOUR-API-KEY"' \
      -H 'Content-Type: application/json' \
      -d '{ "survey_id":"1001", "email":"fake@email.com", "wait_for": "8.hours" }'
```

> <span style="color: #2ecc71">Success Resonse</span>

```json
{
  "status": "success",
  "message": "Email Successfully Sent"
}
```

> <span style="color: #e74c3c">Error Resonse</span>

```json
{
  "status": "error",
  "type": "invalid_params",
  "message": "Invalid Parameter/s",
  "params": {
    "survey_id": "Invalid Survey ID",
    "email": "Invalid Email Address",
    "wait_for": "Invalid Wait Time"
  }
}
```

Send NPS<sup>&reg;</sup> at a certain time / interval to your customer.

For Example:-
This endpoint may come handy when scheduling the survey email to be sent at certain time or interval. eg. `2.days` , `5.hours`, `1.week` etc.

### HTTP Request

`POST https://api.userpoll.io/send_survey`

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
survey_id | false | Survey you created. `survey_id` is available on your dashboard.
email | true | Your email by default (Used to send a test email). Provide customer email address to send email to customer.
wait_for | false | It allows you to wait before sending the survey. Accepts, day(s), week(s), month(s).

<aside class="notice">
  Note — <code>wait_for</code> is optional!
</aside>

