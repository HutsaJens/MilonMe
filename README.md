# MilonMe API Documentation

Welcome to the MilonMe API documentation! This document provides information on how to interact with the MilonMe API to achieve various tasks.

## Table of Contents
- [Introduction](#introduction)
- [Getting Started](#getting-started)
  - [Authentication](#authentication)
  - [Base URL](#base-url)
- [Endpoints](#endpoints)
  - [Endpoint: User Login](#endpoint-user-login)
  - [Endpoint 2](#endpoint-2)
  - [Endpoint 3](#endpoint-3)
- [Request and Response Examples](#request-and-response-examples)
- [Error Handling](#error-handling)
- [Rate Limiting](#rate-limiting)
- [Additional Resources](#additional-resources)

## Introduction
MilonMe API allows developers to access and interact with the users data. This documentation outlines the various endpoints available, authentication requirements, request and response examples, and more.

## Getting Started

### Authentication
To access the MilonMe API, you need to obtain an API key. Follow these steps to retrieve your API key:

1. Visit the [MilonMe website](https://www.milonme.com) and open the developer tools in your browser.

2. Navigate to the "Sources" tab and open the "www.milonme.com" -> static -> js -> main.96bf7d0184213493f51a.js"

3. Press "ctrl+f" and search for "this.browserApiKey"

4. Copy this value, this is your Api key



### Base URL
All API requests should be made to the following base URL:
```
https://www.milonme.com/api/user
```


## Endpoint: User Login
### `POST https://www.milonme.com/api/user/login`
This endpoint is used for user authentication.

#### After testing it seems not all of these are needed, a respone is recieved when using the following: 
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
`long_session`: Set to `1` if you want to keep the session active. ()

Example Response
```json
{
  "id": "*****",          // MilonMe User ID
  "r": 1,                 // Read Permission (1: Allowed, 0: Denied) - [Disclaimer: Exact meaning not confirmed]
  "w": 1,                 // Write Permission (1: Allowed, 0: Denied) - [Disclaimer: Exact meaning not confirmed]
  "ttl": 3600,            // Time-to-Live (Time duration in seconds for the token's validity)
  "idle": 0,              // Idle time (Time duration since the last activity) - [Disclaimer: Exact meaning not confirmed]
  "ip": "1.1.1.1",          // IP Address
  "d": {
    "sid": "*****",       // Studio ID (As a number)
    "gender": "*****",    // User Gender (m/f)
    "birthday": "YYYY-MM-DD",  // User Birthday
    "s": 3,               // Unknown
    "studios": "*****"    // Studio ID (As a string)
  }
}
```


## Endpoint: User Login
### `GET https://www.milonme.com/api/user/stats/home/{studioId}/{userId}`
This endpoint is used for recieving user stats.

#### Headers
- `Content-Type`: application/json;charset=UTF-8
- `X-Api-Key`: [Your API Key]
- `Cookie`: [The cookie revieved in the response header of the login request] 

##### Cookie
The cookie header has the following structure: 
```
"rs-token=REDACTED; mf=http://10.16.168.222:60788"
```
- The "rs-token" part of the the cookie is the same as the "rs-token" part of the response header of the login request
- The mf part: Currenltly not sure



##### Overview of response
```json
{
    "featureFlags": {
        "anamnesis": true,
        "passwordForgotten": true,
        "emails": true,
        "cotrainer": true,
        "cockpit": true,
        "newsImageUpload": true,
        "messageImageUpload": true,
        "userImageUpload": true,
        "appAvailable": true,
        "achievements": true,
        "rankings": true,
        "ctsMatrix": true,
        "ctsDisplay": true,
        "ctsLifeFitness": true,
        "webinars": true,
        "basicDevices": true,
        "disclaimer": true,
        "mmeTracking": false,
        "icpRecordal": false,
        "vitalPageV3": true,
        "tpactive": false,
        "statistic": false,
        "bioage": true,
        "sarcopenia": true
    },
    "attendance": [
        {
            "t": 1715016565,    // Timestamp of training
            "type": "p"         // As far as i know can be "p" or "b", meaning unknown
        }
    ],
    "disclaimer_version": 1,
    "privacy_seen": 1,
    "ads_allowed": 0,       
    "addressed": [],          // Unknown
    "achievements": {
        "d": {
            "counters": {
                "sum_kcal": 2340,                     // total amount of burned caleries?
                "flex_tests": 0,
                "votes_cast": 0,
                "tons_lifted": 0.00,                  // Total amount of tons lifted
                "milon_streak": 0,                    // Milon streak, not sure how this is calculated (could be if user trains at least twice every 10 days)
            "feelings_cast": 0,                       // Amount of times the user has shared there feelings feedback
                "fitness_tests": 0,
                "hours_trained": 0.00,                // hours trained by user (double/float)
                "last_check_in": 0,
                "last_exercise": 0,
                "total_check_ins": 0,
                "total_exercises": 0,
                "trained_on_friday": 0,
                "distance_travelled": 0,
                "last_five_training": 0,
                "last_basic_training": 0,             // Last time the user performed a basic training (unix)
                "total_qfree_devices": 0,
                "total_five_trainings": 0,
                "last_premium_training": 0,           // Last time the user performed a premium training (unix)
                "total_basic_trainings": 0,           // Amount of basic trainings
                "total_premium_devices": 0,           // Amount of premium trainings 
                "total_qfree_trainings": 0,
                "total_premium_trainings": 0,        // Total amout of premium trainings
                "total_premium_nodegroups": 0,       // Not sure
                "total_cardio_devices_trained": 41,  // Not sure how this number is calculated 
                "trained_between_0400_and_0900": 0,  // Self explaining, times trained between 04:00 and 09:00 (Military time for the Americans)
                "trained_between_1600_and_2000": 0,  // See above
                "trained_between_2000_and_2359": 0,  // See above
                "total_traintec_devices_trained": 0  // Total amount of times trained? 
            },
            "achievements": [   // Array of achievements achieved by user
                {
                    "n": "xxxx",      // Achievement name
                    "s": 10,          // Number of points achievement is worth
                    "t": 1649098599,  // Time of achieving achievement 
                    "type": "a"       // Unkown
                }
            ]
        },
        "score": 0,      // Current user score
        "la": 0,         // Last time user achieved an achievement
        "level": 0       // Current user level
    },
    "thirdparty": {
        "milonid": null,
        "connected_apps": []
    },
    "achievements_log": [
        {
            "d": [
                {
                    "n": "xxx",   // Name of achievement
                    "s": 0,      // Achievement worth in points
                    "type": "s"   // Type of achiement "s" is a single "a" is additive (has multiple stages)
                }
            ],
            "ts": 1714673003      // Time of achievement
        }
    ],
    "polls": [],
    "has_app": true,              // if the user has the app installed (true/false)
    "feedback": {
        "t": 1715019209,
        "r": 3,
        "s": 1
    },
    "profile": {
        "_sid": 910,                        // Studio Id
        "role": "USER",
        "lastname": "Doe",                  // Last name of user
        "lastlogin": 0,                     // Last lopin (Unix)
        "lang": "nl_NL",                    // User language see "https://docs.dyspatch.io/localization/supported_languages/"
        "image": null,
        "id": "007",                        // User Id
        "gender": true,                     // Gender, true is male, false is female
        "fitlevel": 0,                      // Unkown
        "firstname": "John",                // firstname
        "email": "john.doe@example.com",    // Email
        "currplan": 10996009,
        "curritem": 5664676,
        "created": "YYYY-MM-DDThh:mm:ssZ",  // Creation of user account
        "birthday": "YYYY-MM-DD",           // User Birthday
        "agegroup": 0                       // Agegroup, multiple of 10
    },
    "studio": {
        "studioname": "John Doe fitness",   // Name of studio
        "studiogroup": null,
        "jsonSettings": {
            "lang": "nl_NL"                 // Language of studio
        }
    },
    "news": [                               // Active news in studio
        {
            "type": "NEWS",
            "id": "xxx",                    // Format: SN{StudioId}S{CreationTime (Unix)}
            "image": "",                    // Format: news_SN{StudioId}S{CreationTime of picture? (Unix)}.PNG
            "created": 0,                   // Creation Date (Unix)
            "subject": "",                  // Name of news
            "body": "",                     // Details of news message
            "isread": true                  // Is read by user
        }
    ],
    "activeTraining": {
        "plan_id": 10996009,
        "training_id": 5664676,
        "active": false,
        "lastactive": 1715019057
    },
    "session": {                            // See login Example Response
        "id": "xxx",                        
        "r": 1,
        "w": 1,
        "ttl": 3600,
        "idle": 0,
        "ip": "",
        "d": {
            "sid": 0,
            "gender": "m",
            "birthday": "YYYY-MM-DD",
            "s": 3,
            "studios": "000"
        }
    },
    "show_nag_banner": false,
    "frontend_config": {
        "exercise_bucket": "https://dio7q6x5myw9r.cloudfront.net/live"
    }
}
```



