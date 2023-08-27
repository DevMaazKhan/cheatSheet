# Vite

Vite is a Command Line Tool, to Scaffold different FrontEnd Projects, it is faster that other tools like: CRA (Create React App)

## Create a Simple React App with Vite

- Open your terminal and type `npm create vite@latest`
- Then follow the commands, select React and you are good to go.
- `npm i` is required, after your project is scaffolded

## Setup Tailwind

- npm i -D tailwindcss postcss autoprefixer
- npx tailwindcss init -p
- open tailwind.config.cjs file
- edit content, add
  - "./index.html"
  - "./src/\*_/_.{js,ts,jsx,tsx}"
- create index.css file in src directory
- add
  - @tailwind base;
  - @tailwind components;
  - @tailwind utilities
