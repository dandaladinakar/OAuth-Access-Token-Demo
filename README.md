# OAuth-Access-Token-Demo
This project demonstrates how to use the OAuth API to get access tokens and retrieve course details.

## Table of Contents

- [1. Overview](#1-overview)
- [2. Getting Started](#2-getting-started)
  - [2.1 Get Access Token](#21-get-access-token)
  - [2.2 Get Course Details](#22-get-course-details)
- [3. Test Cases](#3-test-cases)
- [4. Contributing](#4-contributing)


## 1. Overview

This project helps you learn how to work with the OAuth API. It allows you to obtain access tokens and use them to access protected information.

## 2. Getting Started

### 2.1 Get Access Token

- **HTTP Method**: `POST`
- **URL**: `https://rahulshettyacademy.com/oauthapi/oauth2/resourceOwner/token`

#### Form Parameters (in Postman)

In Postman, set the request to **POST** and do the following:

- **Body Type**: `form-data`
- **Parameters**:
  - `client_id`: Your client ID
  - `client_secret`: Your client secret
  - `grant_type`: `client_credentials`
  - `scope`: `trust`

#### Steps:
1. Set the method to **POST**.
2. Go to the **Body** tab and choose **form-data**.
3. Enter the parameters listed above.
4. Click **Send** to get your access token.

### 2.2 Get Course Details

- **HTTP Method**: `GET`
- **URL**: `https://rahulshettyacademy.com/oauthapi/getCourseDetails`

#### Query Parameter:
- `access_token`: Use the token obtained from the first step.

#### Steps:
1. Set the method to **GET**.
2. Add the access token to the URL as a query parameter.
3. Click **Send** to see the course details.

## 3. Test Cases

The following test cases were executed to validate the OAuth API integration:

| Test Case ID | Description                                          | URL                                                | Method | Request Body                                                                                       | Expected Response                                                           | Status  |
|---------------|----------------------------------------------------|----------------------------------------------------|--------|----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|---------|
| TC_OAuth_001  | Check token creation with correct info             | `https://rahulshettyacademy.com/oauthapi/oauth2/resourceOwner/token` | POST   | `client_id=correct_id&client_secret=correct_secret&grant_type=client_credentials&scope=trust`   | 200 OK and a valid access token                                             | Pass    |
| TC_OAuth_002  | Check token creation with wrong client ID          | `https://rahulshettyacademy.com/oauthapi/oauth2/resourceOwner/token` | POST   | `client_id=wrong_id&client_secret=correct_secret&grant_type=client_credentials&scope=trust`      | 401 Unauthorized and a message about invalid client ID                     | Pass    |
| TC_OAuth_003  | Check token creation with missing info             | `https://rahulshettyacademy.com/oauthapi/oauth2/resourceOwner/token` | POST   | `client_id=correct_id&client_secret=&grant_type=&scope=trust`                                   | 400 Bad Request with a message about missing information                   | Fail    |
| TC_OAuth_004  | Check token creation with wrong grant type         | `https://rahulshettyacademy.com/oauthapi/oauth2/resourceOwner/token` | POST   | `client_id=correct_id&client_secret=correct_secret&grant_type=wrong_grant&scope=trust`          | 401 Unauthorized with a message about the wrong grant type                 | Pass    |
| TC_OAuth_005  | Check access to course details with valid token    | `https://rahulshettyacademy.com/oauthapi/getCourseDetails`           | GET    | N/A                                                                                                | 200 OK and see course details in the response                              | Pass    |
| TC_OAuth_006  | Check access to course details with expired token  | `https://rahulshettyacademy.com/oauthapi/getCourseDetails`           | GET    | N/A                                                                                                | 401 Unauthorized with a message about the expired token                    | Pass    |
| TC_OAuth_007  | Check access to course details with invalid token  | `https://rahulshettyacademy.com/oauthapi/getCourseDetails`           | GET    | N/A                                                                                                | 401 Unauthorized with a message about the invalid token                    | Pass    |
| TC_OAuth_009  | Check course details without token                  | `https://rahulshettyacademy.com/oauthapi/getCourseDetails`           | GET    | N/A                                                                                                | 400 Bad Request with a message about the missing token                     | Fail    |


## 4. Contributing
Feel free to help out! You can make changes or suggest improvements.



