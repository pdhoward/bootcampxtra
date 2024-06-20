# Unit 13 & 14 Instructor Overview: Object-Relational Mapping (ORM) and Model-View-Controller (MVC)

## Overview

In Unit 13, you will teach students to use the ORM library Sequelize to connect to and seed a database. In the process, students will create and configure Sequelize models, use validation tools, encrypt a password using `bcrypt`, automate functionality with Hooks, and use SQL in literals. Students will also model relationships and relate data between SQL tables using Sequelize associations. With the help of RESTful routes, they will map HTTP verbs to CRUD actions and build custom routes that map to instance methods. Additionally, students will learn to catch errors with `try...catch` and use `async` and `await` instead of Promises. 

In Unit 14, students will use the separation of concerns principle and the MVC framework to build full-stack web apps. They will use Handlebars.js features including expressions, built-in helpers, custom helpers, and partials to build static templates that can render dynamic data. Students will use front-end logic to make requests and pass data to the back end. They will begin by using hardcoded data and transition to using seed data with Sequelize and MySQL. They will use the routes in the Controller to manipulate data in the Model, to serialize Sequelize objects before sending them to the View, and create their own custom middleware for user authentication. Students will also incorporate sessions and cookies using the Sequelize store. They will be introduced to Prettier before starting on the mini-project.

Refer to the Class Content Unit Overview for [Unit 13](../../../01-Class-Content/13-ORM/README.md) and [Unit 14](../../../01-Class-Content/14-MVC/README.md)for detailed information on key topics, learning objectives, and homework.

## Instructor/TA Notes

* For Unit 13, take some time to review the Sequelize documentation to refamiliarize yourself with the library. Focus on implementing Hooks, validations, and associations.

* You will use MySQL in all of the activities for this unit, so be sure to have your MySQL server up and running. You can create the databases listed in each activity ahead of time, or you can prepare to demonstrate it live in class.

* Run `npm install` before the Instructor Demo to ensure that you have the full five-minute window for instruction.

* In the first activity of Unit 13, `01-Ins_Sequelize-Setup`, you will hardcode the database credentials in the `connection.js` file. Every subsequent activity uses a `.env` file. Make sure that you create one or rename the existing `.env.EXAMPLE` file before demonstrating each activity. 

* Instead of relying on a front end, all of the activities will use Insomnia Core to test the routes. Be sure to have it installed and ready for class.

* Unit 13 also introduces RESTful routes. Highlight the convention for students and tell them that they will revisit the pattern at a later point.

* The introduction to seeding in this unit differs from what students will find in the Sequelize documentation. Consider warning students about the difference in case they look for more information on seeding in the documentation.

* For Unit 14, take some time to read through the Handlebars.js documentation and the Express Handlebars documentation to refamiliarize yourself with the template engine. This unit uses Express Handlebars, so the Handlebars.js documentation alone might not provide all of the answers. Focus on expressions, built-in helpers, custom helpers, and partials.

* This unit introduces students to the template engine Handlebars.js. The intention is not so much for students to learn Handlebars.js because it will be useful in their careers but more to treat the experience as an introduction to template engines, preparation for React.js, and a way to solidify their understanding of the MVC framework.

* Starting with `07-Ins_Data-Serialization`, each activity requires a `.env` file. Be sure to create one or rename the existing `.env.EXAMPLE` file before demonstrating each activity.

* Be prepared to remind students how to start their MySQL server on Day 1. They will need to use it starting with `08-Stu_Data-Serialization`.

* You'll need to install the VS Code extensions ESLint and Prettier to properly demonstrate both libraries.

* If the students struggle with the Everyone Do: Prettier activity, walk through it with the students using the talking points provided. Otherwise, support the students as they do the activity and do a brief review at the end. 

## Career Connection

* Remind students that related Career Services material can be found in their Career Connection folder for [Unit 13](../../../01-Class-Content/13-ORM/04-Career-Connection/README.md) and [Unit 14](../../../01-Class-Content/14-MVC/04-Career-Connection/README.md).

* If you'd like more information on Career Services, visit the [Career Services resources page](https://mycareerspot.org/).

## Heads-Up

* Starting next week, students will work on their group projects. The project groups and project requirements will be announced in the next class (Day 1 of Unit 15). 

* In the meantime, start thinking about possible project groups. This time, assign three students per group, all around the same skill level. Be ready to assign students to groups in the next class.

* Let students know that they will be allowed to create their own groups for the final project.

## Helpful Links

This section contains links to this unit's lesson plans, homework, slide decks, algorithms, and resources.

### Lesson Plans

  * [07.1 Lesson Plan](./01-Day/01-Day-LessonPlan.md)

  * [07.2 Lesson Plan](./02-Day/02-Day-LessonPlan.md)
  
  * [07.3 Lesson Plan](./03-Day/03-Day-LessonPlan.md)

  * [07.4 Lesson Plan](./04-Day/04-Day-LessonPlan.md)
  
  * [07.5 Lesson Plan](./05-Day/05-Day-LessonPlan.md)

### Homework

  * [Unit 13 Homework](../../../01-Class-Content/13-ORM/02-Homework)

  * [Unit 14 Homework](../../../01-Class-Content/14-MVC/02-Homework)

### Slide Decks

  * [Unit 13: ORM](https://docs.google.com/presentation/d/1_0n8JjM6cgmDyUfqGC6crF47JItD0mn9vzvQeYqZ5OE/edit?usp=sharing)

  * [Unit 14: MVC](https://docs.google.com/presentation/d/1rb2QnbKkUfmwqfUEpdQjV8x6S18ShB1BRdLggIVq6yU/edit?usp=sharing)

### Algorithms

Unit 13:

* [01: Double Triple Map](../../../01-Class-Content/13-ORM/03-Algorithms/01-double-triple-map/)

  * 📹 [Let's Code Double Triple Map!](https://2u-20.wistia.com/medias/pz1ugrv0yu)

* [02: Array Intersection](../../../01-Class-Content/13-ORM/03-Algorithms/02-array-intersection/)

* [03: Squares of a Sorted Array](../../../01-Class-Content/13-ORM/03-Algorithms/03-squares-of-a-sorted-array/)

Unit 14:

  * [01: Common Element](../../../01-Class-Content/14-MVC/03-Algorithms/01-common-element/)

  * [02: Permutation Substring](../../../01-Class-Content/14-MVC/03-Algorithms/02-permutation-substring/)

  * [03: Concert Flyer](../../../01-Class-Content/14-MVC/03-Algorithms/03-concert-flyer/)

    * 📹 [Let's Code Concert Flyer!](https://2u-20.wistia.com/medias/42ac9axtbq)

### Resources

* [Deploy with Heroku and MySQL](https://coding-boot-camp.github.io/full-stack/heroku/deploy-with-heroku-and-mysql)

* [Sequelize documentation](https://sequelize.org/master/)

* [npm documentation on bcrypt](https://www.npmjs.com/package/bcrypt)

* [npm documentation on dotenv](https://www.npmjs.com/package/dotenv)

* [ESLint configuration user guide](https://eslint.org/docs/user-guide/configuring)

* [Sequelize documentation](https://sequelize.org/master/)

* [Handlebars.js](https://handlebarsjs.com/)

* [npm documentation on Express Handlebars](https://www.npmjs.com/package/express-handlebars)

* [npm documentation on connect-session-sequelize](https://www.npmjs.com/package/connect-session-sequelize)

* [GitHub documentation on Express.js session cookies](https://github.com/expressjs/session#cookie)

* [Express.js documentation on using middleware](https://expressjs.com/en/guide/using-middleware.html)

* [ESLint configuration user guide](https://eslint.org/docs/user-guide/configuring)

* [Prettier documentation](https://prettier.io/docs/en/index.html)

---
© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.
