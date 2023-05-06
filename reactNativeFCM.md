# React Native FCM

## FCM

Firebase Cloud Messaging

This is the a way to integrate notifications in your application that is built with react native.

For this tutorial you need a React Native Application, that is built with React Native CLI.

## Steps

1. Create a Firebase Account if you haven't yet.
2. You need a firebase project for this, if you don't have one already, create a new project.
3. In your selected Firebase Project add an Android Application.
4. To create an android application, you will need your Android Package Name, this can be found in your project directory, head over to your project root directory, android/app/build.gradle
   1. In this file, search for, applicationId, the text in the double quotes after applicationId is your Android Package Name.
5. after this, you can click on Register App Button.
6. on the next step, download the google-services.json file, and keep it for now, we will use it later
7. click on next
8. click on next, we will do these things later
9. continue to console
10. Now you have successfully created your Android Application in Firebase Project
11. now in your project root, run this
    1. npm i @react-native-firebase/app @react-native-firebase/messaging react-native-push-notification
    2. npm i --save-dev @types/react-native-push-notification
12. now we need to set up these libraries and the file we downloaded from firebase
13. add the downloaded file to your android/app directory, make sure the name of this file is google-services.json
14. open android/build.gradle, and add this, on "ext" object
    googlePlayServicesVersion = "+"
    firebaseMessagingVersion = "+"
15. Open AndroidManifest.xml file, add this on top,
    <uses-permission android:name="android.permission.VIBRATE" />
    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED"/>
16. In the same file, add this, inside application
    <meta-data  android:name="com.dieam.reactnativepushnotification.notification_foreground"
    				android:value="false"/>
    <meta-data  android:name="com.dieam.reactnativepushnotification.notification_color"
    				android:resource="@color/white"/>
    <receiver android:name="com.dieam.reactnativepushnotification.modules.RNPushNotificationActions" android:exported="false" />
    <receiver android:name="com.dieam.reactnativepushnotification.modules.RNPushNotificationPublisher" android:exported="false" />
    <receiver android:name="com.dieam.reactnativepushnotification.modules.RNPushNotificationBootEventReceiver" android:exported="false">
    <intent-filter>
    <action android:name="android.intent.action.BOOT_COMPLETED" />
    <action android:name="android.intent.action.QUICKBOOT_POWERON" />
    <action android:name="com.htc.intent.action.QUICKBOOT_POWERON"/>
    </intent-filter>
    </receiver>
    <service
    		android:name="com.dieam.reactnativepushnotification.modules.RNPushNotificationListenerService"
    		android:exported="false" >
    <intent-filter>
    <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
    </service>
17. create a file, colors.xml, inside, android/app/src/main/res/values/colors.xml, add this in it
    <resources>
    <color name="white">#FFF</color>
    </resources>
18. in android/build.gradle, add this, in buildscript -> dependencies
    classpath("com.google.gms:google-services:4.3.15")
19. in android/app/build.gradle, add this, dependencies
    implementation 'com.google.firebase:firebase-analytics:17.3.0'
20. in the same file, add this, on root
    apply plugin: 'com.google.gms.google-services'
21. in android/build.gradle, add this, in buildscript -> repositories
    google()
    mavenCentral()
    this goes, on the roor
    allprojects {
    repositories {
    google() // Google's Maven repository
    mavenCentral() // Maven Central repository
    }
    }
22. android/app/build.gradle, add this
    this goes, on the dependencies
    implementation platform('com.google.firebase:firebase-bom:31.5.0')
23. this goes in index.js

import PushNotification from 'react-native-push-notification';
import messaging from '@react-native-firebase/messaging';
    
messaging().setBackgroundMessageHandler(async remoteMessage => {
  console.log('Message handled in the background!', remoteMessage);
});

PushNotification.configure({
  onAction: notification => {
    console.log(notification);
  },
  requestPermissions: Platform.OS === 'ios',
});

24. to get the token use
import firebase from '@react-native-firebase/app';
import messaging from '@react-native-firebase/messaging';
 messaging()
      .getToken({senderId: firebase.app().options.messagingSenderId})
      .then(token => {
        appStore.setDeviceToken(token);
      });


After all these steps, you are good to go, hopefully
