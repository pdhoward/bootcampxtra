# 9.5 Lesson Plan - Intro to Webpack (10:00 AM)

## Overview

In today's class students will be continuing their journey into web performance. Today we will be learning about Webpack. Webpack is a module bundler, with its main purpose being bundling JavaScript files for use in a browser. Webpack provides a lot of functionality that developers can take advantage of to make their programs more performant.

## Learning Objectives

* Create a basic Webpack configuration file.

* Bundle their JavaScript code into a single file.

* Add Webpack plugins to their Webpack configs.

* Convert web applications to PWA using Webpack 

* Perform code splitting using webpack.

## Instructor Notes

* Complete activities `15-Ins-Webpack-Intro` through `23-Stu-Mini-Project`

* Webpack can be a difficult tool to get your head around, so be as clear as possible in your explanations and be ready to answer plenty of student questions. It is recommended that you review the webpack [docs](https://webpack.js.org/concepts). You may want to read [Why Webpack](https://webpack.js.org/concepts/why-webpack) so that you are prepared to answer student questions like "Why are we learning this?".

## Slides

* N/A

## Time Tracker

[9.5 Time Tracker](https://docs.google.com/spreadsheets/d/1ZJwRAu9cPWuUZmjoZ2diRv-3tBUn0ywbI7nzOhi1PZQ/edit#gid=0)

- - -

## Class Instruction

### 1. Instructor Do: Welcome/Intro Webpack (10 mins)

* Welcome students to the class.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ In terms of performance, what are the skills we have learned so far?

  * 🙋 Compression, minification, lazy-loading, and caching.

  * ☝️ What if our application has dependencies? Do we minify those by-hand?

  * 🙋 No, that would be inefficient and take a long time.

  * ☝️ Today we're learning webpack. What do you think webpack does?

  * 🙋 Webpack is a module bundler. What this means is that Webpack takes our JavaScript and all of its dependencies and bundles it into a single file.

* There are two main phases to a module bundler.

  * Dependency Resolution

  * Packing

### 2. Instructor Do: Intro to Webpack (5 mins)

* Navigate to [15-Ins-Webpack-Intro/](../../../../01-Class-Content/18-PWA/01-Activities/15-Ins-Webpack-Intro/) from the command line and run:

  * `npm install webpack webpack-cli -D`

* Open `webpack.config.js` in your IDE and point out the following:

  * In order to use Webpack, we need to provide a configuration file that Webpack will use to build off of.

  * Entry is the main JavaScript file that our application uses.

  * Output is an object describing the bundle that Webpack will build. The path property is the folder that the file will be created in. In this configuration, we are telling Webpack that the output file should be in a folder named `dist` and the file itself should be named `bundle.js`.

  * In the dependency resolution phase, Webpack looks for an entry point. When the entry point is identified the main purpose of dependency resolution is to scan and gather all of the pieces of code and dependencies required to make the code function. The map of required code and dependencies is referred to as a _dependency graph_. Once this graph as been made, we continue to the packing phase.

  * Setting the mode property allows us to create custom configurations for different environments. In this configuration, we are specifying that this build should be used for development.

```js
const config = {
  entry: "./src/app.js",
  output: {
    path: __dirname + "/dist",
    filename: "bundle.js"
  },
  mode: "development"
};
module.exports = config;
```

* Open `package.json` in your IDE and point out the following:

  * 📝 Adding `-D` to the npm install command causes the packages to be saved as "devDependencies" in the `package.json`. While "dependencies" are dependencies that are used at runtime, "devDependencies" are meant to be packages that are only needed in development.

  * The JavaScript bundle that Webpack creates does **not** need Webpack to run.

  * We have added the script "build" so that when `npm run build` is ran, it executes `webpack --watch`. This command will watch over your entry point(s) for changes and build again if any files are changed.

```json
{
  "name": "webpack-demo",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "build": "webpack --watch",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "webpack": "^4.31.0",
    "webpack-cli": "^3.3.2"
  }
}
```

* Run `webpack` from the command line and explain the following:

  * Running `webpack` created a new folder named `dist` with the new bundle inside a file named `bundle.js`.

  * Webpack takes the dependency graph that was created and then packs all of the code and dependencies necessary into an output file specified within the configuration file.

* Open the file `dist/app.js` in your IDE.

  * Show that the JavaScript is a minified bundle of `src/app.js` and any dependencies it has. 

  * Use `Find` with your IDE to point out that the minified bundle contains `console.log` from `src/app.js`.

* Open `index.html` in your IDE.

  * Point out that we have to update the script tag so that it uses our new webpack build.

  ```html
  <script type="text/javascript" src="./dist/bundle.js"></script>
  ```

* Now open `index.html` in your browser and point out the following:

  * `Hello webpack` appears in the console, coming from the file `bundle.js`.

* Lastly run `npm run build` from the command line and explain the following:

  * The build script set up in `package.json` runs and watches for any changes in our files, similar to how `nodemon` watches for changes. In order to kill the process, type `Ctrl + C` in your terminal.

### 3. Student Do: Budget Tracker (10 mins)

```md
# Budget Tracker

In this activity we will create a bundle.js file with Webpack.

## Instructions

* Run the following command: `npm install webpack webpack-cli -D`

* Create a file called `webpack.config.js`.

* Using the entry point of `src/app.js`, make Webpack output a bundle file in a folder called `dist/`.

* In `index.html`, change the JavaScript file src to be your new bundle file.

* Add the necessary scripts to `package.json`, then run Webpack with the `--watch` option.

* Update this application to accomplish the following:

  * When the user types in a value to the price field and clicks submit, the remaining balance should be updated.

  * Using the `require` module and `module.exports`, move the code that calculates the new budget to a file named `calculations.js`.

  * Update the `reset` function so that when clicked, it sets the current balance back to its original balance and clears the list of expenses.

### Hints

* Make sure that Webpack is working properly before attempting to make adjustments to the app.
```

# 4. Instructor Do: Review Budget Tracker (5 mins)

* Open `16-Stu-Webpack-Intro/Solved/` in the browser and demonstrate the following functionality:

  * When we add multiple expenses, we see that our balance adjusts for each submission.

  * When we click the reset button, the expenses list gets cleared and the balance is reset to its original value.

* Open `16-Stu-Webpack-Intro/Solved/app.js` in your IDE and point out the following:

  * At the top of the file, we bring in `module.exports` from the calculations file.

  * Webpack allows us to use modules, including the `require` module just like we can in Node.js apps.

  * 📝 If we were not using Webpack, we wouldn't be able to use `require` in client-side JavaScript.

  ```js
  const calculations = require("./calculations");
  ```

  * Our subtract function needs to parse `balanceEl.innerText` from a String to a Number before perfoming the `-` operation.

```js
function submit() {
    const total = calculations.subtract(Number(balanceEl.innerText), priceEl.value);
    balanceEl.innerText = total;
    addToList(expenseEl.value, priceEl.value);
}

function reset() {
    const total = 2000;
    balanceEl.innerText = total;
    expensesListEl.innerHTML = '';
}
```

* Open `webpack.config.js` in your IDE and point out the following:

  * We use the same configuration as the previous demo.

* Open `package.json` in your IDE and point out the following:

  * We use the same configuration as the previous demo.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ Which JavaScript file do we link to index.html? 

  * 🙋 Our JavaScript bundle, `./dist/bundle.js`

### 5. Instructor Do: Demo Bundle Analyzer Plugin (5 mins)

* Open [17-Ins-First-Plugin/package.json](../../../../01-Class-Content/18-PWA/01-Activities/17-Ins-First-Plugin/package.json) in your IDE and explain the following: 

  * We've added webpack-bundle-analyzer to our devDependencies and the chart.js library to our dependencies.

  * The `webpack-bundle-analyzer` is a plugin that will build an interactive visualization of all of the dependencies in our project.

* Open [17-Ins-First-Plugin/webpack.config.js](../../../../01-Class-Content/18-PWA/01-Activities/17-Ins-First-Plugin/webpack.config.js) in your IDE and point out the following:

  * Webpack plugins can be used to perform tasks that Webpack can't perform by default. Some of these tasks include asset management, additional bundle optimization, and adding PWA capabilities.

  * Plugins could be used multiple times in the same configuration file, so it is important that you create an instance of one by using the keyword `new`.

  * Emphasize that we've simply added a library so that we can analyze its impact on the total bundle size.

* Run `npm run build` from the command line, navigate to [http://127.0.0.1:8888](http://127.0.0.1:8888) in your browser if the tab does not automatically open and explain the following:

![Bundle Analyzer](Images/bundleAnalyzer.png)

  * This plugin helps us analyze the different impacts that libraries have on the bundle size of our application.

  * When we mouse over the `bundle.js` section, then the `chart.js` section we can see that the chart.js library makes up a significant portion of our total bundle size.

  * ☝️ Why is `moment.js` included here, even though we didn't install it?

  * 🙋 Even though we didn't explicitly install `moment.js`, it is a dependency of `chart.js`, and adds to the total bundle size of our application.

### 6. Student Do: Gallery App with Webpack (10 mins)

* **Instructor Note:** Keep in mind that lazily loaded resources will probably not be cached the first time the page is loaded because they will often be fetched _before_ the service worker has finished installing.

* Direct students to the instructions found in [18-Stu-Webpack-Plugin](../../../../01-Class-Content/18-PWA/01-Activities/18-Stu-Webpack-Plugin/README.md):

```md
# PWAs with Webpack

* In this activity we will adjust our Gallery app so that Webpack minifies and bundles our code.

## Instructions

* Before you begin, make sure to install all of the necessary dependencies with `npm install`.

* Run the following command: `npm install webpack-pwa-manifest -D`. (https://github.com/arthurbergmz/webpack-pwa-manifest)

* In a separate tab in your terminal, start a mongodb server with `mongod`.

* Run `npm start` to make sure that the application works as expected.

* Using the entry point of `public/assets/js/app.js`, make Webpack output a bundle file in a folder called `/public/dist/`.

* Update `webpack.config.js` to use the `WebpackPwaManifest` plugin. This will generate a `manifest.json` file to replace the one we manually created. Use the values from `manifest.webmanifest` in activity `13-Stu_Caching_Fetching_Files` to provide the configuration values passed to `WebpackPwaManifest`. Use the plugin to create icons following the example in the [webpack-pwa-manifest documentation](https://github.com/arthurbergmz/webpack-pwa-manifest).

* Add the script `"prestart": "npm run webpack"` to the scripts in `package.json` so that Webpack will build every time the application is started.

* In `index.html`, change the JavaScript file src to be your new bundle file and the link to the manifest to be the one generated by the `WebpackPwaManifest` plugin.

* In `service-worker.js`, update the `FILES_TO_CACHE` array with files generated from Webpack.

* Change the mode to `"production"` in `webpack.config.js` so that the generated bundle will be minified.

### Bonus

* Install the bundle analyzer plugin and identify which modules contribute the most to the total bundle size.

### Hints

* Try clearing application storage and disabling cache after making changes to your application. If it appears to be working, use Chrome DevTools to toggle `offline mode` and ensure that the application uses the service worker.

* You may find it easier to override the default behavior of `webpack-pwa-manifest` by setting the `fingerprints` and `inject` options to `false`, since you are manually providing the links to `manifest.json` and the names of the icon images to cache. 
```

### 7. Instructor Do: Review Gallery App with Webpack (5 mins)

* Open [18-Stu-Webpack-Plugin](../../../../01-Class-Content/18-PWA/01-Activities/18-Stu-Webpack-Plugin/Solved) in your terminal.

* Run the following commands to start the application:

```bash
npm install
node seeders/seed.js
npm start
```

* Navigate to [http://localhost:3000](http://localhost:3000) in your browser and point out the following: 

  * If we inspect our Service Worker with DevTools, we see that `dist/bundle.js` is cached.

  * Additionally, "Service Worker registered successfully" was logged to the console.


  * The plugin, `WebpackPwaManifest`, generates a manifest.json file to be included in our build directory. While most of the properties are the same as a regular manifest.json, this plugin also automatically resizes all of our icons to the appropriate sizes and allows for the use of ES6 features and JavaScript comments. Setting `fingerprints` and `inject` to `false` makes the names of the output files predictable so that we can manually add code to `service-worker.js` to cache the generated manifest and image files. _Point out that there are webpack plugins available that can generate our html using the "fingerprinted" names generated by webpack._

```js
plugins: [
  new WebpackPwaManifest({
    filename: "manifest.json",
    inject: false,
    fingerprints: false,
    name: "Images App",
    short_name: "Images App",
    theme_color: "#ffffff",
    background_color: "#ffffff",
    start_url: "/",
    display: "standalone",
    icons: [
      {
        src: path.resolve(
          __dirname,
          "public/assets/images/icons/icon-512x512.png"
        ),
        size: [72, 96, 128, 144, 152, 192, 384, 512]
      }
    ]
  })
]
```

* Open `package.json` in your IDE and point out the following:

  * Our plugin must be installed as a devDependency. 

  * We've also added the script "prestart", which is a built in npm script that will automatically run before each time `npm start` is run.

### 8. Instructor Do: Demo Pure Functions (10 mins)

* The next demo is going to use a couple of ES6 features that aren't supported in all browsers.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What tool do you think we will need to use to allow us to use ES6 in all browsers?

  * 🙋 Babel. This is true, but in order to use Babel with our Webpack build we will need to utilize a Babel feature known as a **loader**.

  * Normally, Webpack only knows how to process regular JavaScript. Loaders allow Webpack to compile and bundle non-JavaScript resources like CSS, HTML, TypeScript, and more. Specifically, the Babel loader goes through all of our JavaScript files and transpiles ES6 into ES5.

* Open `19-Ins-Pure-Functions/webpack.config.js` in your IDE and point out the following:

  * We've created a new object called module and within it define an array of rules. 

  * `test` is a regular expression that describes the files that you want to match.

  * Since Babel loader is pretty slow, it is especially important that you define an `exclude` property that contains a regular expression that matches all files in your `node_modules` folder.

  * The `use` property is where we define which loader we are going to use, along with any presets or configurations to pass to the loader. Here, we are telling Webpack to use the babel-loader for all JavaScript files that are not in `node_modules`, and to use a preset called `@babel/preset-env`.

```js
 module: {
    rules: [{
        test: /\.m?js$/,
        exclude: /(node_modules)/,
        use: {
            loader: 'babel-loader',
            options: {
                presets: ['@babel/preset-env']
            }
        }
    }]
}
```

  * Now that we've added our loader, we need to install Babel itself, the loader, and any presets that we want to use. 

* Run `npm install @babel/core babel-loader @babel/preset-env -D` from the command line.

* Open up `src/app.js` and point out the reorganization of the files. 

* We have added the `Chart.js` library so that we can see a bar chart of our expenses. 

  * Remember, Webpack allows us to import other npm modules into our application. 
  
  * We've separated the files into files like `elements.js` and `expenses.js` to help further modularize our code. There is no definitively "right" way to split up your code. The main goal when refactoring code to be split between files is to create functions that are reusable and relatively "pure", when possible.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What does it mean for a function to be pure?

  * 🙋 Pure functions are straightforward with singular purposes. They do not have any "side effects" within them. **Side effects** are bits of code that interact with the outside world like database calls or changes to the DOM.
  
  * 🙋 In pure functions, whenever data needs to be modified, it is not mutated. Instead, we create a new variable that describes the new mutation. Pure functions have the advantage of being easily testable and reusable. It is considered best practice to use pure functions whenever possible.
  
  * ☝️ What does it mean for a function to be impure?

  * 🙋 Impure functions tend to have multiple purposes. The might contain database or network calls. Even though it is preferred to keep your functions simple, impure functions are often unavoidable. 

* Open `src/calculations.js` in your IDE and point out the following:

  * The `subtract` function is a pure function. It creates a new variable for the result, instead of modifying the input and contains no side effects.

  ```js
  export function subtract(a, b) {
    const result = a - b
    return result;
  }
  ```

* Open `src/app.js` in your IDE and point out the following:

  * The `submit` function is an impure function. It modifies existing values and has multiple side effects.

  ```js
  function submit() {
    const total = subtract(Number(balanceEl.innerText), priceEl.value);
    balanceEl.innerText = total;
    addToList(expenseEl.value, priceEl.value);
    updateChart(expensesChart, expenseEl.value, priceEl.value);
  }
  ```
  
* Run `npm install` in your terminal and open `index.html` file in your browser and demonstrate the following functionality:

  * The submit button adds new expenses to the list.

  * The chart is updated with the new expenses.

### 9. Student Do: Gallery Pure Functions (15 mins)

* Direct students to the instructions of their next activity in [20-Stu-PWA-refactor/README.md](../../../../01-Class-Content/18-PWA/01-Activities/20-Stu-PWA-refactor/README.md).

```md
# PWA Refactor

In this activity we will adjust our Gallery app so that Webpack minifies and bundles our code.

## Instructions

* Run `npm install`.

* Run `npm install -D babel-loader @babel/core @babel/preset-env`.

* Using `19-Ins-Pure-Functions/webpack.config.js` as a reference, update `Unsolved/webpack.config.js` to use babel-loader.

* Using the ES6 import/export syntax, separate functions out into separate JavaScript files to make your application more modular.

* While there are many ways that you can separate your JavaScript files, it is recommended that you create somethings similar to the following file structure:

  * `app.js` Loads images and calls the `createCards` function.

  * `cardCreation.js` Responsible for all functions related to the creation of cards.

  * `domMethods.js` Responsible for all functions related to manipulating the DOM.

  * `rating.js` Handles the creation of the ratings form and the update method.

* Adjust the files in the `FILES_TO_CACHE` array within `public/service-worker.js` so that the Webpack bundle is cached instead.

* Run `npm start` and make sure that the application still works as expected.

### Hints

* Try testing out functionality of the application on [localhost](<http://localhost:3000>) every time you make changes. This will help you identify the code that does not work as expected.

* You can use the [Babel Loader Docs](https://github.com/babel/babel-loader) as an additional reference.
```

### 10. Instructor Do: Review Gallery Pure Functions (10 mins)

* Open [20-Stu-PWA-refactor/Solved/webpack.config.js](../../../../01-Class-Content/18-PWA/01-Activities/20-Stu-PWA-refactor/Solved/webpack.config.js) in your IDE and explain the following:

  * The configuration object is updated to use `babel-loader` to transpile only files ending in ".js".

  * Code in "node_modules" is not transpiled by the `babel-loader` so that our code will run on a wider range of browsers and browser versions. It allows us to write code that uses more modern syntax and still have the code work on browsers that do not support some features.

  ```js
  module: {
    rules: [
      {
        test: /\.js$/, // files must end in ".js" to be transpiled
        exclude: /node_modules/, // don't transpile code from "node_modules"
        use: {
          loader: "babel-loader",
          options: {
            presets: ["@babel/preset-env"]
          }
        }
      }
    ]
  }
  ```

* Next, open [Solved/public/assets/js/](../../../../01-Class-Content/18-PWA/01-Activities/20-Stu-PWA-refactor/Solved/public/assets/js/) and demonstrate how the code was split up into separate modules.

  * Remind students that there is no definitively "right" way to split up your code. The main goal when refactoring code to split between files is to create functions that are reusable and relatively "pure", when possible.

  * Open the terminal, cd to `.../20-Stu-PWA-refactor/Solved`, and run `npm run build` to run Webpack. (Run `npm install` first if you haven't done so already.)

  * Show students how Webpack created `bundle.js` which includes the code from all the modules from `public/assets/js`.

* If time permits, answer lingering questions on the topics of Webpack, modularizing code, and pure functions.

### 11. Instructor Do: Demo Lazy Loading JavaScript (10 mins)

* Tell the class that just like the lazy loading they worked with using Images, JavaScript can also be loaded as needed.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What is lazy loading?

  * 🙋 Lazy loading allows us to load resources on an as-needed basis, instead of on page load.

  * ☝️ If there is JavaScript specific to a part of the page a user is using, when do you think it should be downloaded?

  * 🙋 We should only download the JavaScript specific to a part of the page when the user navigates to that page.

  * ☝️ Could deferring the downloading save us time on page load?

  * 🙋 Absolutely. Longer bundle sizes result in longer load times.

* Open `21-Ins-Chunking/webpack.config.js` in your IDE and point out the following:

  * We have added a second entry point to our bundle. This entry point is `chart`.

  * `chart` points to `./src/expenseChart.js`.

  * `filename: "[name].bundle.js"` dynamically names our bundle after the name of the entry point. For instance, the entry point `chart` will create a bundle named `chart.bundle.js`.

  * By creating multiple entry points, we can defer the loading of a particular bundle until the code required is needed.

* Open `chart.html` and point out the following:

  * We've added a `<script>` tag to our html that loads our `chart.js` JavaScript bundle.

```html
<script type="text/javascript" src="./dist/chart.bundle.js"></script>
```

* Open `21-Ins-Chunking` in your IDE and run the following commands from your command line:

  * `npm install`

  * `npm run build`

* Open the `index.html` in your browser and point out the following:

  * If we inspect out Network in DevTools, we can see that the chart.js has not been loaded yet.

  * Only once we click the `chart` link in the navbar of the page does the `chart.js` bundle load.

![Network JS](Images/networkJS.png)

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What are the possible setbacks of this method?

  * 🙋 If both of our bundles require some of the same dependencies, those will be included and both bundles and thus we will end up with duplicated code between bundles. 

### 12. Student Do: Gallery Lazy Loading JavaScript (15 mins)

* Direct students to the activity instructions found in [22-Stu-Chunking/README.md](../../../../01-Class-Content/18-PWA/01-Activities/22-Stu-Chunking/README.md)

```md
# Chunking

In this activity, we will practice using multiple entry points to split up our JavaScript code.

## Instructions

* Run `npm install`.

* In `webpack.config.js`, add entry points for JavaScript files for the three pages, home, detail, and favorites.

* Update `service-worker.js` file so that it caches the new bundles.

* Make sure to update each html file so that it also uses the appropriate bundle.

* Note that the gallery application has been upgraded with the ability to save your favorite images to IndexedDb. 

* Once again, there are many ways that you can separate your JavaScript files. It is recommended that you create somethings similar to the following file structure to avoid chunking unused code:

  * `api.js` Loads images from the api.

  * `cardCreation.js` Responsible for all functions related to the creation of cards.

  * `domMethods.js` Responsible for all functions related to manipulating the DOM.

  * `detail.js` Responsible for the Detail page of the application.

  * `favorites.js` Responsible for the Favorites page of the application.

  * `home.js` Responsible for the Home page of the application.

  * `indexedDb.js` Contains a helper method to interact with IndexedDb.

  * `rating.js` Handles the creation of the ratings form and the update method.

* Run `npm start` and make sure that the application still works as expected.

* Navigate to each page and make sure that the bundle files are all being cached by the service worker.

### Hints

* Try testing out functionality of the application at [http://localhost:3000](http://localhost:3000) every time you make changes. This will help you identify the code that does not work as expected.

* If extracting functionality from a JavaScript file causes any of the pages to stop working, do **not** continue until you understand why it's not working as expected.

* Ask the instructor or a TA for help if you get stuck or are unsure why a function isn't working.
```

### 13. Instructor Do: Review Gallery Lazy Loading JavaScript (10 mins)

* Open `22-Stu-Chunking/Solved/webpack.config.js` in your IDE and explain the following:

  * There are now three entry points designated.

  ```js
  entry: {
          app: './public/assets/js/home.js',
          detail: './public/assets/js/detail.js',
          favorites: './public/assets/js/favorites.js'
      },
  ```

  * We also used the `[name].bundle.js` syntax in our output to dynamically name our bundle after the entry point it was built from.

  ```js
  output: {
          path: __dirname + '/public/dist',
          filename: '[name].bundle.js',
      },
  ```

* Now run the following commands from the command line:

  * `npm install`

  * `npm start`

  * In the console, we have 3 `bundle.js` files and the bundle naming aligns with the entry points provided in the `webpack.config.js`

![3 Bundles](Images/multipleBundles.png)

* Run the following command from the command line: `npm run webpack`

* In your browser, navigate to [localhost](<https://localhost:3000>) and explain the following:

  * If we open up our `Network` tab and toggle JS, we can click a picture's name and see that `detail.bundle.js` is loaded when we bring the details of an image.

![Network JS](Images/networkJS.png)

* In your browser, click on the link to the favorites page and point out the following:

  *  `favorites.bundle.js` loads.

  * Lazy loading is a great way to defer loading of resources that are not necessary, but there are possible problems it can raise.

  * Most notably, if multiple entry points have some of the same dependencies, those dependencies will be duplicated across bundles.

### 14. BREAK (30 mins)

### 15. Instructor Do: Introduce Mini-Project (5 mins)

* Run the following commands from the command line: 

  * `npm install`

  * `npm start`

* Navigate to [localhost:3000](http://localhost:3000) in your browser and point out the following:

  * Newsy is a news aggregator app that allows us to search for articles classified by topic, then save our favorites.

  * The home page of the application has some default topics, but we can create your own or remove the default topics.

  * Clicking on one of the topics causes the page to display a list and allows us to save each article to our favorites.

  * Saving a couple of articles to our favorites causes the button to update to a _remove_ button.

  * Navigate to the favorites page in your browser and point out the following:

    * The favorites we selected are listed.

    * The favorites data was stored in IndexedDb, since we are not using a local database for this application.

# 16. Student Do: Work on Mini-Project (60 mins)

* Spend a few minutes getting students acclimated to this application setup in terms of the npm scripts used. They will not have seen this yet, but it's a good preview for the upcoming MERN-related weeks.

```md
# PWA Mini-Project

In this activity we will take an existing news aggregator application and transform it into a PWA that can be installed on a user's device. We will also utilize webpack's minify and chunking features to help reduce the total size of the application.

## Instructions

* Open the [Unsolved](Unsolved) folder and study the existing contents, specifically in the `package.json` file at the root of the application. 

* We use a library called `if-env` to check what Node environment we're in when we start our app. If we're in development, then we'll execute the `npm run start:dev` script.

* We use another library called `concurrently` in development so we can run two processes at once. One for our Express server and one for Webpack. This way we don't have to start and stop the server every time something changes.

* Install dependencies by running `npm install` at the project root. This will also install the once in the `client` directory.

* Start the app by running `npm start` from the project root.

* Once the app starts open your browser to [localhost:3000](http://localhost:3000).

* Open [index.js](Unsolved/assets/js/index.js).

* There are 3 main sections in this application:

  * A section that allows you to manage a list of topics.

  * A section that displays different articles of a given topic. This page will also allow you to save articles to your favorites.

  * A favorites page to view a list of the user's favorite articles. This page also allows the user to remove articles from their favorites.

### Part 1

* Using the `webpack.config.js` from the previous activities, update the `webpack.config.js` file that uses a babel loader and the necessary plugins to transform the application to a PWA.

* Create an entry point for each file in `assets/js`.

* Create a `service-worker.js` and make sure to cache all of the bundle files.

### Part 2

* Take a moment to study the contents of `index.js`:

  1. `renderTopics()` renders all of the topics to the page using `createTopics`.

  2. `topicData` is an array of predefined topics to populate the page with.

  3. `createElement()` allows you to create a document element using the a string of its type, and object containing its attributes, and children elements.

* Since `createElement` is a general purpose function that we can use throughout our application, we are going to create a separate file to keep it in named `domMethods`. By doing this, we will be able to import `createElement` into any component we would like without duplicating code.

* Take a moment to study the contents of `topic.js`:

  1. Remove the `createElement` function and modify the file to use the `createElement` from `domMethods.js`.

  2. Extract the code necessary for indexedDb into its own file and be sure to import it into `topic.js`.

  3. Extract the `loadArticles` function to a new file called API and be sure to import any of its dependencies.

* Take a moment to study the contents of `favorites.js`:

  1. Remove the all function declarations for utilities, indexedDb, API, and domMethods.

  2. Using ES6 syntax, import all necessary functions.

### Hints

* You will **not** have to modify any files that are not in the `client` folder.

* Ask the instructor or a TA if you're having difficulty understanding any of the activity requirements.
```

# 17. Instructor Do: Review Mini-Project (15 mins)

* Open `index.js` in your IDE and point out the following:

  * All of the functions pertaining to the `home` page are in `index.js`.

  * `createElement` is brought in from the `domMethods.js` file.

* Open `domMethod.js` in your IDE and point out the following:

  * It is not entirely necessary for us to understand exactly how every line in `createElement` works. 
  
  * It is valuable to get practice working with code we do not fully understand because new developers almost always start their careers working with an unfamiliar codebase.

  * The `createElement` function returns a DOM element and has the following parameters:

  1. A string that represents the type of element.

  2. An object containing all of the attributes to add to the element.

  3. 1 or more children elements to be appended to the element.

  * The `createArticle` function uses a ternary expression to render a `Save to Favorites` button or a `Remove from Favorites` button depending on whether the article is already part of the user's favorites.

  * `loadPage` is a callback passed to the `createElement`. The actual function will either use the results from an AJAX request or the results from IndexedDb to render the page, depending on which function was passed through as a callback.

  ```js
  !favorite
    ? createElement(
      "button",
      {
        class: "button button--primary",
        onclick: () => {
          useIndexedDb("articles", "ArticleStore", "put", {
            source,
            author,
            title,
            description,
            url,
            urlToImage,
            publishedAt,
            _id
          });
          loadPage();
        }
      },
      "Save to Favorites"
    )
  ```

  * `createPlaceholders()` displays placeholders so that content is rendered on the page while the user waits for results from the AJAX request. Although they will only display on the page for a few seconds, they play a significant role in increasing the user's experience on the site.

  ```js
  // Create and return 4 placeholder articles
  function createPlaceholders() {
    const fragment = document.createDocumentFragment();

    for (let i = 0; i < 4; i++) {
      const placeholder = createPlaceholder();
      fragment.appendChild(placeholder);
    }

    return fragment;
  }

  // Returns markup for a placeholder article
  function createPlaceholder() {
    return createElement(
      "div",
      { class: "article-skeleton" },
      createElement(
        "div",
        { class: "article-skeleton__header" },
        createElement("div", { class: "article-skeleton__title" }),
        createElement("div", { class: "article-skeleton__published" })
      ),
      createElement(
        "div",
        { class: "article-skeleton__content" },
        createElement("div", { class: "article-skeleton__image" }),
        createElement("div", { class: "article-skeleton__text" }),
        createElement("div", { class: "article-skeleton__text" }),
        createElement("div", { class: "article-skeleton__text" }),
        createElement("div", { class: "article-skeleton__text" }),
        createElement("div", { class: "article-skeleton__text" })
      )
    );
  }
  ```

* Open `topic.js` in your IDE and explain the following:

  * When the `Topic` page is opened, `useIndexedDb` is called to check if any of the articles have been favorited. This is necessary so that articles that have already been saved to the user's favorites can display a `Remove from Favorites` button.

```js
import { useIndexedDb } from "./indexedDb";
import { loadArticles } from "./API";
import { renderArticles } from "./domMethods";
// Call renderArticles on page load
function loadPage() {
  useIndexedDb("articles", "ArticleStore", "get").then(results => {
    const favorites = results;
    loadArticles().then(data => {
      const mappedData = data.map(article => {
        article.favorite = false;
        favorites.forEach(fav => {
          if (article._id === fav._id) {
            article.favorite = true;
          }
        });
        return article;
      });
      renderArticles(mappedData, loadPage);
    });
  });
}

loadPage();

```

* Open `service-worker.js` in your IDE and point out the following:

  * Each html file should be cached with its respective bundle.

```js
const FILES_TO_CACHE = [
  '/',
  '/index.html',
  '/favorites.html',
  '/topic.html',
  '/assets/css/style.css',
  '/dist/app.bundle.js',
  '/dist/favorites.bundle.js',
  '/dist/topic.bundle.js',
  'https://fonts.googleapis.com/css?family=Istok+Web|Montserrat:800&display=swap',
  'https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css',
];
```

* Open `webpack.config.js` in your IDE and point out the following:

  * There are 3 different entry points created for each app. 

  * Each bundle will include all dependencies brought into each entry file with ES6 `import`.

```js
entry: {
    app: "./assets/js/index.js",
    favorites: "./assets/js/favorites.js",
    topic: "./assets/js/topic.js"
  },
  output: {
    path: __dirname + "/dist",
    filename: "[name].bundle.js"
  },
```

  * Although most of the configuration can vary, depending on the app, it's important that the icon `src` points to a valid path to an icon for the application.

  ```js
  plugins: [
    new WebpackPwaManifest({
      fingerprint: false,
      name: "Newsy app",
      short_name: "Newsy",
      description: "An application that allows you to view different news articles and save your favorites.",
      background_color: "#01579b",
      theme_color: "#ffffff",
      "theme-color": "#ffffff",
      start_url: "/",
      icons: [{
        src: path.resolve("assets/images/icons/android-chrome-192x192.png"),
        sizes: [96, 128, 192, 256, 384, 512],
        destination: path.join("assets", "icons")
      }]
    })
  ]
  ```

* If time permits, ask the students if there are any parts of the application that they would like to spend more time going over. 

  * Some students may be frustrated with the amount of time they needed to spend refactoring code so that it could be easily chunked by webpack.

  * If this is the case, remind students that one of the main motivations behind chunking is reducing the bundle size of your code. While there are many strategies one can take to split up their code, it is important that it's split in a way that makes the code reusable and clear in purpose. Sometimes this means large amounts of refactoring functions. This is time well spent since they are making their code easier to test and easier for other developers to work with.

---

### 18. Review Unit 18 (40 mins)

* Spend the rest of class answering lingering questions about the Mini Project, then proceed to lead a review on units 17 and 18.

### 19. END (0 mins)

* Recommend students go through the following material at home before next class if possible. These articles will help them better understand the material covered today in class.

### Lesson Plan Feedback

How did today’s lesson go? Your feedback is important. Please take 5 minutes to complete this anonymous survey.

[Class Survey](https://forms.gle/nYLbt6NZUNJMJ1h38)
