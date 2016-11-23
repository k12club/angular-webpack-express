# AngularJS Node js full stack kit
**(Webpack, Express, gulp, Sass)**  

It is a full stack project for AngularJS web application which objects is:
- Organize all assets with webpack gulp and sass;
- Provide easy to use extensibility with npm managers;
- Create mockup server for your application;
- Give the basic folders and modules structure of angular application;

## Future updates (We are working on it)
- Currently sass files are compiled by gulp, need to make webpack compile sass
- Need to update angular modules for better bundling using webpack
- Live watch need to be updated
- Add Typescript support

## Installation

1) Create a new folder for your project, and clone this repo inside it
```
git clone https://github.com/sonujose/Angularjs-Nodejs-Express-Fullstack-solution.git
```
2) Install all npm dependencies
```
npm install
```
3) Install gulp and webpack if you don't have it already.
```
npm install --global gulp webpack
```
4) Run the application (Webpack and gulp)
```
npm start
```
5) Wait untill gulp do its job, when you'll see toast notification `Server listening on port 9000` then go to `http://localhost:9000`  
6) Congratulations, you've just setup your angular application!

### Basic folder structure
Some job for Captain Obvious
```
client/           // Cleint side files
node_modules/     // Node Modules
server/           // Server side files
gulpfile.js       // File with all gulp commands
index.html        // Basic page for angular project
```

### Client folder structure

```
app/          // Angular app files
build/        // concatenated assets generated by gulp
webpack-build // concatenated assets generated by webpack
styles/       // Your general scss files which will includes in main entry for application scss
vendor/       // Bower_components folder
main.js       // Main entry for angular app js
main.scss     // Main entry for application scss
vendor.js     // Main entry for vendor js (you can require both node_modules and bower packages from it).
vendor.scss   // Main entry for vendor css (if you have an external package with css or scss - include it here).
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
scss are organised as partials in the styles folder, containing partial folder for different types of styles , all those are imported in app.scss. Also styles for different components are put in their corresponding folders and are called from app.scss
**note:** no need to write browser prefixes like `-webkit`, `-moz` or `-ms` it will be added automatically by `gulp-autoprefixer` for 2 latest versions of all major browsers (you can change this option in `gulpfile.js` - task `buildSass`).  

####3) How to use bootstrap styles
Inorder to use bootstrap styles you need to uncommnet requird styles from the `client/styles/vendors/bootstrap`. This is made inorder to decrease the file size of vendor styles

####4) How can I install extension
To add an extension to your app you must install it either from `npm`, then you just require it from `client/vendor.js` or load as dependency in webpack vendor entry. 
If this extension has its own styles you can just `@import` it from vendor.scss  
**note:** if you want to import `.css` file create root-relative path for it `/client/vendor/..` or `/node_modules/..`  

####5) How can I use mockup server  
When you've run `gulp` you automatically start the node server with express.    
If you want to add your api route - just go to the `server/routes.js` and create one (use test route as example).  
Add json file to the `server/data/` folder and send it body in your new route with `dataLoader`, or just send whatever you want in your route.


