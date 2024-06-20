# Unit 14 Instructor Overview: Model-View-Controller (MVC)

## Overview

In this unit, students will use the separation of concerns principle and the MVC framework to build full-stack web apps. They will use Handlebars.js features including expressions, built-in helpers, custom helpers, and partials to build static templates that can render dynamic data. Students will use front-end logic to make requests and pass data to the back end. They will begin by using hardcoded data and transition to using seed data with Sequelize and MySQL. They will use the routes in the Controller to manipulate data in the Model, to serialize Sequelize objects before sending them to the View, and create their own custom middleware for user authentication. Students will also incorporate sessions and cookies using the Sequelize store. They will be introduced to Prettier before starting on the mini-project.

Refer to the [Class Content Unit Overview](../../../01-Class-Content/14-MVC/README.md) for detailed information on key topics, learning objectives, and homework.

## Instructor/TA Notes

* Take some time to read through the Handlebars.js documentation and the Express Handlebars documentation to refamiliarize yourself with the template engine. This unit uses Express Handlebars, so the Handlebars.js documentation alone might not provide all of the answers. Focus on expressions, built-in helpers, custom helpers, and partials.

* This unit introduces students to the template engine Handlebars.js. The intention is not so much for students to learn Handlebars.js because it will be useful in their careers but more to treat the experience as an introduction to template engines, preparation for React.js, and a way to solidify their understanding of the MVC framework.

* You will be using MySQL for the majority of this unit's activities. Be sure to have your MySQL server up and running. You can create the databases ahead of time or demonstrate it live in class.

* Starting with `07-Ins_Data-Serialization`, each activity requires a `.env` file. Be sure to create one or rename the existing `.env.EXAMPLE` file before demonstrating each activity.

* Be prepared to remind students how to start their MySQL server on Day 1. They will need to use it starting with `08-Stu_Data-Serialization`.

* You'll need to install the VS Code extensions ESLint and Prettier to properly demonstrate both libraries for Day 3.

* If the students struggle with the Everyone Do: Prettier activity, walk through it with the students using the talking points provided. Otherwise, support the students as they do the activity and do a brief review at the end. 

## Career Connection

* Remind students that related Career Services material can be found in their [Career Connection folder](../../../01-Class-Content/14-MVC/04-Career-Connection/README.md).

* If you'd like more information on Career Services, visit the [Career Services resources page](https://mycareerspot.org/).

## Heads-Up

* Starting next week, students will work on their group projects. The project groups and project requirements will be announced in the next class (Day 1 of Unit 15). 

* In the meantime, start thinking about possible project groups. This time, assign three students per group, all around the same skill level. Be ready to assign students to groups in the next class.

* Let students know that they will be allowed to create their own groups for the final project.

## Helpful Links

This section contains links to this unit's lesson plans, homework, slide decks, algorithms, and resources.

### Lesson Plans

  * [14.1 Lesson Plan](./01-Day_Handlebars/14.1-LESSON-PLAN.md)

  * [14.2 Lesson Plan](./02-Day_Authentication/14.2-LESSON-PLAN.md)
  
  * [14.3 Lesson Plan](./03-Day_Review/14.3-LESSON-PLAN.md)

### Homework

  * [Unit 14 Homework](../../../01-Class-Content/14-MVC/02-Homework)

### Slide Decks

  * [Unit 14: MVC](https://docs.google.com/presentation/d/1rb2QnbKkUfmwqfUEpdQjV8x6S18ShB1BRdLggIVq6yU/edit?usp=sharing)

### Algorithms

  * [01: Common Element](../../../01-Class-Content/14-MVC/03-Algorithms/01-common-element/)

  * [02: Permutation Substring](../../../01-Class-Content/14-MVC/03-Algorithms/02-permutation-substring/)

  * [03: Concert Flyer](../../../01-Class-Content/14-MVC/03-Algorithms/03-concert-flyer/)

    * 📹 [Let's Code Concert Flyer!](https://2u-20.wistia.com/medias/42ac9axtbq)

### Resources

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
