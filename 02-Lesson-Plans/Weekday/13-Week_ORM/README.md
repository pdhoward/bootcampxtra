# Unit 13 Instructor Overview: Object-Relational Mapping (ORM)

## Overview

In this unit, you will teach students to use the ORM library Sequelize to connect to and seed a database. In the process, students will create and configure Sequelize models, use validation tools, encrypt a password using `bcrypt`, automate functionality with Hooks, and use SQL in literals. Students will also model relationships and relate data between SQL tables using Sequelize associations. With the help of RESTful routes, they will map HTTP verbs to CRUD actions and build custom routes that map to instance methods. Additionally, students will learn to catch errors with `try...catch` and use `async` and `await` instead of Promises. 

Refer to the [Class Content Unit Overview](../../../01-Class-Content/13-ORM/README.md) for detailed information on key topics, learning objectives, and homework.

## Instructor/TA Notes

* Take some time to review the Sequelize documentation to refamiliarize yourself with the library. Focus on implementing Hooks, validations, and associations.

* You will use MySQL in all of the activities for this unit, so be sure to have your MySQL server up and running. You can create the databases listed in each activity ahead of time, or you can prepare to demonstrate it live in class.

* Run `npm install` before the Instructor Demo to ensure that you have the full five-minute window for instruction.

* In the first activity in this unit, `01-Ins_Sequelize-Setup`, you will hardcode the database credentials in the `connection.js` file. Every subsequent activity uses a `.env` file. Make sure that you create one or rename the existing `.env.EXAMPLE` file before demonstrating each activity. 

* Instead of relying on a front end, all of the activities will use Insomnia Core to test the routes. Be sure to have it installed and ready for class.

* Day 2 introduces RESTful routes. Highlight the convention for students and tell them that they will revisit the pattern at a later point.

* The introduction to seeding in this unit differs from what students will find in the Sequelize documentation. Consider warning students about the difference in case they look for more information on seeding in the documentation.

## Career Connection

* Remind students that related Career Services material can be found in their [Career Connection folder](../../../01-Class-Content/13-ORM/04-Career-Connection/README.md).

* If you'd like more information on Career Services, visit the [Career Services resources page](https://mycareerspot.org/).

## Heads-Up

In the next unit, students will combine everything they've learned so far to create their first full-stack application&mdash;with Handlebars.js, MVC architecture, and front-end authentication.

## Helpful Links

This section contains links to this unit's lesson plans, homework, slide decks, algorithms, and resources.

### Lesson Plans

* [13.1 Lesson Plan](./01-Day_Basics/13.1-LESSON-PLAN.md)

* [13.2 Lesson Plan](./02-Day_Authentication/13.2-LESSON-PLAN.md)
  
* [13.3 Lesson Plan](./03-Day_Relationships/13.3-LESSON-PLAN.md)

### Homework

* [Unit 13 Homework](../../../01-Class-Content/13-ORM/02-Homework)

### Slide Decks

* [Unit 13: ORM](https://docs.google.com/presentation/d/1_0n8JjM6cgmDyUfqGC6crF47JItD0mn9vzvQeYqZ5OE/edit?usp=sharing)

### Algorithms

* [01: Double Triple Map](../../../01-Class-Content/13-ORM/03-Algorithms/01-double-triple-map/)

  * 📹 [Let's Code Double Triple Map!](https://2u-20.wistia.com/medias/pz1ugrv0yu)

* [02: Array Intersection](../../../01-Class-Content/13-ORM/03-Algorithms/02-array-intersection/)

* [03: Squares of a Sorted Array](../../../01-Class-Content/13-ORM/03-Algorithms/03-squares-of-a-sorted-array/)

### Resources

* [Deploy with Heroku and MySQL](https://coding-boot-camp.github.io/full-stack/heroku/deploy-with-heroku-and-mysql)

* [Sequelize documentation](https://sequelize.org/master/)

* [npm documentation on bcrypt](https://www.npmjs.com/package/bcrypt)

* [npm documentation on dotenv](https://www.npmjs.com/package/dotenv)

* [ESLint configuration user guide](https://eslint.org/docs/user-guide/configuring)

---
© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.
