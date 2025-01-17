# 03.5 Full-Time Lesson Plan: Server-side APIs

## Overview 

In this lesson, students will review topics they've learned throughout the course so far to help prepare them for the mini-project and homework. They'll also learn how to set up a GitHub repository for collaboration and how to actually collaborate with others on an application. The purpose of this lesson is to show students how everything they've learned is used in a slightly bigger application.

`Overview: Complete activities 21-27 in Unit 06`

## Instructor Notes

* In this lesson, students will complete activities `21-Ins_Review-Part-One` through `27-Stu_Mini-Project`.

* Because today is more about review than introducing new material, the first two instructor demos and student activities will demonstrate the same application at different complexity levels. Please take a minute or two to review each variation and identify talking points of your own if you find something worth mentioning.

* The two Git activities are intended to train students on collaborating with others in a single repository. If time allows, walk students through all the steps and demonstrate how it works.

* Remind students to do a `git pull` of the class repo to have today's activities ready and open in VS Code. 

* If you are comfortable doing so, live-code the solutions to the activities. If not, just use the solutions provided and follow the prompts and talking points for review.

* Let students know that the Bonus at the end of each activity is not meant to be extra coding practice, but instead is a self-study on topics beyond the scope of this unit for those who want to further their knowledge.

* If the students struggle with the `Everyone Do: Git` activity, walk through it with the students using the talking points provided. Otherwise, support the students as they do the activity and do a brief review at the end. 

## Learning Objectives

By the end of class, students will be able to:

* Reverse-engineer and learn from reviewing larger applications.

* Set up their GitHub repositories for a collaborative environment.

* Successfully collaborate with others in a single GitHub repository.

* Build a larger-scale application that uses all their previously learned skills.

## Time Tracker

| Start   | #  | Activity Name                      | Duration |
|---      |--- |---                                 |---       |
| 10:00AM | 1  | Instructor Do: Stoke Curiosity     | 0:10     |
| 10:10AM | 2  | Instructor Demo: Review Part One   | 0:05     |
| 10:15AM | 3  | Student Do: Review Part One        | 0:15     |
| 10:30AM | 4  | Instructor Review: Review Part One | 0:10     |
| 10:40AM | 5  | Instructor Demo: Review Part Two   | 0:05     |
| 10:45AM | 6  | Student Do: Review Part Two        | 0:15     |
| 11:00AM | 7  | Instructor Review: Review Part Two | 0:10     |
| 11:10AM | 8  | Instructor Demo: Git Repo Setup    | 0:05     |
| 11:15AM | 9  | Student Do: Git Repo Setup         | 0:15     |
| 11:30AM | 10 | Instructor Review: Git Repo Setup  | 0:10     |
| 11:40AM | 11 | Everyone Do: Git Collaboration     | 0:20     |
| 12:00PM | 12 | BREAK                              | 0:30     |
| 12:30PM | 13 | Instructor Demo: Mini-Project      | 0:05     |
| 12:35PM | 14 | Student Do: Mini-Project           | 0:60     |
| 1:35PM  | 15 | Instructor Review: Mini-Project    | 0:10     |
| 1:45PM  | 16 | Introduce Homework                 | 0:05     |
| 1:50PM  | 17 | FLEX                               | 0:40     |
| 2:30PM  | 18 | END                                | 0:00     |

---

## Class Instruction

### 1. Instructor Do: Stoke Curiosity (10 min)

* Welcome students to class.

* Congratulate the class on how much they've learned up to this point, as their new skills in working with server-side APIs have prepared them to build more complex applications.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * 🙋 How have we used HTML, CSS, and JavaScript together?

  * ☝️ We use HTML to put the page together, CSS to style the page, and JavaScript to handle any updates or changes that occur on the page.

  * 🙋 What name do we use to classify tools like Fetch, Document, Console, or even jQuery?

  * ☝️ They are all **APIs**, or **application programming interfaces**.

  * 🙋 Are these built into the JavaScript language?

  * ☝️ No, they are collections of custom JavaScript functionality designed to extend development capabilities.

  * 🙋 What about data? How can we use data that we don't explicitly create within an application?

  * ☝️ We can request that data using the Fetch API and print response data to the page.

  * 🙋 Do we know how to do all of these things?

  * ☝️ Yes, we do!

* Explain that we will spend today synthesizing everything we've learned up to this point so that we can see how it works in a larger application. Larger applications require more developers on a single project, so we'll also learn how to collaborate using Git and GitHub.

### 2. Instructor Demo: Review Part One (5 min) 

* Open `21-Ins_Review-Part-One/index.html` in your browser and demonstrate the following:

  * 🔑 When we search for a GitHub user, a list of their repositories and the number of repository issues appear.

  * 🔑 We can also filter by a specific coding language to find the most popular repos in that language.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How would we build this?

  * 🙋 We'll use HTML, CSS, JavaScript, and Fetch to query GitHub's API. In other words, we'll use everything we've learned so far!

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `22-Stu_Review-Part-One/README.md`.

### 3. Student Do: Review Part One (15 min) 

* Direct students to the activity instructions found in `22-Stu_Review-Part-One/README.md`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 📐 Add Comments to Implementation of Git It Done Application: Part One 

  Work with a partner to add comments describing the functionality of the code found in the HTML and JavaScript files in [Unsolved](./Unsolved)

  ## 📝 Notes

  Refer to the documentation: 

  [GitHub API documentation](https://docs.github.com/en/rest/overview/resources-in-the-rest-api)

  ---

  ## 🏆 Bonus

  If you have completed this activity, work through the following challenge with your partner to further your knowledge:

  * What are some examples of open source software that we can contribute to on GitHub?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 4. Instructor Review: Review Part One (10 min)  

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with how this application works? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points:

  * ✔️ Font Awesome icons

  * ✔️ HTML data attributes and `.getAttribute()`

  * ✔️ Query URL with params

* Open `22-Stu_Review-Part-One/Solved/index.html` in your IDE and explain the following: 

  * 🔑 We use the library called Font Awesome to include SVG-based icons in the HTML, as shown in the following code:

    ```html
    <!-- In the <head> -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.11.2/css/all.min.css">

    <!-- In the <body> -->
    <h1 class="app-title">
      <!-- The `<i>` element is for icons. These classes come from the Font Awesome font icon library. -->
      <i class="fab fa-github"></i> Git it Done!
    </h1>
    ```

  * 🔑 We use HTML data attributes on the language buttons so that we can read the value when the button is clicked to form a request in `homepage.js`, as follows:

    ```html
    <!-- These data-attribute values will be used to search for repositories when a button is clicked. -->
    <button data-language="javascript" class="btn">JavaScript</button>
    <button data-language="html" class="btn">HTML</button>
    <button data-language="css" class="btn">CSS</button>
    ```

  * We create an empty HTML element to be a container to hold response data from the GitHub API, as shown in the following example:

    ```html
    <div class="col-12 col-md-8">
      <h2 class="subtitle">Showing Repositories for: <span id="repo-search-term"></span></h2>
      <!-- There needs to be an empty HTML element for us to write repository data to. -->
      <div id="repos-container" class="list-group"></div>
    </div>
    ```

* Open `22-Stu_Review-Part-One/Solved/assets/js/homepage.js` in your IDE and explain the following: 

  * 🔑 We read the HTML data attributes from the buttons when we click them, as follows:

    ```js
    // In `homepage.js`
    var buttonClickHandler = function (event) {
      // `event.target` is a reference to the DOM element of what programming language button was clicked on the page
      var language = event.target.getAttribute('data-language');

      // If there is no language read from the button, don't attempt to fetch repos
      if (language) {
        getFeaturedRepos(language);

        repoContainerEl.textContent = '';
      }
    };
    ```

  * 🔑 We piece together the query URL before making the API request to GitHub and add parameters as needed, as shown in the following example:

    ```js
    var apiUrl = 'https://api.github.com/search/repositories?q=' + language + '+is:featured&sort=help-wanted-issues';
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [GitHub API documentation](https://docs.github.com/en/rest/overview/resources-in-the-rest-api), and stick around for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 5. Instructor Demo: Review Part Two (5 min) 

* Open `23-Ins_Review-Part-Two/index.html` in your browser, search for a GitHub user or select a button to display repos, and demonstrate the following:

  * 🔑 Now when we select one of the repositories, we're taken to a second page, where we get the list of issues for the repository.

  * 🔑 We get that information by including the repository name in the URL as a parameter (i.e., `single-repo.html?repo=angular-ui/ui-grid`) and searching for that repo.

* Open `23-Ins_Review-Part-Two/assets/js/homepage.js` in your IDE and explain the following:

  * We create those URLs when we write the repos to the page in the `displayRepos()` function, as shown in the following code:
  
    ```js
    var repoEl = document.createElement('a');
    repoEl.classList = 'list-item flex-row justify-space-between align-center';
    repoEl.setAttribute('href', './single-repo.html?repo=' + repoName);
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How would we get that information from the URL on the second page?

  * 🙋 We could use the browser's `location` object!

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `24-Stu_Review-Part-Two/README.md`.

### 6. Student Do: Review Part Two (15 min) 

* Direct students to the activity instructions found in `24-Stu_Review-Part-Two/README.md`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 📐 Add Comments to Implementation of Git It Done Application: Part Two 

  Work with a partner to add comments describing the functionality of the code found in [single.js](./Unsolved/assets/js/single.js).

  ## 📝 Notes

  Refer to the documentation: 

  [GitHub API documentation](https://docs.github.com/en/rest/overview/resources-in-the-rest-api)

  ---

  ## 🏆 Bonus

  If you have completed this activity, work through the following challenge with your partner to further your knowledge:

  * For an open source contributor, what is the significance of knowing whether an issue has an associated pull request or not?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 7. Instructor Review: Review Part Two (10 min)  

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with an application scaled out like this? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points:

  * ✔️ URL search params

  * ✔️ API response pagination

  * ✔️ Nothing to display

* Open `24-Stu_Review-Part-Two/Solved/assets/js/single.js` in your IDE and explain the following: 

  * 🔑 We retrieve the repository name from the URL in `getRepoName()` so that we can use it in a `fetch()` request, as shown in the following code:

    ```js
    // This is coming from the URL search bar in the browser. It is what comes after the `?`.
    var queryString = document.location.search;
    var repoName = queryString.split('=')[1];
    ```

  * If there is no repo name in the URL, then let's send the user back to the homepage, as follows:

    ```js
    document.location.replace('./index.html');
    ```

  * 🔑 Because GitHub only returns 30 issues at a time, we should check whether there are more than 30 and let users know about it. As shown in the following example, GitHub alerts us with a `Link` property in the response header that gives us the next query URL, in case we want to display the next 30 issues:

    ```js
    // See this value in the Chrome DevTools network tab
    if (response.headers.get('Link')) {
      displayWarning(repo);
    }
    ``` 

  * 🔑 If we search a repository that has no issues, instead of displaying a blank screen, we should let users know with the following code in `displayIssues()`:

    ```js
    if (issues.length === 0) {
      issueContainerEl.textContent = 'This repo has no open issues!';
      return;
    }
    ``` 

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ Why would GitHub limit its API response size to 30 issues?

  * 🙋 If a server were to respond with all possible data, it could impact the performance of the request and slow down the application. 

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material and stick around for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 8. Instructor Demo: Git Repo Setup (5 min) 

* Open the [React GitHub repo](https://github.com/facebook/react)&mdash;or any other repository that you don't have write access to&mdash;in your browser, and demonstrate the following:

  * 🔑 By default, we can clone anyone's repository to the machines and make as many commits as we want to the codebase.

  * 🔑 However, we can't push any code back up to the repository if we don't have permission to do so.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How can we set up the repository to allow other users to contribute directly?

  * 🙋 GitHub has settings for that!

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `25-Stu_Git-Repo-Setup/README.md`.

### 9. Student Do: Git Repo Setup (15 min) 

* Direct students to the activity instructions found in `25-Stu_Git-Repo-Setup/README.md`.

* Break your students into pairs that will work together on this activity. 

* While everyone is working on the activity, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 10. Instructor Review: Git Repo Setup (10 min)  

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel setting up repositories? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points:

  * ✔️ `.gitignore` file

  * ✔️ Branch protection

  * ✔️ Adding collaborators

* Open a repository that you own or create a new one on [GitHub](https://github.com) in your browser and demonstrate the following: 

  * 🔑 After creating the repository, it's best that the repository owner creates some of the boilerplate files such as the `.gitignore` file.

  * 🔑 In the repository settings, we make it so that no new code can be merged into the `main` branch without at least one other reviewer. This way, no one on a team can autonomously merge code into production.

  * 🔑 We can also add collaborators directly by looking them up and inviting them.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ Why would we want to enforce code review?

  * 🙋 All developers, no matter their intentions, are prone to errors. It's best to have at least one person look at the code before merging.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, see the [GitHub documentation on collaboration with issues and pull requests](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests), and stick around for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `26-Evr_Git-Collaboration/README.md`.

### 11. Everyone Do: Git Collaboration (20 min)

* Open the [GitHub guide on collaboration flow](https://guides.github.com/introduction/flow/) in your browser and explain the following:

  * When multiple developers collaborate on a single project, establishing a workflow that everyone agrees on is crucial to success.

  * The typical workflow consists of each developer creating their own branches to work on separate parts of the application, pushing that branch up and opening a pull request, reviewing that pull request, and ultimately merging the updated code into `main`.

  * Communication around a project is as important as the actual code being written. No developer should autonomously make decisions that affect the product without the input and review of the other developers. 

* Direct students to the activity instructions found in `26-Evr_Git-Collaboration/README.md`.

* While everyone is working on the activity, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

* If time allows, set up this demonstration yourself, with other instructional staff or students as collaborators, and walk through the guide to demonstrate the following: 

  * When we want to start work on a new feature, we create a new branch, as follows:

    ```bash
    git checkout -b feature/awesome-feature

    # or like this...
    git branch feature/awesome-feature
    git checkout feature/awesome-feature
    ```

  * We do the work, commit and push the branch, and then open a pull request and add the collaborators as reviewers. Because we protected the `main` branch, we need someone else to review and merge for us.

  * The reviewers now have to look at this pull request, review the updates to the project, and either request changes or approve the pull request.

  * When the pull request is merged to `main`, everyone should get their local branches in sync so that all updated code is in place.

* Explain that the Git and GitHub workflow is not an exact science. It's okay if merge conflicts or errors happen every once in a while. The key to smooth development processes is communication and cooperation amongst collaborators.

* Answer any questions before students go on break.

### 12. BREAK (30 min)

### 13. Instructor Demo: Mini-Project (5 min) 

* Open `27-Stu_Mini-Project/Main/index.html` in your browser and demonstrate the following:

  * 🔑 When we search for information from the Library of Congress API, we see the results on another page.

  * 🔑 We can fine-tune the search by adding a format that the Library of Congress API understands.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How would we build this?

  * 🙋 By using HTML, CSS, JavaScript, and server-side APIs!

* Answer any questions before allowing students to start the mini-project.

### 14. Student Do: Mini-Project (60 min)

* Direct students to the activity instructions found in `27-Stu_Mini-Project/README.md`.

* Break your students into groups that will work together on this activity.

  ```md
  # Unit 06 Mini-Project: Library of Congress Search Tool

  In this activity, you will work with a group to build an application that searches and displays results from the Library of Congress API.

  ## Instructions

  The completed application should meet the following criteria:

  * As a user, I can submit a search query from the application to request data and receive a response from the Library of Congress.

  * As a user, I can either perform a generic search for data in all formats or I can select a format in the form to help filter results.

  * As a user, I can see all of the results of my search displayed on a separate page.

  * As a user, I can conduct additional searches from the results page as well.

  To learn about how to use this API, see the Requests section of the [Library of Congress API documentation.](https://libraryofcongress.github.io/data-exploration/)

  ### The Homepage

  The homepage (`index.html`) should have the following:

  * A simple, well thought-out UI.

  * A form with a text input field to capture a search query and an option select dropdown to capture the format of the search query. The options in the dropdown should be a list of the possible format values listed in the [Library of Congress API documentation on requests](https://libraryofcongress.github.io/data-exploration/requests.html#format).

  * A browser event listener attached to the form to execute a function on submission, which will capture both form values and redirect the user to a search results page with those values included in the URL as query parameters. This will use the browser's `location.replace()` method.

  * If there is no format selected from the dropdown, the URL should look something like the following example:

      ```http
      /search-results.html?q=dogs&format=
      ```

  * If there is a format selected from the dropdown, the URL should look something like the following example:

      ```http
      /search-results.html?q=dogs&format=photos
      ```

  ### The Search Results Page

  The search results page (`search-results.html`) should have and do the following:

  * On page load, if there are query parameters, immediately parse them and use them in a request URL to fetch data from the Library of Congress API.

  * If there is a value for the format query parameter, use the format endpoint to search for something based on the chosen format. For more information, see the [Library of Congress API documentation on the format endpoint](https://libraryofcongress.github.io/data-exploration/requests.html#format).

  * If there is no value for the format query parameter, use the search endpoint to search for all types of data. For more information, see the [Library of Congress API documentation on the search endpoint](https://libraryofcongress.github.io/data-exploration/requests.html#search).

  * The response from the API request will then be displayed on the page. It is up to you and your team to determine which data should be displayed from the overall `response` object, but you must use data from the `results` property in the `response` object. For more information, see the [Library of Congress API documentation on responses](https://libraryofcongress.github.io/data-exploration/responses.html).

  * The same form from the homepage should be here as well. Instead of redirecting a user to another page, however, it will perform a search right on the page and display the new results.

  ## Assets

  The following image demonstrates the homepage's appearance and functionality:

  ![The homepage shows a search bar that can select a format from a dropdown menu.](./Images/01-homepage.png)

  The following image demonstrates the search results page's appearance and functionality:

  ![The search results page displays results from a search conducted in the form on the left side of the page.](./Images/02-search-results-page.png)

  ---

  ## 💡 Hints

  Will every result have the same data? If not, how will we handle printing it to the page? Can the form design and functionality from the homepage be reused for the search results page?

  ## 🏆 Bonus

  * How can we build this application using our knowledge in Git collaboration? 
  ```

* While breaking everyone into groups, be sure to remind students and the rest of the instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 15. Instructor Review: Mini-Project  (10 min)  

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with this mini-project? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points:

  * ✔️ The Library of Congress API documentation

  * ✔️ Passing params from page to page

  * ✔️ Reusing search functionality

* Open `https://libraryofcongress.github.io/data-exploration/requests.html` in your browser and explain the following: 

  * 🔑 We can see exactly how to use this API through their documentation. This way we can study how to create a request to multiple endpoints depending on whether there's a format or not.

* Open `https://libraryofcongress.github.io/data-exploration/responses.html` in your browser and explain the following: 

  * 🔑 We also must study which data returns from the API so that we can determine what should or shouldn't be displayed on the page.

* Open `27-Stu_Mini-Project/Main/assets/js/script.js` in your IDE and explain the following: 

  * 🔑 On form submission, we gather the form inputs and use them as search parameters on the search results page, as follows:

    ```js
    var searchInputVal = document.querySelector('#search-input').value;
    var formatInputVal = document.querySelector('#format-input').value;

    if (!searchInputVal) {
      console.error('You need a search input value!');
      return;
    }

    var queryString = './search-results.html?q=' + searchInputVal + '&format=' + formatInputVal;
    ```

  * As shown in the following example, we use `location.assign()` to maintain correct functionality of the Back button in the browser&mdash;which wouldn't be the case if we were to use `location.replace()`:

    ```js
    var queryString = './search-results.html?q=' + searchInputVal + '&format=' + formatInputVal;

    location.assign(queryString);
    ```

* Open `27-Stu_Mini-Project/Main/assets/js/display-search.js` in your IDE and explain the following: 

  * 🔑 On page load, we execute the `getParams()` function to retrieve the search params from the URL and use them for a `fetch()` request, as follows:

    ```js
    function getParams() {
      var searchParamsArr = document.location.search.split('&');

      var query = searchParamsArr[0].split('=').pop();
      var format = searchParamsArr[1].split('=').pop();

      searchApi(query, format);
    }
    ```

  * 🔑 We want search functionality to occur on this page as well, so we reuse the functionality from `script.js` in `display-search.js` and modify it to make an API request, as shown in the following example:

    ```js
    function handleSearchFormSubmit(event) {
      event.preventDefault();

      var searchInputVal = document.querySelector('#search-input').value;
      var formatInputVal = document.querySelector('#format-input').value;

      if (!searchInputVal) {
        console.error('You need a search input value!');
        return;
      }

      searchApi(searchInputVal, formatInputVal);
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What happens if a search returns with no entries?

  * 🙋 We print a message to the screen informing the user so that they don't think something's wrong.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [Library of Congress API documentation](https://libraryofcongress.github.io/data-exploration/), and stick around for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 16. Instructor Demo: Introduce Homework (5 min)

* Open `02-Homework/Main/index.html` in your browser and demonstrate the following:

  * We will build a weather application that gives us a five-day forecast.

  * The previous searches also get added to the left column so that we can quickly search again.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What are we learning?

  * 🙋 How to build applications that use external data.

  * ☝️ How does this project build off or extend previously learned material?

  * 🙋 We'll have to use HTML, CSS, JavaScript, and server-side APIs to build this. In other words, we'll bring together all of the skills we've picked up so far!

  * ☝️ How does this project relate to your career goals?

  * 🙋 Most applications on the web today rely on making requests to an API for data. You will be hard-pressed to find a development job that doesn't involve server-side APIs in some way.

* Ask TAs to direct students to the Homework Requirements found in `02-Homework/README.md`.

### 17. FLEX (40 min)

* This time can be utilized for reviewing key topics learned so far in this unit or getting started on the homework.

* Ask the students if there is anything they would like to review from Unit 05 and 06.

* Answer any questions before ending the class.

### 18. END (0 min)

How did today’s lesson go? Your feedback is important. Please take 5 minutes to complete this [anonymous survey](https://forms.gle/RfcVyXiMmZQut6aJ6).

---
© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.