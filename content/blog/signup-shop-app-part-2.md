# Flutter, Getting Started with Firebase.

How to add firebase to flutter app ? Let’s get started.

# Step 1: Set up your environment

Fluter.io provides a neat document on how to install flutter and setup your favourite IDE : [Get Started](https://flutter.dev/docs/get-started/install/macos)

Once you have completed setup create a new Flutter project with your desired name.

# Step 2: Create a Firebase project

Before adding firebase to flutter app go to [Firebase console](https://console.firebase.google.com/) and create new Firebase project.

Tap on Add Project enter your Projects name , firebase will assign a project id based on the entered name you can also edit , Accept terms and Create project.

![Image for post](https://miro.medium.com/max/50/1*yrx6SuCPr2dNJohzB4WZag.png?q=20)

<noscript><img alt="Image for post" class="s t u by ai" src="https://miro.medium.com/max/1178/1*yrx6SuCPr2dNJohzB4WZag.png" width="589" height="698" srcSet="https://miro.medium.com/max/552/1*yrx6SuCPr2dNJohzB4WZag.png 276w, https://miro.medium.com/max/1104/1*yrx6SuCPr2dNJohzB4WZag.png 552w, https://miro.medium.com/max/1178/1*yrx6SuCPr2dNJohzB4WZag.png 589w" sizes="589px"/></noscript>

Your new firebase project will be created.

# Step 3: Configure your app to use Firebase

To configure firebase to flutter we need some platform specific details to android and iOS apps. If you are working only on android you don’t need to add iOS specific changes.

# Configure an iOS App: (Optional )

1.  In your Firebase project console overview page , Launch the iOS setup wizard.

*   Find this bundle ID by opening your app in XCode, then accessing the **General** tab in the top-level `Runner` directory. The value of the **Bundle Identifier** field is the iOS bundle ID (for example,`com.yourcompany.yourproject`). ([Source](https://firebase.google.com/docs/flutter/setup))

2\. Enter the Name and app store id (optional ) click next. Now download the **GoogleService-info.plist**

Copy the **GoogleService-info.plist into** _iOS — Runner — Runner_ directory of your flutter project. In console click next and skip other steps.

**_Your iOS app is configured with Firebase._**

# Configure an Android App: (Optional )

1.  In your Firebase project console overview page , Launch the Android setup wizard.

Enter your **application id** into the **Android package field**, other fields are optional.

*   _An application ID is sometimes referred to as as a package name._
*   _Find this application ID in your module (app-level) Gradle file, usually_ `_android/app/build.gradle_`_(example application ID:_ `_com.yourcompany.yourproject_`_). (_[_Source_](https://firebase.google.com/docs/flutter/setup)_)_

Register the app. On the next step download **google-services.json** and move the file into **android/app** folder of your flutter project.

2\. Android requires another few more steps to add firebase support in your app .

In your root-level **(project-level)** Gradle file (`android/build.gradle`), add rules to include the Google Services plugin. Check that you have Google’s Maven repository, as well.


```
buildscript {
  // ...
  dependencies {
    // ...
    // Add the following line:
    classpath 'com.google.gms:google-services:3.2.1'  // Google Services plugin
  }
}
allprojects {
  // ...
  repositories {
    // Check that you have following line (if not, add it):
    google()  // Google's Maven repository
    // ...
  }
}</span>
```


In your module (app-level) Gradle file (usually `android/app/build.gradle`), add the following line to the _bottom of the file_.


```
dependencies {
  // ...
}

// ...

// Add the following line to the bottom of the file:
apply plugin: 'com.google.gms.google-services'  // Gradle plugin</span>
```


Run `flutter packages get`.

Now our app is ready to integrate flutter firebase plugins.

Open your **pubspec.yaml** file and add the following line under dependencies


```
dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^0.2.5  # add dependency for Firebase Core</span>
```


Run your app and verify if app is working.

Documentation from [firebase.google.com](https://firebase.google.com/docs/flutter/setup).