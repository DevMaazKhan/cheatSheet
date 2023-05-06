Initialize Node JS Project
-- npm init

Create Src Directory
-- mkdir src

Create app.ts file in src directory
-- touch src/app.ts

Install Additional typescript dependencies
-- npm i ts-node-dev typescript -D

Create Typescript Config File
-- npx tsc --init

Install Express
-- npm i express

Install additional typescript libraries
-- npm i @types/node @types/express -D

Now Install add eslint
-- npm i -D eslint

Install AirBNB style guide, run
-- npx install-peerdeps --dev eslint-config-airbnb-base

Initialize EsLint Configs, use airbnb style config, run
-- npx eslint --init

Initialize Prettier, run
-- npm i -D prettier eslint-config-prettier eslint-plugin-prettier

Create Prettier config file
-- touch .prettierrc.cjs

Edit package.json file, add scripts entry, add a Dev Script entry in scripts entry
-- dev:ts-node-dev --respawn --transpile-only src/app.ts

Now Create a simple express App, edit app.ts file
import express from 'express';
const app = express();
app.get('/', (req, res) => {
return res.send("Hello world")
})
app.listen(3000, () => {
console.log("Server listening on PORT -> 3000")
})

Edit eslint config file, Add ParserOptions,
-- project: './tsconfig.json'

Create script for eslint:fix
-- "lint:fix": "eslint --fix ./src/\*.ts"

add this in prettier config file
module.exports = {
trailingComma: 'es5',
tabWidth: 2,
semi: true,
singleQuote: true
}

add prettier in eslint config file, plugins section

add prettier config in extends
plugin:prettier/recommended
