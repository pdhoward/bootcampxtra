## 10.5 Lesson Plan - React.js / Intro to Project #3 <!--links--> &nbsp; [⬅️](../04-Day/04-Day-LessonPlan.md) &nbsp; 

## Overview

In this class, students will learn the benefits of declarative Redux-style code and implement an architecture that mirrors Redux with a store, reducer, and actions.

## Instructor Notes

* `Summary: Complete activities 16-22 in Unit 20`.

* You should scaffold out a React application with Create React App at the beginning of class and suggest students do the same. The activities we go over today will only include the applications `src` folder which you should replace in your React app's boilerplate to avoid repetitive installs. It's recommended that you completely restart the dev server between activities.

* Today's lesson will rely heavily on Redux concepts. It is recommended that you spend some time getting familiar with the activities before class starts.

## Learning Objectives

* Transform an app that manages state in Container components into one that follows a Redux pattern.

* Identify the appropriate time to make a React app use Redux or follow a similar design pattern.

* Grasp general concepts of declarative, pure, immutable functions, in a way that is abstracted from Redux or any particular library.

* Implement a Redux-like store in a React app.

## Slides

[10.5: State Management with the Store](https://docs.google.com/presentation/d/104SKRoUtY9whNLEVqH_8_6MX_OHmbXQfO9qpwypi9s8/edit?usp=sharing)

## Time Tracker

[State Management with the Store](https://docs.google.com/spreadsheets/d/1RXwsq15tBqtAc20Y8OJVRwnf7monRBQWR9f2uACN0SA/edit?usp=sharing)

- - -

### 1. Instructor Do: Introduction (10 mins)

* Welcome students to their final day of React before project week! Let them know that in the first half of the class, they will learn about Redux concepts and practice applying them in activities. The second half of the class will be dedicated to creating a mini-project that will involve them creating their very own CMS (Content Management System) using Redux patterns. 

* Ask the students the following questions:

  * ☝️ What were some of the pain points of working with context and hooks?

  * 🙋 Managing many different contexts and hooks can gets complex very quickly.

  * ☝️ What is the difference between mutability and immutability, and what are the advantages of each?

  * 🙋 **Mutable** objects can have their properties changed or _mutated_, whereas **Immutable objects** can not. Typically immutable objects help prevent your application from getting over-complicated. They often make it easy to identify _why_ the state changed, since every time an object needs to change, a new object has to be explicitly created. This also tends to make testing your components significantly easier. 

  * ☝️ How might we manage state when if there are several different objects to keep track of, and several components that have the ability to update them?

  * 🙋 We can create a single global state that contains all of the states needed throughout our application.

* Open [20.3: State Management with the Store](https://docs.google.com/presentation/d/1rRxhoiKoa6op_sE3Z0koGxq6SSy97UQHe-SrnLmvnL8/edit?usp=sharing)

* **Pure functions vs impure functions**: Pure functions are straightforward with singular purposes.
They do not have any side effects within them. Whenever data needs to be modified, it is not mutated. Impure functions tend to have multiple purposes. The might contain database or network calls.

* **The impure function** here modifies its argument instead of creating a new argument.

* **The pure function** has a singular purpose, making it more developer-friendly.

* **Redux** is a state management library that helps organize the state of complex applications. While Redux requires a lot of boilerplate code, its utility skyrockets as applications get more complex.

* **The principles of Redux**: 

  * The first premise of Redux is that every stateful aspect of your application can be represented by a single JavaScript object known as the state tree.

  * The second principle of Redux is that the state tree is read only. This means that in order to change the state tree, you need to dispatch an action. The action describes the change that the state will undergo in a declarative manner.

* **Actions, reducers, and store**: 

  * **Actions** are declarative objects that define what the store should do to the state.
  * **The Reducer** takes the previous state and action, then returns a new state. It is important that the reducer is a pure function. 
  * **The Store** servers as the global state. It gives different pieces of our application access to data held in the state and the reducer function.

### 2. Instructor Do: useReducer Demo (10 mins)

* Run [16-Ins_useReducer](../../../../01-Class-Content/20-state/01-Activities/16-Ins_useReducer/) by copying the `src` folder into your prepared CRA application. Navigate to http://localhost:3000/ in your browser and demonstrate the following:

  * The application is similar to earlier click counter demos

  * Clicking the `Add` or `Subtract` buttons increments and decrements the numerical value accordingly

* Open [App.js](../../../../01-Class-Content/20-state/01-Activities/16-Ins_useReducer/src/App.js) in your IDE and explain the following points:

  * We import the `useReducer` method from `react`.

  ```js
  import React, { useReducer } from 'react';
  ```

  * Within our `App` component, we invoke the `useReducer` method, and, using array destructuring, capture the returned value in `count` and `dispatch` variables.

  ```js
  const [count, dispatch] = useReducer((state, action) => {
    if(action === "add") {
      return state + 1;
    } else if(action === "subtract") {
      return state - 1;
    } else {
      return state;
    }
  }, 0)
  ```

  * 🔑 Similar to the `reduce` array method, `useReducer` expects to receive two arguments, a function with `state` and `action` values, and an initial state value, which we set here to `0`.

  * When a button is clicked, `dispatch` is passed either an `add` or `subtract` value and, based on the conditional logic in the anonymous function passed to `useReducer`, it will increment or decrement state accordingly.

  ```js
  return (
    <div className="App">
      <h1>This time... With Redux!</h1>
      <button className="btn btn-success mt-5 mb-5" onClick={()=> dispatch('add')} >Add</button>
        <div>{count}</div>
      <button className="btn btn-danger mt-5" onClick={()=> dispatch('subtract')} >Subtract</button>
    </div>
  );
  ```

### 3. Students Do: useReducer (15 mins)

* Introduce [useReducer/Unsolved](../../../../01-Class-Content/20-state/01-Activities/16-Stu_useReducer/Unsolved)

```md
In this activity we will practice using the `useReducer` Hook.

# Instructions

* Replace your React application's src folder with [Unsolved/src](Unsolved/src).

* Start the application in dev mode by running `npm start` in your terminal.

* Open your browser to [localhost:3000](http://localhost:3000) and study the rendered application.

* Update this application to accomplish the following:

* Create a `useReducer` Hook that checks for two different cases (one for each dog).

* The second argument in `useReducer` should be an object with two properties.

* Each case should return a _new_ state object with the updated properties.

* Add the necessary code to display the number of praises that each dog has.

* When a dog is praised, an action should be dispatched that contains an identifier so that the correct dog's praises can be updated.

```

### 4. Instructor Do: Review useReducer (10 mins)

* Open [App.js solved](../../../../01-Class-Content/20-state/01-Activities/16-Stu_useReducer/Solved/src/App.js) and explain the following:

  * This application keeps track of how many times you've praised each dog.

  * Our reducer allows for two different actions. For simplicity's sake, we've hard-coded `praiseHarry` and `praiseHermione` as separate actions.

  * Ask the students the following questions:

  * ☝️ How might we rewrite our reducer so that any number of dogs can be praised?

  * 🙋 We could create a single case that handles all actions in a similar manner. This way, the initial state would also have to into an array, so that the dogs would be easy to iterate through.

  * ☝️ What logic in our reducer is repeated that we might be able to extract?

  * 🙋 The return statements are almost identical. A more scalable solution might update a `praises` property on a `dog` object. The action would contain a unique identifier so that the proper item in the state array could be updated.

  * 🔑 This time, the initial state value is set to be an _object_ that keeps track of how many praises each dog has.

  ```js
  const [state, dispatch] = useReducer((state, action) => {
      if(action === "praiseHarry") {
        return { ...state, HarryPraises: state.HarryPraises + 1 };
      } else if(action === "praiseHermione") {
        return { ...state, HermionePraises: state.HermionePraises + 1 };
      } else {
        return state;
      }
    }, { HarryPraises: 0, HermionePraises: 0 });
  ```

  * To display each dog, we use the `map` method on our `dogs` array and return a div with a unique key. In this case we can use `item.name` since there are only two dogs. In a larger list of dogs, it would be better to use a unique id.

  * Point out that the code that displays how many times each dog has been praised uses the bracket notation to dynamically grab the dogs name.

  * 📝This workaround is only necessary because our reducer state is an object. If the reducer state was an array, we may be able to utilize the `index` property in `map`.

  ```js
  {
  dogs.map((item) => (
    <div key={item.name} className="card mx-auto col-4">
      <img className="card-img-top" src={item.image} alt={item.name} />
      <div className="card-body">
        <h4 className="card-title">{item.name}</h4>
        <p className="card-text">{item.name} has been praised {state[item.name+"Praises"]} times!</p>
        <button className="btn btn-primary" onClick={() => dispatch("praise" + item.name)} >Praise</button>
      </div>
    </div>
  )
  )}
  ```

### 5. Instructor Do: useRef Demo (10 mins)

* Run [useReducer/Solved](../../../../01-Class-Content/20-state/01-Activities/18-Ins_useRef/Solved) by copying the `src` folder into your prepared CRA application. Navigate to http://localhost:3000/ in your browser and demonstrate the following:

  * Clicking the increment button still works as in the previous demo

  * Entering a new value in the input field updates the counterimmediately.

* Open [App.js solved](../../../../01-Class-Content/20-state/01-Activities/18-Ins_useRef/Solved) in your IDE and explain the following:

  * `useRef` is a Hook that allows you to use the `ref` attribute on an input element. To access the value from a specific input element, we must attach its reference to our new `useRef` hook. The value of the input field is stored in the `current.value` property.

  ```js
  const inputRef = useRef();
  const [count, dispatch] = useReducer((state, action) => {
    switch (action) {
    case "add":
      return state + 1;
    case "subtract":
      return state - 1;
    case "change":
      // convert the value from the input into an integer
      const newCount = parseInt(inputRef.current.value);

      // only update the count if the value is numeric
      if (isNaN(newCount)) {
        return state
      }
      return newCount;
    default:
      return state;
    }
  }, 0);
  ```

  * Now that we've added another conditional to our reducer, it makes sense to convert it into a switch case statement for better readability.

  * We _did not_ use the `onChange` handler. Although we could have used `onChange`, we opted to make our input field _uncontrolled_, since we only need the value from the field when the form is submitted. Not only does this mean we needed to write less code, but it also means that our component will not be unnecessarily subscribed to a value that is frequently changing.

  ```js
  <input className="form-control w-25 mx-auto mt-5" placeholder="Type new value..." ref={inputRef} />
  ```

### 6. Students Do: useRef (15 mins)

```md
In this activity we will practice using the `useRef` Hook by creating a Todo list application.

# Instructions

* Replace your React application's src folder with [Unsolved/src](Unsolved/src).

* Start the application in dev mode by running `npm start` in your terminal.

* Open your browser to [localhost:3000](http://localhost:3000) and study the rendered application.

* Update this application to accomplish the following:

* Create a `reducer` that handles Todo creation.

* This time, instead of passing a string as an argument to the `dispatch` method, `action` should be an object with the following properties:

  * `type`: The string that will be used to identify each action.

  * `name`: The string that is passed in through your input field.

* The second argument in `useReducer` should be an empty array.

* Each case should return a _new_ array with the updated properties.

* **BONUS**: Update the component so that there is a button next to each list item called `remove` that removes that Todo from the list. You will need to create a new case in your reducer method that returns a _new_ array without the removed Todo. ***HINT***: You may want to pass a unique identifier as an argument in the `dispatch` method.

```

### 7. Instructor Do: Review useRef (10 mins)

* Run [useReducer/Solved](../../../../01-Class-Content/20-state/01-Activities/19-Stu_useRef/Solved) by copying the `src` folder into your prepared CRA application. Navigate to http://localhost:3000/ in your browser and demonstrate the following:

  * Entering a task in the input field and clicking on `Add to list` creates a new Todos

  * Clicking the `Remove` button on any item removes it from the list

* Open [App.js Solved](../../../../01-Class-Content/20-state/01-Activities/19-Stu_useRef/Solved/src/App.js) in your IDE and explain the following points:

  * We initialize a variable, `inputRef` with `useRef`.

  ```js
  const inputRef = useRef();

  const [items, dispatch] = useReducer((state, action) => {
    switch (action.type) {
    case "add":
      return [
        ...state,
        {
          id: state.length * Math.random(),
          name: action.name
        }
      ];
      // Bonus: Remove a todo from the list.
    case "remove":
      return state.filter((_, index) => {
        return index !== action.index;
      });
    default:
      return state;
    }
  }, []);
  ```

  * Our switch case checks the `type` property on the action object.

  * In the `add` case, we return a _new_ array that contains all of the items in the previous state _and_ a new object made up of the `name` property from the action object and a unique id.

  * In order to fake a unique id we generate one from the length of the array. In a full-stack application, the id would be a unique value created by the database.

  * The `remove` case returns a new array that contains every item from the previous array _except_ for the item that should be removed.

  * 📝The `filter` method returns a _new_ array instead of modifying the existing array. This is a good opportunity to remind students that mutations should be avoided inside reducers.

  * `_` is used as a placeholder since we do not intend to use the first argument in the `filter` callback.

  * `inputRef` is attached to the `ref` attribute on our input field.

  * In the `handleSubmit` function, we dispatch a new action that passes the `inputRef.current.value` to our reducer. Remember to access the `current.value` property on the `inputRef` object.

  ```js
    const handleSubmit = (e) => {
    e.preventDefault();
    dispatch({
      type: "add",
      name: inputRef.current.value
    });
    inputRef.current.value = "";
  }

  return (
    <div className="container text-center">
      <h1>Create a Todo List!</h1>
      <form className="form-group mt-5" onSubmit={handleSubmit}>
        <input className="form-control" ref={inputRef} placeholder="Start typing what you need to do..." />
  ```

### 8. Instructor Do: Store Demo 🏬 (10 mins)

* Run [Ins_Store](../../../../01-Class-Content/20-state/01-Activities/20-Ins_Store) by copying the `src` folder into your prepared CRA application. Navigate to http://localhost:3000/ in your browser and demonstrate the following:

  * As before, clicking buttons increments or decrements a counter. This time, however, we are going to keep the counter data in a global state object called the **store**.

* Open the `src` folder in your IDE and point out the following:

  * The application has been separated into multiple files so that we create a flow that is more similar to Redux.

* Open [Ins_Store](../../../../01-Class-Content/20-state/01-Activities/20-Ins_Store/src/App.js) in your IDE and explain the following points:

  * From our `GlobalState` util, we import a `CountProvider`. We also import a `Count` component.

  ```js
  import React from "react";
  import { CountProvider } from "./utils/GlobalState";
  import Count from "./components/Count";
  import "./App.css";
  ```

  * Inside the `App` component, we wrap the children of `App` in a the `CountProvider`.

  ```js
  const App = () => {
    return (
      <CountProvider>
        <div className="App">
          <Count />
        </div>
      </CountProvider>
    );
  }
  ```
* Ask the students the following question(s):

  * ☝️ If we are importing an object named `CountProvider`, what do you think we will find in `GlobalState`?

  * 🙋 Based on the name `CountProvider`, we can expect to find `createContext` used to create the exported object.

  * ☝️ If `GlobalState` is performing the function its name suggests, what else might we find in it?

  * 🙋 We can find `GlobalState` in any component of our application that will need access to the global state.

* Open [Ins_Store](../../../../01-Class-Content/20-state/01-Activities/20-Ins_Store/src/utils/GlobalState.js) in your IDE and explain the following points:

  * This file contains what is commonly referred to as the **store**. The store is in charge of handling all of the actions that are passed to it from any component in the application. Once a reducer handles an action, it creates a _new_ state and passes it through the Provider to the global Context object.

  * At the top of the file, we create a new Context object. We then use object destructuring so that we may refer to its Provider object as `Provider`.

  ```js
  const CountContext = createContext();
  const { Provider } = CountContext;
  ```

  * Again, we are checking the `type` property on the action that this reducer will receive from a dispatch. This time, if the action type isn't one of the two cases, we will throw an Error so that we can quickly identify when we've incorrectly implemented an action.

  ```js
    const reducer = (state, action) => {
      switch (action.type) {
      case "add":
        return { count: state.count + 1 };
      case "subtract":
        return { count: state.count - 1 };
      default:
        throw new Error(`Invalid action type: ${action.type}`);
      }
  };
  ```

  * The `CountProvider` function takes in a value argument, which we set to be `0` by default, and the properties from our `props` object. It then returns a Provider with `state` and `dispatch` passed through to the Context object.

  ```js
  const CountProvider = ({ value = 0, ...props }) => {
    const [state, dispatch] = useReducer(reducer, { count: value });

    return <Provider value={[state, dispatch]} {...props} />;
  };
  ```

  * 📝 The `reducer` method is set up, abstracted from the `useReduce` Hook. We don't actually attach it to the `useReducer` Hook until we set up the `CountProvider`. This means that if you want to, you can use the same reducer in multiple providers that have different initial states.

  * `useCountContext` is created so that we will not have to import both the `useContext` Hook and the `CountContext` object every time we want to use the `CountContext`.

  ```js
  const useCountContext = () => {
    return useContext(CountContext);
  };
  ```

  * Lastly, we export `CountProvider` and `useCountContext`

  ```js
  export { CountProvider, useCountContext };
  ```

### 9. Students Do: Store 🏬 (20 mins)

Introduce students to [Store unsolved](../../../../01-Class-Content/20-state/01-Activities/21-Stu_Store/Unsolved).

```md
In this activity we will create a store that contains the global state and a reducer. We will also add some functionality to our Todo list.

# Instructions

* Replace your React application's src folder with [Unsolved/src](Unsolved/src).

* Start the application in dev mode by running `npm start` in your terminal.

* Open your browser to [localhost:3000](http://localhost:3000) and study the rendered application.

* Update this application to accomplish the following:

* Separate the Form and List parts of the application into two different components. Place them both in a folder called `components`.

* Create a folder called `utils` and within it, create a single file that will be the application **store**. This file should export a Provider that will be used to wrap the entire application and a `useTodoContext` object that will be used to inject the Context into any component that needs access to the store.

* Add an action handler that will allow users to prioritize a Todo.

* Make sure your application works properly before moving on.

* Add numbering to the list so that each item has its index next to the Todo title. If items are removed from the array, the index should update to reflect the changed state.

* Change the `List` component so that each Todo has a button next to it that dispatches the `prioritize` action.

* Make the necessary changes so that the title of the Todo will appear in bold if it is prioritized.  

```

### 10. Instructor Do: Review Store 🏬 (10 mins)

* Run [Store Solved](../../../../01-Class-Content/20-state/01-Activities/21-Stu_Store/Solved) by copying the `src` folder into your prepared CRA application. Navigate to http://localhost:3000/ in your browser and demonstrate the following:

  * Add Todos to the list with the input field

  * The remove functionality still works as expected

  * If the `prioritize` button is clicked, the text of the Todo is bolded

* Open `/src/App.js` in your IDE and explain the following points:

  * The two components `Form` and `List` are wrapped in a `TodoProvider`. It is very important that we wrap the entire application with our Provider. Without the Provider, `useTodoContext` will not work in any of the components that it's injected into.

  ```js
  <div className="container">
    <TodoProvider>
      <Form />
      <TodoList />
    </TodoProvider>
  </div>
  ```

* Open [GlobalState.js](../../../../01-Class-Content/20-state/01-Activities/21-Stu_Store/Solved/src/utils/GlobalState.js) in your IDE and point out the following:

  * The `TodoContext` is provided with default values whose types are consistent with the type we intend to provide later. While this is not required, it is considered best practice.

  ```js
  const TodoContext = createContext({
    id: "",
    name: "",
    priority: false
  });
  ```

  * Using object destructuring, we create a new variable for the Provider.

  ```js
  const { Provider } = TodoContext;
  ```

  * The `reducer` function uses a switch case to handle the action that will be passed to `dispatch`. Each case returns a new array. Within the "prioritize" case `map` method, we use `Object.assign` because it creates a _new_ object from the old Todo object and the new value of priority. Both of these methods are essential to ensure that our state stays immutable.

  * `priority: !item.priority` sets the priority value to be the opposite of what it previously was. This means that when the `prioritize` button is pressed, the value is _toggled_ rather than explicitly set.

  ```js
  const reducer = (state, action) => {    
    switch (action.type) {
      case "add":
        return [
          ...state,
          {
            id: state.length * Math.random(),
            name: action.name
          }
        ];
      case "remove":
        return state.filter((_, index) => {
          return index !== action.index
        });
      case "prioritize":
        return state.map((item, index) => {
          if(index === action.index ) {
            return Object.assign({}, item, {
              priority: !item.priority
            })
          }
          return item;
        });
      default:
        return state;
    }
  };
  ```

  * The `TodoProvider` returns a `<Provider>` element that we will use to wrap our entire application with. 

  * We create this file in our `GlobalState` so that it can provide access to the `useReducer` method to any component in our application.

  ```js
  const TodoProvider = ({ value = [], ...props }) => {
    const [state, dispatch] = useReducer(reducer, []);

    return <Provider value={[state, dispatch]} {...props} />;
  }

  const useTodoContext = () => {
    return useContext(TodoContext);
  }

  export { TodoProvider, useTodoContext };
  ```

* Open [Form.js](../../../../01-Class-Content/20-state/01-Activities/21-Stu_Store/Solved/src/components/Form.js) in your IDE and point out the following:

  * We import `useRef` from `react` and `useTodoContext` from our store.

  ```js
  import React, {useRef} from 'react';
  import {useTodoContext} from "../utils/GlobalState";
  ```

  * Within the `Form` component, we create a a new `useRef`, `inputRef`, and call `useTodoContext` so that we can dispatch an action to our `Todo` reducer.

  * 📝 Since this form is not responsible for displaying any information from the state, the first variable from our destructured Context array can be `_`.

  ```js
  const Form = () => {
    const inputRef = useRef();
    const [_, dispatch] = useTodoContext();

    ...

  }
  ```


  * `dispatch` is used within `handleSubmit` to dispatch an action that will update the store with each Todo that is created using the `inputRef` we created above.

  ```js
  const handleSubmit = (e) => {
    e.preventDefault();
    dispatch({
      type: "add",
      name: inputRef.current.value
    });
    inputRef.current.value = "";
  }
  ```

  * The `input` element has a ref attribute of `inputRef` so that we can use the `useRef` Hook to easily grab the value from our input field upon form submission.

  * The `form` element has an `onSubmit` callback of `handleSubmit`.


  ```js
  return (
    <div>
      <h1>Create a Todo List!</h1>
      <form className="form-group mt-5" onSubmit={handleSubmit}>
        <input className="form-control" ref={inputRef} placeholder="Start typing what you need to do..." />
        <button className="btn btn-success mt-3 mb-5" type="submit">Add to List</button>
      </form>
    </div>
  );
  ```

* Open [TodoList.js](../../../../01-Class-Content/20-state/01-Activities/21-Stu_Store/Solved/src/components/TodoList.js) in your IDE and explain the following:

  * We again import our store so that we can use the `TodoContext`.

  ```js
  import {useTodoContext} from "../utils/GlobalState";
  ```
  * Within our `TodoList` component, we use the `index` parameter from our `state.map` callback to number each Todo on the list. Each item contains two buttons with `onClick` methods returning `dispatch`. We pass to `dispatch` either "prioritize" or "remove", respectively, and the index of the list item.

  ```js
  const TodoList = () => {
    const [state, dispatch] = useTodoContext();
    return (
      <div>
        <h4>My Todo List:</h4>
          <ul className="list-group">
            {state.map((item, index) => (
              <li className="list-group-item col-12" key={item.id}>
                <button className="btn btn-warning mr-4" onClick={() => dispatch({ type: "prioritize", index })}>Prioritize</button>
                <button className="btn btn-danger mr-4" onClick={() => dispatch({ type: "remove", index })}>
                  X Remove
                </button>
                {index}:<span className={item.priority ? "font-weight-bold" : ""}> {item.name}</span>
              </li>
              ))}
            </ul>
        </div>
      );
    }
  ```

  * `<span className={item.priority ? "font-weight-bold" : ""}>` uses a ternary operator to determine whether or not to bold the Todo.


### 11. Break (30 mins)

### 12. Instructor Do: Demo Mini-Project (5 mins)

* Open another tab in your terminal and run `mongod`.

* Return to the tab with the [GlobalState.js](../../../../01-Class-Content/20-state/01-Activities/22-Stu_Mini_Project/Solved/) directory open and run `npm install` followed by `npm start`.

* Open [http://localhost:3000](http://localhost:3000) in your browser and explain the following:

  * All of our posts can be viewed on the [http://localhost:3000](http://localhost:3000) page.

  * Start by creating a blog post. Show students that the title and body reset, but the screen name does not.

  * Point out that for a brief second, `Loading...` appears in the top right section of the navigation bar. During this time, the `Save Post` button is also disabled.

  * Point out that there are no favorites yet on the right hand side.

  * Click on `View all posts`, then click on the post that you just created.

  * This will take you to another page where you can view the details of the post.

  * Click on the `Favorite` button, then navigate back to the home page. The post you just selected has been added to the favorite posts list. Show the students that you can remove a post from the favorite posts list by clicking the red `x`. 

  * Favorites are only stored in the `store`, not the database.

### 13. Students Do: Mini-Project (60 mins)

* Introduce students to the [Mini-Project](../../../../01-Class-Content/20-state/01-Activities/22-Stu_Mini_Project/Unsolved/)

```md
# Custom CMS

In this activity we will create a CMS (Content Management System) that allows users to upload blog posts. Users will also be able to view blog posts by other authors and filter them based on category. We will use the Context API to manage the application state globally, adhering to a design pattern that closely follows Redux. Although very complex applications may have several stores, we are going to keep it simple and store all stateful data in a single global store.

## Instructions

* Open the [Unsolved](Unsolved) folder and install dependencies by running `npm install` at the project root.

* Open another tab in your terminal and run `mongod`.

* Start the app by running `npm start` from the project root.

* Once the app starts open your browser to [localhost:3000](http://localhost:3000).

* Open [App.js](Unsolved/client/src/App.js).

* There are 4 main sections in this application:

  * A section that allows you to create new posts.

  * A section that lists all of the posts.

  * A detail page to view the contents of an individual post.

  * (BONUS): A Favorites page that lists all of your favorite posts.

### Part 1

* Set up a store for your application with support for the following actions:

  1. UPDATE_POSTS: Updates the state with the latest posts.

  2. ADD_POST: Adds a post to the posts array.

  3. REMOVE_POST: Removes a specified post from your posts array.

  4. SET_CURRENT_POST: Sets the current post in the store. This action will only be dispatched from the detail page.

  5. LOADING: Indicates when the app is saving a post or retrieving posts from the database.

* Since this application is larger than our previous applications, we are going to create a separate file for our action types. By doing this, we will be able to import the actions into any component we would like, thus reducing the chance of mispelling them thanks to the autocomplete feature in our IDE.

* In `client/src/utils`, create a file named `actions.js`.

* Inside the actions file, export a `const` for each action type so that you will be able to easily import it into whichever file you would like.

  * Ex: `export const GET_POSTS = "GET_POSTS";`

* In `client/src/utils/GlobalState.js`, create a store for your application with with a reducer that can handle each action type.

* Export a `StoreProvider` and `useStoreContext` Hook.

* In `App.js`, wrap your entire application with the `StoreProvider`.

### Part 2

* Open up `client/src/components/CreatePostForm` and add the functionality for creating new posts.  

* Open up `client/src/components/PostsList` and add the functionality for getting the latest posts _and_ deleting a single post.

* Open up `client/src/pages/Detail.js` and add the functionality for viewing a selected post.

* 📝 With every API call, dispatch the `LOADING` action. Then make the API call. Dispatch your action within the `then` method.
 
*  Update the `UPDATE_POSTS`, `SET_CURRENT_POST`, and `ADD_POST` action handlers so that the `loading` property on the state changes to `false`.

* In `client/src/components/Nav`, use the global store to make the `Loading...` text appear whenever the global state is loading.

* In `client/src/components/CreatePostForm`, update the submit button so that it is `disabled` if the global state is loading.

### BONUS

* In `client/src/pages/Detail.js`, add a `❤️ Add to Favorites` button that adds the blog post to a `favorites` array in the store.

* Here are some actions you might choose to use:

  1. UPDATE_FAVORITES: Updates the state with the latest favorites.

  2. ADD_FAVORITE: Adds a favorite to the favorites array.

  3. REMOVE_FAVORITE: Removes a specified post from your favorites list.

### Hints

* You will **not** have to modify any files that are not in the `client` folder.

* If you are stuck or running into errors, try to `console.log` the `action` in your store. Try to make sure that the reducer is functioning as expected before looking at your component.

* Use the `utils/GlobalState.js` file from the previous activity to help scaffold the store.

* Ask the instructor or a TA if you're having difficulty understanding any of the activity requirements.

```

### 14. Instructor Do: Review Mini-Project (15 mins)

* Start by opening [actions.js](../../../../01-Class-Content/20-state/01-Activities/21-Stu_Store/Solved/client/src/utils/actions.js) in your IDE.

  * First, we exported each string as a `const` so that we won't have to worry about misspelling our actions at any point in our application. This also allows us to take advantage of the autocomplete feature in our IDE. 

  * It is also considered best practice in Redux to make all of your action types capitalized. This makes it much easier for you to quickly find actions in your code.

  * Let the students know that we'll return to the `Favorites` actions if there's time.

  ```js
  export const UPDATE_POSTS = "UPDATE_POSTS";
  export const REMOVE_POST = "REMOVE_POST";
  export const SET_CURRENT_POST = "SET_CURRENT_POST";
  export const ADD_POST = "ADD_POST";
  export const LOADING = "LOADING";
  ```

  * At the top, we import all of the action types from our actions file.

  * Walkthrough each case in our switch statement:

  * `SET_CURRENT_POST` returns a _new_ state object by combining the previous state with the `post` object from the `action`. We also set the loading property in our state to be `false`.

  * `UPDATE_POSTS` also returns a _new_ state object. This time, we created a _new_ array by using the spread operator on the posts array from the action. Again, we set the loading property in our state to be `false`.

  * `REMOVE_POST` returns a _new_ state object. The posts array is created by using the `filter` method on the posts array from our previous state. Remember, the `filter` method returns a _new_ array instead of mutating the existing one.

  * `ADD_POST` returns a _new_ state object. We create a new array from the post object from the `action` and the posts from the previous state. Again, we set the loading property in our state to be `false`.

  * `LOADING` returns a _new_ state object with loading set to `true`.

  ```js
  import React, { createContext, useReducer, useContext } from "react";
  import { SET_CURRENT_POST, REMOVE_POST, UPDATE_POSTS, ADD_POST, LOADING } from "./actions";

  const StoreContext = createContext();
  const { Provider } = StoreContext;

  const reducer = (state, action) => {
    switch (action.type) {
      case SET_CURRENT_POST:
        return Object.assign({}, state, {
          currentPost: action.post,
          loading: false
        })

      case UPDATE_POSTS:
        return Object.assign({}, state, {
          posts: [...action.posts],
          loading: false
        })

      case REMOVE_POST:
        return Object.assign({}, state, {
            posts: state.posts.filter((post) => {
            return post._id !== action._id 
          })
        })

      case ADD_POST:
        return Object.assign({}, state, {
          posts: [action.post, ...state.posts],
          loading: false
        })

      case LOADING:
        return Object.assign({}, state, {
          loading: true
        })

      default:
        return state;
    }
  };
  ```

  * The `Store Provider` uses the `useReducer` Hook so that we can provide the global state to all of our components. 

  * The second argument in the `useReducer` Hook is the initial state.

  * `dispatch` is also provided globally so that all components can use the reducer.

  ```js
  const StoreProvider = ({ value = {}, ...props }) => {
    const [state, dispatch] = useReducer(reducer, {
      posts: [],
      currentPost: {
        _id: 0,
        title: "",
        body: "",
        author: ""
      },
      favorites: [], 
      loading: false
    });

    return <Provider value={[state, dispatch]} {...props} />;
  };

  const useStoreContext = () => {
    return useContext(StoreContext);
  };

  export { StoreProvider, useStoreContext };

  ```

* Open [createPostForm.js](../../../../01-Class-Content/20-state/01-Activities/22-Stu_Mini_Project/Solved/client/src/components/createPostForm.js) in your IDE and explain the following:

  * We create separate `ref`s for each input field.

  * The `useStoreContext` Hook is called so that we have access to the store.

  ```js
  const titleRef = useRef();
  const bodyRef = useRef();
  const authorRef = useRef();
  const [state, dispatch] = useStoreContext();
  ```

  * `handleSubmit` dispatches the `LOADING` action _before_ calling the API.

  * We save our post with `API.savePost`, then dispatch an action to update the store.

  * Both the `titleRef` and `bodyRef` are set back to empty strings.

  ```js
  const handleSubmit = (e) => {
    e.preventDefault();
    dispatch({ type: LOADING });
    API.savePost({
      title: titleRef.current.value,
      body: bodyRef.current.value,
      author: authorRef.current.value
    }).then((result) => {
      dispatch({
        type: ADD_POST,
        post: result.data
      });
    }).catch(err => console.log(err));
    titleRef.current.value = "";
    bodyRef.current.value = "";
  };
  ```

  * Each `ref` Hook is attached to its respective input field.

  * The button has a `disabled` attribute that activates if `state.loading` is true.

  ```js
  <form className="form-group mt-5 mb-5" onSubmit={handleSubmit}>
    <label htmlFor="title">Title:</label>
    <input className="form-control mb-5" required ref={titleRef} id="title" placeholder="Title" />
    <label htmlFor="body">Body:</label>
    <textarea className="form-control mb-5" required ref={bodyRef} id="body" placeholder="Body" />
    <label htmlFor="screen name">Screen Name:</label>
    <input className="form-control mb-5" ref={authorRef} id="screen name" placeholder="Screen name" />
    <button className="btn btn-success mt-3 mb-5" disabled={state.loading} type="submit">
       Save Post
    </button>
  </form>
  ```

* Open [PostsList.js](../../../../01-Class-Content/20-state/01-Activities/22-Stu_Mini_Project/Solved/client/src/components/PostsList.js) and explain the following:

  * The `removePost` function takes in the id argument and executes `API.deletePost(id)`. Once the deletion is complete, we dispatch an action to remove the post from our store. We pass the id property to the store so that the store will be able to use the `filter` method.

  * `useEffect` is called with no dependencies. This means our `getPosts` method will only run after the component first renders. 

  ```js
  const [state, dispatch] = useStoreContext();

  const removePost = (id) => {
    API.deletePost(id)
      .then(() => {
        dispatch({
          type: REMOVE_POST,
          _id: id
        });
      })
      .catch(err => console.log(err));
  };

  const getPosts = () => {
    dispatch({ type: LOADING });
    API.getPosts()
      .then(results => {
        dispatch({
          type: UPDATE_POSTS,
          posts: results.data
        });
      })
      .catch(err => console.log(err));
  };

  useEffect(() => {
    getPosts();
  }, []);
  ```

  * The ternary operation renders our posts _only_ if there are posts in the state. Otherwise, it will return a heading that let's the user know they haven't created any posts yet. 

  * By mapping each one of the posts to a `ListItem`, we can display its properties and pass its `_id` to the `removePost` method.

  ```js
  {state.posts.length ? (
    <List>
      {state.posts.map(post => (
        <ListItem key={post._id}>
          <Link to={"/posts/" + post._id}>
            <strong>
              {post.title} by {post.author}
            </strong>
          </Link>
          <DeleteBtn onClick={() => removePost(post._id)} />
        </ListItem>
      ))}
    </List>
  ) : (
    <h3>You haven't added any posts yet!</h3>
  )}
  ```

* Open [Detail](../../../../01-Class-Content/20-state/01-Activities/22-Stu_Mini_Project/Solved/client/src/pages/Detail) and explain the following: 

  * The `useEffect` Hook has no dependencies, so it will only run once when the component mounts.

  * We use `ADD_FAVORITE` and `REMOVE_FAVORITE` actions that mirror the `ADD_POST` and `REMOVE_POST` actions.

  ```js
  useEffect(() => {
    API.getPost(props.match.params.id)
      .then(res => dispatch({ type: SET_CURRENT_POST, post: res.data }))
      .catch(err => console.log(err));
  }, []);

  const addFavorite = () => {
    dispatch({
      type: ADD_FAVORITE,
      post: state.currentPost
    });
  };

  const removeFavorite = () => {
    dispatch({
      type: REMOVE_FAVORITE,
      _id: state.currentPost._id
    });
  };
  ```

  * A ternary operator determines whether to show the `Remove from Favorites` or `Add to Favorites` button based on whether or not the `currentPost` is within the current state's `favorites` array.

  ```js
  <>"   "{ state.currentPost ? (
    <Container fluid>
      <Row>
        <Col size="md-12">
          <Jumbotron>
            <h1>
              {state.currentPost.title} by {state.currentPost.author}
            </h1>
          </Jumbotron>
        </Col>
      </Row>
      <Row>
        <Col size="md-10 md-offset-1">
          <article>
            <h1>Content:</h1>
            <p>
              {state.currentPost.body}
            </p>
          </article>
        </Col>
        {
          state.favorites.indexOf(state.currentPost) !== -1 ? (
            <button className="btn btn-danger" onClick={removeFavorite}>Remove from Favorites!</button>
          ) : (
            <button className="btn" onClick={addFavorite}>❤️ Add to Favorites</button>
          )
        }
      </Row>
      <Row>
        <Col size="md-2">
          <Link to="/">← Back to Posts</Link>
        </Col>
      </Row>
    </Container>
    ): (<div>loading...</div>) }" "</>
  ```

### 15. Review Unit 20 (30 mins)

* Spend a moment to answer any lingering questions about the mini project. If no questions arise, proceed to review everything we've learned in Unit 20. 

* Ask the students the following questions and use their answers to guide your review:

  * ☝️ Which concepts are still difficult to grasp?

  * ☝️ Are there any activities that we've done in the last week that you would like to spend some time walking through?

- - -

### Instructor Do: Private Self-Reflection (0 min)

Take some time on your own after class to think about the following questions. If there's anything that you're not sure how to answer, feel free to reach out to the curriculum team!

1. How did today's class go?
2. How did you teach it?
3. How well do you feel you did teaching it?
4. Why are you teaching it?
5. Why did you teach it that way?
6. What evidence can I collect to show my students are understanding?
7. How will my students know they are getting it?

### Lesson Plan Feedback

How did today’s lesson go? Your feedback is important. Please take 5 minutes to complete this anonymous survey.

[Class Survey](https://forms.gle/nYLbt6NZUNJMJ1h38)
