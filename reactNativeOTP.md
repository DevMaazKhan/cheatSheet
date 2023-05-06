# React Native OTP

To enable OTP verification for your android application, you need to follow these steps.
before starting make sure you have a running android Application built with React Native CLI

1. You need a firebase account for this, if you dont have 1 already create one.
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
    1. npm i @react-native-firebase/app @react-native-firebase/auth
12. now you need to add SHA Key to your firebase android app, open settings for the app, and scroll down to the bottom, there you will see SHA certificate fingerprints run this command on android/app, to generate a key
    `keytool -list -v -keystore debug.keystore -alias androiddebugkey -storepass android -keypass android`
13. now we need to set up these libraries and the file we downloaded from firebase
14. add the downloaded file to your android/app directory, make sure the name of this file is google-services.json
15. copy SHA256 key, head over to firebase, click add fingerPrint, and paste the key, save
16. head over to firebase project, authentication, click phone, enable, additional configuration, click on android
17. in android configuration screen, click on Android DeviceCheck API
18. Click on Enable, make sure you have the right project selected
19. make sure in your, android/build.gradle file you have this, buildscript -> dependencies
    `classpath("com.google.gms:google-services:4.3.15")`
20. make sure in your, android/app/build.gradle file you have this, root
    `apply plugin: 'com.google.gms.google-services'`
21. run the project
22. add test phone number on firebase console, in your authentication, phone section, select phone numbers for testing
    add phone number: +44 7444 555666
    and code: 123456
23. this code is for the phone auth, paste it where you want the authentication to happen, e:g login
    const confirmation = await auth().signInWithPhoneNumber(phoneNumber);
    setConfirm(confirmation);
    await confirm.confirm(code);
