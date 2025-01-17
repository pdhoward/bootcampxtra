## 10.4 - The Context API <!--links--> &nbsp; [⬅️](../03-Day/03-Day-LessonPlan.md) &nbsp; [➡️](../05-Day/05-Day-LessonPlan.md)

## Overview

This class introduces students to the React Context API, an easier and lighter weight alternative to state management libraries like Redux or MobX. Learning how to use the Context API will also introduce students to the concept of state management, as well as the benefits/pitfalls of tightly-coupled components.

## Instructor Notes

- `Summary: Complete activities 7-14 in Unit 20.`

- The demos and activities will only include the `src` folder which you will need to replace in your React app's boilerplate to avoid repetitive installs. It's recommended that you completely restart the dev server between activities.

- Today's lesson will rely on instructor led demonstrations, so be sure to spend some time before class reviewing the examples.

## Learning Objectives

- Create Context Objects and use them as a means to share state.

- Learn about general good practices when working with component-based applications.

- Identify proper use cases of Context API, while staying aware of its shortcomings.

- Utilize a combination of Context Objects, Providers, and consumers via the `useContext` Hook to manage global state.

- Use multiple Context Providers to manage complex state.

## Slides

[10.4: The React Context API](https://docs.google.com/presentation/d/1rHP32SL8aAlHn_0FE-EeD_e6lvERTBwtEpC4UvARdq0/edit?usp=sharing)

## Time Tracker

[10.4 Time Tracker](https://docs.google.com/spreadsheets/d/144jIaroDbesRzXbTiQAu32knQ9HjNfeNUwO-1czv6t0/edit?usp=sharing)

---

### 1. Students Do: Third Party Hooks (20 mins)

- If time permits, introduce students to [07-Stu_ThirdPartyHooks/](../../../../01-Class-Content/20-State/01-Activities/07-Stu_ThirdPartyHooks/README.md). Since this activity uses third party Hooks, only proceed with this activity if the students seem to have a solid grasp of Hooks. Otherwise, spend the rest of class answering lingering questions, reviewing, and skimming over the solution with the class.

  - In this activity we will practice using third party Hooks. Specifically, we will be creating a survey form using the `react-hanger` package on npm.

  - Let the students know that `react-hanger` is one of many custom Hooks packages on GitHub. This package contains multiple custom

  ````md
  - Replace your React application's src folder with [Unsolved/src](Unsolved/src).

  - Install react-hanger by running `npm install react-hanger` in your terminal.

  - **Recommended:** Add the Bootstrap and Font Awesome CDNs to your application's `index.html` file:

    ```html
    <link
      href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"
      rel="stylesheet"
    />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.0.0/css/bootstrap.min.css"
    />
    ```
  ````

  - Start the application in dev mode by running `npm start` in your terminal.

  - Open your browser to [localhost:3000](http://localhost:3000) and study the rendered application.

    - There are a few fields in our survey form. Before writing any code, try thinking about how you would manage the state of this form.

  - Navigate to the [react-hanger docs](https://github.com/kitze/react-hanger) familiarize yourself with the `useInput`, `useBoolean`, and `useNumber` Hooks.

  - Update this application to accomplish the following:

    - Each user input should be handled using the `react-hanger` Hooks.

    - When the user clicks an emoji, indicate which type of response they selected by displaying the text: `You responded that you feel FEELING`. `FEELING` should be replaced with the value of the emoji that they clicked.

    - Make your survey form a little more dynamic by displaying a field for additional comments when the user clicks on an emoji.

    - When the form is submitted, `console.log` an object containing all of the values from the form.

  ### Hints

  - There are many ways to satisfy the requirements of this application. It is recommended that you attempt the most straightforward solution first, then refactor your working app.

  ```

  ```

### 2. Instructor Do: Review Third Party Hooks (10 mins)

- Replace your React application's src folder with [07-Stu_ThirdPartyHooks/Solved](../../../../01-Class-Content/20-State/01-Activities/07-Stu_ThirdPartyHooks/Solved/src) and start the development server by running `npm start`. See the rendered application at [localhost:3000](http://localhost:3000).

- Demonstrate that the application satisfies the requirements:

  - Fill out each field in the form with dummy data.

  - Click `submit`.

  - Open the console and show that the form object contains the value from each field.

- Open [Survey/index.js solved](../../../../01-Class-Content/20-State/01-Activities/07-Stu_ThirdPartyHooks/Solved/src/pages/Survey/index.js) in your IDE and demonstrate the following:

  - Even though we used `textarea` instead of `input`, we can still use the `useInput` hook.

  - `showComment` is initialized to `false` so that the additional input field is not visible initially.

  - Since we will be setting the rating manually, we do not need to give it upper and lower bounds.

  ```js
  const favoriteThing = useInput("");
  const showComment = useBoolean(false);
  const comment = useInput("");
  const feeling = useInput("");
  const rating = useNumber(0);
  ```

  - Our form object contains the value of each field. Since `showComment` is only used for display purposes, we do **not** include it in the form object.

  ```js
  const handleSubmit = () => {
    const form = {
      favoriteThing: favoriteThing.value,
      comment: comment.value,
      feeling: feeling.value,
      rating: rating.value
    };
    console.log(form);
  };
  ```

  - `...favoriteThing.eventBind` binds both the `value` and the `onChange` props of an element, as long as it has a `event.target.value`.

  - This single method would also work with input fields and select elements.

  ```js
  <textarea {...favoriteThing.eventBind} />
  ```

  - It is very important that we include `role="img"` and `aria-label="angry"` to make the emojis accessible.

  - The onClick method toggles our `showComment` boolean and sets the feeling value to angry.

  ```js
  <span
    role="img"
    aria-label="angry"
    onClick={() => {
      showComment.toggle();
      feeling.setValue("angry");
    }}
  >
    😠
  </span>
  ```

  - We use a ternary operator so that the additional comments textarea only renders if the `showComment` boolean is true.

  - Once again, `onClick` and `value` are bound to the comment variable.

  ```js
  <div className="response">
    {showComment.value ? (
      <textarea
        {...comment.eventBind}
        placeholder="Please add any additional comments"
      />
    ) : null}
  </div>
  ```

### 3. Stoke Curiosity (10 mins)

- Tell the students that this unit covers content that is considered the bleeding edge of React. It is important to note that although some of the concepts are brand-new, they are being quickly adopted into the React ecosystem by the community.

- The reasons that we learn about these new features are:

  - Learning brand-new features helps you become employer-competitive.

  - Learning these features will help you to become better versed in React, making you more effective and improving your ability to adapt to new advancements.

  - Oftentimes, new features enable a faster, smaller (in file size), or better crafted application.

  - In this unit, the features that we will learn helped solve problems that React developers had been trying to solve for years.

### 4. Students Do: Prop Drilling (20 mins)

- Introduce [08-Stu_PropDrilling/Unsolved](../../../../01-Class-Content/20-State/01-Activities/08-Stu_PropDrilling/Unsolved)

````md
# Prop Drilling

In this activity we will review passing props down the component tree in React.

## Instructions

* Replace your React application's src folder with [Unsolved/src](Unsolved/src).

* Install axios by running `npm install axios` in your terminal.

* **Recommended:** Add the Bootstrap and Font Awesome CDNs to your application's `index.html` file:

  ```html
  <link
    href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"
    rel="stylesheet"
  />
  <link
    rel="stylesheet"
    href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
    integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T"
    crossorigin="anonymous"
  />
  ```

* Start the application in dev mode by running `npm start` in your terminal.

* Open your browser to [localhost:3000](http://localhost:3000) and study the rendered application.

* The `fetchUsers` function in `src/utils/API.js` returns an array of users that follow this format:

  ```js
  [
    {
      login: "username",
      profileUrl: "https://github.com/username",
      image: "https://avatars0.githubusercontent.com/u/00000000?v=4"
    }
  ];
  ```

* Update this application to accomplish the following:

  * The card on the gallery page should contain an image of the user, their programming language, and arrow buttons that allow for navigation through different users.

  * The props should be passed through each component layer in the following manner:

    * title (login): Gallery > CardContainer > Card > CardHeading > CardTitle > CardTitleText

    * image: Gallery > CardContainer > Card > CardImage

    * profileUrl: Gallery > CardContainer > Card > CardBody

    * handleClick: Gallery > CardContainer > Card > CardBtn

  * Each arrow click should _not_ make an additional API call.

````

### 5. Instructor Do: Review Prop Drilling (15 mins)

* Run `npm start` in [08-Stu_PropDrilling/Solved](../../../../01-Class-Content/20-State/01-Activities/08-Stu_PropDrilling/Solved) and demonstrate the functioning application in your browser.

* Open [Gallery.js](../../../../01-Class-Content/20-State/01-Activities/08-Stu_PropDrilling/Solved/src/pages/Gallery.js)  in your IDE. Point out the following key aspects of the activity:

  * `Gallery.js` is a stateful component responsible for application logic such as performing API requests. It stores the data response from API requests in state.

  * We use the `useState` hook multiple times so that it's easier to individually manage the different aspects of our state.

* Ask the students the following question:

  * ☝️ Is there a different way we could have organized our state?

  * 🙋 We could have chosen to use one big state object instead of separating them out. This is a tradeoff that students will constantly encounter when trying to manage state. Ideally, we want to organize our code in a way that makes sense.

  * 🙋 Oftentimes, it is best to group similar logic into their own state objects. For example, we may make one state object to contain all of our users, and another to manage the current state of the application. (Combine userIndex and user into one state object)

  ```js
  const [user, setUser] = useState({});
  const [users, setUsers] = useState([]);
  const [userIndex, setUserIndex] = useState(0);
  ```

- When the component mounts , we run `loadUsers`. Since the second argument is an empty array, `loadUsers` will only be ran once.

```js
useEffect(() => {
  loadUsers();
}, []);
```

- `loadUsers` makes a request to our API using the `fetchUsers` method and _then_ updates the respective properties using their setter methods.

```js
function loadUsers() {
  API.fetchUsers()
    .then(users => {
      setUsers(users);
      setUser(users[0]);
    })
    .catch(err => console.log(err));
}
```

- In the `return` block, we return a Row component with a CardContainer. We pass to the CardContainer title, image, profileUrl, and handleBtnClick props.

```js
return (
  <div>
    <h1 className="text-center">Welcome to LinkedUp</h1>
    <p className="text-center h3">Click on the arrows to browse users</p>
    <Row>
      <CardContainer
        title={user.login}
        image={user.image}
        profileUrl={user.profileUrl}
        handleBtnClick={handleBtnClick}
      />
    </Row>
  </div>
);
```

- When a user clicks one of the buttons in the browser, `handleBtnClick` is called. Using `getAttribute`, we grab the `data-value` attribute off the button that triggered the event. If the value is equal to “next”, we call the `nextUser` method, otherwise we call `previousUser`

```js
function handleBtnClick(event) {
  // Get the title of the clicked button
  const btnName = event.target.getAttribute("data-value");
  if (btnName === "next") {
    const newUserIndex = userIndex + 1;
    nextUser(newUserIndex);
  } else {
    const newUserIndex = userIndex - 1;
    previousUser(newUserIndex);
  }
}
```

- The `nextUser` and `previousUser` methods each update state with the `userIndex` value returned from `handleBtnClick`

```js
function nextUser(userIndex) {
  // Ensure that the user index stays within our range of users
  if (userIndex >= users.length) {
    userIndex = 0;
  }
  setUser(users[userIndex]);
  setUserIndex(userIndex);
}

function previousUser(userIndex) {
  // Ensure that the user index stays within our range of users
  if (userIndex < 0) {
    userIndex = users.length - 1;
  }
  setUser(users[userIndex]);
  setUserIndex(userIndex);
}
```

- Answer any questions related to `Gallery.js`.

- Then open [Components/Card](../../../../01-Class-Content/20-State/01-Activities/08-Stu_PropDrilling/Solved/src/components/CardContainer/index.js) and point out the following:

  - The CardContainer component imports the Card component and passes to it the title, image, profileUrl, and handleBtnClick, props received from the Gallery component.

  - We use Object destructuring to get `props.title`, `props.image`, etc. This is not required, but it helps keep our code clean and easy to read.

```js
function CardContainer({ title, image, profileUrl, handleBtnClick }) {
  return (
    <div className="jumbotron card-container">
      <Card
        title={title}
        image={image}
        profileUrl={profileUrl}
        handleBtnClick={handleBtnClick}
      />
    </div>
  );
}
```

- Next, open [Components/Card](../../../../01-Class-Content/20-State/01-Activities/08-Stu_PropDrilling/Solved/src/components/Card/index.js) and point out the following:

  - The Card component imports the CardHeading, CardImg, CardBtn and CardBody components.

```js
import CardBody from "../CardBody";
import CardBtn from "../CardBtn";
import CardImg from "../CardImage";
import CardHeading from "../CardHeading";
```

- The Card component receives props from `CardContainer` and passes the `handleBtnClick` props to both instances of `CardBtn`.

- The remaining props are passed through the `CardHeading`, `CardImg`, and `CardBody` components.

- Note the data-value props passed to each CardBtn component.

```js
function Card({ title, image, profileUrl, handleBtnClick }) {
  return (
    <div>
      <CardHeading title={title} />
      <CardImg image={image} />
      <CardBody profileUrl={profileUrl} />
      {!image && <i className="fa fa-spinner fa-spin" aria-hidden="true" />}
      <CardBtn
        style={{ opacity: image ? 1 : 0 }}
        onClick={handleBtnClick}
        data-value="back"
      />
      <CardBtn
        style={{ opacity: image ? 1 : 0 }}
        onClick={handleBtnClick}
        data-value="next"
      />
    </div>
  );
}
```

- Next, open [Components/Card](../../../../01-Class-Content/20-State/01-Activities/08-Stu_PropDrilling/Solved/src/components/CardBtn/index.js) and point out the following:

  - The `CardBtn` component receives props from the Card component and renders them as attributes.

```js
function CardBtn(props) {
  return (
    <button onClick={props.onClick} className={`card-btn ${props["data-value"]}`} {...props} />
  );
}
```

- Open the components files in the following order: `CardHeading > CardTitle > CardTitleText`.

  - Point out that each intermediate component doesn't actually use props for anything besides passing the value down to the next component.

- Return to http://localhost:3000/gallery in the browser and, using the DOM Inspector, point out the corresponding attributes as well as the onClick event associated with each button.

- Ask the students the following questions:

  - ☝️ Why do we refer to this approach as “prop drilling”?

  - 🙋 Prop drilling is the process of passing props down through multiple levels of components.

  - ☝️ What are the pros and cons of prop drilling?

  - 🙋 Prop drilling makes it simple to keep track of values since the props data only moves in one direction. When the prop drilling is only a couple of levels deep, it is easy to find out exactly where the props are being used. On the other hand, prop drilling can make your code more complex when you have to drill through many levels of components. Prop drilling can also make your code harder to understand if props are renamed halfway through. You may also pass down more props than necessary and create problems when deleting an intermediate component that uses the props.

  - ☝️ Is there another component where we could make the API call?

  - 🙋 We could make the API call from the image component itself, but we avoid doing that since we want the purpose of the image component to be presentational only.

### 6. Instructor Do: Giving Context Slides (10 mins)

- Open the slide deck [10.4: The React Context API](https://docs.google.com/presentation/d/1rHP32SL8aAlHn_0FE-EeD_e6lvERTBwtEpC4UvARdq0/edit?usp=sharing).

- Using the slides as guide and reference, explain the following:

  **Component Lifecycle**: The 3 main phases of the component lifecycle are mounting, updating, and unmounting. Point out that the 2 primary ways of causing a component to re-render are passing it _new_ props or by using the `setState()` method.

  **Prop Drilling**: Prop drilling is the process that you have to go through to get data to parts of the React Component tree. Remind the students that it's often best to keep the state as close to where it's relevant as possible. We can't simply add state to the lowest level component because that would defeat the purpose of using presentational components. Use this question as a segway into the next slide.

  **Presentational vs. Container Components**: We separate the _logic_ and the _looks_ of our application so that our code is easier to understand, test, debug, and maintain. Container components include the logic of the application, which is often stored in the component's state, requiring us to use class components instead of functional components. Presentational components are primarily used for UI elements like layout, and often use stateless functional components (often referred to as "dumb" components) to render their content.

  **ContextAPI**: Oftentimes, applications need an easier way to manage state than passing `props` down several component levels. To avoid adding in unnecessary state, we can use a feature called the React Context API. The React Context API provides a solution to this problem without introducing the complexity of an entire state management library.

  **Providers & Consumers**: Explain that a Context `Provider` is used to wrap a component that has a child component that will need access to the Context Object. Explain that a Context `Consumer` is used to access properties of a Context Object. All `Consumer`s must be descendants of their respective `Provider`s.

  **Loosely Coupled Components**: Make sure to emphasize the importance of keeping components loosely coupled. This is a topic that is important for students to grasp.

  **State Management**: Let students know that they should be mindful of how often they're using the Context API. If they begin to use the Context API rampantly throughout their code, it may be time to consider using Redux or another state management library.

### 7. Instructor Do: useContext Demo (10 mins)

- Run [useContext Demo](../../../../01-Class-Content/20-state/01-Activities/09-Ins_useContext/) by copying the `src` folder into your prepared CRA application. Navigate to http://localhost:3000/ in your browser and demonstrate the following:

  - The application still works the same as the previous iteration, but this time utilizes global state.

- Open [DeveloperContext.js](../../../../01-Class-Content/20-state/01-Activities/09-Ins_useContext/src/utils/DeveloperContext.js) in your IDE and explain the following:

  - We create and export a new Context object initialized with default values:

  ```js
  import React from "react";

  const DeveloperContext = React.createContext({
    name: "",
    mood: "",
    lifeLongLearner: false,
    excitementLevel: 0
  });

  export default DeveloperContext;
  ```

- Open [Developer.js](../../../../01-Class-Content/20-state/01-Activities/09-Ins_useContext/src/components/Developer.js) in your IDE and explain the following:

  - We import the `DeveloperContext` object:

  ```js
  import DeveloperContext from "../utils/DeveloperContext";
  ```

  - The `useContext` Hook replaces the need for a `contextConsumer` that you'll find in the React docs.

  ```js
  const DeveloperInfo = () => {
    const { name, mood, excitementLevel } = useContext(DeveloperContext);

    return (
      <div className="container">
        <h2>Name: {name}</h2>
        <h3>Status: {mood}</h3>
        <h3 style={mood === "determined" ? { opacity: 1 } : { opacity: 0 }}>
          Excitement Level: {excitementLevel}
        </h3>
      </div>
    );
  };
  ```

  - 📝 The `useContext` Hook takes a Context Object as an argument. This means that you cannot forget to import the proper context into your file.

  - 📝 The `useContext` Hook is read only, meaning you cannot set the Context Object by passing in properties.

  - 📝 The `useContext` Hook still requires you to wrap one of its ancestor components with a Context Provider.

  - 🎗️ Just like the Context API, the best use-case for `useContext` is avoiding prop drilling.

- Open [App.js](../../../../01-Class-Content/20-state/01-Activities/09-Ins_useContext/src/App.js)
  and explain the following:

  - We import the `DeveloperContext`:

  ```js
  import DeveloperContext from "./utils/DeveloperContext";
  ```

  - The `DeveloperContext.Provider` still wraps all of the components that will need to consume its state. We pass `developerState` to the Context Provider as the value prop.

  ```js
  <DeveloperContext.Provider value={developerState}>
    <DeveloperInfo />
    <MoodBtns changeMood={changeMood} />
  </DeveloperContext.Provider>
  ```

  - 📝`changeMood` is passed as a prop into `MoodBtns` so that the change in state still happens at the top-level component.

### 8. Students Do: Hooking in Context Activity (15 mins)

- Introduce students to [useContext unsolved](../../../../01-Class-Content/20-State/01-Activities/10-Stu_useContext/Unsolved)

```md
In this activity we will practice using the useContext Hook in React by creating a global state for our articles.

# Instructions

- Replace your React application's src folder with [Unsolved/src](Unsolved/src).

- Start the application in dev mode by running `npm start` in your terminal.

- Open your browser to [localhost:3000](http://localhost:3000) and study the rendered application.

- Update this application to accomplish the following:

- Combine all of the `useState` Hooks that are relevant to the information retreived from the Wikipedia article into a single `useState` Hook.

- Create a Context Object that will be used to store the state of the article called `ArticleContext`.

- Wrap the components that will need access to the Context Object with a Context Provider.

- Update the `SearchResults` component with the `useContext` Hook to to elimintate the need for props.
```

### 9. Instructor Do: Review Hooking in Context Activity (10 mins)

- Open up [useContext Solved Search page](../../../../01-Class-Content/20-State/01-Activities/10-Stu_useContext/Solved/src/pages/Search/index.js) in your IDE.

  - Note that the `articleState` only contains the necessary properties: `title` and `url`.

  ```js
  const [articleState, setArticleState] = useState({
    title: "",
    url: ""
  });
  ```

  - The `articleState` is set after the article is retrieved with a single Hook.

  - Note that we do not have to change the `[search]` provided as the second argument of the `useEffect` Hook because we kept that part of our state isolated.

  ```js
  useEffect(() => {
    API.searchTerms(search)
      .then(res => {
        if (res.data.length === 0) {
          throw new Error("No results found.");
        }
        if (res.data.status === "error") {
          throw new Error(res.data.message);
        }
        setArticleState({
          title: res.data[1][0],
          url: res.data[3][0]
        });
      })
      .catch(err => setError(err));
  }, [search]);
  ```

- Open up [SearchResults component](../../../../01-Class-Content/20-State/01-Activities/10-Stu_useContext/Solved/src/components/SearchResults/index.js).

  - First, we import the context object from its utility file.

  - Then, we pass it into the `useContext` Hook.

  - Remind students that we no longer need to receive props from a parent component and can use the `article` object instead.

  ```js
  import ArticleContext from "../../utils/ArticleContext";
  function SearchResults() {
    const { title, url } = useContext(ArticleContext);
    return (
      <ul className="list-group search-results">
        <li className="list-group-item">
          <h2>{title}</h2>
          <a href={url}>{url}</a>
        </li>
      </ul>
    );
  }
  ```

  - Show that we wrapped all of the components in a Context Provider.

  ```js
  return (
    <ArticleContext.Provider value={articleState} >
    <div>
        <Container style={{ minHeight: "100vh" }}>
          <h1 className="text-center">Search For Anything on Wikipedia</h1>
          <Alert
            type="danger"
            style={{ opacity: error ? 1 : 0, marginBottom: 10 }}
          >
  ...
  )
  ```

### 10. Everyone Do: Break (30 mins)

### 11. Instructor Do: Demo Dynamic Context (10 mins)

- Run [DynamicContext Demo](../../../../01-Class-Content/20-state/01-Activities/11-Ins_DynamicContext/) in your browser to demonstrate the application. Click each button and show that the alert changes for each button.

- Open [AlertContext.js Solved](../../../../01-Class-Content/20-state/01-Activities/11-Ins_DynamicContext/src/AlertContext.js) in your IDE and point out the following:

  - The Context Object has been isolated to its own file.

  - The `.createContext` React method is still used to create a new context, this time using an object instead of a primitive type.

  - The object contains the same keys that we intend to pass to the Consumer with our Provider. Since we know that we'll end up overwriting all of these values, we set up default values that have the same type.

  - There is an empty onClick method since we will need some way of updating our Alert component. For now, `undefined` is returned, since the method will later be provided in `App.js`.

  - 📝 Context API best practices require that we initialize the default values to have a consistent type with the values we intend to provide later. Ex: `onClick` should **not** be initialized as an empty string.

  ```js
  import React from "react";
  // default context object with properties corresponding to Provider values

  const AlertContext = React.createContext({
    display: false,
    theme: "",
    onClick: () => undefined
  });

  export default AlertContext;
  ```

- Open [App.js Solved](../../../../01-Class-Content/20-state/01-Activities/11-Ins_DynamicContext/src/App.js) and point out the following:

  - We import our Home component from pages and our AlertContext object from the components directory.

  ```js
  import * as React from "react";
  import Home from "./pages/Home";
  import AlertContext from "./components/AlertContext";
  ```

  - `App` is a functional component. We initialize `state` with properties that correspond to those we declared in our `AlertContext` object. The `onClick` method takes in the parameters `theme` and `display`. These parameters will later be used to control the class of our Alert component to determine whether or not to display it.

  ```js
  function App() {
    const [pageState, setPageState] = useState({
      display: false,
      theme: "success",
      onClick: (theme, display) => {
        // Remember, the setter method on state does not merge like this.setState does
        // We use the spread operator so that we don't lose our onClick method whenever the state is updated.
        setPageState({ ...pageState, theme, display });
      }
    });
    // App component that provides initial context values
    // Here we are overwritting the context object to be equal to the state of App
    return (
      <AlertContext.Provider value={pageState}>
        <Home />
      </AlertContext.Provider>
    );
  }
  ```

  - We wrap the `AlertContext` object around the `Home` component and pass to the Provider the object stored in state.

  - 📝 We did not pass props to the `Home` component.

- Open [Home.js Solved](../../../../01-Class-Content/20-state/01-Activities/11-Ins_DynamicContext/src/pages/Home.js) in your IDE and point out that there are no references to props.

  ```js
  function Home() {
    document.title = "Dynamic Context";
    return (
      <div>
        <div style={{ textAlign: "center" }}>
          <h1>Dynamic Context API Practice!</h1>
          <h3 className="mb-4">Press a button to get an alert!</h3>
        </div>
        <div style={{ margin: "0 auto" }}>
          <Content />
        </div>
      </div>
    );
  }
  ```

- Open [Content.js Solved](../../../../01-Class-Content/20-state/01-Activities/11-Ins_DynamicContext/src/components/Content.js) and point out the following:

  - We import the `useContext` Hook, the `Alert` component and the `AlertContext` object:

  ```js
  import React, { useContext } from "react";
  import Alert from "./Alert";
  import AlertContext from "./AlertContext";
  ```

  - The Content component returns the `AlertContext` object wrapped around a `div` containing three buttons and the `Alert` component. Using the `useContext` Hook, we inject the values passed from state to the Provider in the `App` component.

  - Each button uses the `onClick` method provided by the `AlertContext`, passing in different strings corresponding with the `className` of the button.

    ```js
    const Content = () => {
      const alert = useContext(AlertContext);
      return (
        <div className="text-center">
          <button
            onClick={() => alert.onClick("success", true)}
            className="btn btn-success mx-3"
          >
            Success
          </button>
          <button
            onClick={() => alert.onClick("warning", true)}
            className="btn btn-warning mx-3"
          >
            Warning
          </button>
          <button
            onClick={() => alert.onClick("danger", true)}
            className="btn btn-danger mx-3"
          >
            Danger
          </button>
          <Alert style={{ opacity: alert.display ? 1 : 0 }} type={alert.theme}>
            You pressed a {alert.theme} button!
          </Alert>
        </div>
      );
    };
    ```

  ```

  * 📝 We pass to the `Alert` component props pulled off the `alert` object.

  ```

- Open [Alert.js Solved](../../../../01-Class-Content/20-state/01-Activities/11-Ins_DynamicContext/src/components/Alert.js) and point out that it accepts props as we expect it to.

```js
const Alert = props => {
  return (
    <div
      role="alert"
      className={`alert alert-${props.type} fade in`}
      style={{ width: "80%", margin: "0 auto", marginTop: 18, ...props.style }}
    >
      {props.children}
    </div>
  );
};
```

- Answer any questions before starting the activity.

### 12. Students Do: Dynamic Context (20 mins)

- Files: [05-Stu_DynamicContext](../../../../01-Class-Content/21-react/01-Activities/05-Stu_DynamicContext)

````md
# Dynamic Context

In this activity we will continue to practice using the Context API in React. This activity continues where the first activity left off. To help strengthen your Context API skills, you will replace as many instances of prop drilling as you can.

## Instructions

- Replace your React application's src folder with [Unsolved/src](Unsolved/src).

- Install axios by running `npm install axios` in your terminal.

- **Recommended:** Add the Bootstrap and Font Awesome CDNs to your application's `index.html` file:

  ```html
  <link
    href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"
    rel="stylesheet"
  />
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.0.0/css/bootstrap.min.css"
  />
  ```

- Start the application in dev mode by running `npm start` in your terminal.

- Open your browser to [localhost:3000](http://localhost:3000) and study the rendered application.

- Update this application to include the following:

  - Add a Context API file to the `utils` folder.

  - Remove prop-drilling from the application and replace it with the Context API.

  - The Context object should include the user information and any methods you might.

  - Use a Context Provider to wrap the components that will need access to the Context.

  - Use Context Consumers to access the properties that are stored in the Context.

### Hints

- The Context object that you will create will need to be the same for both the Provider and the Consumer. How can you ensure that it's the same object without using state?
````

### 13. Instructor Do: Review Dynamic Context (10 mins)

- Open [Dynamic Context solved](../../../../01-Class-Content/20-state/01-Activities/12-Stu_DynamicContext/Solved) in your IDE and point out the following:

  - The solution is designed to showcase how a single Context Object may be used in multiple places. In this example, we primarily use the UserContext in our `CardImg` and `CardTitleText` components to display the user's information. However, we still make use of the consumer in the `CardBtn` component as well to handle the button click.

  - It is worth noting that we only used the consumers as close as possible to the components that needed the data.

  - We import the API, `CardContext` object and CardContainer and Row components.

  ```js
  import React, { Component } from "react";
  import API from "../utils/API";
  import UserContext from "../utils/userContext";
  import CardContainer from "../components/CardContainer";
  import Row from "../components/Row";
  ```

  ```js
  const [users, setUsers] = useState([]);
  const [user, setUser] = useState({});
  const [userIndex, setUserIndex] = useState(0);

  // When the component mounts, a call will be made to get users.
  useEffect(() => {
    loadUsers();
  }, []);

  function loadUsers() {
    API.getLanguagesList()
      .then(languages => {
        API.getUsersByLanguage(languages[0]).then(users => {
          setUsers(users);
          setUser(users[0]);
        });
      })
      .catch(err => console.log(err));
  }
  ```

  - The `UserContext` Provider passes in each state variable as properties of an object to the Context Object as the default `value` prop. This includes the `handleBtnClick` method that our button will use.

  ```js
  return (
    <UserContext.Provider value={{ user, users, handleBtnClick }}>
      <div>
        <h1 className="text-center">Welcome to LinkedUp</h1>
        <h3 className="text-center">Click on the arrows to browse users</h3>
        <Row>
          <CardContainer />
        </Row>
      </div>
    </UserContext.Provider>
  );
  ```

- Open [UserContext.js Solved](../../../../01-Class-Content/20-state/01-Activities/12-Stu_DynamicContext/src/utils/UserContext.js) in your IDE and point out the following:

  - The User Context was added to a separate file in order to decouple it from any particular component.

  - The user property values are initialized to `""` to demonstrate that they will be overwritten by the new values given by the Provider.

  ```js
  import React from "react";

  const UserContext = React.createContext({
    login: "",
    language: "",
    image: "",
    handleBtnClick: () => {}
  });

  export default UserContext;
  ```

  - 📝 Context API best practices require that we initialize the default values to have a consistent type with the values we intend to provide later. Ex: `handleBtnClick` should **not** be initialized as an empty string.

- Ask the students the following question:

  - ☝️ How many of you created separate contexts for the images and titles?

  - 🙋 While having multiple providers may be overkill for this small application, let the students know that in a larger application, there could be several component layers separating related components. In those situations, having multiple providers would be better than passing a single context object through multiple levels of components.

### 14. Instructor Do: Demo Multiple Contexts (10 mins)

- Walk students through the process of using multiple context objects.

  - Point out that before creating multiple context objects, students should think about why it might not always suit them to only use one.

  - The Context Object for a theme may be set instantly within a stateless component, whereas other properties may rely on AJAX calls in a stateful component.

  - Creating multiple Context Objects can help separate concerns, preventing unnecessary pieces of data from being passed to consumers that may not need access to them.

  - Providers must wrap the parents of whichever components need access to context.

- Open up `App.js` point out the following:

  - There's a new `getUserToken` method that returns a dummy value.

  - We've split our state into two objects. This makes it much easier to separate the two contexts.

  - 🗒Note that in `setAlert`, we used the spread operator since setters do not automatically merge with the previous state object.

```js
import React, { useState } from "react";
import Home from "./pages/Home";
import ThemeContext from "./components/ThemeContext";
import UserContext from "./components/UserContext";
import AlertContext from "./components/AlertContext";

function App() {

  const [user, setUser] = useState({
    name: "Bob",
    getUserToken: getUserToken
  })

  const [alert, setAlert] = useState({
    display: false,
    theme: "success",
    onClick: (theme, display) => setAlert({...alert, theme, display})
  })

  function getUserToken() {
    return "SampleToken123";
  }
```

- In our `return` block, 3 providers are returned, but it doesn't matter if one Provider wraps another, as long as they both wrap an ancestor of the element with the `useContext` Hook.

- The Alert and User Providers receive state objects as their value, while the Theme Provider receives a string literal.

```js
<AlertContext.Provider value={alert}>
  <UserContext.Provider value={user}>
    <ThemeContext.Provider value={"dark"}>
      <Home />
    </ThemeContext.Provider>
  </UserContext.Provider>
</AlertContext.Provider>
```

- Take a moment to go over `NavLink.js`.

  - Bring up that `useContext` is once again being used at the closest possible element that it can to avoid prop drilling.

  ```js
  const NavLink() {
    const { name } = useContext(UserContext);
    return (
      <div style={{ marginLeft: "40px" }}>
        <h2>Welcome {name}!</h2>
      </div>
    );
  }
  ```

- Address any lingering questions students have.

### 15. Student Do: Multiple Contexts (20 mins)

- Files: [14-Stu_MultipleContexts](../../../../01-Class-Content/20-State/01-Activities/14-Stu_MultipleContexts)

````md
# Multiple Contexts
In this activity we will continue to practice using the Context API in React. This activity continues where the last activity left off. To help strengthen your Context API skills, you will introduce another Context Object to your application.

## Instructions

* Replace your React application's src folder with [Unsolved/src](Unsolved/src).

* Install axios by running `npm install axios` in your terminal.

* **Recommended:** Add the Bootstrap and Font Awesome CDNs to your application's `index.html` file:

  ```html
  <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.0.0/css/bootstrap.min.css" />
  ```

* Start the application in dev mode by running `npm start` in your terminal.

* Open your browser to [localhost:3000](http://localhost:3000) and study the rendered application.

* Update this application to include the following:

  * Create a separate Context Object for the languages.

  * Update the application so that data pertaining to the user is stored in a nested object within the Gallery state.

  * Add the ability to select a different language.

  * Ensure that data pertaining to the language is stored in a different nested object within the Gallery state.

  * If a new language is selected, the card should be updated with the information of the first user of the selected language.

### Hints

* Try to get the user functionality working before moving on to the language selector.

* Make sure you call `loadUser` whenever the language changes.

````

### 16. Instructor Do: Review The Gallery Multiple Contexts (10 mins)

- Open [14-Stu_MultipleContexts/Solved/src/utils/userContext.js](../../../../01-Class-Content/20-State/01-Activities/14-Stu_MultipleContexts/Solved/src/utils/userContext.js) in your IDE and go over the following:

  - Point out that the properties of `UserContext` are only relevant to the user information. The `language` property is not referring to the current selected language, but instead, it refers to the user's `language` property.

  ```js
  import React from "react";

  const UserContext = React.createContext({
    login: "",
    language: "",
    image: "",
    handleBtnClick: () => {}
  });

  export default UserContext;
  ```

  - Open [14-Stu_MultipleContexts/Solved/src/pages/Gallery.js)](../../../../01-Class-Content/20-State/01-Activities/14-Stu_MultipleContexts/Solved/src/pages/Gallery.js) in your IDE.

  - Point out that **both** the `UserContext.Provider` and the `LanguageContextProvider` wrap the contents of the entire page. Even though the `LanguageSelector` does not use the `UserContext`, there is no harm in wrapping components with Providers they do not need.

  - Also note that the User Context Provider wraps the Language Context Provider. It doesn't matter which provider wraps the other, as long as they both wrap an ancestor of the component that will use the `useContext` Hook.

  - We create language and user objects by individually passing the variables we declared at the top of the file.

  - We don't need to contain the indexes in our context objects since they are only needed in the `Gallery.js` file.

  ```js
  return (
    <UserContext.Provider value={{ user, users, handleUserBtnClick }}>
      <LanguageContext.Provider
        value={{ language, languages, handleLanguageBtnClick }}
      >
        <div>
          <h1 className="text-center">Welcome to LinkedUp</h1>
          <h3 className="text-center">Click on the arrows to browse users</h3>
          <LanguageSelector />
          <Row>
            <CardContainer />
          </Row>
        </div>
      </LanguageContext.Provider>
    </UserContext.Provider>
  );
  ```

  - Maintaining large state objects can be complex, often involving the use of the `...` spread operator. In this use case, it was reasonable to create separate variables for each property of each context object.

  - 🗒 Note that we don't need to create states for the `handleBtnClick` functions in each context object, since they will never change.

  ```js
  const [languages, setLanguages] = useState([]);
  const [language, setLanguage] = useState("");
  const [languageIndex, setLanguageIndex] = useState(0);

  const [users, setUsers] = useState([]);
  const [user, setUser] = useState({});
  const [userIndex, setUserIndex] = useState(0);
  ```

- Address any lingering questions students have.

### 17. Students Do: Work on HW (30 mins)

### 18. End

* Note that there is an extra `15-Bonus_ClassContext` example activity for students who are curious about using the Context API in regular class components.

### Lesson Plan Feedback

How did today’s lesson go? Your feedback is important. Please take 5 minutes to complete this anonymous survey.

[Class Survey](https://forms.gle/nYLbt6NZUNJMJ1h38)
