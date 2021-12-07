# Civility Optics Delivery Docs

#### Contents

- [Backend Installation Guide](#backend-installation-guide)
- [Backend Release Notes](#backend-release-notes)
- [Android Installation Guide](#android-installation-guide)
- [Android Release Notes](#android-release-notes)
- [iOS Installation Guide](#ios-installation-guide)
- [iOS Release Notes](#ios-release-notes)

***

# Backend Installation Guide

## Pre-requisites
Make sure you have Node.js version 14.16 and NPM version 6.14 installed: https://nodejs.org/en/download/. You can follow the tutorial provided here: https://phoenixnap.com/kb/install-node-js-npm-on-windows.

To access the project on your local computer, clone [the repository on GitHub](https://github.com/vibestudios/civility-optics-ios) by running `git clone https://github.com/vibestudios/civility-optics-android.git`.

<br>

If you want to run the backend locally, you must create a `.env` folder in the `backend` directory and define the following environment variables:
```
GOOGLE_MAPS_API_KEY="<GOOGLE PLACES API KEY>"
JWT_KEY="<ANY STRING OF YOUR CHOICE>"
PORT="<PORT NUMBER (5000 for Windows, 5001 for MacOS)>"
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

## Troubleshooting
- A common issue that may arise is that you'll revieve an error due not having the right environment variables. Please put the correct environment variables in your created `.env` folder before attempting to run the backend.
- If you are getting a CANNOT GET... or a CANNOT POST... when hitting an endpoint, make sure you are specifying the correct method (POST or GET) with the corresponding endpoint.
- If you are getting a Status 200 OK but recieving no results, look at your request body and ensure that the values you pass in are correct. A great way to debug API requests is to use a tool called [Postman](https://www.postman.com/)

# Backend Release Notes

#### [v 1.0.0, build 1](https://github.com/vibestudios/civility-optics-api)

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

## Pre-requisites 
Depending on your system, different requirements must be met before you can successfully download the third party applications needed to build the Android Civility Optics code, like Android Studio:
- Windows:
  - Windows 7/8/10 (64 bit) (Windows 10 recommended)
  - 4 GB of RAM (8 GB recommended)
  - 2 to 4 GB of free disk space
  - (Recommended) Intel Core i5-8400 3.0 GHz CPU or better 
- MacOS:
  - MacOS 10.1 or higher (macOS 10.5 recommended)
  - 4 GB of RAM (8 GB recommended)
  - 2 to 4 GB of free disk space
  - (Recommended) Intel Core i5-8400 3.0 GHz CPU or better 
  - SSD recommended
Because you also will need additional disk space to download (if not already present on your machine) Android Studio, Gradle, Java SDK, and an emulator, it is recommended that you have another ~5-10 GB of free space.  

## Dependent libraries that must be installed
Because we are providing the raw source code for the Civility Optics Android application, in order to successfully access and build the project, you must download Android Studio. Android Studio Arctic Fox 2020.3.1 was the development environment used. You will also need the Android Gradle plugin with a version that is 3.1 or higher, and version 7.0.2 was used during development. The application is written in Java, version 1.8.0_291, so you will need to install the Java Runtime Environment to run the Java application; this can be done by installing the Java SDK (Software Development Kit). Similarly, in order to emulate the application’s build on your computer, you must download a virtual device emulator, which can then show you the functionality of the application. During development the functionality was emulated with the Pixel 3a API 28 (Pie) emulator under the “Phone” category, which can be downloaded by opening the project and navigating to Tools>AVD Manager>Create Virtual Device. 

## Download Instructions 
To access the source code locally, clone the repository from the [civility-optics-android repo on Github](https://github.com/vibestudios/civility-optics-android). You can do this by going to the repository on Github and clicking the green “Code” button dropdown, copying the link provided, and then opening Android Studio. From there you can click “Git” from the top task bar, and then pasting the link provided after clicking the “Clone” button. This will give you access to the code that was written for the application.

## Build instructions
To build the project, you can either navigate to Build>Make Project (Ctrl+F9 on Windows, Command+F9 on Windows), or you can select the hammer (Make Project) button at the top of the window. This will compile your project and bring together the resources and dependencies within the project.

## Run Instructions
To effectively run the application (compile and view output on an emulator) within Android Studio, you can navigate to Run>Run App (Shift+F10 on Windows and Mac) at the top of the screen. This will automatically begin the execution and will launch the emulator, to which you can then interact with the application in. In order to see changes made while the emulator is running, you have to stop running, apply changes, and restart running (Ctrl+F10 on Windows, Command+F10 on Mac).

## Troubleshooting
When building or running the project, simple issues may arise:
If your build performance is slow, it is possible that your antivirus software is impacting it. This can be handled by adding the directory of the project as an “exclusion” to your antivirus software.
Emulators can take a long time to launch if multiple processes are running on your system at once; closing out other CPU heavy applications on your machine before running will improve launch times. 

# Android Release Notes

#### [v 1.0.0, build 1](https://github.com/vibestudios/civility-optics-android)

## Features:
- Rating module implementation:
  - The ability to select a rating on a scale of five was implemented.
- Tag selection implementation:
  - The ability to select tags that correspond to the rating was implemented. This included adding four different dropdowns with a variety of unique tag options provided.
  - The ability to clear all of the selected tags under a specific tag category was added.
  - The ability to cancel tag selections before applying changes was added.
  - When tags are selected, a preview of which tags were selected is then shown on the dropdown box.
- Tag categories specified:
  -Tag category names were specified above the tag selection dropdowns. 

## Bug fixes:
- The rating screen’s tag functionality initially had issues correctly saving the state of which tags the user selected: if tags were selected under one category, then it would select tags under another category as well. This was fixed so that each tag category is unique, and one tag selection does not affect other tag selections.
- Activity components were not bound previously, so during runtime they would appear in the top left corner of the screen. We handled this by binding all of the components to a fixed spot in the activity design window. 
- Previews for tag selections in the dropdown window initially showed each tag selected in each tag category: we made it so that the previews only showed the tags selected for that specific category.

## Known bugs and defects
- The Android application is missing the Search UI and the Business Profile functionality. It also hasn’t been connected effectively to the backend, so ratings are not being saved currently. 

***

# iOS Installation Guide

### 1. Required Software

On MacOS Big Sur (12+), install Xcode (12.3+) from the App Store to get started.

### 2. Clone the Code

Use git to clone [this repository](https://github.com/vibestudios/civility-optics-ios):

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

#### [v 1.0.0, build 1](https://github.com/vibestudios/civility-optics-ios)

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
