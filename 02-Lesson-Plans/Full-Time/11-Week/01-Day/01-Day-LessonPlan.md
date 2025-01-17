## 11.1 - MERN (10:00 AM) <!--links--> &nbsp; [⬅️](../../10-Week/05-Day/05-Day-LessonPlan.md) &nbsp; [➡️](../02-Day/02-Day-LessonPlan.md)

## Overview

In this class, we will be deepening students understanding of ReactJS through reviewing all of the concepts covered over the previous few classes to build applications. We will also cover connecting Create React App to an Express backend as well as deploying to Heroku. 

At the end of class, we will introduce the final project's requirements and help the students conceptualize their project idea.

## Instructor Notes

* `Summary: Complete activities 01-06 in Unit 21`.

* Today's activities will contain significantly more boilerplate than the previous React lessons. Be sure to direct the class's attention to the important aspects of each exercise.

* Today's class will introduce little new material but will provide plenty of opportunity to review concepts covered over the past few classes.

* Leverage the TAs to help any groups struggling to conceptualize their final project idea. We want to give students as much time to brainstorm project ideas as possible.

## Learning Objectives

* To obtain a basic understanding of connecting a Create React App to an Express backend.

* To become comfortable communicating with an Express server from a React app.

* To increase understanding and comfort using React Router.

* To conceptualize final project idea with project group.

## Slides

[11.1: MERN](https://docs.google.com/presentation/d/1pO7pPyaCtPqP-d7fwkqORi9Mcx8wcZXlXLAUvJPyOEA/edit?usp=sharing)

[Final Project](https://docs.google.com/presentation/d/1FrCs35N0763wNqv6SRKFgF0IcDzBa5J7r6XM46nHqy4/edit?usp=sharing)

## Time Tracker

[11.1 Time Tracker](https://docs.google.com/spreadsheets/d/1gK-Ac1LTLa-up748RZouk9-VIxAeLtQxEK-YNBSWnMI/edit?usp=sharing)

- - -

### 1. Instructor Do: Welcome Class (5 mins)

* Take a moment to congratulate them on making it this far. This is historically by far one of the most challenging topics covered in the entire course.

* Check the pulse of the class so far. Ask them what their thoughts are so far when it comes to working with the library. Ask which concepts they'd like to spend more time on. Make a mental note to focus a bit more on those concepts as they come up during class today.

* If students feel as though they haven't totally mastered React yet, assure them that even seasoned developers sometimes struggle to wrap their heads around many of the ideas introduced by the library.

* We've covered a ton of material over the past week, and even more so over the entirety of the course. Try to put into perspective how amazing their progress has been.

### 2. Instructor Do: Slides (15 mins)

* Open the [11.1: MERN](https://docs.google.com/presentation/d/1pO7pPyaCtPqP-d7fwkqORi9Mcx8wcZXlXLAUvJPyOEA/edit?usp=sharing) slide deck. Be sure to give students enough time to answer each question and discuss before going over the answers.

### 3. Instructor Do: Mern Demo (15 mins)

* In this example you will demonstrate Create React App with an Express backend.

* Explain to the class that since beginning to learn React we've only been working with front-end code. We haven't set up a database, or an express server, we've just been working on the front-end with React.

* Point out that we _have been_ using a development server with Create React App. This development server's only purpose is to provide us with the live reloading functionality. When it comes time to deploy our app for production, Create React App can generate a static, standalone, HTML and JavaScript file containing the app.

* Explain that in most real applications, we'll often need a production quality server such as Express for connecting to a database or setting up API routes.

* Inform students that we'll be providing them with a Create React App Express boilerplate which they can use for the homework assignment or projects. There's no need to completely understand every aspect of the code in order to be productive, but we're going to walk through an example to give them at least a working high level understanding. This set up is _loosely_ based off of [Fullstack React's Food Lookup Demo](https://github.com/fullstackreact/food-lookup-demo).

* Open [01-Ins_Mern](../../../../01-Class-Content/21-MERN/01-Activities/01-Ins_Mern) in your editor and cd into it.

* In your editor, point out your sidebar with the `client` folder expanded, ask the class: What's something unusual we see here?

  ![Mern Sidebar](Images/01-MernSidebar.png)

  * We have 2 `package.json` files, with different sets of dependencies.

* Explain that Create React App handles what would have otherwise been a complicated build process and also gives our app live reloading in development. In order to still hang on to all of these benefits, our boilerplate consists of 2 node applications working together.

  * One app is Create React App.

  * The other is the Node/Express backend.

* Explain that since we have two node apps, we have to install dependencies for both. While at the root of the project directory, run the following commands:

  ```
  npm install
  ```

  * You should now have 2 `node_modules` folders: one at the root of the project and one inside of the `client` folder.

* Explain that during development (while we're working on the app and running it locally) the live reloading development server still runs on port 3000.

* Open the `package.json` file inside of the `client` folder:

  ![CRA Proxy](Images/02-CRAProxy.png)

  * Explain that the `proxy` setting is part of Create React App and can be read about in its documentation. It automatically forwards all HTTP requests from our React application to another specified base url.

  * Ask the class: If our live reloading server is on port 3000 by default, why might we be forwarding our React app's requests to port 3001?

    * We don't want to send HTTP requests to the dev server, instead we want to send them to our Express app which we have running on port 3001 — though we could use any port as long as we specify it.

      ![Server](Images/03-Server.png)

    * In a nutshell, we'd make HTTP requests to the endpoints defined in our Express server, but wouldn't have to specify that it's running on a different port in every request, e.g. we'd write `axios.get('/api/books');` instead of `axios.get('http://localhost:3001/api/books');`.

* Now point out the `package.json` at the root of the application directory:

  ![Server Package](Images/04-ServerPackage.png)

  * Bring the class's attention to the `scripts` section of the `package.json` file. Explain that we can define shortcuts for commands which we need to use in order to work with our node apps. So far we haven't had too much use for these, but with our current setup we need to run multiple, sometimes complex commands for various actions such as starting both the live-reloading server and the Express application.

  * While the number of scripts may seem initially overwhelming, we only need to care about two, _maybe_ three of these.

    * Point out the `start` command. Explain that if we are running our application on Heroku, it simply starts the Node server. If we're running it locally, it starts the Node server and live reloading Create React App server at the same time. The React app should appear to start as expected on port 3000, however in the background the Express server is running on PORT 3001.

    * Now, stop both servers and point out the `build` command. Explain that this builds a static version of our React app which can be deployed. With the `client` folder expanded, go ahead and run `npm run build` in your terminal.

    * Point out how we now have a `client/build` folder. This contains static versions of our HTML page, CSS, minified JavaScript, and other assets. Explain that we won't actually use these locally on our machines, but our Express app will serve these on Heroku. The `heroku-post-build` script tells heroku to run this command automatically for us when we deploy so we don't have to keep doing this ourselves.

    * Inform the class that for now, if the only thing they remember is `npm start` runs the API server and the React app, then they're fine for now.

* Slack out [Fullstack React's Food Lookup Demo](https://github.com/fullstackreact/food-lookup-demo) for them to look at on their own time.

* Take another few minutes to answer any high level questions. Assure everyone that they're about to get some hands-on experience in the next activity.

### 4. Students Do: React Recipes (15 mins)

* Introduce [02-Stu_Recipes](../../../../01-Class-Content/21-MERN/01-Activities/02-Stu_Recipes)

* In this example students will complete a recipe finder application by adding code to render a list of recipes retrieved from an AJAX request.

```md
* Open [Unsolved](Unsolved) in your editor. From the root of the project folder, run `npm install` to install the required dependencies.

* This application uses a Mongo database, so be sure to start `mongod`.

* In order to initially populate the database, run the following command at the project root: `npm run seed`.

* This should insert a few records into the MongoDB.

* Run `npm start` to start the React app and Express server. Visit [localhost:3000](http://localhost:3000) in your web browser to view the app.

* Enter a search term, e.g. "burgers" in the input field and submit. This won't have any visible affect on the page yet, but should submit an AJAX request and log the response to the console. Take a moment to study the response logged.

  ![Recipe Log](Images/01-RecipeLog.gif)

* The goal of this activity is to render these recipes to the DOM.

### Part 1

* For this section the only file you will need to modify is `App.js`. Take a few moments to study the code in the file.

* Using the `RecipeList` and `RecipeListItem` components, add code to render the array of recipes where indicated in the file.

  * The `RecipeList` component renders a `ul` tag and accepts children. The `RecipeListItem` component renders an `li` tag with some formatting to hold the recipe's title, thumbnail, etc.

* Using a `RecipeList` component as a container, map over `recipes` and render one `RecipeListItem` component for each recipe object in `recipes`.

* Pass the rendered `RecipeListItem` components each property of their recipe object, i.e. :

  * `title`

  * `href`

  * `ingredients`

  * `thumbnail`

* Test your solution by searching for a recipe in your browser. If successful so far, you should see the following:

  ![Recipe Incomplete](Images/02-RecipeIncomplete.gif)

* No matter the search query, the same hard coded recipe is being rendered in each `RecipeListItem` component. We'll address this problem next!

### Part 2

* If the previous section was completed correctly, the only file you should need to modify for this section is `RecipeListItem.js`.

* Currently the rendered `RecipeListItem` components are displaying hard coded recipe data. Modify the `RecipeListItem` component file so that it utilizes all of the passed props where appropriate. Look at the hard coded data to determine how each prop should be used.

* If completed successfully, searching for a recipe in your browser should render dynamic results relevant to the search. (Keep in mind the data set is limited so not all searches will return something. Try "pizza", "hamburger", "turkey", or "quinoa" for a few.)

  ![Recipe List](Images/03-RecipeList.gif)

### Hints

* Check out the [React Documentation](https://facebook.github.io/react/docs/lists-and-keys.html) on rendering lists of components if you need a refresher on this.

* Rather than mapping over recipes and rendering primitive `ul` and `li` tags, you'll be using the pre-built `RecipeList` and `RecipeListItem` components.

* Ask for help if you're stuck!

### Bonus

* Add code so that if a recipe doesn't come with a thumbnail url, use a placeholder image instead. Check out [placehold.it](https://placeholder.com/) for placeholder images.

* Add code so that if `recipes` is an empty array, render a message indicating that no recipes are available.

```

### 5. Instructor Do: Review React Recipes (10 mins)

* Open [02-Stu_Recipes/Solved](../../../../01-Class-Content/21-MERN/01-Activities/02-Stu_Recipes/Solved) in your IDE.

* Run `npm install` to install dependencies at the project root, this should also install the dependencies in the `client` folder.

* This application uses a Mongo database, so be sure to start `mongod`.

* In order to initially populate the database, run the following command at the project root: `npm run seed`.

* This should insert a few records into the MongoDB.

* Cd back up to the project root and run `npm start` to start the application. Open [localhost:3000](http://localhost:3000) in your browser to demonstrate the solution.

  ![Recipe List](Images/06-RecipeList.gif)

* Whenever we search for a recipe in the search field, a list of recipes is rendered using the data from the AJAX request.

  * Avoid letting students get too hung up on the server side code. The main focus of today's lesson is still React, and they can dig into the code in its entirety on their own time.

* Open the [client/src/App.js](../../../../01-Class-Content/21-MERN/01-Activities/02-Stu_Recipes/Solved/client/src/App.js) file and go over the new code:

  * Make sure everyone understands where the props we're passing the `RecipeListItem` components are coming from.

  * The recipe objects received from the AJAX request have these properties. We're passing them to the `RecipeListItem` to be used.  

```js
<Row>
  <Col size="xs-12">
    {!recipes.length ? (
      <h1 className="text-center">No Recipes to Display</h1>
    ) : (
      <RecipeList>
        {recipes.map(recipe => {
          return (
            <RecipeListItem
              key={recipe.title}
              title={recipe.title}
              href={recipe.href}
              ingredients={recipe.ingredients}
              thumbnail={recipe.thumbnail}
            />
          );
        })}
      </RecipeList>
    )}
  </Col>
</Row>
```

* Now open [client/src/components/RecipeList/index.js](../../../../01-Class-Content/21-MERN/01-Activities/02-Stu_Recipes/Solved/client/src/components/RecipeList/index.js) in your IDE and point out the following:

  * `props.thumbnail` (an image URL for the recipe) is passed to the `Thumbnail` component which renders the image

  * `props.title` (the name of the recipe) is rendered inside of the heading

  * `props.ingredients` (a comma-delimited list of ingredients) is rendered inside of the paragraph tag

  * `props.href` (the URL to the original recipe) is rendered inside of the anchor tag

```js
export function RecipeListItem({
  thumbnail,
  title,
  ingredients,
  href
}) {
  return (
    <li className="list-group-item">
      <Container>
        <Row>
          <Col size="xs-4 sm-2">
            <Thumbnail src={thumbnail || "https://placehold.it/300x300"} />
          </Col>
          <Col size="xs-8 sm-9">
            <h3>{title}</h3>
            <p>Ingredients: {ingredients}</p>
            <a rel="noreferrer noopener" target="_blank" href={href}>
              Go to recipe!
            </a>
          </Col>
        </Row>
      </Container>
    </li>
  );
}
```

* Take a few minutes to answer any questions about this activity.

* Explain that while this activity was interesting, it didn't have any kind of persistent storage. The next few activities will utilize a Mongo database and should help prepare them for their homework assignment and final projects.

### 6. Students Do: AJAX Books (10 mins)

* Introduce students to [03-Stu_AJAXBooks](../../../../01-Class-Content/21-MERN/01-Activities/03-Stu_AJAXBooks)

* In this activity students will work to add functionality to a full stack React Reading List application.

```md
# AJAX Books

In this activity we will add functionality to a full stack React application for retrieving books from a database.

## Instructions

* Open the [Unsolved](Unsolved) folder in your editor and run `npm install` at the project's root.

* This application uses a Mongo database, so be sure to start `mongod`.

* In order to initially populate the database, run the following command at the project root: `npm run seed`.

* This should insert a few records into the MongoDB.

* Run `npm start` at the project root to start the application.

* Open your browser to [localhost:3000](http://localhost:3000) and take a moment to study the rendered application.

  * This example is a reading list application. **Currently the app isn't fully functional.**

* Open up `client/src/pages/Books.js` and add code so that when the component mounts, it performs an AJAX request to retrieve all of the books in the database. Once the AJAX request is complete, it should set `books` equal to the array of books.

* If successful, a list of books should be rendered on the right side of the page.

  * We'll work on making the form functional in the next activity.

## Hints

* Use the API helper module (`client/src/utils/API.js`) to perform an AJAX request which should return _all_ of the books in the database.

* The only file you will need to modify is `client/src/pages/Books.js`.

```

* Instructional staff should be walking around the room during this activity, available for assistance.

### 7. Instructor Do: Review AJAX List (10 mins)

* Open and run the [03-Stu_AJAXBooks/Solved](../../../../01-Class-Content/21-MERN/01-Activities/03-Stu_AJAXBooks/Solved) to the previous activity and demonstrate the result in your browser:

  * ![Ajax List](Images/06-AJAXList.gif)

* The goal of this activity was just to render the initial list of books. We'll work on actually making the form functional in the next activity.

* Open the `Books` component [client/src/pages/Books.js](../../../../01-Class-Content/21-MERN/01-Activities/03-Stu_AJAXBooks/Solved/client/src/pages/Books.js) in your IDE.

* Have a volunteer explain the code to you.

  * We import the `API` module into our component.

  * When the component is created the `useEffect` callback is called. Inside we call `loadBooks()` which we've defined below.

  * `loadBooks()` uses the pre-written `API` module to retrieve all of the books from the database and then sets them to `books`.

  * Point out how even though we don't know much about how our backend is configured, we were still able to make an AJAX request to it to retrieve all of the books. This is because we're using the `API` helper module which contains methods for making requests to various endpoints.

  ```js
  function Books() {
  // Setting our component's initial state
  const [books, setBooks] = useState([])
  const [formObject, setFormObject] = useState({})

  // Load all books and store them with setBooks
  useEffect(() => {
    loadBooks()
  }, [])

  // Loads all books and sets them to books
  function loadBooks() {
    API.getBooks()
      .then(res => 
        setBooks(res.data)
      )
      .catch(err => console.log(err));
  };

  ```

  * Further down below, a list is being rendered from `books`. When the list is empty, a message is displayed explaining this. Otherwise the list of books is rendered.

```js
{books.length ? (
  <List>
    {books.map(book => {
      return (
        <ListItem key={book._id}>
          <a href={"/books/" + book._id}>
            <strong>
              {book.title} by {book.author}
            </strong>
          </a>
          <DeleteBtn onClick={() => deleteBook(book._id)} />
        </ListItem>
      );
    })}
  </List>
) : (
  <h3>No Results to Display</h3>
)}
```

  * Take a few moments to make sure everyone understands these pieces of code.

### 8. Students Do: AJAX Form Delete (15 mins)

* Introduce students to [04-Stu_AJAXFormDelete](../../../../01-Class-Content/21-MERN/01-Activities/04-Stu_AJAXFormDelete)

* In this activity students will add functionality to the React Reading List app to save and delete books.

```md
* Open the [Unsolved](Unsolved) folder and install dependencies by running `npm install` at the project root.

* Start the app by running `npm start` from the project root.

* Once the app starts open your browser to [localhost:3000](http://localhost:3000).

* Open [Unsolved](Unsolved/client/src/pages/Books.js).

### Part 1

* Open the `Books.js` file. Add code so that `formObject.title`, `formObject.author`, and `formObject.synopsis` are updated as their corresponding `Input` components are updated (see the `name` properties on each `Input`). Any props you attach to the `Input` components will be passed down to their underlying elements, so there's no need to modify any code other than the code inside of `Books.js`.

* Add code so that when the `FormBtn` is clicked, an AJAX request is performed saving the new book. An object containing the new book's `title`, `author` and `synopsis` should be passed into the `API.saveBook` method.

### Part 2

* Add code to the `Books.js` file so that when the `DeleteBtn` (`✗` button) component is clicked, its book is deleted from the database and the books displayed are updated. To accomplish this you should create a new method (`deleteBook`) on the `Books` component, which calls the `API.deleteBook` method when the `DeleteBtn` is clicked.

#### Hints

* The only file you need to modify is `Books.js`.

* See [React's Documentation on Handling Events](https://facebook.github.io/react/docs/handling-events.html)

```

### 9. Instructor Do: Review AJAX Form Delete (10 mins)

* Open up the [04-Stu_AJAXFormDelete/Solved](../../../../01-Class-Content/21-MERN/01-Activities/04-Stu_AJAXFormDelete/Solved) to the previous activity and go over the new code as a class. The only changes that needed to be made are in the `client/src/pages/Books.js` file.

  * It may be easier to explain starting by going through the code in the `return` block involving the form elements.

  * In order to capture the values from the form, we add `value` and `onChange` props to the `Input` components.

```js
return (
  <Container fluid>
    <Row>
      <Col size="md-6">
        <Jumbotron>
          <h1>What Books Should I Read?</h1>
        </Jumbotron>
        <form>
          <Input
            onChange={handleInputChange}
            name="title"
            placeholder="Title (required)"
            value={formObject.title}
          />
          <Input
            onChange={handleInputChange}
            name="author"
            placeholder="Author (required)"
            value={formObject.author}
          />
          <TextArea
            onChange={handleInputChange}
            name="synopsis"
            placeholder="Synopsis (Optional)"
            value={formObject.synopsis}
          />
          <FormBtn
            disabled={!(formObject.author && formObject.title)}
            onClick={handleFormSubmit}
          >
            Submit Book
          </FormBtn>
        </form>
      </Col>
      <Col size="md-6 sm-12">
        <Jumbotron>
          <h1>Books On My List</h1>
        </Jumbotron>
        {books.length ? (
          <List>
            {books.map(book => {
              return (
                <ListItem key={book._id}>
                  <a href={"/books/" + book._id}>
                    <strong>
                      {book.title} by {book.author}
                    </strong>
                  </a>
                  <DeleteBtn onClick={() => deleteBook(book._id)} />
                </ListItem>
              );
            })}
          </List>
        ) : (
          <h3>No Results to Display</h3>
        )}
      </Col>
    </Row>
  </Container>
);
```

  * Ask the class: How roles do the `value`, `name`, and `onChange` props have in updating our component state with the form data?

  * When the user attempts to type into one of the input fields, the input field doesn't update right away, instead the `onChange` event handler is fired.

  ```js
  function handleInputChange(event) {
    const { name, value } = event.target;
    setFormObject({...formObject, [name]: value})
  };
  ```

  * Like event handlers in jQuery and vanilla JavaScript, `handleInputChange` receives an `event` object containing information about the event which occurred as a parameter.

  * From this event object we can grab the `name` attribute and `value` of the input field. The `value` is what the input would change to if it weren't being controlled by React, and the `name` is the name of the input's corresponding state value.

  * Then we update `formObject[name]` to be the new `value`.

  * `onChange` updates the component's `state` which then updates the text displayed in the input field.

* Go over the `handleFormSubmit` method:

  * We first prevent the default behavior of the form submission (which would have been to refresh the page).

  * Next we check that the `title` and `author` (the "required" fields) are not null before continuing.

  * If we have a `title` and `author`, submit the book data using the `API.saveBook` method.

  * Once the request completes successfully, run `loadBooks()` in order to update the books displayed.

  ```js
  function handleFormSubmit(event) {
    event.preventDefault();
    if (formObject.title && formObject.author) {
      API.saveBook({
        title: formObject.title,
        author: formObject.author,
        synopsis: formObject.synopsis
      })
        .then(() => setFormObject({
          title: "",
          author: "",
          synopsis: ""
        }))
        .then(() => loadBooks())
        .catch(err => console.log(err));
    }
  };
  ```

* Finally, go over the `delete` book method:

  * It expects to receive an `id` argument to pass to the `API.deleteBook` method.

  * Once complete, `loadBooks()` is run to retrieve and display the updated list of books.

  ```js
  function deleteBook(id) {
    API.deleteBook(id)
      .then(res => loadBooks())
      .catch(err => console.log(err));
  }
  ```

  * Point out how we wrap the `onClick` handler in an anonymous function so that we can pass in the `_id` of the book as an argument.

  * Wrapping a click handler in an anonymous function is another way of passing arguments into it.

```js
<ListItem key={book._id}>
  <a href={"/books/" + book._id}>
    <strong>
      {book.title} by {book.author}
    </strong>
  </a>
  <DeleteBtn onClick={() => deleteBook(book._id)} />
</ListItem>
```

* Take a few moments to answer any remaining questions.

- - -

### 10. Everyone Do: BREAK (30 mins)

- - -

### 11. Students Do: React Router (20 mins)

* Introduce [05-Stu_ReactRouter](../../../../01-Class-Content/21-MERN/01-Activities/05-Stu_ReactRouter)

* _The unsolved activity will throw exceptions until students complete the first part of the activity._

* In this activity students will add React Router to the React Reading List in order to add a books `Detail` page and a `NoMatch` 404 page. Students will need to look up how to use route params with React Router.

* Instructional staff should be walking around the classroom during this activity, available for assistance and making sure students understand all of the activity requirements.

```md

* Open the [Unsolved](Unsolved) folder and install dependencies by running `npm install` at the project root.

* Start the app by running `npm start` from the project root.

* Once the app starts open your browser to [localhost:3000](http://localhost:3000).

* Open [App.js](Unsolved/client/src/App.js).

### Part 1

* Set up React Router inside of the `client/src/App.js` file.

  * The `/` and `/books` routes should both render the `Books` component page.

### Part 2

* Notice that inside of the `pages` folder we have a `NoMatch` component. This is the component for our 404 page.

* Add a route for the new `NoMatch` component. This should only render if no other routes are matched. e.g. `/sjdfhjsdhfjsa` or `/notarealroute/lalala` should both render the `NoMatch` component page. 

  * You will need to use the `Switch` component from the React Router Dom library to accomplish this. An example can be found [here](https://reacttraining.com/react-router/web/example/no-match).

### Part 3

* Notice that in the `pages` folder we have a `Detail` component. This component displays additional information about a book.

* Add a route for the the new `Detail` component. This should render when the `/books/:id` path is matched. e.g. if a book's `_id` is `59a39cf2549cf482c814333f`, then `/books/59a39cf2549cf482c814333f` should render its book `Detail` page.

* Inside of the `Detail` component, add code so that when the component mounts, we retrieve the book for the rendered route and save it to `book`. e.g. when the route is `/books/59a39cf2549cf482c814333f`, an AJAX request should be made to get the book with an `_id` of `59a39cf2549cf482c814333f`. If completed successfully, you should see the book's synopsis on this page.

  * You may need to look into [URL params with React Router](https://reacttraining.com/react-router/web/example/url-params) to accomplish this.

### Hints

* Parts 1 - 2 will only require you modify the `client/src/App.js` file.

* The React Router DOM library should already be installed.

* The React Router documentation is your friend!

* Ask the instructor or a TA if you're having difficulty understanding any of the activity requirements.

```

### 12. Instructor Do: Review React Router (15 mins)

* Once time's up, go over the [05-Stu_ReactRouter/Solved](../../../../01-Class-Content/21-MERN/01-Activities/05-Stu_ReactRouter/Solved) version of the last activity.

* Open the [client/src/App.js](../../../../01-Class-Content/21-MERN/01-Activities/05-Stu_ReactRouter/Solved/client/src/App.js) file in your IDE go over the new code:

  * Point out how both the `/` and `/books` `Route` components both render the `Books` component.

  * The `/books/:id` `Route` component renders the `Detail` component.

  * This component is for rendering details about a particular book.

```js
import React from "react";
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";
import Books from "./pages/Books";
import Detail from "./pages/Detail";
import NoMatch from "./pages/NoMatch";
import Nav from "./components/Nav";

function App() {
  return (
    <Router>
      <div>
        <Nav />
        <Switch>
          <Route exact path={["/", "/books"]}>
            <Books />
          </Route>
          <Route exact path="/books/:id">
            <Detail />
          </Route>
          <Route>
            <NoMatch />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

export default App;
```

  ![Details](Images/17-Details.png)

  * Similar to routes in Express, we can utilize route parameters. The values of any route parameters are available to us inside of the rendered component the object provided by the `useParams` hook. Inside of the `client/src/pages/Detail.js` file, we access the `id` parameter:

  ```js
  import { Link, useParams } from "react-router-dom";
  
  // ...

  function Detail(props) {
    const [book, setBook] = useState({})

    // When this component mounts, grab the book with the _id of props.match.params.id
    // e.g. localhost:3000/books/599dcb67f0f16317844583fc
    const {id} = useParams()
    useEffect(() => {
      API.getBook(id)
        .then(res => setBook(res.data))
        .catch(err => console.log(err));
    }, [])
  ```

  * Go back to the `App.js` file and point out the `Route` component rendering the `NoMatch` component . Explain that this component _should_ be rendered on every route since we haven't provided it a `path` prop.

  * The reason the `NoMatch` route works as expected is because of the `Switch` component wrapping our `Route`s. The `Switch` component ensures that once one of the routes are rendered, none of the routes that come after it are even checked. So as long as one of the routes match, the `NoMatch` component is not rendered. But if _none_ of the routes match, then `NoMatch` is rendered. It is like the "default" case in a switch-case statement.

```js
<Router>
  <div>
    <Nav />
    <Switch>
      <Route exact path={["/", "/books"]}>
        <Books />
      </Route>
      <Route exact path="/books/:id">
        <Detail />
      </Route>
      <Route>
        <NoMatch />
      </Route>
    </Switch>
  </div>
</Router>
```

* Take another few minutes answering any remaining questions.

### 13. Students Do: Deploy (15 mins)

* In this final activity, students are tasked with deploying the React Reading List app to Heroku. They can use the [05-Stu_ReactRouter/Solved](../../../../01-Class-Content/21-MERN/01-Activities/05-Stu_ReactRouter/Solved) version of the previous activity.

* **Instructions:** [06-Stu_Deployment/README.md](../../../../01-Class-Content/21-MERN/01-Activities/06-Stu_Deployment/README.md)

### 14. Instructor Do: Review Deploy (5 mins)

* Take a poll to see how many students were able to successfully deploy the React Reading List to Heroku.

* Explain that when it comes to their homework assignments and final projects, they should make sure they have deployment figured out sooner rather than later.

* There are now more reasons why a Heroku deployment could fail than there ever have been before, so urge them to not try and push to Heroku for the first time right before an assignment is due.

* They can refer back to the instructions provided with the activity for deploying a full stack react app to Heroku, and as always, yourself and the TAs are available to help during office hours.

### 15. Instructor Do: What's Next? (03 mins)

* Open the [Final Project Slides](https://docs.google.com/presentation/d/1FrCs35N0763wNqv6SRKFgF0IcDzBa5J7r6XM46nHqy4/edit?usp=sharing) and explain what to expect in the last few classes.

* Congratulate the students on getting this far! Go over what they have learned in the past few months.

* Tell them about the lectures they can expect, as well as final project presentations and their day with potential employers.

* Announce: no homework for the rest of the course! Well, except for:

  * This week's homework (they still gotta hand that one in).

  * Weekly project deliverables -- more on that soon.

* Tell class that learning doesn't end when they finish the course. There's a literal argosy of languages, frameworks, libraries and other technologies for web developers to study -- and no doubt, this heap of knowledge will build as the years pass.

* Point being: web developers must always teach themselves new skills to stay relevant in this field!

* But add in something along these lines. "No problem! If you learned anything in this boot camp, it's how to grasp these technologies quick &mdash; you're ready for this."

### 16. Instructor Do: Final Project - The Deets (07 mins)

* Spend a few minutes introducing the requirements for the final project (Slides 7-20).

* Tell students should challenge themselves, and that you'll take no excuses. They've made it this far already &mdash; it's time for them to take everything they learned and produce their best work yet.

* **Go over what's expected for the project:**

  * Whatever they build should have utility.

  * They should have market or real-world research that proves their idea has REAL value to people.

  * They should perform research on other web / mobile applications in their app's domain.

  * They should put serious time and thought into this.

  * They should report problems they're facing along the way.

  * They should use some form of project management system (Jira, Trello and so on).

  * They should dig deep into documentation and external resources to find the tools they need.

* **Go over what's required of each group. Each Project:**

  * Must use ReactJS.

  * Must use a Node and Express Web Server.

  * Must be backed by a MySQL or MongoDB Database with a Sequelize or Mongoose ORM.

  * Must have both GET and POST routes for retrieving and adding new data.

  * Must be deployed using Heroku (with Data).

  * Must utilize at least two libraries, packages, or technologies that we haven't discussed.

  * Must allow for or involve the authentication of users in some way.

  * Must have a polished frontend / UI.

  * Must have folder structure that meets MVC Paradigm.

  * Must meet good quality coding standards (indentation, scoping, naming).

* **Finally, go over each Project Deliverables**

  * **Deliverable 1**: A detailed plan of action with the following:

    * An overview of the intended application and WHY you feel it's valuable.

    * A breakdown of roles by group member.

    * A schedule for completion of various tasks.

    * A screenshot of your Jira, Trello, or Project Management Board that shows breakdown of tasks assigned to group members with a schedule.

    * A set of DETAILED screen-by-screen design layouts with annotations describing all UI/UX components and all data relevant to the screen.

      * On this note, show Slides 18-19 as an example of a UI/UX and Data Flow layout. Tell the class that you'll expect something akin to these drafts.

  * **Deliverable 2**: A functioning **minimal viable product** (i.e., a prototype version of your app that shows the intended function). This should be as close to a working app as possible and include:

    * A 5-7 minute presentation that discusses what your app is, what it does, and how it works. You will be presenting to instructors and TAs during class.

    * A screenshot of your Jira, Trello, or Project Management Board that shows breakdown of tasks assigned to group members with a schedule. This should be updated to reflect remaining priorities and completed tasks.

  * **Deliverable 3**: A significantly more polished version of the app.

    * This should literally seem like an app that you would submit.

    * Include a summary of significant issues faced to date and their resolution.

    * Provide a detailed description of each person's contributions.

    * Submit a detailed plan that describes remaining efforts. This should describe remaining issues like:
      * Stretch Features
      * Bugs
      * Enhancements
      * UI Polishing

  * **Deliverable 4**: The Presentation!
    * A 7-10 minute demonstration of your app.
    * More on this as we near closer to the end.

* Ask if anyone has any questions before moving on.

### 17. Students Do: Conceptualize the Final App (70 mins)

* When you close the Slide Deck, direct your students to form into their groups to think about the app they'll create over the next month.

* By the time the class ends, they should tell you the following details about their project:

  * What the app will do.
  * What technologies they expect their app to implement.
  * Who will be responsible for each part of the app.
  * Who will be responsible for each part of deliverable #1.

* Record these responses in a list and make sure each group has given you those four items before they leave class.

* As they're thinking about their apps, you and the TAs should walk the classroom and check in on their progress. Once again, make sure they pick something that will challenge them (but not something so ambitious that it will destroy them).

- - -

### 18. END (0 mins)

