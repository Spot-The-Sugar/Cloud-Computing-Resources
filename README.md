# API Documentation

## Register
<pre>POST /register</pre>

- Body Request
  ```
  {
      "name": "Charlie Davis",
      "email": "charlie.davis@example.com",
      "pass": "password"
  }
  ```

- Response
  ```
  {
      "status": "success",
      "message": "User created successfully"
  }
  ```

## Login
<pre>POST /login</pre>

- Body Request
  ```
  {
      "email": "charlie.davis@example.com",
      "pass": "password"
  }
  ```

- Response
  ```
  {
      "status": "success",
      "message": "login successful",
      "data": {
          "token": "<tokenValue>"
      }
  }
  ```

## Profile
<pre>GET /profile</pre>

- Headers Request
  ```
  Key: Authorization
  Value: Bearer <tokenValue>
  ```

- Response
  ```
  {
      "status": "success",
      "message": "read successful",
      "data": {
          "user_id": 5,
          "user_name": "Charlie Davis",
          "user_email": "charlie.davis@example.com",
          "user_age": null,
          "user_height": null,
          "user_weight": null,
          "sugar_limit": null
      }
  }
  ```

## Edit Profile
<pre>PUT /profile/edit</pre>

## History
<pre>GET /history</pre>

## History Detail
<pre>GET /history/{scanId}</pre>

## Grade
<pre>GET /grade/{gradeId}</pre>

## Track
<pre>GET /track</pre>

## Scan
<pre>Not Available Yet</pre>

## Consume
<pre>PUT /consume</pre>


