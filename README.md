# AngularJS Node js full stack kit
**(Webpack, ES2015, Express, Sass, Babel)**  

It is a full stack project for AngularJS web application which objects is:
- Webpack build and bundle all the assests.
- Provide easy to use extensibility with npm managers;
- Mockup server for your application;
- Supports ES2015 using Babel 
- Supports SASS for styling you application
- Give the basic folders and modules structure of angular application;

## Future Updates (Working on it)
- Integrate MongoDB

## Installation

1) Create a new folder for your project, and clone this repo inside it
```
git clone https://github.com/sonujose/Angularjs-Nodejs-Express-Fullstack-solution.git
```
2) You need to have node and npm installed on your system, npm version should be grater than 2.x , Install webpack if you don't have it already. Need webpack cli for running the application 
```
npm install --global webpack
```
3) Install all npm dependencies
```
npm install
```
4) Run the api server 
```
npm test
```
5) Run the application (Webpack-dev-server) [open another terminal]
```
npm start
```
6) Will be directed to `http://localhost:8080`, wait untill webpack bundles all your files and server.
[Your api server will be running at localhost:9000, webpack-dev-server will autimatically navigate to server on /api/ calls, you dont need to worry]

6) Congratulations, you've just setup your Angular Node fullstack application!

### Basic folder structure
Some job for Captain Obvious
```
client/           // Client side files
node_modules/     // Node Modules
server/           // Server side files
index.html        // Basic page for angular project
```

### Client folder structure

```
app/          // Angular app files
build/        // concatenated assets generated by gulp
webpack-build // concatenated assets generated by webpack
styles/       // Your general scss files which will includes in main entry for application scss
app.js        // Main entry for angular app with router config
vendor.js     // Main entry for vendor js .[currently not added , can be added if you need other modules, refer that in webpack vendor entry]
```

### Server Folder Structure
```
data/         // Folder with mockup json data for server api
  test.json     // Mockup json file whic will be returned to the client by server api
libs/         // Folder with server libs
  loader.js     // Json files loader
routes.js     // Server routes
server.js     // Main server file which create and setup express application
```
## Usage

####1) How do I start creating my own app  
Just see angular folder structure comments and look at the existing components and shared modules.  
It'll give you the picture of overall application structure.  
So basically: you have main angular file `client/app.modules.js`. It contains your main app which requires `components` and `shared` modules. Components modules contains all single components of your application (like pages for example or single use directives), and shared module contains all elements of your app like shared assets, directives, templates etc..
The main point here is using modular structure so later you can just delete the folder with your module and it's gone from your app completely (with all its directives, services, styles and views). So yes, you must put all files related to the module in its own folder, even the scss.  

####2) How can I style my app  
For styling you must use scss. The main entry for all your styles is `client/styles/app.scss`, you can include in it all partials scss from your application. You must have two kinds of partial scss files.  
scss are organised as partials in the styles folder, containing partial folder for different types of styles , all those are imported in app.scss. Also styles for different components are put in their corresponding folders and are called from app.scss.

####3) How to use bootstrap styles
Inorder to use bootstrap styles you need to uncommnet requird styles from the `client/styles/vendors/bootstrap`. This is made inorder to decrease the file size of vendor styles

####4) How can I install extension
To add an extension to your app you must install it either from `npm`, then you just require it from `client/vendor.js` or load as dependency in webpack vendor entry. 
If this extension has its own styles you can just `@import` it from vendor.scss  
**note:** if you want to import `.css` file create root-relative path for it `/client/vendor/..` or `/node_modules/..`  

####5) How can I use mockup server  
When you've run `npm test` you automatically start the node server with express.    
If you want to add your api route - just go to the `server/routes.js` and create one (use test route as example).  
Add json file to the `server/data/` folder and send it body in your new route with `dataLoader`, or just send whatever you want in your route.

####6) Using webpack
Here webpack is used for bundling the js files. `webpack.config.js` file bundles the entire js files into two modules app and vendor and are minified and used as reference in `index.html`.
The output of bundled files are in the `client/webpac-build` file. if you need to test webpack bundling just run command `webpack` 

####7) ES2015 is supported (can be upgraded to ECMA Script latest version) 
All the js files inside app support es2015 , used babel loader as the transpiler for es2015. you can upgrade to latest ECMAScipt version in `package.json`, change the `presets` value of `babel` from`es2015` to `latest`

####8) Analyze your webpack modules
1) Run 
```
webpack --profile --json >> stats.json
```
2) open
```
http://webpack.github.io/analyse/#modules
```
3) upload stats.json file from your repository

## Have FuN


