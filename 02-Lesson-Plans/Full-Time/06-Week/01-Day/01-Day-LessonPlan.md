# 6.1 Lesson Plan - Intro to Node Servers (10:00 AM)

## Overview

In this class, we will provide students with a deep conceptual understanding of server-side code and use vanilla Node.js to create basic servers.

## Instructor Notes

* `Summary: Complete activities 01-12 in Unit 11`

* This class is all about introducing students to the concept of server-side code. Coming into class today, students will have a fairly rudimentary notion of servers. Without your guidance it will be difficult for them to understand how the terminal-side code they've been creating thus far using Node.js fits into the big picture of web development. Today's class is all about filling these conceptual gaps.

* Consistently, in this unit, we'll be relying on an analogy that servers are like "big empty boxes". In this analogy, we fill these boxes with sub-modules or code snippets that enable the server to have the functionality we need. Do your part in using this analogy to provide your students with a visual understanding of how server-side code works.

* Also note that in today's class, we will be introducing students to the plain Node approach for creating servers. Let them know that for today's class understanding the exact syntax is _less_ important than understanding the conceptual picture. You can also let them know that in the next class they will be introduced to Express.js, which will simplify some of the code complexity of today.

* Remind students to sign up for a Heroku account and have the **Heroku CLI installed** before coming to the next class!

* In Unit 12, students will start using MySQL. Advise the students to have both MySQL Server and Workbench installed **before** the next unit.

## Learning Objectives

* To gain a conceptual understanding of server-side code.

* To learn the fundamentals of building a server using plain Node.js to listen and respond to client-side requests.

## Slides

[6.1: Intro to Node Servers](https://docs.google.com/presentation/d/1tVXZx3l2azL-NsN-sVPlHmYPbkYsKrvLE_mXR6XH96M/edit?usp=sharing)

## Time Tracker

[06.1 Time Tracker](https://docs.google.com/spreadsheets/d/105fwzlYpuj5EqJutMqekdjo9_fcyiMhE/edit#gid=194207795)

- - -

## Class Instructions

### 1. Instructor Do: Server-Side Slide Show (0:25)

* Welcome students to class and then dive into the slide deck [6.1: Intro to Node Servers](https://docs.google.com/presentation/d/1EWJxjwlLUBqfhVrYlfqNG6RJGDVBZCYOYRitbnVHeD0/edit?usp=sharing). Be sure to spend the appropriate amount of time with this presentation. It offers students important warnings about the challenge of this week's class as well as advice on succeeding in the week ahead.

* Use the presentation as cues to ask your students basic review questions on servers and clients. Try to call on individual students as you proceed through these slides.

* Spend the appropriate amount of time discussing the physical (hardware) nature of servers. Ensure that students understand that servers are little more than central computers that respond to requests from users accessing the machine.

![Central Server](./Images/00-Server.png)

* Use this time to also preface the fact that during development, we use our machines to both emulate the client-side (browser) and the central server (`localhost`). Warn students that this is a concept that will seem tricky, but is fundamentally important to keep straight. You can specifically use the line: "In a way, our computer will be modeling two different computers at once."

* Then proceed through the slides on "Building a Server". Offer the students the perspective that when they purchase a server or a server instance from a cloud provider, they are only getting an empty box. It is up to them as developers to create the code that powers this box, such that it can respond to requests in the ways we've talked about thus far.

![LocalHost](./Images/00-Server3.png)

* Use the slides provided to walk students through the core functions common to most servers:

  * Listeners that listen for client-side requests.

  * URL Parsers for breaking down the URLs that clients make requests to. (You can use the example of how news websites use URLs that mix dates and article titles to identify, which resource to grab)

  * Route Handling for determining what _happens_ when a user visits or sends data to a specific URL.

  * The ability to send HTML or send JSONs in response to users requesting data.

  * The ability to receive POSTs (i.e. data that users send).

  * The ability to initiate more complex server-side logic in response to any of these requests.

  * And more (Authentication, Logging, Database Connections, etc.)

* From here proceed with the coding activities.

### 2. Instructor Do: My First Server (0:20)

* In this exercise, go through the process of re-creating the server.js file found in `01-FirstServer`. If at all possible, create this server "live" and comment on it as you go.

  ```js
  // Require/import the HTTP module
  const http = require('http');

  // Define a port to listen for incoming requests
  const PORT = 8080;

  // Create a generic function to handle requests and responses
  const handleRequest = (request, response) => {
    // Send the below string to the client when the user visits the PORT URL
    response.end(`It Works!! Path Hit: ${request.url}`);
  };

  // Use the Node HTTP package to create our server.
  // Pass the handleRequest function to empower it with functionality.
  const server = http.createServer(handleRequest);

  // Start our server so that it can begin listening to client requests.
  server.listen(PORT, () => {
    // Log (server-side) when our server has started
    console.log(`Server listening on: http://localhost:${PORT}`);
  });

  ```

* During your commentary be sure to point out how:

  * We incorporated the `http` module. This, in essence, is a package ("small box") which allows our server ("big box") to have the capability of handling http requests and responses. HTTP is package that comes with the standard Node library.

  * We specified a port. This could be anything between 80 and above. In essence, a port is like a portal through which servers and clients communicate. The number itself doesn't matter so much for right now, but later we'll be using port 80 which is the standard port URLs use.

  * We created a function for handling requests and responses and then gave this function to our created server.

  * Finally, we set up the server such that it listens at the PORT specified.

* Once you have completed the code write-up, run the application by typing `node server.js` from the command line. Then visit the URL `localhost:PORT`, where `PORT` is the port you specified in the server file. Point out how this emulates our browser (client) making a request of our localhost (server), and in turn receiving a single string response.

  ```sh
  Server listening on: http://localhost:8080
  ```

  ![/Images/001-ServerBasic3.png](./Images/001-ServerBasic3.png)

* Answer any questions that remain for this example before proceeding to the next activity.

### 3. Students Do: Two Servers App (0:20)

* Now it's students' turn to build a web server (or rather two). Slack out the following:

* **Instructions**

  * Using the previous example as a guide, create an app that has two web servers: one that listens on port 7000 and one that listens on port 7500.

  * Each server will respond with a different inspirational quote of your choosing.

  **Bonus**

  * Randomly select the quotes from a predefined array.

### 4. Instructor Do: Review Two Servers App (0:05)

* Congratulate the students for having just built their very own web servers!

* Run `02-Two-Servers/Solved/server.js` and demonstrate how the message differs when you visit `http://localhost:7000` vs `http://localhost:7500`.

* Then open the code and explain to students the solution. In offering your solution, be sure to mention that in this example, we effectively created two servers. Each server used a different port, a different listener, and a different function for handling requests.

```js
// We require/import the HTTP module
const http = require('http');

// Then define the ports we want to listen to
const PORTONE = 7000;
const PORTTWO = 7500;

// We need two different functions to handle requests, one for each server.
const handleRequestOne = (request, response) => {
  response.end(
    'To err is human, but to really foul things up you need a computer.'
  );
};

const handleRequestTwo = (request, response) => {
  response.end("Never trust a computer you can't throw out a window.");
};

// Create our servers
const serverOne = http.createServer(handleRequestOne);
const serverTwo = http.createServer(handleRequestTwo);

// Starting our servers
serverOne.listen(PORTONE, () => {
  // Callback triggered when server is successfully listening. Hurray!
  console.log(`Server listening on: http://localhost:${PORTONE}`);
});

serverTwo.listen(PORTTWO, () => {
  // Callback triggered when server is successfully listening. Hurray!
  console.log(`Server listening on: http://localhost:${PORTTWO}`);
});
```

* Slack a copy of the completed app to the class: `02-Two-Servers/Solved/server.js`.

* Then proceed to the next demo.

### 5. Instructor Do: Portfolio Server (0:15)

* In this demonstration, you will be showing students a basic "url parsing" and "routing" example. Remember! Let students know that the exact syntax of this example isn't what's important. (They will be using Express in the next class to do it more simply). However, they should take the time necessary to understand what is happening here at a conceptual level.

* Open the file `server.js` inside of `03-Portfolio`. Run the application using Node.js.

```js
const http = require('http');

const PORT = 8080;

// When someone visits the "http://localhost:8080/portfolio" path, this function is run.
const displayPortfolio = (res) => {
  const myHTML = `
  <html>
    <body>
      <h1>My Portfolio</h1>
      <a href='/'>Go Home</a>
    </body>
  </html>`;

  // Configure the response to return a status code of 200 (meaning everything went OK), and to be an HTML document
  res.writeHead(200, { 'Content-Type': 'text/html' });

  // End the response by sending the client the myHTML string (which gets rendered as an HTML document thanks to the code above)
  res.end(myHTML);
};

// When someone visits the "http://localhost:8080/" path, this function is run.
const displayRoot = (res) => {
  const myHTML = `
  <html>
    <body>
      <h1>Home Page</h1>
      <a href='/portfolio'>Portfolio</a>
    </body>
  </html>`;

  // Configure the response to return a status code of 200 (meaning everything went OK), and to be an HTML document
  res.writeHead(200, { 'Content-Type': 'text/html' });

  // End the response by sending the client the myHTML string (which gets rendered as an HTML document thanks to the code above)
  res.end(myHTML);
};

// When someone visits any path that is not specifically defined, this function is run.
const display404 = (url, res) => {
  const myHTML = `
  <html>
    <body>
      <h1>404 Not Found </h1>
      <p>The page you were looking for: ${url} can not be found</p>
    </body>
  </html>`;

  // Configure the response to return a status code of 404 (meaning the page/resource asked for couldn't be found), and to be an HTML document
  res.writeHead(404, { 'Content-Type': 'text/html' });

  // End the response by sending the client the myHTML string (which gets rendered as an HTML document thanks to the code above)
  res.end(myHTML);
};

// Create a function which handles incoming requests and sends responses

const handleRequest = (req, res) => {
  // Capture the url the request is made to
  const path = req.url;

  // Depending on the URL, display a different HTML file.
  switch (path) {
    case '/':
      return displayRoot(res);

    case '/portfolio':
      return displayPortfolio(res);

    default:
      return display404(path, res);
  }
};

// Assign our createServer method to a variable called "server"
const server = http.createServer(handleRequest);

// Start our server
server.listen(PORT, () => {
  // Callback triggered when server is successfully listening. Hurray!
  console.log(`Server listening on: http://localhost:${PORT}`);
});
```

* In discussing the code, point out the following discussion items:
  * The use of the abbreviated terms `req` and `res`, which are short for request and response.

  * The use of the switch-case statement which routes the code to a different function depending on the URL provided.
  * Finally, the way in which we created HTML dynamically and rendered it on the page in each function.

* Slack out the solution when complete.

### 6. Students Do: Discuss Portfolio (0:05)

* Have students discuss the code with one another before asking them to re-explain it back to you. Tie up any loose ends that may remain.

### 7. Instructor Do: Serving HTML (0:15)

* In this next activity, we will be using `fs` to read and serve HTML files.

* Open the code for `04-Serving-HTML/server.js` and give students a minute to look it over. Ask them what they think is going to happen when you visit `localhost:80`?

```js
// Dependencies
const http = require('http');
const fs = require('fs');

// Set our port to 8080
const PORT = 8080;

// Create a function for handling the requests and responses coming into our server
const handleRequest = (req, res) => {
  // Here we use the fs package to read our index.html file
  fs.readFile(`${__dirname}/index.html`, (err, data) => {
    if (err) throw err;
    // We then respond to the client with the HTML page by specifically telling the browser that we are delivering
    // an html file.
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.end(data);
  });
};

// Create our server
const server = http.createServer(handleRequest);

// Starts our server
server.listen(PORT, () => {
  console.log(`Server is listening on PORT: ${PORT}`);
});
```

* Run `04-Serving-HTML/server.js` and open `localhost:80` in your browser. It's a website!

* Point out how, in this example, we used the `fs` package to read in the `index.html` file. We then used the node server to output this same file back to the user as a response.

### 8. Students Do: Discuss Serving HTML (0:05)

* Have students discuss the code with one another before asking them to re-explain it back to you. Tie up any loose ends that may remain.

- - -

### 9. Break (0:30)

- - -

### 10. Students Do: Serve-Favorites (0:30)

* Next, run the `server.js` file found in `05-Serve-Favorites/Solved`. Visit each of the routes in that file (i.e. `localhost:8080/food`, `localhost:8080/movies`, etc.). Point out how the contents of the page changes each time.

* Then slack out the following activity for students to complete.

* **Instructions:**

  * Create a website with four routes:
    * Home
    * Favorite Food
    * Favorite Movies
    * Favorite CSS Frameworks
  * Each route should be triggered by a different URL.
  * Each route should display an HTML page listing your favorite three things of each.
  * Be sure to use `fs` to serve your HTML files.

### 11. Instructor Do: Review Students Serve Favorites (0:10)

* Open up the `server.js` file found in `05-Serve-Favorites/Solved` and review the code in this example. During your discussion, be sure to point out:

  * How we created the basic skeleton of a Node server (requiring: `http` and the port number)

  * How we set up a listener to initiate the server's handling of requests.

  * Created a function `handleRequest` which takes in a request URL, parses it, then relays the user to the correct page.

```js
// Require dependencies
const http = require('http');
const fs = require('fs');

// Set our port to 8080
const PORT = 8080;

const handleRequest = (req, res) => {
  // Capture the url the request is made to
  const path = req.url;

  // When we visit different urls, read and respond with different files
  switch (path) {
    case '/food':
      return fs.readFile(`${__dirname}/food.html`, (err, data) => {
        if (err) throw err;
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(data);
      });

    case '/movies':
      return fs.readFile(`${__dirname}/movies.html`, (err, data) => {
        if (err) throw err;
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(data);
      });

    case '/frameworks':
      return fs.readFile(`${__dirname}/frameworks.html`, (err, data) => {
        if (err) throw err;
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(data);
      });

    // default to rendering index.html, if none of above cases are hit
    default:
      return fs.readFile(`${__dirname}/index.html`, (err, data) => {
        if (err) throw err;
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(data);
      });
  }
};

// Create the server, assign it to a variable called "server"
const server = http.createServer(handleRequest);

// Starts our server.
server.listen(PORT, () => {
  console.log(`Server is listening on PORT: ${PORT}`);
});
```

* This solution contains a lot of repeated code.  Ask your students if they have any suggestions how we might refactor this.  Then open `server-bonus.js` and point out how we implement just one `fs.readFile()` command by passing in a filePath into a `renderHTML` function.

### 12. Instructor Do: Request Methods (0:10)

* Up until now, students have just been exposed to GET requests. (They may not even realize it yet, but all the URL visits they've made thus far have been GET requests). In this activity, we will very briefly introduce them to other HTTP methods.

* Open `06-Request-Methods/server.js` in your editor.

* Briefly run through the code and explain that this app is going to log the type of request it receives, along with any information that was sent with the request in the console. We will test it out using a new application called Insomnia Core.

  ```js
  // Dependencies
  const http = require('http');

  const PORT = 8080;

  const handleRequest = (req, res) => {
    // Saving the request data as a variable
    let requestData = '';

    // When the server receives data...
    req.on('data', (data) => {
      // Add it to requestData.
      requestData += data;
    });

    // When the request has ended...
    req.on('end', () => {
      // Log (server-side) the request method, as well as the data received!
      console.log(`You did a ${req.method}, with the data:\n, ${requestData}`);
      res.end();
    });
  };

  // Create the server, assign it to a variable called "server"
  const server = http.createServer(handleRequest);

  // Start our server
  server.listen(PORT, () => {
    console.log(`Server listening on: http://localhost:${PORT}`);
  });
  ```

* Have students download the application Insomnia Core. Direct the students to the [Insomnia Core website](https://insomnia.rest/) and follow the instructions for downloading the application for your operating system. The site mentions pricing, but we're going to use the free tier of the application, as those features will really cover all of our needs!

* **Important**: It's important you install the Insomnia Core application and not Insomnia Designer. Insomnia Designer is an application for helping teams design APIs, but we need the Insomnia Core application in order to test our API, not design it.

* If you've never worked with Insomnia Core before, it's a simple application interface for performing HTTP requests (GET, POST, PUT, DELETE, and more).

* Once it's downloaded, open the application and you should see a screen like the following image:

![The Insomnia Core opening page has three columns for managing requests, making requests, and viewing response data.](./Images/400-insomnia-main.jpg)

* Walk through how to use Insomnia Core by testing a GET route.

* **Important**: You can refer the students to the [Getting Started with Insomnia page](https://support.insomnia.rest/article/11-getting-started). Don't forget to bookmark the [Insomnia Core documentation](https://support.insomnia.rest/) as well!

* Let's start by clicking the New Request button. You can also click the plus sign (+) in the left column and select New Request.

* After clicking, a modal window should appear asking you to name your request and pick what type of method it is. The default is GET. You can also name your request to help you identify it. Click Create.

* So now there are three columns that seem to be active. The left column will maintain the list of requests we make, just in case we ever want to get back to them and run it again. This is extremely useful, so don't forget that it does that!

* The middle one is where we actually form the request. The URL bar at the top lets you pick what type of request method you'll use and enter the address of the API endpoint you want to test. Let's enter our endpoint, which is `localhost:8080`.

* **Important**: Make sure you turn on your server using `npm start` before testing.

* When we click Send, we should get a `200 OK` status returned. If we check our console, we see the message below:

```bash
You did a GET with the data:

```

* Great! We successfully made a GET request. Let's try some others.

* Below the URL bar is a subnavigation that allows us to enter more information about the request, as shown below:

  ![Insomnia Core with dropdown menu showing subnavigation.](./Images/04-Insomnia-request.png)

* In the Body dropdown menu, choose Other. Let's send a POST request with the body text "Hello World".

* We should get a `200 OK` status returned and if you check the console, you will see the following message:

```bash
You did a POST with the data:
 Hello World
```

* Let's do a PUT request. Change the type of request method to PUT and replace the body text with "Hi World". Click Send and you should see the following message in your console:

```bash
You did a PUT with the data:
 Hi World
```

* Lastly, let's do a DELETE request. Change the type of request method to DELETE and remove the body text. Click Send and you should wee the following message in your console:

```bash
You did a DELETE with the data:

```

* Perfect! We are able to test our routes!

* Alternatively you can use CURL

  * `curl -i -H "Accept: application/json" -X GET -d "firstName=james" http://localhost:8080`
  * `curl -i -H "Accept: application/json" -X POST -d "firstName=james" http://localhost:8080`
  * `curl -i -H "Accept: application/json" -X PUT -d "firstName=james" http://localhost:8080`
  * `curl -i -H "Accept: application/json" -X DELETE -d "firstName=james" http://localhost:8080`

* Slack students a copy of this server code: `06-Request-Methods/server.js`.

* Let students know that we will be fleshing out this concept over the course of the week.

### 13. Instructor Do: Introduce Note Taker Homework (0:05)

* Finally, end the class by opening the solution to the Homework (Note Taker). Run the application using `node server.js` then visit `localhost`. Walk students through the basic gist of the application, describing it as an application that uses a server to allow us to view and create notes that can be stored server-side using the `fs` module.

* Stress that students should deploy their assignment as early as possible and ask for help if they run into issues. Explain that a non-deployed assignment will take a grade hit and won't help students professionally.

### 14. Instructor Do: Quick Recap "Server" Concepts (0:05)

* Open the slide deck [6.2: Express Yourself](https://docs.google.com/presentation/d/1W0_OTbihkOibQbwIt3nbeqOJchgM9IBAkvgPMOm7Oq4/edit?usp=sharing) and walk students through the slides. These are fairly light slides meant merely to offer a visualization of routing. Feel free to cut slides completely if you feel they detract from your teaching style.

* Use the slides to help you guide students through a recap of the concepts behind servers.

### 15. Everyone Do: Introduce Express (0:05)

* Use the slides to introduce the concept of the Express framework and routing.

* At one point in the slideshow you will be pointed to the NYT Scraper App website. Remind students how the webpage works (namely that the site lets users retrieve articles from the New York Times and store them in a "saved" list). Then use the proceeding slides to discuss the concept of GET and POST routes. Give them a heads-up that we'll be able to use `fetch` to make both these types of communications.

### 16. Instructor Do: Demo basic routing with server1.js (0:05)

* Before you start working with the code go to the link: [starwars-express-fsf.herokuapp.com/](https://starwars-express-fsf.herokuapp.com/) and show students how the page works. Essentially, you can type in a Star Wars Character's name and search the "database" to see his/her properties. You can also add characters to the database using the simple form. Add a character and show how it gets displayed on both the page and the API. (Note: When searching do not enter spaces between character names).

  ![1-FinalApp](./Images/1-FinalApp.png)

* To show the API you can simply go to this link: <http://starwars-express-fsf.herokuapp.com/api/characters>. The api also accepts an additional parameter at the end of the URL in the form of <http://starwars-express-fsf.herokuapp.com/api/characters/:charactername>. As an example: <http://starwars-express-fsf.herokuapp.com/api/characters/yoda>.

* Now open the file `server1.js` (`08-StarWars-1`). Walk students through the general gist of the code. _For now the key focus is to give them an understanding of express(), routing, and the listener_.

* Run the `server1.js` file and show them how it works. (Don't forget to talk about `npm install`).

* Once you've discussed the key pieces proceed to the first activity.

### 17. Students Do: Add Route to server1.js (0:10)

* Slack out the following file and instructions:

* **File:**

  * `server1.js` (`08-StarWars-1`)

* **Instructions:**

  * Work with those around you to confirm your `server1.js` file working. This means figuring out: what dependencies to install, how to run the file, and how to view the resulting website in your browser. This step requires you to make ZERO changes to the code file. At this point, you are just getting the file you are given to run.

  * Then, once you've gotten the original code to display in the browser, create a new `Obi Wan Kenobi route` to display Kenobi's information. Use the comments and the previous code in the file as a guide.

  * Help those around you when done.

### 18. Instructor Do: Review Previous Activity (0:05)

* Review the previous activity by coding it out yourself. Your solution should look like something of the below:

```js
const obiwankenobi = {
  name: "Obi Wan Kenobi",
  role: "Jedi Knight",
  age: 42,
  forcePoints: 1350
}

app.get('/obiwankenobi', (req, res) =>
  res.json(obiwankenobi));
})
```

### 19. Partners Do: Dissect req.params (0:05)

* Next slack out the following file and instructions.

* **File:**

  * `server2.js` (`09-StarWars-2`)

* **Instructions:**

  * Examine the code sent to you. Once again, run the `server2.js` file and view the page in the browser. Troubleshoot any issues that arise. Again NO CODE CHANGES required.

  * Then once you have a working server instance, begin to examine the file. Try to explain to yourself and those around you what the significance of `/:character` and `req.params.character` is.

  * Create a test case to check your hypothesis.

### 20. Instructor Do: Review Previous Activity (0:05)

* Have students try to explain to you what they found.

* If no one offers the correct answer, explain that the `/:character` syntax is a way of saying we have a "variable" parameter in the URL route. Show them via the browser that this means they can search for a given character using the URL and it will display in the console.

```js
app.get('/:character', (req, res) => {
  const chosen = req.params.character;

  // What does this log?
  console.log(chosen);

  res.end();
});
```

### 21. Partners Do: Dissect Parameter Match (0:05)

* Now slack out the next file:

* **File:**

  * `server3.js` (`10-StarWars-3`)

* **Instructions:**

  * Examine the code flagged in the comments. Explain to those around you what it does and how it works. Be sure to create test cases that confirm your hypothesis.

### 22. Instructor Do: Review Previous Activity (0:05)

* Use the same process as before to ask students to explain the for-loop concept to you.

* If no one offers the correct answer, explain that this for-loop "checks" which character is being sought after in the URL -- then finds that character's information and re-displays it back to the user in the form of a JSON.

```js
app.get('/api/characters/:character', (req, res) => {
  // What does this code do?
  const chosen = req.params.character;
  console.log(chosen);

  // What does this code do?
  for (let i = 0; i < characters.length; i++) {
    const currentChar = characters[i];
    if (chosen === currentChar.routeName) {
      return res.json(currentChar);
    }
  }

  // What does this code do?
  return res.send('No character found');
});
```

* Show them how this works by searching for the character `yoda`. Then try searching for a non-existent character like `hansolo`.

* Ask students of an example where this concept of routing where the URL is changing might be found. (suggested answer: Newspapers. Every newspaper has a url like `/2016/01/01/Great-story-of-the-day` )

### 23. Instructor Do: Re-demonstrate Previous Solved Activity (0:10)

* If needed, open the file `server4.js` (`11-StarWars-4`). This file simply includes a line-by-line commenting of the previous example. Slack out this file to students so they can look over it during the next few exercises.

### 24. Instructor Do: Show code for Post Route (0:05)

* Now open the file `server5.js` (`12-StarWars-5`). In this example, simply point students through the fact that we've created a new POST route. Explain that this route will take in JSON inputs then DO work with them. In this case it will save the JSON to the database and return a JSON of the new character.

```js
app.post('/api/characters', (req, res) => {
  const newCharacter = req.body;

  console.log(newCharacter);

  characters.push(newCharacter);

  res.json(newCharacter);
});
```

### 25. Students Do: req.body dissection (0:10)

* Now slack out the following file and instructions.

* **File:**

  * `server5.js` (`12-StarWars-5`)

* **Instructions:**

  * Spend a few moments researching what `express.json` is for and what `req.body` means in the context of Express.

  * Then research how you can POST data to the Express server.

## Heads Up

* In the next class, students will start using Heroku.

* Direct the students to the `04-Important` folder where there are [instructions](../../../../01-Class-Content/11-express/04-Important/heroku-install.md) for signing up for a Heroku account and installing the Heroku CLI.

* Remind the students to sign up for a Heroku account and have the Heroku CLI installed **before** coming to class!

* In a few classes, students will start using MySQL.

* Direct the students to the `04-Important` folder where there are installation instructions for both the MySQL Server and Workbench for [Mac](../../../../01-Class-Content/11-express/04-Important/mysql-mac-guide.md) and [Windows](../../../../01-Class-Content/11-express/04-Important/mysql-windows-guide.md) computers, as well as instructions on initializing the MySQL Shell.

* Advise the students to have both MySQL Server and Workbench installed **before** the next unit.

### Lesson Plan Feedback

How did today’s lesson go? Your feedback is important. Please take 5 minutes to complete this anonymous survey.

[Class Survey](https://forms.gle/nYLbt6NZUNJMJ1h38)
