# 9.4 Lesson Plan - PWAs (10:00 AM)

## Overview

Today's class will continue our journey into web performance by learning about progressive web apps. We will start with our basic Gallery App and step by step, implement a web app manifest as well as a service worker. This new functionality will provide us with a fully functioning progressive web app that delivers an offline experience to our users.

## Instructor Notes

* Complete activities `05-Stu_Gallery-Lazy-Load` through `14-Stu_Map-PWA`.

* You may need to clear your storage periodically in order to see each iteration of activities. Do so in DevTools under `Application > Clear storage > Clear site data`.

* Some of today's activities use mongoDB to store data. It is recommended that you open a separate tab in your terminal and run `mongod`. Don't forget to kill the process at the end of class.

* It is recommended that you take some time to familiarize yourself with service workers before class begins. Specifically, look over the service worker lifecycle and caching and returning requests at https://developers.google.com/web/fundamentals/primers/service-workers/.


## Learning Objectives

* Explain the benefits a progressive web app offers a user over a traditional app.

* Implement and explain the role of a web app manifest.

* Implement and explain the role of a service worker.

* Successfully cache and fetch files to deliver them in an offline experience.

* Install a PWA on both desktop and mobile devices

## Slides

N/A

## Time Tracker

[9.4 Time Tracker](https://docs.google.com/spreadsheets/d/1yFXTsN96pl6jbyMS2fhDWsNKppWdzxZt9DQs6uVUcwQ/edit#gid=0)

---

## Class Instruction

### 1. Student Do: Lazy Loading (15 mins)

* Direct students to the activity instructions located in [05-Stu_Gallery-Lazy-Load](../../../../01-Class-Content/18-web-performance/01-Activities/05-Stu_Gallery-Lazy-Load/README.md)

```md
# Lazy Loading Images

In this activity you are going to work with the Intersection Observer API to implement lazy loading functionality for our Gallery App.

## Instructions

* In this activity you are going to take the Gallery App and implement Lazy Loading functionality.

  * This will allow for us to load images only as they are needed, saving loading times.

* You will primarily be working within `loadImages.js`

* Inside of `public/assets/images` is a `.zip` file containing all the images needed for the app. Unzip this file and make sure the contents end up in your images folder.

* After you have completed implementing lazy loading, open your Dev Tools and run another Lighthouse Audit.
```

### 2. Instructor Do: Review Lazy Loading (5 mins)

* Open the [solved Gallery Lazy Loading app](../../../../01-Class-Content/18-web-performance/01-Activities/05-Stu_Gallery-Lazy-Load/Solved/).

* Walk students through the code that enables lazy loading in our application.

```js
function initLazyImages() {
  const lazyImages = document.querySelectorAll(".lazy-image");
```

  * First we create a `const` called `lazyImages`. We save all elements with the class `lazy-image` to this constant variable

```js
  function onIntersection(imageEntities) {
    imageEntities.forEach(image => {
      if (image.isIntersecting) {
        observer.unobserve(image.target);
        image.target.src = image.target.dataset.src;
      }
    });
  }
```
  * Next, we create an `onIntersection` function. In this function we state that for each mage, if the image is intersecting the viewport we load our image and stop observing it as it is now on screen.

```js
  const observer = new IntersectionObserver(onIntersection);
```

  * We used a constructor function to create a new instance of IntersectionObserver, saving it to a constant variable `observer`. This allowed us to use it in our `onIntersection` function.

```js
  lazyImages.forEach(image => observer.observe(image));
}
```
  * The final line subscribes all images to be observed by IntersectionObserver to it can download the proper image when the placeholder is scrolled into view.

* Answer any questions before introducing the final activity.

### 3. Instructor Do: Intro Gallery App Full Optimization (5 mins)

* Let students know they are doing well! Web performance is important, and they now have a foundation to learn more and become great at optimizing applications.

### 4. Student Do: Optimize Gallery App (20 mins)

* Direct students to the activity instructions found in [Solved Lazy Loading Gallery](../../../../01-Class-Content/18-PWA/01-Activities/06-Stu_Gallery-Optimize/Solved)

```md
# Optimize Gallery App

In this activity you will use the Lazy Loading, GZip Compression, Image Compression, and Lighthouse to improve the performance of the Gallery App.

## Instructions

* First, unzip the uncompressed images zip file found in `public/assets/images`.

* Run the following commands:

  * Start MongoDB (run `mongod` in your terminal)
  * In a new terminal window run `npm install`
  * `npm run seed`
  * `node server.js`

* Now that the application is running, navigate to the [localhost](https://localhost:3000)

* Open your Chrome Dev tools and run a Lighthouse audit on the application. Take note of the `performance` score listed at the top of the audit report and the `opportunities` section under `performance`.

* Now, using the compression npm package, enable gzip compression in the application.

* Restart your server and run a new audit.

* Next, using [Tiny PNG](https://tinypng.com/), compress all of the images found within the `public/assets/images`

* Once you have compressed all of the images, replace the newly compressed images with the original uncompressed found in the applications images directory.

* Restart your server and run a new audit.

* Now that we have compressed our images and enabled gzip compression, our last step is to minify our JavaScript.

* Create a `dist` folder in `/public`.

  * Inside of `public/dist` create a file called `index.js`

  * Link this `index.js` to your application in `public/index.html`.

* Head to [JSCompress](https://jscompress.com/).

* Take the contents of `/public/assets/js/loadImages.js` and paste it into the text area. Check the box labeled `ECMAScript 2019 (via babel-minify)`. Click `Compress JavaScript`.

  * Take the resulting minified code and copy/paste it into your `/public/dist/index.js`

* Finally, restart your server and run a new audit.
```

### 5. Instructor Do: Review Final Gallery App (5 mins)

* Navigate to [06-Stu_Gallery-Optimize/Solved](../../../../01-Class-Content/18-PWA/01-Activities/06-Stu_Gallery-Optimize/Solved) and run the following commands:

  * npm install

  * npm install compression

* Navigate to the [06-Stu_Gallery-Optimize/Solved/server.js](../../../../01-Class-Content/18-PWA/01-Activities/06-Stu_Gallery-Optimize/Solved/server.js)
  
```js
const compression = require("compression");

app.use(compression());  
```

  * With these two lines of code we can easily enable GZip compression in our application for our served files.

* Ask the class, "Is Tiny PNG our only option for Image Compression?"

  * We can use many different tools when looking to compress images. For our purposes we chose to use Tiny PNG for its ease of use. Feel free to research other image compression tools if you'd like to dive deeper.

  * We will not go through the process of compressing all of the images as we did that earlier in the class, but image compression is an important and easy way to decrease load times.

* Ask the class, "Can you see the ways you can use these performance enhancements in your existing applications?"

  * Optimizing our applications to be performant on all devices and connection speeds will make us better developers. We need to consider those with smaller devices or slower speeds at all times as to not alienate any user base.

* Answer any remaining questions.

### 6. Instructor Do: Progressive Web Apps (10 mins)

* Welcome students to class.

* Navigate to [https://image-gallery-cache.herokuapp.com/](https://image-gallery-cache.herokuapp.com/) in your browser and point out the following: 

  * It's the Image Gallery application from earlier. But there's something different about it...
 
  * If we open the Settings in Chrome, we will see an option to `Install Images App...`
 
  * When we select `Install Images App...` we are presented with an option to "Install app?"
 
  * When we click `Install`, a new Chrome window opens with our application running in it. 
 
  * It is now installed as a desktop app! If we search our applications, we will find "Images App" listed among them.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What is different about our Image Gallery application? 
  
  * 🙋 There is added functionality to install it as a desktop application.

  * ☝️ If we can install the Images App application on our laptops, where else might we install it? 
 
* Use student answers to transition to the next activity.

### 7. Student Do: Progressive Web Applications (15 mins)

* Direct students to the activity instructions found in [07-Stu_PWAs](../../../../01-Class-Content/18-PWA/01-Activities/07-Stu_PWAs).

```md

  # Progressive Web Applications

  In this activity, you will install a progressive web application (PWA) using your smart phone. You will also research the definition and production of a PWA. If you are unable to find the icons mentioned in this activity, try them in Chrome on your computer.

  ## Instructions

  * Follow these instructions to install a PWA for your specific smartphone OS:

  * iOs:

    * 1. Navigate to [https://image-gallery-cache.herokuapp.com/](https://image-gallery-cache.herokuapp.com/) with Safari.

    * 2. Tap the Share button in Safari.

    * 3. Tap the icon labeled Add to Home Screen.

    * 4. Tap Add in the upper-right corner.

    * 5. Name your PWA, then tap Add in the upper-right corner.

  * Android:

    * 1. Navigate to [https://image-gallery-cache.herokuapp.com/](https://image-gallery-cache.herokuapp.com/) with Chrome.

    * 2. Tap the menu button in the upper right corner of Chrome.

    * 3. Tap the icon labeled Add to Home Screen.

    * 4. Name your PWA, then tap Add below the promp.

  * Be prepared to answer the following question(s): 

      * What is a progressive web application? 

      * How do we create progressive web applications?


  ## 🏆 Bonus

  * What are examples of popular PWAs?
```

### 8. Instructor Do: Progressive Web Apps Review (5 min)

* Use the prompts and talking points below to review the following key point(s):
  
  * ✔️ Progressive web applications (PWAs) are mobile or desktop apps delivered through the web, built using HTML, CSS & JavaScript, that allow users to work offline
  
  * ✔️ PWAs require a manifest, a service worker and the Cache API
  
* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What is a progressive web application?
  
  * 🙋 Progressive web applications (PWAs) are mobile or desktop apps delivered through the web, built using HTML, CSS & JavaScript
  
  * ☝️ What is meant by the term 'native' app?
  
  * 🙋 The term "native app" refers to applications written for specific platforms. For example, native iPhone apps are written in iOs and Android apps are primarily written in Java. Apple apps will not run on Android devices and vice versa. 

  * ☝️ How are PWAs different from native apps?

  * 🙋 Traditional Mobile Apps require multiple builds across platforms, are less discoverable by search engines and have high abandonment rates.They also offer less usability and don’t leverage mobile device capabilities and are often slow and bloated. PWAs provide advantages of both web and mobile apps such as push notifications, offline experiences,speed and stability. Plus, you can convert a web app into a PWA quickly without the build time of a mobile app.
  
  * ☝️ What do we need to learn to convert an application into a progressive web application?

  * 🙋 There are three primary things we need to learn: Manifests, Service Workers and the Cache API.
  
* Navigate to [https://image-gallery-cache.herokuapp.com/](https://image-gallery-cache.herokuapp.com/), open DevTools and explain the following: 
  
  * 🔑 If we look under the Application tab in DevTools for our Image Gallery App, we see **Manifest**, **Service Workers** and **Cache Storage** panels.

    ![Application Sidebar](Images/application-sidebar.png)

  * 🔑 If we check the `offline` button in the Service Workers panel, we see that the application still delivers a full experience with an Internet connection!

  ![Offline](Images/offline-mode.png)

* Answer any lingering questions before proceeding to the next demo. 

### 9. Instructor Do: Web App Manifest Demo (5 mins)

* Use the prompts and talking points below to demonstrate the following key point(s):

  * ✔️ `manifest.webmanifest` is JSON file providing information for mobile and desktop installation
  
  * ✔️ Manifest properties are referred to as members
  
* Open [08-Ins_Manifest/manifest.webmanifest](../../../../01-Class-Content/18-PWA/01-Activities/08-Ins_Manifest/manifest.webmanifest) in your IDE and explain the following: 

  * 🔑 A web app manifest is a simple JSON file containing some metadata about a web application. 
  
 ```js
  {
    "short_name": "Demo",
    "name": "Web App Manifest Demo",
    "icons": [
      {
        "src": "/assets/images/icons-192.png",
        "sizes": "192x192",
        "type": "image/png"
      },
      {
        "src": "/assets/images/icons-512.png",
        "sizes": "512x512",
        "type": "image/png"
      }
    ],
    "start_url": "/",
    "background_color": "#808080",
    "display": "standalone",
    "theme_color": "#808080"
  } 
  ```
  * 🔑 Each of the properties in our manifest file is referred to as a **member**.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What do we think the difference is between `name` and `short_name`?

  * 🙋 `short_name` is used on the home screen and in the application menu
  
  * ☝️ What are "icons"?

  * 🙋 The `icons` array contains information about the thumbnail images used when installing the PWA on mobile or desktop

  * ☝️ What is the `start_url` member?

  * 🙋 Defines what page is opened when the app is first launched (start_url).
  
  * ☝️ What does the `display` member do?

  * 🙋 By using a web app manifest, our app can tell the browser you want your app to open in a standalone window


### 10. Student Do: Web App Manifest (15 mins)

* Direct students to the activity instructions found in [09-Stu_Manifest](../../../../01-Class-Content/18-PWA/01-Activities/09-Stu_Manifest)

```md
# Web App Manifest

In this activity, you will write your first progressive web application manifest.

## Instructions

* Using the instructor demo as a guide, create a manifest for the Image Gallery app.

  * 🤔 Where do you create the `manifest.webmanifest` in the application architecture?

  * 🤔 How do you deploy a manifest? Hint: You will need to somehow link it with the web page. (See [Web App Manifest - Deploying a manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest#Deploying_a_manifest_with_the_link_tag).)

* When finished, run the commands:

  * `npm install`

  * `npm run seed`

  * `npm start`

* Navigate to [localhost:3000](localhost:3000) and open `DevTools > Application > Manifest` to verify successful loading of the manifest.

## 💡 Hint(s)

Read the [MDN Web App Manifest documentation](https://developer.mozilla.org/en-US/docs/Web/Manifest) 

## 🏆 Bonus

* Add additional members to your manifest.
```

### 11. Instructor Do: Review Web App Manifest (10 mins)

* Use the prompts and talking points below to review the following key point(s):

  * The web app manifest tells the browser about your web application and how it should behave once installed. 

* Open [09-Stu_Manifest/Solved/public/manifest.webmanifest](../../../../01-Class-Content/18-PWA/01-Activities/09-Stu_Manifest/Solved/public/manifest.webmanifest) in your IDE and explain the following:

  * We give our PWA a name and short name. These can have different values, but for the sake of simplicity, we give them the same value.

  * There are numerous icons for our app, starting at the size of `72x72` through `512x512`.

  * We set both the theme color and the background color to be white.

  * We tell the app to run in standalone mode, which means the web app will look and feel like a standalone native app. The app runs in its own window, separate from the browser, and hides standard browser UI elements like the URL bar.

  * 📝 The other display modes we could specify are `fullscreen`, `minimal-ui`, and `browser`.

  ```json
    {
    "name": "Images App",
    "short_name": "Images App",
    "icons": [
      {
        "src": "assets/images/icons/icon-72x72.png",
        "sizes": "72x72",
        "type": "image/png"
      },
      ...
      {
        "src": "assets/images/icons/icon-512x512.png",
        "sizes": "512x512",
        "type": "image/png"
      }
    ],
    "theme_color": "#ffffff",
    "background_color": "#ffffff",
    "start_url": "/",
    "display": "standalone"
  }  
  ```

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ Which file do we include the `manifest.webmanifest` in?

  * 🙋 `index.html` 

  * ☝️ What's next on our list of things to do?
  
  * 🙋 Add a service worker!

### 12. Instructor Do: Intro To Service Workers (5 mins)

* Use the prompts and talking points below to demonstrate the following key point(s):

  * ✔️ A service worker is a script that your browser runs in the background on a separate thread from your webpage.

  * ✔️ Certain functionality can _only_ be implemented from within a service worker, such as caching assets in order to make the application useable without an internet connection or notifying the browser that the application should be installable.

  * ✔️ **Cache API** Similar to localstorage and indexedDB in that this browser API is used for storing data. However Cache API can be used to store entire all front end assets such as images, javascript, HTML, CSS, etc. along with API responses.

  * ✔️ **Thread** A thread is an independent set of values for the processor that controls what executes in what order. Think of this as another JavaScript application running at the same time as our main application, with the ability to communicate and pass data between threads.

  * ✔️ Service workers have a lifecycle that consists of 3 main parts.

  * ✔️ **Installation**: The service worker creates a version-specific cache.

  * ✔️ **Waiting**: The updated service worker waits until the existing service worker is no longer controlling clients. This step is often skipped with a function, since service workers rarely exist past a new service workers installation.

  * ✔️ **Activation**: This event fires after the service worker has been installed and the previous one has been removed.

* Navigate to [10-Ins_Service_Workers](../../../../01-Class-Content/18-PWA/01-Activities/10-Ins_Service_Workers) and run the following commands in your terminal:

  ```
  npm install
  npm run seed
  node server.js
  ```

* In a separate tab, run `mongod`.

* Open your Chrome Dev Tools > Application and demonstrate that the service worker has been registered and installed.

  * When our app launches, it registers and installs the service worker.

  * Using the Chrome Dev Tools, we can unregister the service worker.

  * Now, if we refresh the page, we can see that the service worker was installed and registered again.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What are the 2 main steps in service worker lifecycle?

  * 🙋 Installation and activation. There is also a waiting step that is often skipped.

---

### 13. Break (30 mins)

---

### 14. Student Do: Register Service Worker (15 mins)

* Direct students to the next activity located in [11-Stu_Service_Workers](../../../../01-Class-Content/18-PWA/01-Activities/11-Stu_Service_Workers/Unsolved).

* **Instructions**

* Add the following script just above the closing `</body>` tag in `index.html`

```html
<script>
  if ("serviceWorker" in navigator) {
    window.addEventListener("load", () => {
      navigator.serviceWorker.register("service-worker.js")
        .then(reg => {
          console.log("We found your service worker file!", reg);
        });
    });
  }
</script>
```

* Create a `service-worker.js` file in the `public` directory and add the following line of code.

```js
console.log("Hello from your service worker file!");
```

* Refresh your Gallery App or launch it with `npm start` if it is not running.

* Open your Chrome Dev Tools and navigate to Application then your Service Worker tab. Check to see if your service worker file was successfully found. You should see two messages, one from the `service-worker.js` file and one from the script tag that you put in your `index.html` file.

  ![Service Worker Console](Images/sw-console.png)

### 15. Instructor Do: Review Register Service Worker (15 mins)

* Use the prompts and talking points below to review the following key point(s):

  * ✔️ We are adding an event listener to our window element, listening for the `load` event.

  * ✔️ We register our service worker using the `navigator` object.

  * ✔️ We console.log a message letting us know that the service worker registration was successful.

* Open [11-Stu_Service_Workers/Solved/public/index.html](../../../../01-Class-Content/18-PWA/01-Activities/11-Stu_Service_Workers/Solved/public/index.html) and explain the following points:

  * We tell the browser to register our service worker file.

```html
<script>
  if ("serviceWorker" in navigator) {
    window.addEventListener("load", () => {
      navigator.serviceWorker.register("service-worker.js")
        .then(reg => {
          console.log("We found your service worker file!", reg);
        });
    });
  }
</script>
```

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What step of the service worker lifecycle have we just completed? 

  * 🙋 The registration step. 

### 16. Instructor Do: Creating An Offline Experience (5 mins)

* Use the prompts and talking points below to demonstrate the following key point(s):

  * ✔️ All files that need to be cached are stored as strings in an array.

  * ✔️ All files that need to be cached are precached in the `install` step.

  * ✔️ The `activate` step clears out the all outdated caches.

  * ✔️ The `fetch` listener intercepts all fetch requests and uses data from the cache to return a response.

* Open [12-Ins_Caching_Fetching_Files/Solved/](../../../../01-Class-Content/18-PWA/01-Activities/12-Ins_Caching_Fetching_Files/) in your IDE and run the following commands:

  * `npm install`

  * `npm start`

* Navigate to [localhost:3000](http://localhost:3000) in your browser and explain the following points:

  * If we inspect our Sources with DevTools, we can see that our service worker is running on a separate thread.

  ![Threads](Images/sw-threads.png)

* Open [12-Ins_Caching_Fetching_Files/Solved/public/service-worker.js](../../../../01-Class-Content/18-PWA/01-Activities/12-Ins_Caching_Fetching_Files/public/service-worker.js) in your IDE and explain the following:

  * Now that we have successfully registered our service worker, we'll step through the code that will install and activate it. This will give our service worker the ability to cache the files we tell it to and deliver them in an offline experience for our users.

  * Our `FILES_TO_CACHE` variable keeps track of each file that we want to store in our cache. 

  * This is an array of _files_ only, attempting to include entire folders won't work.

  📝 The `ALL_CAPS_SEPARATED_BY_UNDERSCORES` style is just standard convention for the global variables in our service worker. 

  ```js
  const FILES_TO_CACHE = [
    "/",
    "/index.html",
    "/assets/css/style.css",
    "/assets/js/loadPosts.js",
    "/assets/images/Angular-icon.png",
    "/assets/images/React-icon.png",
    "/assets/images/Vue.js-icon.png",
    "/manifest.webmanifest",
    ...
    ...
  ];

  // set cache variable names
  const CACHE_NAME = 'static-cache-v2';
  const DATA_CACHE_NAME = 'data-cache-v1';
  ```

  * Inside our install event listener callback we open our cache and call `addAll`, passing in `FILES_TO_CACHE`.

  ```js
  // install
  self.addEventListener('install', function(evt) {
    evt.waitUntil(
      caches.open(CACHE_NAME).then(cache => {
        console.log('Your files were pre-cached successfully!');
        return cache.addAll(FILES_TO_CACHE);
      })
    );

  // skipWaiting() ensures that any new versions of our service worker will take over the page and become activated immediately
    self.skipWaiting();
  });
  ```

  * Inside the activate event listener callback, we activate our service worker, cleaning up outdated caches.

  ```js
  // activate
  self.addEventListener('activate', function(evt) {
    evt.waitUntil(
      caches.keys().then(keyList => {
        return Promise.all(
          keyList.map(key => {
            if (key !== CACHE_NAME && key !== DATA_CACHE_NAME) {
              console.log('Removing old cache data', key);
              return caches.delete(key);
            }
          })
        );
      })
    );

  // Tells our new service worker to take over.
    self.clients.claim();
  });
  ```

  * Here we modify the service worker to handle requests to `/api` and store the responses in our cache, so we can easily access them later.

  ```js
  // fetch
  self.addEventListener('fetch', function(evt) {
    if (evt.request.url.includes('/api/')) {
      console.log('[Service Worker] Fetch (data)', evt.request.url);

      evt.respondWith(
        caches.open(DATA_CACHE_NAME).then(cache => {
          return fetch(evt.request)
            .then(response => {
              // If the response was good, clone it and store it in the cache.
              if (response.status === 200) {
                cache.put(evt.request.url, response.clone());
              }

              return response;
            })
  ```

  * If the network request fails, we try to get the response from our cache.

  ```js
    .catch(err => {
      return cache.match(evt.request);
    });
  ```
  
  * _**Note for instructor:** You will notice that the api requests are not cached on the first visit, when the service worker is installed for the first time. Solutions to deal with this case are most likely too complicated to introduce at this point in the class. Simply refresh the page to allow the service worker to cache the api request making the posts from the database available when the page is viewed offline._

  * If the request path does not include `/api`, then we will assume the requests is for a static file. The file is returned from the cache if a matching request is found and falls back to fetching the resource if nothing is cached.

  ```js
  evt.respondWith(
    caches.match(evt.request).then(function(response) {
      return response || fetch(evt.request);
    })
  );
  ```

* Open [12-Ins_Caching_Fetching_Files/public/assets/js/loadPosts.js](../../../../01-Class-Content/18-PWA/01-Activities/12-Ins_Caching_Fetching_Files/public/assets/js/loadPosts.js) in your IDE and explain the following:

  * We are going to skip past the DOM element creation and focus on the handling of our "like" POST request. 

  * When a user likes a post, we increment it's `data-likes` attribute by 1.

  ```js
  function incrementLikes(event) {
    const statusEl = document.querySelector("#status")

    const id = event.currentTarget.getAttribute("id");
    const oldLikes = parseFloat(event.currentTarget.getAttribute("data-likes"));
    const likes = oldLikes + 1;

    event.currentTarget.setAttribute("data-likes", likes);

    statusEl.innerText = "";
  ```

  * `incrementLikesRequest` makes an API call, then sets a status DOM element at the top of the page to let the user know whether or not their save was successful. 

  ```js
  incrementLikesRequest(id, likes)
    .then(() => {
      statusEl.innerText = "Save successful!"
      updateLikesDisplay(id, likes, true)
    })
    .catch(() => {
      statusEl.innerText = "Sorry, your 'like' cannot be recorded while you are offline."
      updateLikesDisplay(id, likes, false)
    });
  ```

  * In `updateLikesDisplay` we indicate to the user whether or not their likes count is up to date by appending `(not saved)` to the like count for each post.

  ```js
  function updateLikesDisplay(id, likes, saved) {
    const likesCount = document.querySelector(`#likes-count-${id}`);
    likesCount.innerText = `Likes: ${likes}`;
    if(!saved) {
      likesCount.innerText += " (not saved)";
    }
  }
  ```

* There is quite a bit of code here so take the time to step through it, clarifying any questions as you go.

  * Our service worker is caching all of the files we tell it to so when a user doesn't have a connection, it can deliver them an offline browsing experience. If a user is offline, we must make sure that they can still use the application as much as possible, even if this means letting them know their data won't be saved until later.

* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What kind of events do we have to listen for in our service worker file?

  * 🙋 Install and activate. We also listen for `fetch` if our application interacts with an API.

### 17. Student Do: Caching Files (10 mins)

* Direct students to the next activity located in [13-Stu_Caching_Fetching_Files](../../../../01-Class-Content/18-PWA/01-Activities/13-Stu_Caching_Fetching_Files/Unsolved/).

* Instructions are here: [13-Stu_Caching_Fetching_Files/README.md](../../../../01-Class-Content/18-PWA/01-Activities/13-Stu_Caching_Fetching_Files/README.md/)

### 18. Instructor Do: Review Caching Files (5 mins)

* Open [13-Stu_Caching_Fetching_Files/Solved/public/service-worker.js](../../../../01-Class-Content/18-PWA/01-Activities/13-Stu_Caching_Fetching_Files/Solved/public/service-worker.js) in your IDE and explain the following: 

  * First we set up the files that we need to cache.

  ```js
  const FILES_TO_CACHE = [
    '/',
    '/index.html',
    '/favicon.ico',
    '/manifest.webmanifest',
    '/assets/css/style.css',
    '/assets/js/loadImages.js',
    '/assets/images/icons/icon-72x72.png',
    '/assets/images/icons/icon-96x96.png',
    '/assets/images/icons/icon-128x128.png',
    '/assets/images/icons/icon-144x144.png',
    '/assets/images/icons/icon-152x152.png',
    '/assets/images/icons/icon-192x192.png',
    '/assets/images/icons/icon-384x384.png',
    '/assets/images/icons/icon-512x512.png',
    '/assets/images/1.jpg',
    '/assets/images/2.jpg',
    '/assets/images/3.jpg',
    '/assets/images/4.jpg',
    '/assets/images/5.jpg',
    // ...
  ];

  const CACHE_NAME = 'static-cache-v2';
  const DATA_CACHE_NAME = 'data-cache-v1';
  ```

* Then, we install and register our service worker.

  ```js
  self.addEventListener('install', function(evt) {
    evt.waitUntil(
      caches.open(CACHE_NAME).then(cache => {
        console.log('Your files were pre-cached successfully!');
        return cache.addAll(FILES_TO_CACHE);
      })
    );

    self.skipWaiting();
  });
  ```

  * If done successfully, we should see our static cache in our Application tab.

  ![Static Cache](Images/static-cache.png)

  * Next we activate our service worker.

  ```js
  self.addEventListener('activate', function(evt) {
    evt.waitUntil(
      caches.keys().then(keyList => {
        return Promise.all(
          keyList.map(key => {
            if (key !== CACHE_NAME && key !== DATA_CACHE_NAME) {
              console.log('Removing old cache data', key);
              return caches.delete(key);
            }
          })
        );
      })
    );

    self.clients.claim();
  });
  ```

  * Lastly, we handle all fetching for any request with a url that includes `/api/`.

  * If the response is successful, we clone it and store it in our cache.

  * If the network request fails, we grab it from our cache.

  ```js
  self.addEventListener('fetch', function(evt) {
    if (evt.request.url.includes('/api/')) {
      evt.respondWith(
        caches.open(DATA_CACHE_NAME).then(cache => {
          return fetch(evt.request)
            .then(response => {
              if (response.status === 200) {
                cache.put(evt.request.url, response.clone());
              }

              return response;
            })
            .catch(err => {
              return cache.match(evt.request);
            });
        })
      );

      return;
    }

    evt.respondWith(
      caches.open(CACHE_NAME).then(cache => {
        return cache.match(evt.request).then(response => {
          return response || fetch(evt.request);
        });
      })
    );
  });
  ```

  * If done successfully we will see your data cache in your Application tab. At this point we should be able to put our application in offline mode for an offline experience.

  ![Data Cache](Images/data-cache.png)

  ![Offline](Images/offline.png)
  
* Ask the class the following question(s) and call on students for the corresponding answer(s):

  * ☝️ What does a service worker do?

  * 🙋 A service worker acts as an intermediate step in between an API call and the browser. It can cache files and help provide an offline experience.

  * ☝️ When using a service worker, can we send POST requests to an API while offline?

  * 🙋 No, POST/PUT requests must be handled separately. If we wish to "cache" the POST data, we can store it in IndexedDb.

  * ☝️ How many times does the install event run for each service worker? 

  * 🙋 Once.

  * ☝️ What does `self.skipWaiting()` do? 

  * 🙋 `self.skipWaiting()` forces the service worker to activate as soon as it's finished installing.

### 19. Instructor Do: Demo Trip Planner PWA (5 mins)

* Use the prompts and talking points below to demonstrate the following key point(s):

* Navigate to [14-Stu_Map-PWA](../../../../01-Class-Content/18-PWA/01-Activities/14-Stu_Map-PWA/Solved) and demonstrate the following functionality: 

  * Open up the Chrome Developer Tools and navigate to the `Service Worker` tab. Here, let's toggle the offline version and refresh the app.

  ![offline mode](./Images/offline-mode.png)

  * Just like our other two apps, all of our resources have been cached and do not require a connection to access.

  * Also demonstrate the PWA install icon in the browser address bar with the PWA logo prompt.
  
### 20. Student Do: Trip Planner PWA (30 mins)

* Direct students to the activity instructions found in [14-Stu_Map-PWA](../../../../01-Class-Content/18-PWA/01-Activities/14-Stu_Map-PWA)

```md
# Create a PWA

For this activity you are going to convert the Trip Planner website into a PWA.

## Instructions

* Refer back to the activities we previously worked through to help you accomplish the following steps.

  * Link the app manifest to the website - the `manifest.webamanifest` file has been created for you.

  * Install the service worker to cache static assets - the service worker has been registered for you.

  * Retrieve cached files for an offline experience.

  * Download the PWA.

## BONUS

* Can we use the Cache Storage in the browser to store dynamic requests from the user, for example from a web form? If not, then what can we use?

Use Google or another search engine to research the preceding topic. 
```

### 21. Instructor Do: Review Trip Planner PWA (15 mins)

* Open [14-Stu_MAP-PWA/Solved/index.html](../../../../01-Class-Content/18-PWA/01-Activities/14-Stu_Map-PWA/Solved/index.html) in your IDE and explain the following: 

  * We add the link to the `webmanifest.manifest` file in the `<head>`.

  ```html
  <link rel="manifest" href="./manifest.webmanifest" />
  ```

* Open [14-Stu_Map-PWA/Solved/service-worker.js](../../../../01-Class-Content/18-pwa/01-Activities/14-Stu_Map-PWA/Solved/service-worker.js) in your IDE and explain the following: 

  * The files we need to cache are `index.html`, `style.css`, and the image files; `brandenburg.jpg`, `reichstag.jpg`, and `map.jpg`

  * Our cache will be named `static`.

  * When the install event is emitted, we will add all of our specified files to the `static` cache.

  ```js
  // install event handler
  self.addEventListener('install', (event) => {
    event.waitUntil(
      caches.open('static').then((cache) => {
        return cache.addAll([
          './',
          './index.html',
          './assets/css/style.css',
          './assets/images/brandenburg.jpg',
          './assets/images/reichstag.jpg',
          './assets/images/map.jpg'
        ]);
      })
    );
    console.log('Install');
    self.skipWaiting();
  });
  ```

  * 📝 The `fetch` call will retrieve the assets from the cache when the network call isn't possible.

  ```js
  // retrieve assets from cache
  self.addEventListener('fetch', event => {
    event.respondWith(
      caches.match(event.request).then( response => {
        return response || fetch(event.request);
      })
    );
  });
  ```

### 22. END (0 mins)

### Lesson Plan Feedback

How did today’s lesson go? Your feedback is important. Please take 5 minutes to complete this anonymous survey.

[Class Survey](https://forms.gle/nYLbt6NZUNJMJ1h38)
