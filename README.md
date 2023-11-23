# MilonMe API Documentation

Welcome to the MilonMe API documentation! This document provides information on how to interact with the MilonMe API to achieve various tasks.

## Table of Contents
- [Introduction](#introduction)
- [Getting Started](#getting-started)
  - [Authentication](#authentication)
  - [Base URL](#base-url)
- [Endpoints](#endpoints)
  - [Endpoint 1](#endpoint-1)
  - [Endpoint 2](#endpoint-2)
  - [Endpoint 3](#endpoint-3)
- [Request and Response Examples](#request-and-response-examples)
- [Error Handling](#error-handling)
- [Rate Limiting](#rate-limiting)
- [Additional Resources](#additional-resources)

## Introduction
MilonMe API allows developers to access and interact with the users data. This documentation outlines the various endpoints available, authentication requirements, request and response examples, and more.

### Base URL
All API requests should be made to the following base URL:
```
https://www.milonme.com/api/user
```

## Endpoint: User Login
### `POST https://www.milonme.com/api/user/login`
This endpoint is used for user authentication.

#### Headers

- `authority`: www.milonme.com
- `method`: POST
- `path`: /api/user/login
- `scheme`: https
- `Accept`: application/json, text/plain, */*
- `Accept-Encoding`: gzip, deflate, br
- `Accept-Language`: nl-NL,nl;q=0.9,en-GB;q=0.8,en-US;q=0.7,en-NL;q=0.6,en;q=0.5,ru-RU;q=0.4,ru-MD;q=0.3,ru;q=0.2
- `Content-Length`: 73
- `Content-Type`: application/json;charset=UTF-8
- `Cookie`: [Your Cookie Information] <!-- Redacted for security -->
- `Dnt`: 1
- `Origin`: https://www.milonme.com
- `Referer`: https://www.milonme.com/login
- `Sec-Ch-Ua`: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"
- `Sec-Ch-Ua-Mobile`: ?0
- `Sec-Ch-Ua-Platform`: "Windows"
- `Sec-Fetch-Dest`: empty
- `Sec-Fetch-Mode`: cors
- `Sec-Fetch-Site`: same-origin
- `User-Agent`: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36
- `X-Api-Key`: [Your API Key] <!-- Redacted for security -->

### After testing it seems not all of these are needed, a respone is recieved when using the following: 
- `Content-Type`: application/json;charset=UTF-8
- `X-Api-Key`: [Your API Key]

#### Request Body

```json
{
  "email": "email@example.com",
  "password": "password123",
  "long_session": 0
}
```

`email`: The user's email address.
`password`: The user's password.
`long_session`: Set to `1` if you want to keep the session active.

Example Response
```json
{
  "id": "*****",          // Redacted for security
  "r": 1,
  "w": 1,
  "ttl": 3600,
  "idle": 0,
  "ip": "*****",          // Redacted for security
  "d": {
    "sid": "*****",       // Redacted for security
    "gender": "*****",    // Redacted for privacy
    "birthday": "*****",  // Redacted for privacy
    "s": 3,
    "studios": "*****"    // Redacted for privacy
  }
}
```



