# Login API

StartFragmentThis API allows users to log in by providing valid credentials. Upon successful authentication, it returns an access token that must be used in subsequent requests to access protected resources within the system. This token verifies the user's identity and permissions.EndFragment

## 1\. URL

`http://127.0.0.1:8000/api/auth/login`

## 2\. Method

`POST`

## 3\. Requested Parameters

- `email`: The email address of the user attempting to log in.
    
- `password`: The password associated with the user's account.
    

## 4\. Required Parameters

- `email`
    
- `password`
    

### Query Parameters

| Parameter | Type | Description |
| --- | --- | --- |
| email | string | The email address of the user attempting to log in. |
| password | string | The password associated with the user's account. |

### Required Parameters

- `email`
    
- `password`
    

### Example Request

``` http
POST /api/auth/login?email=superadmin@email.com&password=12344321 HTTP/1.1
Host: 127.0.0.1:8000
Content-Type: application/json

 ```

### Response Fields (Success)

| Key | Type | Description |
| --- | --- | --- |
| status | string | Status of the authentication attempt. |
| dongle_id | int | Identifier for the user's dongle (if applicable). |
| access_token | string | The token to be used for authenticated requests. |
| token_type | string | The type of the token (e.g., Bearer). |
| expires_in | int | Duration in seconds until the token expires. |
| issued_at | int | Timestamp of when the token was issued. |
| ip_address | string | IP address of the user at the time of login. |
| location | string | Location of the user at the time of login. |

## 5\. Data Types

- `email`: string
    
- `password`: string
    

## 6\. JSON Responses

### Success Response

**Status Code:** 200 OK  
**Content-Type:** application/json

<img src="https://content.pstmn.io/5ea170ae-3ae9-4a62-a93a-406dc460242c/U2NyZWVuc2hvdCAyMDI1LTA4LTA0IDAxMjkyMC5qcGc=">

``` json
{
    "status": "",
    "dongle_id": 0,
    "access_token": "",
    "token_type": "",
    "expires_in": 0,
    "issued_at": 0,
    "ip_address": "",
    "location": ""
}

 ```

Error Responses

| HTTP Code | Description |
| --- | --- |
| 400 | Bad Request (missing or invalid parameters) |
| 401 | Unauthorized (invalid email or password) |
| 500 | Internal Server Error (unexpected error) |

**Status Code:** 401 Unauthorized  
**Content-Type:** application/json

<img src="https://content.pstmn.io/5a00a1d0-6ede-4367-8e7a-8c6a10d7535a/U2NyZWVuc2hvdCAyMDI1LTA4LTA0IDAxNDMyMS5qcGc=">

**Status Code:** 500 UInternal Server Error  
**Content-Type:** application/json

<img src="https://content.pstmn.io/53bd691a-6ced-435c-8cf0-57c8eda7053d/U2NyZWVuc2hvdCAyMDI1LTA4LTA0IDE4MDQ1Ny5qcGc=">

This endpoint allows users to authenticate and obtain an access token for subsequent requests. By providing valid credentials, users can log in and receive a token that grants access to protected resources.

## Error Responses

``` plaintext
+------------------+---------------------------+
| Status Code      | Description               |
+------------------+---------------------------+
| 400              | Bad Request               |
| 401              | Unauthorized              |
| 404              | Not Found                 |
| 500              | Internal Server Error     |
+------------------+---------------------------+

 ```

Ensure to provide valid credentials to avoid errors. For any issues, refer to the error responses section above.

This endpoint allows users to authenticate by logging in with their email and password. Upon successful authentication, the server responds with an access token and related information.

### Response

Upon a successful login, the API will return a JSON object with the following fields:

- `status` (string): The status of the login attempt (e.g., success or error message).
    
- `dongle_id` (integer): An identifier for the user's session or device.
    
- `access_token` (string): The token that must be included in the header of subsequent requests for authorization.
    
- `token_type` (string): The type of the token issued (e.g., Bearer).
    
- `expires_in` (integer): The duration in seconds for which the access token is valid.
    
- `issued_at` (integer): The timestamp indicating when the token was issued.
    
- `ip_address` (string): The IP address from which the login request was made.
    
- `location` (string): The geographical location associated with the login request.
    

### Notes

- Ensure that the email and password are correctly provided in the request to receive a valid token.
    
- The access token is required for accessing protected endpoints after successful login.
    

This endpoint is used to authenticate users by logging them in with their email and password. Upon successful authentication, the server responds with an access token that can be used for subsequent requests.
# Heartbeat API

StartFragmentThis API is used to send a heartbeat signal from a device. It helps the server identify the device, verify authorization, and track its current status and related information.EndFragment

## URL

`http://127.0.0.1:8000/api/`heartbeat

## Method

`POST`

## Query Parameters

| Parameter | Type | Description |
| --- | --- | --- |
| device_name | string | The name of the device sending the heartbeat. |

## Auth

No authentication is required for this endpoint.

## Success Response (200 OK)

<img src="https://content.pstmn.io/26b1a1e9-20cd-4158-b494-797ba49642f1/U2NyZWVuc2hvdCAyMDI1LTA4LTA1IDAxMjYwNC5qcGc=">

On a successful request, the server responds with a JSON object containing the following fields:

``` json
{
    "status": "",
    "message": "",
    "admin_id": 0,
    "device_name": "",
    "data": {
        "id": 0,
        "admin_id": 0,
        "name": "",
        "db_name": "",
        "db_user": "",
        "db_password": "",
        "db_server": "",
        "table_name": "",
        "gps_position": "",
        "gps_notes": "",
        "device_note": "",
        "send_email": "",
        "status": "",
        "shutdown_by": "",
        "created_at": "",
        "updated_at": ""
    },
    "checked_at": ""
}

 ```

- `status`: Status of the heartbeat request.
    
- `message`: Additional information regarding the request.
    
- `admin_id`: Identifier for the admin associated with the device.
    
- `device_name`: The name of the device that sent the heartbeat.
    
- `data`: Contains detailed information about the device and its state.
    
- `checked_at`: Timestamp of when the heartbeat was checked.
    

## Error Responses

The following error responses may be returned:

- **400 Bad Request**: The request was invalid or missing required parameters.
    
- **404 Not Found**: The specified endpoint does not exist.
    
- **500 Internal Server Error**: An unexpected error occurred on the server.
    

### Request

- **Method**: POST
    
- **URL**: `http://127.0.0.1:8000/api/heartbeat?device_name={device_name}`
    

#### Query Parameters

- `device_name` (string): The name of the device sending the heartbeat signal.
    

### Response

The response from the server will be in JSON format and will include the following fields:

- `status` (string): The status of the heartbeat request.
    
- `message` (string): A message providing additional information about the request.
    
- `admin_id` (integer): The ID of the administrator associated with the device.
    
- `device_name` (string): The name of the device that sent the heartbeat.
    
- `data` (object): Contains detailed information about the device, including:
    
    - `id` (integer): Unique identifier for the device.
        
    - `admin_id` (integer): The ID of the administrator associated with the device.
        
    - `name` (string): The name of the device.
        
    - `db_name` (string): The name of the database associated with the device.
        
    - `db_user` (string): The username for the database.
        
    - `db_password` (string): The password for the database.
        
    - `db_server` (string): The server address for the database.
        
    - `table_name` (string): The name of the table in the database.
        
    - `gps_position` (string): The GPS position of the device.
        
    - `gps_notes` (string): Any notes related to the GPS position.
        
    - `device_note` (string): Additional notes about the device.
        
    - `send_email` (string): Indicates whether an email should be sent.
        
    - `status` (string): The current status of the device.
        
    - `shutdown_by` (string): Information about who shut down the device, if applicable.
        
    - `created_at` (string): Timestamp of when the device was created.
        
    - `updated_at` (string): Timestamp of the last update to the device.
        
- `checked_at` (string): Timestamp of when the heartbeat was checked.
    

### Example Response

``` json
{
    "status": "",
    "message": "",
    "admin_id": 0,
    "device_name": "",
    "data": {
        "id": 0,
        "admin_id": 0,
        "name": "",
        "db_name": "",
        "db_user": "",
        "db_password": "",
        "db_server": "",
        "table_name": "",
        "gps_position": "",
        "gps_notes": "",
        "device_note": "",
        "send_email": "",
        "status": "",
        "shutdown_by": "",
        "created_at": "",
        "updated_at": ""
    },
    "checked_at": ""
}

 ```

This structure allows for comprehensive monitoring and management of devices through their heartbeat signals.

## Note

Ensure that the `device_name` parameter is correctly formatted and accurately reflects the device sending the heartbeat to avoid errors in processing the request.

This endpoint is used to send a heartbeat signal from a device to the server. It is typically used to indicate that the device is active and functioning correctly. The heartbeat request can include the name of the device, which helps in tracking and managing multiple devices.
# List API

StartFragmentThis API retrieves a list of log files stored on the server. It includes details such as filename, size, status (complete or not), last modified time, and a direct download link for each file.EndFragment

## URL

`http://127.0.0.1:8000/api/list`

## Method

`POST`

## Required Headers

- `Content-Type: application/json` (specifies the media type of the resource)
    

## Request Body Parameters

The request body must contain the following parameters:

- **name** (string): The name of the item to be added to the list.
    
- **size** (integer): The size of the item in bytes.
    
- **status** (string): The current status of the item.
    
- **modified** (string): The timestamp of the last modification.
    
- **download_url** (string): The URL where the item can be downloaded.
    

## Successful Response

A successful response will return a status code of `200` along with a JSON object containing the requested data.

<img src="https://content.pstmn.io/ff61b8e0-d74a-4908-8a26-f3c576682e5a/U2NyZWVuc2hvdCAyMDI1LTA4LTA0IDIyNTIzNy5qcGc=">

## Response Fields

The response JSON object will include the following fields:

- **status** (string): The status of the request.
    
- **message** (string): A message providing additional context.
    
- **data** (array): An array of objects, each representing an item with the following fields:
    
    - **name** (string): The name of the item.
        
    - **size** (integer): The size of the item.
        
    - **status** (string): The status of the item.
        
    - **modified** (string): The last modified timestamp of the item.
        
    - **download_url** (string): The URL to download the item.
        
- **checked_at** (string): The timestamp indicating when the data was last checked.
    

## Error Response Example

In case of an error, the response may contain a status code other than `200`, along with a JSON object that provides error details. Example:

``` json
{
    "status": "error",
    "message": "Invalid request parameters."
}

 ```

## Purpose / Usage

This endpoint is used to add items to a list and retrieve information about the added items. It is useful for managing and tracking items with specific attributes such as name, size, and download links.

This endpoint allows users to create a new list by sending a POST request to the specified URL. The request should include the necessary parameters to define the list being created.

### Request Parameters

The request body must be formatted as JSON and should include the following parameters:

- **name** (string): The name of the list to be created.
    
- **size** (integer): The size of the list.
    
- **status** (string): The current status of the list.
    
- **modified** (string): The timestamp indicating when the list was last modified.
    
- **download_url** (string): A URL from which the list can be downloaded.
    

### Response Structure

Upon a successful request, the server will respond with a JSON object containing the following fields:

- **status** (string): Indicates the status of the request.
    
- **message** (string): A message providing additional information about the request.
    
- **data** (array): An array containing the details of the created list, which includes:
    
    - **name** (string): The name of the created list.
        
    - **size** (integer): The size of the created list.
        
    - **status** (string): The current status of the created list.
        
    - **modified** (string): The timestamp of the last modification of the created list.
        
    - **download_url** (string): The URL to download the created list.
        
- **checked_at** (string): A timestamp indicating when the request was processed.
    

### Example Response

``` json
{
  "status": "",
  "message": "",
  "data": [
    {
      "name": "",
      "size": 0,
      "status": "",
      "modified": "",
      "download_url": ""
    }
  ],
  "checked_at": ""
}

 ```

This endpoint is essential for managing lists within the application, enabling users to create and retrieve their lists efficiently.

## Station API

StartFragmentThis API allows you to add a new station to the system. It requires authentication and expects a JSON payload containing the necessary station details such as name, location, and capacity.EndFragment

## URL

`http://127.0.0.1:8000/api/stations`

## Method

`POST`

## Request Parameters

This endpoint accepts the following parameters in the request body:

- **admin_id**: The identifier for the admin adding the station. (Integer)
    
- **station_name**: The name of the station being added. (String)
    
- **location**: The geographical location of the station. (String)
    
- **capacity**: The maximum capacity of the station. (Integer)
    

### Headers

- **Authorization**: `Bearer {access_token}` - Required for authenticated requests.
    
- **Content-Type**: `application/json` - Indicates that the request body contains JSON data.
    

## Required Fields

- `admin_id`
    
- `station_name`
    
- `location`
    
- `capacity`
    

## Parameter Types

- `admin_id`: Integer
    
- `station_name`: String
    
- `location`: String
    
- `capacity`: Integer
    

## Response (Success)

On a successful request, the server responds with a status code of `200` and a JSON object containing:

- `status`: Status of the request (String)
    
- `message`: A message providing additional information (String)
    
- `admin_id`: The ID of the admin who added the station (Integer)
    
- `data`: An array containing the details of the added station (Array)
    
- `checked_at`: Timestamp of when the operation was checked (String)
    

<img src="https://content.pstmn.io/e3d7882b-c6cd-4311-930a-d4ab44cf23ff/U2NyZWVuc2hvdCAyMDI1LTA4LTA0IDIxMzYxMy5qcGc=">

Example Response:

``` json
{
  "status": "",
  "message": "",
  "admin_id": 0,
  "data": [],
  "checked_at": ""
}

 ```

## Response (Error)

In case of an error, the server will return an appropriate status code along with a JSON object that includes:

- `status`: Status of the error (String)
    
- `message`: Description of the error (String)
    

<img src="https://content.pstmn.io/8d962e0a-0cfd-400b-ae24-15b4ca8cbd79/U2NyZWVuc2hvdCAyMDI1LTA4LTA0IDIxMzg0NS5qcGc=">

## Purpose / Usage

This endpoint is used to add a new station to the system. It requires the admin's ID and the details of the station to be added. Upon successful addition, it returns relevant information confirming the operation.

This endpoint allows users to add a new station to the system.

### Request Method

- **POST**
    

### Endpoint

- `http://127.0.0.1:8000/api/stations`
    

### Request Parameters

The request body must include the following parameters:

- **admin_id** (integer): The ID of the administrator adding the station.
    
- **status** (string): The status of the station being added.
    
- **checked_at** (string): A timestamp indicating when the station was checked.
    

### Expected Response

Upon a successful request, the server will respond with a status code of **200** and the following JSON structure:

``` json
{
    "status": "",
    "message": "",
    "admin_id": 0,
    "data": [],
    "checked_at": ""
}

 ```

- **status** (string): Indicates the status of the operation.
    
- **message** (string): Provides additional information about the operation.
    
- **admin_id** (integer): Echoes the ID of the administrator who added the station.
    
- **data** (array): An array that may contain additional information related to the added station.
    
- **checked_at** (string): The timestamp of when the station was last checked.
    

Ensure that all required parameters are included in the request body to receive the expected response.
# Shutdown API

StartFragmentThis API is used to initiate a remote shutdown command for a specific device. Once triggered, it generates a shutdown script and updates the device's status in the system. Authentication is required to perform this operation.EndFragment

## URL

`http://127.0.0.1:8000/api/shutdown/1`

## Method

`POST`

## Request Parameters

This endpoint does not require any request body parameters.

## Success Response (200 OK)

<img src="https://content.pstmn.io/43da9354-103b-43e7-a2be-472def2ae3cd/U2NyZWVuc2hvdCAyMDI1LTA4LTA1IDAwNTExOC5qcGc=">

Upon a successful request, the response will return a JSON object with the following structure:

``` json
{
  "status": "",
  "message": "",
  "checked_at": ""
}

 ```

- `status`: A string indicating the status of the shutdown operation.
    
- `message`: A string providing additional information about the operation.
    
- `checked_at`: A string representing the timestamp when the request was processed.
    

## Error Responses

The API may return various error responses depending on the situation. Common error responses include:

- `400 Bad Request`: If the request parameters are invalid.
    
- `404 Not Found`: If the specified resource does not exist.
    
- `500 Internal Server Error`: If there is an unexpected error on the server.
    

#### Request Parameters

- **id** (path parameter): The unique identifier of the resource that you want to shut down. In this case, the example uses `1`.
    

#### Expected Response

Upon a successful shutdown request, the server responds with a status code of `200` and returns a JSON object containing the following fields:

- **status**: A string indicating the status of the shutdown operation.
    
- **message**: A string providing additional information about the shutdown process.
    
- **checked_at**: A string representing the timestamp when the shutdown was checked.
    

#### Notes

- Ensure that you have the necessary permissions to execute a shutdown on the specified resource.
    
- The response fields may be empty strings, indicating that the operation was processed without specific details.
    
- Always verify the shutdown status through the returned message for confirmation.
# info API

StartFragmentThis API retrieves detailed information about a specific device, including database configuration, status, and activity logs. It also fetches the most recent activity status from the device’s connected database. Requires authentication.EndFragment

## URL

`http://127.0.0.1:8000/api/info/1`

## Method

`POST`

## Request Parameters

This endpoint does not require any specific parameters in the request body for execution.

## Success Response (200 OK)

<img src="https://content.pstmn.io/6a18a97e-2e3b-4dcf-865e-3abf1d2a3832/U2NyZWVuc2hvdCAyMDI1LTA4LTA1IDAwMDMxNy5qcGc=">

Upon a successful request, the response will return a JSON object containing the following structure:

``` json
{
    "status": "",
    "message": "",
    "device": {
        "id": 0,
        "name": "",
        "host_name": null,
        "db_server": "",
        "db_user": "",
        "db_name": "",
        "status": null,
        "shutdown_by": null,
        "created_at": "",
        "updated_at": ""
    },
    "activity_status": {
        "status": "",
        "error": ""
    }
}

 ```

- **status**: Indicates the status of the operation.
    
- **message**: Contains a message related to the operation.
    
- **device**: An object that provides details about the device, including:
    
    - `id`: Unique identifier for the device.
        
    - `name`: Name of the device.
        
    - `host_name`: Host name of the device (can be null).
        
    - `db_server`: Database server associated with the device.
        
    - `db_user`: Database user for the device.
        
    - `db_name`: Database name for the device.
        
    - `status`: Current status of the device (can be null).
        
    - `shutdown_by`: Indicates who shut down the device (can be null).
        
    - `created_at`: Timestamp when the device was created.
        
    - `updated_at`: Timestamp when the device was last updated.
        
- **activity_status**: An object that provides details about the activity status, including:
    
    - `status`: Current status of the activity.
        
    - `error`: Error message if any occurred.
        

## Error Responses

The API may return various error responses depending on the issue encountered during the request. Common error responses include:

- **400 Bad Request**: Indicates that the request was invalid.
    
- **404 Not Found**: Indicates that the specified resource was not found.
    
- **500 Internal Server Error**: Indicates an unexpected error occurred on the server.
    

### uest Parameters

This endpoint does not specify any request body parameters in the provided information. However, it is expected that the request may include parameters relevant to device information in a JSON format.

### Expected Response Format

The response will be in JSON format and will include the following structure:

- **status**: A string indicating the status of the request.
    
- **message**: A string providing additional information regarding the request.
    
- **device**: An object containing details about the device:
    
    - **id**: An integer representing the unique identifier of the device.
        
    - **name**: A string for the name of the device.
        
    - **host_name**: A nullable string for the host name of the device.
        
    - **db_server**: A string for the database server.
        
    - **db_user**: A string for the database user.
        
    - **db_name**: A string for the database name.
        
    - **status**: A nullable string indicating the current status of the device.
        
    - **shutdown_by**: A nullable string indicating who shut down the device.
        
    - **created_at**: A string representing the creation timestamp of the device.
        
    - **updated_at**: A string representing the last updated timestamp of the device.
        
- **activity_status**: An object providing information about the activity status:
    
    - **status**: A string indicating the current activity status.
        
    - **error**: A string detailing any error that may have occurred.
        

### Response Status

The expected response status code is `200`, indicating that the request was successful.

## Note

Ensure that the request is properly formatted and that the endpoint is accessible. The response structure may vary based on the device's current state and the operation performed.
