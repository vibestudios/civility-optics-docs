# Civility Optics Delivery Docs

***

# Backend Installation Guide

## Pre-requisites
Make sure you have Node.js version 14.16 and NPM version 6.14 installed: https://nodejs.org/en/download/. You can follow the tutorial provided here: https://phoenixnap.com/kb/install-node-js-npm-on-windows.

To access the project on your local computer, clone the repository on GitHub by running `git clone https://github.com/vibestudios/civility-optics-android.git`.

<br>

If you want to run the backend locally, you must create a `.env` folder in the `backend` directory and define the following environment variables:
```
GOOGLE_MAPS_API_KEY="<GOOGLE PLACES API KEY>"
JWT_KEY="<ANY STRING OF YOUR CHOICE>"
PORT="<PORT NUMBER (5000 for Windows, 5001 for MAC)>"
```
<br>
Install the required packages by running the following commands in the terminal:

```
npm install express
npm install express-async-handler
npm install mongoose
npm install cors
npm install dotenv
npm install mongodb
npm install axios
npm install validator
npm install bcryptjs
npm install jsonwebtoken
npm install nodemailer
```

## Running

To start the backend service locally, enter the `civility-optics-api/backend` directory and run the command `node server.js` in the terminal.

To run the server to the database, use the command `mongod` anywhere in the terminal.

# Backend Release Notes

#### v 1.0.0, build 1

## Features
- Post user-submitted ratings for a certain venue to our database.
- Get user-submitted ratings for a certain venue from our database.
- Get comments from users about a vertain venur from our database.
- Create user accounts, login users, and logout users from our system.
- Leverage Google Places API to return a list of nearby venues based on a user's input
- Leverage Google Places API to return specific info about a venue.

## Known Issues
- Some requests are formatted as POST but should really be GET.
- In getRatings, ratings from the last 30 days should be returned, but all ratings are being returned.
- In getReviews, null reviews aren't bring filtered out.

***

# Android Installation Guide

***

# iOS Installation Guide

### 1. Required Software

On MacOS Big Sur (12+), install Xcode (12.3+) from the App Store to get started.

### 2. Clone the Code

Use git to clone this repository:

```
git clone https://github.com/vibestudios/civility-optics-ios.git
```

### 3. Open and build the Project.

Open `Civility Optics.xcodeproj`. Use Command+B to build the project, which will automatically resolve Swift package dependencies.

### 4. Change Settings

In `NetworkingService.swift`, change `NetworkingService.baseURL` to the url of the backend. The current code points to `http://localhost:5001/`. 

## Troubleshooting

### I can't load the app on my phone.

If you attempted to install this app on your phone, you might need an [Apple Developer account](https://developer.apple.com). Sign in to your developer account on your Mac to resolve the issue.

### The app does not connect to the backend.

If you are running the backend locally, ensure `NetworkingService.baseURL` matches the port selected by your backend, and make sure the backend is running. This will connect simulator instances to the backend, and will not work for apps installed to a physical device.

If you are hosting the backend online, change this url to the public url. This public url will work for app instances on the simulators and on physical devices.

# iOS Release Notes

#### v 1.0.0, build 1

## Features
- Create new accounts
- Login to existing accounts
- Search for nearby venues
- View venue ratings and comments
- Submit a Five Fist Rating
- Select a date visited for ratings
- Add tags to ratings
- Add a comment to ratings

## Known Issues and Limitations
- The login page is unintentionally accessible through the back navigation arrow. This may freeze the app and require a reboot.
- Errors related to login or account creation (such as invalid password or failed attempts) are not shown to the user. Instead, only valid login and registration attempts change the page.
