# 07.5 Full-Time Lesson Plan: Model-View-Controller (MVC)

## Overview

In today's class, students will have a chance to review MVC architecture, Handlebars.js, user authentication, and ESLint. Students will also be introduced to Prettier before starting on the mini-project.
## Instructor Notes

* In this lesson, students will complete activities `21-Ins_MVC-Review` through `28-Stu_Mini-Project`.

* Be sure to have your MySQL server up and running. You can create the `user_db`, `crowdfund_db`, and `tech_blog_db` databases ahead of time, or you can demonstrate it live in class.

* The first two activities, the mini-project, and the homework each use a `.env` file. Be sure to create one or rename the existing `.env.EXAMPLE` file before demonstrating these activities.

* The activities (but not the homework) each also include a seeds script that can be executed with `npm run seed`.

* You will need to install the ESLint and Prettier VS Code extensions to properly demonstrate both libraries.

* Remind students to do a `git pull` of the class repo to have today's activities ready and open in VS Code. 

* If you are comfortable doing so, live-code the solutions to the activities. If not, just use the solutions provided and follow the prompts and talking points for review.

* Let students know that the Bonus at the end of each activity is not meant to be extra coding practice, but instead is a self-study on topics beyond the scope of this unit for those who want to further their knowledge.

* If the students struggle with the Everyone Do: Prettier activity, walk through it with the students using the talking points provided. Otherwise, support the students as they do the activity and do a brief review at the end. 

## Learning Objectives

By the end of class, students will be able to:

* Explain the interactions between the Model, View, and Controller.

* Implement user authentication in a Node.js app.

* Explain the purpose of ESLint.

* Explain and add Prettier to an existing project.

## Time Tracker
| Start  | #   | Activity Name                      | Duration |
|---     |---  |---                                 |---       |
| 10:00AM| 1   | Instructor Do: Stoke Curiosity     | 0:10     |
| 10:10AM| 2   | Instructor Demo: MVC Review        | 0:05     |
| 10:15AM| 3   | Student Do: MVC Review             | 0:15     |
| 10:30AM| 4   | Instructor Review: MVC Review      | 0:10     |
| 10:40AM| 5   | Instructor Demo: Auth Review       | 0:05     |
| 10:45AM| 6   | Student Do: Auth Review            | 0:15     |
| 11:00AM| 7   | Instructor Review: Auth Review     | 0:10     |
| 11:10AM| 8   | Instructor Demo: Lint Review       | 0:05     |
| 11:15AM| 9   | Student Do: Lint Review            | 0:15     |
| 11:30AM| 10  | Instructor Review: Lint Review     | 0:10     |
| 11:40AM| 11  | Everyone Do: Prettier              | 0:20     |
| 12:00PM| 12  | BREAK                              | 0:30     |
| 12:30PM| 13  | Instructor Demo: Mini-Project      | 0:05     |
| 12:35PM| 14  | Student Do: Mini-Project           | 0:60     |
| 1:35PM | 15  | Instructor Review: Mini-Project    | 0:10     |
| 1:45PM | 16  | Introduce Homework                 | 0:05     |
| 1:50PM | 17  | FLEX                               | 0:40     |
| 2:30PM | 18  | End                                | 0:00     |

---

## Class Instruction

### 1. Instructor Do: Stoke Curiosity (10 min)

* Welcome students to class.

* Congratulate the class on learning new back-end skills to complement their front-end skills. They now have everything they need to build full-stack applications!

* Remind students that the upcoming group project will involve combining all of these skills to make something of their own choosing.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What kinds of apps would require a database?

  * 🙋 Any app that requires users to create an account&mdash;for instance, scheduling appointments, tracking fitness or financial progress, or shopping.

  * ☝️ What's the benefit of letting users create accounts?

  * 🙋 Their information is saved indefinitely and can be accessed across multiple devices (as opposed to using `localStorage`).

  * ☝️ Which content or features would you want to restrict to only logged-in users?

  * 🙋 A user's personal dashboard or profile page, the ability to create public posts, the ability to interact with other users, and so on.

  * ☝️ What kind of account-based app would aid your own personal interests?

  * 🙋 Answers might include apps that let you share or save recipes, schedule meetups, discuss and review movies, trade collectibles, plan a trip, or anything along those lines.

* Answer any questions before proceeding to the next activity.

### 2. Instructor Demo: { ACTIVITY NAME } (5 min) 

Instructor Demo: MVC Review (5 min) 

* Navigate to `21-Ins_MVC-Review` and explain the following:

  * This is a full-stack application that follows MVC architecture.

  * The folders labeled `models`, `views`, and `controllers` contain the three main pieces of the application.

* Open `21-Ins_MVC-Review/models/User.js` in your IDE and explain the following:

  * The Model is in charge of data-related logic. This particular Model maps to a `user` table in the database, as shown in the following example:

    ```js
    User.init(
      {
        id: {
          type: DataTypes.INTEGER,
          allowNull: false,
          primaryKey: true,
          autoIncrement: true,
        },
        name: {
          type: DataTypes.STRING,
          allowNull: false,
        },
        email: {
          type: DataTypes.STRING,
          allowNull: false,
          unique: true,
          validate: {
            isEmail: true,
          },
        },
        password: {
          type: DataTypes.STRING,
          allowNull: false,
          validate: {
            len: [8],
          },
        },
      },
    );
    ```

* Open `21-Ins_MVC-Review/controllers/homeRoutes.js` in your IDE and explain the following:

  * The Controller processes requests. In the following example, the Controller is an Express.js route that renders a Handlebars.js template:

    ```js
    router.get('/', async (req, res) => {
      res.render('homepage');
    });
    ```

* Open `21-Ins_MVC-Review/views/homepage.handlebars` in your IDE and explain the following:

  * The View represents what the user sees in the browser. The View is built with Handlebars.js. However, currently the templates render hardcoded test data, as shown in the following example:

    ```hbs
    <div class="row align-center mb-5">
      <div class="col-md-6">
        <h2>{{{get_emoji}}} Test User</h2>
      </div>
      <div class="col-md-6">
        <h3><a href="mailto:test@gmail.com">test@gmail.com</a></h3>
      </div>
    </div>
    ```

* From the `21-Ins_MVC-Review` directory in the command line, run `npm install`, `npm run seed`, and `npm start`. Open <http://localhost:3001/> in the browser to show the hardcoded data.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How would we build this with real data?

  * 🙋 Run a Sequelize `findAll()` method in the Controller and send the serialized data to the Handlebars.js template.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `22-Stu_MVC-Review/README.md`.

### 3. Student Do: MVC Review (15 min) 

* Direct students to the activity instructions found in `22-Stu_MVC-Review/README.md`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 🏗️ Populate User Registry with Database Data

  Work with a partner to implement the following user story:

  * As a user, I want to see a list of other users who are registered with the app.

  ## Acceptance Criteria

  * It's done when the homepage displays the user data from the database instead of the hardcoded values.

  * It's done when the user data is rendered as part of a Handlebars.js template.

  * It's done when the users are sorted alphabetically by name.

  ## Assets

  The following image demonstrates the web application's appearance and functionality:

  ![The homepage displays a list of users and their email addresses.](./Images/01-user-registry.png)

  ---

  ## 💡 Hints

  Without a signup form, how can you quickly add new users to the database? What needs to happen with the Sequelize data before it can be passed into the Handlebars.js template?

  ## 🏆 Bonus

  If you have completed this activity, work through the following challenge with your partner to further your knowledge:

  * What are some other paradigms besides MVC?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 4. Instructor Review: MVC Review (10 min) 

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with MVC and Handlebars.js? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points:

  * ✔️ Sequelize serialization

  * ✔️ Handlebar.js expressions

* Open `22-Stu_MVC-Review/Solved/controllers/homeRoutes.js` in your IDE and explain the following: 

  * We perform a Sequelize `findAll()` to get the user data, excluding the users' passwords but ordering them by name, as follows:

    ```js
    const userData = await User.findAll({
      attributes: { exclude: ['password'] },
      order: [['name', 'ASC']],
    });
    ```

  * 🔑 We serialize the data to remove extraneous properties that Handlebars.js doesn't need, as shown in the following example:

    ```js
    const users = userData.map((project) => project.get({ plain: true }));
    ```

  * 🔑 We pass the serialized array of users into the `homepage.handlebars` template, as follows:

    ```js
    res.render('homepage', { users });
    ```

* Open `22-Stu_MVC-Review/Solved/views/homepage.handlebars` in your IDE and explain the following:

  * 🔑 We use a Handlebars.js `#each` helper to loop over the users and render a `<div>` element for each one, like in the following example:

    ```hbs
    {{#each users as |user| }}
    <div class="row align-center mb-5">
      <div class="col-md-6">
        <h2>{{{get_emoji}}} {{user.name}}</h2>
      </div>
      <div class="col-md-6">
        <h3><a href="mailto:{{user.email}}">{{user.email}}</a></h3>
      </div>
    </div>
    {{/each}}
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What is another built-in helper that you can use with Handlebars.js?

  * 🙋 The `#if` helper.

  * ☝️ What is the difference between double- and triple-bracket expressions in Handlebars.js?

  * 🙋 Double brackets render text; triple brackets render HTML.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [Sequelize documentation on models](https://sequelize.org/master/class/lib/model.js~Model.html) and the [npm documentation on Express Handlebars](https://www.npmjs.com/package/express-handlebars), and stick around for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 5. Instructor Demo: Auth Review (5 min) 

* Navigate to `23-Ins_Auth-Review` from the command line and run `npm install`, `npm run seed`, and `npm start`.

* Open <http://localhost:3001/> in your browser and demonstrate the following:

  * 🔑 A non logged-in user is immediately redirected from `/` to `/login`.

  * 🔑 Logging in with the credentials "sal@hotmail.com" and "password12345" immediately redirects to the homepage.

  * The homepage displays a list of all registered users with the app.

  * 🔑 Refreshing the page or closing and reopening the tab does not log the user out.

  * 🔑 Selecting the "logout" button redirects to the `/login` page.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What keeps the user logged in?

  * 🙋 Sessions and cookies.

  * ☝️ How would we build this from scratch?

  * 🙋 We would need to install and configure `express-session` and `connect-session-sequelize`. We would need to create and destroy the session in the correct routes.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `24-Stu_Auth-Review/README.md`.

### 6. Student Do: Auth Review (15 min) 

* Direct students to the activity instructions found in `24-Stu_Auth-Review/README.md`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 📐 Add Comments to Implementation of a Login Route

  Work with a partner to add comments describing the functionality of the code found in the following files:

  * [Unsolved/server.js](./Unsolved/server.js)

  * [Unsolved/controllers/api/userRoutes.js](./Unsolved/controllers/api/userRoutes.js)

  * [Unsolved/utils/auth.js](./Unsolved/utils/auth.js)

  * [Unsolved/controllers/homeRoutes.js](./Unsolved/controllers/homeRoutes.js)

  * [Unsolved/views/layouts/main.handlebars](./Unsolved/views/layouts/main.handlebars)

  * [Unsolved/public/js/login.js](./Unsolved/public/js/login.js)

  * [Unsolved/public/js/logout.js](./Unsolved/public/js/logout.js)

  ---

  ## 🏆 Bonus

  If you have completed this activity, work through the following challenge with your partner to further your knowledge:

  * What other tools can be used to handle user authentication in a Node.js application?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 7. Instructor Review: Auth Review (10 min) 

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with user authentication? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points:

  * ✔️ Redirects

  * ✔️ Sessions

  * ✔️ Sequelize store

* Open `24-Stu_Auth-Review/Solved/server.js` in your IDE and explain the following: 

  * 🔑 We create a new Sequelize store using the `express-session` package, as follows:

    ```js
    const SequelizeStore = require('connect-session-sequelize')(session.Store);
    ```

  * 🔑 We configure the session object with the Sequelize store and add it as middleware to Express.js, as shown in the following example:

    ```js
    const sess = {
      secret: 'Super secret secret',
      cookie: {},
      resave: false,
      saveUninitialized: true,
      store: new SequelizeStore({
        db: sequelize
      })
    };

    app.use(session(sess));
    ```

* Open `24-Stu_Auth-Review/Solved/controllers/api/userRoutes.js` in your IDE and explain the following: 

  * In the `/login` route, we find the user whose email matches the posted data, like in the following example:

    ```js
    const userData = await User.findOne({ where: { email: req.body.email } });
    ```

  * We compare the encrypted version of the posted password against what's saved in the database, as follows:

    ```js
    const validPassword = await userData.checkPassword(req.body.password);
    ```

  * 🔑 If the email and password validate, we create new session variables before sending a response back, as follows:

    ```js
    req.session.save(() => {
      req.session.user_id = userData.id;
      req.session.logged_in = true;
      
      res.json({ user: userData, message: 'You are now logged in!' });
    });
    ```

  * 🔑 In the `/logout` route, we destroy the session, if one exists, as shown in the following example:

    ```js
    if (req.session.logged_in) {
      req.session.destroy(() => {
        res.status(204).end();
      });
    }
    ```

* Open `24-Stu_Auth-Review/Solved/utils/auth.js` in your IDE and explain the following:

  * 🔑 We have a middleware function, shown in the following example, that will redirect the request if there is no session:

    ```js
    if (!req.session.logged_in) {
      res.redirect('/login');
    } else {
      next();
    }
    ```

* Open `24-Stu_Auth-Review/Solved/controllers/homeRoutes.js` in your IDE and explain the following:

  * 🔑 We add the `withAuth()` middleware to protect routes from non logged-in users, as follows:

    ```js
    router.get('/', withAuth, async (req, res) => {

    });
    ```

  * We pass the session variable into the Handlebars.js template to conditionally render elements later on, as follows:

    ```js
    res.render('homepage', {
      users,
      logged_in: req.session.logged_in,
    });
    ```

  * 🔑 In the `/login` route, we redirect the request if the user has already logged in, as follows:

    ```js
    if (req.session.logged_in) {
      res.redirect('/');
      return;
    }
    ```

* Open `24-Stu_Auth-Review/Solved/views/layouts/main.handlebars` in your IDE and explain the following:

  * We use the `#if` helper to conditionally render elements for logged-in users, as shown in the following example:

    ```hbs
    {{#if logged_in}}
    <nav>
      <button class="btn" id="logout">logout</button>
    </nav>
    {{/if}}
    ```

  * We also conditionally render the `logout.js` script to avoid unnecessary errors and network requests, as shown in the following example:

    ```hbs
    {{#if logged_in}}
    <script src="/js/logout.js"></script>
    {{/if}}
    ```

* Open `24-Stu_Auth-Review/public/js/login.js` in your IDE and explain the following:

  * We stop the browser from submitting the form so that we can handle the POST request ourselves, as follows:

    ```js
    event.preventDefault();
    ```

  * We capture the user's credentials from the form elements, as shown in the following example:

    ```js
    const email = document.querySelector('#email-login').value.trim();
    const password = document.querySelector('#password-login').value.trim();
    ```

  * We make a POST request with `fetch()` to send the user's credentials to the server, as follows:

    ```js
    const response = await fetch('/api/users/login', {
      method: 'POST',
      body: JSON.stringify({ email, password }),
      headers: { 'Content-Type': 'application/json' },
    });
    ```

* Open `24-Stu_Auth-Review/public/js/logout.js` in your IDE and explain the following:

  * To log a user out, we make a POST request to the `/logout` endpoint, as shown in the following example:

    ```js
    const response = await fetch('/api/users/logout', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
    });
    ```

  * 🔑 After receiving a successful response, we redirect on the front end, as follows:

    ```js
    if (response.ok) {
      document.location.replace('/login');
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What keeps a user logged in?

  * 🙋 The session and (on a long-term basis) the cookie.

  * ☝️ What creates the cookie?

  * 🙋 The Sequelize store.

  * ☝️ In the client-server model, who has access to the session and cookie?

  * 🙋 The server has access to both; the client can only access the cookie.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [npm documentation on express-session](https://www.npmjs.com/package/express-session) and the [npm documentation on connect-session-sequelize](https://www.npmjs.com/package/connect-session-sequelize), and stick around for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 8. Instructor Demo: Lint Review (5 min) 

* Open `25-Ins_Lint-Review/package.json` in your IDE and explain the following:

  * 🔑 We add `eslint` as a dependency to this project, as shown in the following example:

    ```json
    "devDependencies": {
      "eslint": "^7.12.1"
    }
    ```

* Open `25-Ins_Lint-Review/.eslintrc.json` in your IDE and explain the following:

  * In the config file, we specify that ESLint shouldn't look at parent folders for other configurations&mdash;as shown in the following example:

    ```json
    "root": true
    ```

  * 🔑 We add an `env` property to specify the different environments and features we want ESLint to support&mdash;including ES6 syntax&mdash;as follows:

    ```json
    "env": {
      "browser": true,
      "commonjs": true,
      "node": true,
      "es6": true
    }
    ```

* Open `25-Ins_Lint-Review/index.js` in your IDE and explain the following:

  * Based on the ESLint rules, unused variables should be highlighted as an error, as shown in the following example:

    ```js
    const example = true;
    ```

  * Empty functions are not allowed, as shown in the following example:

    ```js
    const sayHello = () => {

    };
    ```

  * Strings should use single quotes instead of double quotes, outlined as follows:

    ```js
    sayHello("hello");
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ Why is ESLint useful?

  * 🙋 It enforces best practices and consistent code across the team.

  * ☝️ How do we know what other rules ESLint supports?

  * 🙋 Read the documentation!

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `26-Stu_Lint-Review`.

### 9. Student Do: Lint Review (15 min) 

* Direct students to the activity instructions found in `26-Stu_Lint-Review`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 🐛 Fix Project's ESLint Rules

  Work with a partner to resolve the following issues:

  * As a developer, I don't want to see warnings when I use the `**` exponentiation operator.

  * As a developer, I want to discourage other team members from explicitly assigning variables to `undefined`.

  ## Expected Behavior

  * The project's ESLint rules allow the use of `**` operators. 

  * ESLint displays an error when variables are assigned to `undefined`. For example, `let x = undefined;` is unnecessary, because `let x;` on its own is sufficient.

  ## Actual Behavior

  * ESLint displays an error when developers use `**` operators. For example, `let x = 5 ** 2;`.

  * Developers can assign variables to `undefined` without any warning from ESLint.

  ## Steps to Reproduce the Problem

  1. Run `npm install` to install the ESLint dependencies.

  2. Open `index.js` in VS Code.

  3. Note the underlined error on line 6.

  ---

  ## 💡 Hints

  How do you adjust the rules for an ESLint configuration? And in which version of JavaScript were `**` exponentiation operators introduced?

  ## 🏆 Bonus

  If you have completed this activity, work through the following challenge with your partner to further your knowledge:

  * What other options can you add to your ESLint config file?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 10. Instructor Review: Lint Review (10 min) 

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with ESLint configurations? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points:

  * ✔️ ES7

  * ✔️ ESLint rules

* Open `26-Stu_Lint-Review/Solved/.eslintrc.json` in your IDE and explain the following: 

  * 🔑 The exponentiation operator is an ES7 feature, so we add `es2017` as an environment that we want ESLint to support, as follows:

    ```json
    "es2017": true
    ```

  * 🔑 We add `no-undef-init` to the list of rules to disallow assigning variables to `undefined`, as shown in the following example:

    ```json
    "no-undef-init": "error"
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ Why would we want to discourage `undefined` variable assignments?

  * 🙋 Variables are already `undefined` as soon as they are declared.

  * ☝️ How could we find out what other features come with ES7?

  * 🙋 Google it!

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [ESLint documentation on configuring](https://eslint.org/docs/user-guide/configuring), and stick around for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `27-Evr_Prettier/README.md`.

### 11. Everyone Do: Prettier (20 min)

* Open the [Prettier website](https://prettier.io/) in your browser and explain the following:

  * ESLint will highlight code that doesn't meet certain standards, but it's still up to the developer to make those changes.

  * Prettier is a library that will automatically format your code, using either its own rules or rules that you and your team configure.

  * Prettier includes rules like adding spaces between certain keywords, moving chained methods to a new line, adding trailing commas after object properties, and keeping quotes consistent.

  * Prettier and ESLint work hand in hand, because Prettier is more concerned with visual formatting whereas ESLint focuses on the code itself.

* Direct students to the activity instructions found in `27-Evr_Prettier/README.md`.

* While everyone is working on the activity, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

* Open `27-Evr_Prettier/Solved/package.json` in your IDE and explain the following:

  * 🔑 We add `prettier` and the `eslint-config-prettier` plugin to the project's dependencies, as follows:

    ```json
    "devDependencies": {
      "eslint": "^7.12.1",
      "eslint-config-prettier": "^6.15.0",
      "prettier": "^2.1.2"
    }
    ```

* Open `27-Evr_Prettier/Solved/.prettierrc.json` in your IDE and explain the following:

  * 🔑 We create a Prettier config file to specify an additional rule for single quotes, as shown in the following example:

    ```json
    {
      "singleQuote": true
    }
    ```

* Open `27-Evr_Prettier/Solved/.prettierignore` in your IDE and explain the following:

  * We create a `.prettierignore` file to exclude markdown files, as follows:

    ```text
    *.md
    ```

* Open `27-Evr_Prettier/Solved/.eslintrc.json` in your IDE and explain the following:

  * We update the ESLint config file to make ESLint aware of Prettier, like in the following example:

    ```json
    "extends": ["prettier"]
    ```

* 🔑 We can run Prettier once, with the command `npx prettier`, or install the VS Code extension to automatically format files when saving.

* Answer any questions before students go on break.

### 12. BREAK (30 min)

### 13. Instructor Demo: Mini-Project (5 min) 

* Navigate to `28-Stu_Mini-Project/Main` from the command line and run `npm install`, `npm run seed`, and `npm start`.

* Open <http://localhost:3001/> in your browser and demonstrate the following:

  * The homepage template renders a list of projects that are saved in the database.

  * Each project links to a separate route (for example, `/project/2`) that renders a different View.

* Navigate to <http://localhost:3001/login> in your browser and demonstrate the following:

  * Users can create a new account or log in with an existing account.

* Log in with the credentials "sal@hotmail.com" and "password12345" to demonstrate the following:

  * After logging in, a user is redirected to the `/profile` route.

  * In their profile, a user can create a new project listing or delete a project from the database.

* Explain that the Sequelize models and API routes are already built.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How would we build the remaining functionality?

  * 🙋 With Sequelize queries, Handlebars.js templates, sessions, and client-side JavaScript.

* Answer any questions before allowing students to start the mini-project.

### 14. Student Do: Mini-Project (60 min)

* Direct students to the activity instructions found in `28-Stu_Mini-Project/README.md`.

* Break your students into groups that will work together on this activity.

  ```md
  # Unit 14 Mini-Project: Crowdfunding App

  In this mini-project, you will work with a group to build a full-stack crowdfunding app using Node.js, Express.js, Sequelize, Handlebars.js, and MVC architecture.

  ## User Stories

  * As a user, I want to see a list of current projects seeking funding.

  * As a user, I want to be able to create an account.

  * As a registered user, I want to post my own projects to ask for funding.

  ### Acceptance Criteria

  * It's done when the `/` homepage route renders a list of all projects from the database.

  * It's done when the `/project/:id` route renders an individual project's details based on the route parameter id.

  * It's done when the `/login` route renders a form to log in and a form to create a new account.

  * It's done when an existing user can enter their credentials on the login page to create a session on the server.

  * It's done when a new user can create an account on the login page and then be immediately logged in with a session.

  * It's done when the `/profile` route renders the logged-in user's projects and a form to create a new project.

  * It's done when only a logged-in user can visit the `/profile` route.

  * It's done when a logged-in user is redirected to `/profile` when they try to visit `/login` again.

  * It's done when a user on the profile page can use the form to create a new project in the database.

  * It's done when a user on the profile page can select a "Delete" button to remove their project from the database.

  * It's done when a logged-in user can select a "Logout" button to remove their session.

  * It's done when the API routes to create and delete posts are protected from non logged-in users.

  * It's done when the code is organized using MVC architecture.

  * It's done when the views are rendered with Handlebars.js templates.

  ## Specifications 

  * The database models have the following fields and associations:

    * `User`

      * `id`: primary key

      * `name`

      * `email`

      * `password`

    * `Project`

      * `id`: primary key

      * `name`

      * `description`

      * `date_created`

      * `needed_funding`

      * `user_id`: foreign key that references `User.id`

    * Users have many projects, and projects belong to a user.

      * If a user is deleted, all associated projects are also deleted.

  ---

  ## 💡 Hints

  * What tools can you use to test the existing API routes if you don't yet have a front end?

  * Where would you place the client-side JavaScript for capturing form data?

  * How can middleware help protect routes from non logged-in users?

  * How can Handlebars.js helpers (both built-in and custom) be used to render the desired results?

  ## 🏆 Bonus

  If you have completed this activity, work through the following challenge with your partner to further your knowledge:

  * Add an `/edit/:id` route for logged-in users to update their projects' details. Then deploy the app to Heroku!
  ```

* While breaking everyone into groups, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 15. Instructor Review: Mini-Project (10 min) 

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with this mini-project? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points:

  * ✔️ Sessions

  * ✔️ Handlebars.js

  * ✔️ Sequelize queries

* Open `28-Stu_Mini-Project/Main/controllers/homeRoutes.js` in your IDE and explain the following: 

  * 🔑 In the `/` route, we find all projects, joining with the `user` table to get the user's name, like in the following example:

    ```js
    const projectData = await Project.findAll({
      include: [
        {
          model: User,
          attributes: ['name'],
        },
      ],
    });
    ```

  * We serialize the data and pass the array and the session variable into the template, as follows:

    ```js
    const projects = projectData.map((project) => project.get({ plain: true }));

    res.render('homepage', { 
      projects, 
      logged_in: req.session.logged_in 
    });
    ```

  * 🔑 In the `/profile` route, we use a custom `withAuth()` middleware function to protect the route against non logged-in users, as shown in the following example:

    ```js
    router.get('/profile', withAuth, async (req, res) => {

    });
    ```

  * 🔑 In the `/profile` route, we find the user in the database using the session id and `JOIN` with their projects. The data is then serialized and passed into the template, as shown in the following example:

    ```js
    const userData = await User.findByPk(req.session.user_id, {
      attributes: { exclude: ['password'] },
      include: [{ model: Project }],
    });

    const user = userData.get({ plain: true });

    res.render('profile', {
      ...user,
      logged_in: true
    });
    ```

* Open `28-Stu_Mini-Project/Main/views/profile.handlebars` in your IDE and explain the following:

  * We use Handlebars.js expressions to render the data from Sequelize, as follows:

    ```hbs
    <h2>Welcome, {{name}}!</h2>
    ```

  * 🔑 We use the `#if` helper to only render the project list if this user has projects, as follows:

    ```hbs
    {{#if projects.length}}
    <div class="col-md-6 project-list">

    </div>
    {{/if}}
    ```

  * 🔑 We use the `#each` helper to iterate over the projects and render a button with a `data-id` attribute, as follows:

    ```hbs
    {{#each projects as |project|}}
    <div class="row mb-2">
      <div class="col-md-8">
        <h4><a href="/project/{{project.id}}">{{project.name}}</a></h4>
      </div>
      <div class="col-md-4">
        <button class="btn btn-sm btn-danger" data-id="{{project.id}}">DELETE</button>
      </div>
    </div>
    {{/each}}
    ```

* Open `28-Stu_Mini-Project/Main/public/js/profile.js` in your IDE and explain the following:

  * We include client-side JavaScript to capture a "delete" button click, read the `data-id` attribute, and send a DELETE request to the server with the id. See the following code for an example:

    ```js
    const delButtonHandler = async (event) => {
      if (event.target.hasAttribute('data-id')) {
        const id = event.target.getAttribute('data-id');

        const response = await fetch(`/api/projects/${id}`, {
          method: 'DELETE',
        });
      }
    };
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What are the benefits of using a template engine like Handlebars.js instead of rendering the data with client-side JavaScript?

  * 🙋 This results in cleaner HTML and JS code, fewer network requests to the server, template reusability, improved SEO, and more.

  * ☝️ Why is client-side JavaScript still needed when rendering data with Handlebars.js?

  * 🙋 There are still user interactions (like button clicks) that we need to capture.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [npm documentation on Express Handlebars](https://www.npmjs.com/package/express-handlebars) and the [npm documentation on express-session](https://www.npmjs.com/package/express-session), and stick around for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 16. Instructor Demo: Introduce Homework (5 min)

* Navigate to `02-Homework/Main` from the command line and run `npm install` and `npm start`.

* Open <http://localhost:3001/signup> in your browser and demonstrate the following:

  * We are building a community tech blog where anyone can create an account to contribute.

* Create a new account on the signup page to demonstrate the following:

  * Creating a new account redirects you to the dashboard page.

  * On the dashboard page, users can select the "New Post" button to create a new blog post.

* Navigate to <http://localhost:3001/dashboard/new> in your browser and demonstrate the following:

  * Creating a new post will add it to the user's dashboard.

  * If the user clicks on the post, they have the option to update its content or delete it.

* Navigate to <http://localhost:3001/post/1> in your browser and demonstrate the following:

  * Logged-in users can leave a comment on their own or others' blog posts.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What are we learning?

  * 🙋 We are learning true full-stack development!

  * ☝️ How does this project build off or extend previously learned material?

  * 🙋 The Model is more complex than what we have seen before, with additional CRUD operations.

  * ☝️ How does this project relate to your career goals?

  * 🙋 It combines everything you have learned previously into a single app that serves a real-world purpose, which will be useful to include in your portfolio for potential employers.

* Ask TAs to direct students to the Homework Requirements found in `02-Homework/README.md`.

### 17. FLEX (40 min)

* This time can be utilized for reviewing key topics learned so far in this unit or getting started on the homework.

* Answer any questions before ending the class.

### 18. END (0 min)

How did today’s lesson go? Your feedback is important. Please take 5 minutes to complete this [anonymous survey](https://forms.gle/RfcVyXiMmZQut6aJ6).

---
© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.
