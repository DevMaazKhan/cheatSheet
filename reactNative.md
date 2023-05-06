# React Native

## How to start a fresh React Native Project ?

- open terminal on the directory you want your project to be created, and run this command
  `npx react-native init projectName`
- Make sure to replace projectName with your projectName, special characters and numbers and spaces are not allowed in projectName.

Now you have a project ready to be worked on.

## How to run React Native app on Android Device.

- open your package.json, there you will find start script, which will be like npx react-native start, change it to - `npx react-native start --reset-cache`
- Now run on the root of your project, - `npm start`
- once the metro has started press "a" to run the app on android, it will open android emulator automatically, or if you have connected you physical mobile device it will run the app on that.
