# How to set Custom Fonts in React Native

add your fonts on the root
create a folder assets
in assets folder, create another folder
create fonts folder inside assets folder

in the fonts folder paste all your fonts

create a file on the root, react-native.config.js
paste this into it

module.exports = {
project: {
ios: {},
android: {}, // grouped into "project"
},
assets: ['./assets/fonts/'], // stays the same
};

after this, open terminal on root, and run
npx react-native-asset

to use the font into the App

call by its file name
