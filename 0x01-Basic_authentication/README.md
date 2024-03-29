# Authentication
Authentication is the process of verifying the identity of a user, system, or entity to ensure that they are who they claim to be. In the context of computer security and information technology, authentication is a fundamental component of access control.

Authentication methods typically involve the presentation of credentials, such as usernames and passwords, security tokens, biometric data (like fingerprints or iris scans), or other forms of identification. The goal is to grant access only to authorized individuals or systems while preventing unauthorized users from gaining entry.

## Basic Authentication
### Introduction
Basic Authentication is a simple authentication mechanism commonly used in web applications. It involves the use of a username and password for verification.

### How it Works
1. Request Header: The client includes a special "Authorization" header in the HTTP request.
2. Encoding: The username and password are combined into a string in the format username:password.
3. Base64 Encoding: The combined string is encoded using Base64 encoding.
4. Authorization Header: The resulting Base64-encoded string is included in the "Authorization" header as Basic <Base64-encoded-string>.
### Example
GET /example HTTP/1.1
Host: example.com
Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=

In this example, the username is "username," and the password is "password."

Note: While Basic Authentication is simple, it's not secure when used alone, as the credentials are easily decoded from the Base64-encoded string. It is recommended to use it over HTTPS to encrypt the communication.

## Base64 Encoding
Base64 encoding is a binary-to-text encoding scheme that represents binary data in an ASCII string format. It is commonly used for encoding data in environments where binary data is not easily handled.

### How to Use Base64 Encoding
* Encoding: Convert binary data into a Base64-encoded string.
* Decoding: Convert the Base64-encoded string back into binary data.

### Example (Python)
import base64

# Encode
data = b'Hello, World!'
encoded_data = base64.b64encode(data)
print(f'Encoded: {encoded_data.decode()}')

# Decode
decoded_data = base64.b64decode(encoded_data)
print(f'Decoded: {decoded_data.decode()}')
In this example, the string "Hello, World!" is encoded and then decoded using Base64.

=============================================================================== for the models, simpleAPI


# Simple API

Simple HTTP API for playing with `User` model.


## Files

### `models/`

- `base.py`: base of all models of the API - handle serialization to file
- `user.py`: user model

### `api/v1`

- `app.py`: entry point of the API
- `views/index.py`: basic endpoints of the API: `/status` and `/stats`
- `views/users.py`: all users endpoints


## Setup

```
$ pip3 install -r requirements.txt
```


## Run

```
$ API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
```


## Routes

- `GET /api/v1/status`: returns the status of the API
- `GET /api/v1/stats`: returns some stats of the API
- `GET /api/v1/users`: returns the list of users
- `GET /api/v1/users/:id`: returns an user based on the ID
- `DELETE /api/v1/users/:id`: deletes an user based on the ID
- `POST /api/v1/users`: creates a new user (JSON parameters: `email`, `password`, `last_name` (optional) and `first_name` (optional))
- `PUT /api/v1/users/:id`: updates an user based on the ID (JSON parameters: `last_name` and `first_name`)
