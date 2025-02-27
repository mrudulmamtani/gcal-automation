# Google Calendar Automation
## Overview

This Python script automates the creation of Google Calendar events for a comprehensive GMAT study plan spanning from March to May 2025. It helps users maintain a consistent study schedule by automatically creating calendar events with detailed study topics and resources.

## Prerequisites

- Python 3.6 or higher
- Google account with Calendar access
- Google Cloud Platform project with Calendar API enabled


## Required Packages

```
pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib
```


## Setup Instructions

### 1. Create a Google Cloud Project

1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project (e.g., "caltry" or any name you prefer)
3. Enable the Google Calendar API for your project

### 2. Configure OAuth Consent Screen

1. Navigate to "APIs \& Services" > "OAuth consent screen"
2. Select "External" user type
3. Fill in the required application information:
    - App name
    - User support email
    - Developer contact information
4. Add the scope: `https://www.googleapis.com/auth/calendar`
5. Add test users (your Google account email)

### 3. Create OAuth Credentials

1. Navigate to "APIs \& Services" > "Credentials"
2. Click "Create Credentials" > "OAuth client ID"
3. Select "Desktop application" as the application type
4. Name your OAuth client
5. Add the following to "Authorized redirect URIs":
    - `http://localhost:8080/`
6. Download the credentials JSON file
7. Rename it to `credentials.json` and place it in the same directory as the script

## Usage

1. Run the script:
```
python gmat_study_scheduler.py
```

2. The first time you run the script, it will:
    - Open a browser window for Google authentication
    - Ask you to sign in to your Google account
    - Request permission to access your Google Calendar
    - Create study events according to the predefined plan

## Troubleshooting

### Error 400: redirect_uri_mismatch

- Ensure the redirect URI in your Google Cloud Console matches exactly with `http://localhost:8080/`
- Check that your credentials.json file is up to date


### Error 403: access_denied

- Your app hasn't completed the Google verification process
- For personal use, add your email as a test user in the OAuth consent screen
- If you're the developer, you can still use the app while in testing mode


## Study Plan Details

The script creates a comprehensive GMAT study plan with:

- Weeks 1-2: Foundational Learning
- Week 3: Maintenance Mode during exams
- Week 4: Concept Reinforcement
- Weeks 5-8: Maintenance Mode during finals
- Weeks 9-10: Advanced Practice
- Week 11: Full-Length Practice Tests
- Week 12: Final Review and Test-Taking Strategies


## Notes

- The calendar events include detailed information about study resources and focus areas
- The schedule adjusts based on the day of the week (different times for Monday, Thursday, etc.)
- You can modify the study plan in the `get_study_plan()` function to customize your schedule

