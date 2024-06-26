# API Documentation

## Register
<pre>POST /register</pre>

- Body Request
  ```
  {
      "name": "Charlie",
      "email": "charlie@example.com",
      "pass": "password",
      "age": 20
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
      "data": [
          {
              "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjUsImlhdCI6MTcxODcyMjg0NH0.LFv5Of9mgWmWUkuo0yWxARsH1DGxsOQRKwC7kacm0oo"
          },
          {
              "userData": {
                  "user_id": 5,
                  "user_name": "Charlie Davis",
                  "user_email": "charlie.davis@example.com",
                  "user_age": 40,
                  "user_height": 170,
                  "user_weight": 68,
                  "sugar_limit": 55
              }
          }
      ]
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

- Headers Request
  ```
  Key: Authorization
  Value: Bearer <tokenValue>
  ```

- Body Request
  ```
  {
      "name": "Charlie Davis",
      "age": 40,
      "height": 170.0,
      "weight": 68.0,
      "limit": 55
  }
  ```

- Response
  ```
  {
      "status": "success",
      "message": "update successful"
  }
  ```

## History
<pre>GET /history</pre>

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
      "data": [
          {
              "scan_id": 6,
              "scan_date": "2024-06-05T17:00:00.000Z",
              "scan_consume": 1,
              "user_id": 5,
              "product_id": 6,
              "product_name": "Broccoli",
              "product_category": "Vegetable",
              "product_type": "Fresh",
              "product_grade": "B",
              "serving_size": 85,
              "serving_pack": 1,
              "serving_sugar": 1,
              "total_sugar": 1,
              "image_url": "https://storage.googleapis.com/sts-dummy-image/dummy-image/01-silverqueen-dark.jpeg"
          },
          {
              "scan_id": 7,
              "scan_date": "2024-06-05T18:00:00.000Z",
              "scan_consume": 0,
              "user_id": 5,
              "product_id": 7,
              "product_name": "Chocolate Bar",
              "product_category": "Snack",
              "product_type": "Processed",
              "product_grade": "F",
              "serving_size": 50,
              "serving_pack": 1,
              "serving_sugar": 25,
              "total_sugar": 25,
              "image_url": "https://storage.googleapis.com/sts-dummy-image/dummy-image/01-silverqueen-dark.jpeg"
          }
      ]
  }
  ```

## History Detail
<pre>GET /history/{scanId}</pre>

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
      "data": [
          {
              "scan_id": 6,
              "scan_date": "2024-06-05T17:00:00.000Z",
              "scan_consume": 1,
              "user_id": 5,
              "product_id": 6,
              "product_name": "Broccoli",
              "product_category": "Vegetable",
              "product_type": "Fresh",
              "product_grade": "B",
              "serving_size": 85,
              "serving_pack": 1,
              "serving_sugar": 1,
              "total_sugar": 1,
              "image_url": "https://storage.googleapis.com/sts-dummy-image/dummy-image/01-silverqueen-dark.jpeg"
          }
      ]
  }
  ```

## Grade
<pre>GET /grade/{gradeId}</pre>

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
          "grade_id": 1,
          "grade_name": "Grade A",
          "grade_desc": "Drinks with grade A contain little sugar, no sweeteners, and little saturated fat content. On average it only contains less than 1g of sugar per 100 ml."
      }
  }
  ```

## Scan
<pre>POST /scan</pre>

- Headers Request
  ```
  Key: Authorization
  Value: Bearer <tokenValue>
  ```

- Body Request
  ```
  {
      "predictedClass": "8992753033713"
  }
  ```

- Response
  ```
  {
      "status": "success",
      "message": "image predicted",
      "data": [
          {
              "productResult": {
                  "product_id": 11,
                  "product_name": "Frisian Flag",
                  "product_category": "Minuman",
                  "product_type": "Susu UHT Strawberry Low Fat",
                  "product_grade": "C",
                  "serving_size": 225,
                  "serving_pack": 1,
                  "serving_sugar": 21,
                  "total_sugar": 21,
                  "image_url": "https://storage.googleapis.com/sts-dummy-image/dummy-image/frisian-flag-susu-uht-strawberry-low-fat.jpg",
                  "product_barcode": "8992753033713"
              }
          },
          {
              "recResults": [
                  {
                      "rec_id": 3,
                      "product_barcode": "8992753033713",
                      "rec_product": "8992753033713",
                      "product_id": 11,
                      "product_name": "Frisian Flag",
                      "product_category": "Minuman",
                      "product_type": "Susu UHT Strawberry Low Fat",
                      "product_grade": "C",
                      "serving_size": 225,
                      "serving_pack": 1,
                      "serving_sugar": 21,
                      "total_sugar": 21,
                      "image_url": "https://storage.googleapis.com/sts-dummy-image/dummy-image/frisian-flag-susu-uht-strawberry-low-fat.jpg"
                  },
                  {
                      "rec_id": 2,
                      "product_barcode": "8992753033713",
                      "rec_product": "8992753033713",
                      "product_id": 11,
                      "product_name": "Frisian Flag",
                      "product_category": "Minuman",
                      "product_type": "Susu UHT Strawberry Low Fat",
                      "product_grade": "C",
                      "serving_size": 225,
                      "serving_pack": 1,
                      "serving_sugar": 21,
                      "total_sugar": 21,
                      "image_url": "https://storage.googleapis.com/sts-dummy-image/dummy-image/frisian-flag-susu-uht-strawberry-low-fat.jpg"
                  },
                  {
                      "rec_id": 1,
                      "product_barcode": "8992753033713",
                      "rec_product": "8992753033713",
                      "product_id": 11,
                      "product_name": "Frisian Flag",
                      "product_category": "Minuman",
                      "product_type": "Susu UHT Strawberry Low Fat",
                      "product_grade": "C",
                      "serving_size": 225,
                      "serving_pack": 1,
                      "serving_sugar": 21,
                      "total_sugar": 21,
                      "image_url": "https://storage.googleapis.com/sts-dummy-image/dummy-image/frisian-flag-susu-uht-strawberry-low-fat.jpg"
                  }
              ]
          }
      ]
  }
  ```

## Consume
<pre>PUT /consume</pre>

- Headers Request
  ```
  Key: Authorization
  Value: Bearer <tokenValue>
  ```

- Body Request
  ```
  {
      "consumeSugar": 15
  }
  ```

- Response
  ```
  {
      "status": "success",
      "message": "update successful"
  }
  ```

## Track
<pre>GET /track</pre>

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
          "user_name": "Charlie Davis",
          "sugar_limit": 55,
          "consume_sugar": 35,
          "consume_date": "2024-06-11T00:00:00.000Z"
      }
  }
  ```
