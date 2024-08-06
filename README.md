# Deploying a React App with Vite to GitHub Pages

This tutorial will guide you through the steps to deploy a React application built with Vite to GitHub Pages.

## Prerequisites

- Node.js and npm installed on your machine.
- A GitHub account.
- A React application created with Vite.

## Step 1: Install GitHub Pages Package

First, install the `gh-pages` package as a development dependency:

```sh
npm install gh-pages --save-dev
```

## Step 2: Update package.json
Add the following lines to the scripts section of your package.json file:

```json
"predeploy": "npm run build",
"deploy": "gh-pages -d dist"
```
Also, add the homepage field to the package.json file, replacing [usergithub] with your GitHub username and [repositoryname] with your repository name:

```json
"homepage": "https://[usergithub].github.io/[repositoryname]"
```
Here is an example package.json:

```json
{
  "homepage": "https://julioraf4.github.io/githubpages-tutorial",
  "name": "juliopeixoto",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.56",
    "@types/react-dom": "^18.2.19",
    "@typescript-eslint/eslint-plugin": "^7.0.2",
    "@typescript-eslint/parser": "^7.0.2",
    "@vitejs/plugin-react": "^4.2.1",
    "eslint": "^8.56.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.5",
    "typescript": "^5.2.2",
    "vite": "^5.1.4"
  }
}
```

## Step 3: Update Vite Configuration
Add the base property to the Vite configuration file (vite.config.js or vite.config.ts) with the value of your repository name:

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  base: "/githubpages-tutorial"
})
```

## Step 4: Deploy to GitHub Pages
Run the following command to deploy your application:

```sh
npm run deploy
```
This command will build your application and deploy it to the gh-pages branch of your repository.

Step 5: Access Your Deployed Application
After the deployment is complete, you can access your application at:

```arduino
https://[usergithub].github.io/[repositoryname]
```
