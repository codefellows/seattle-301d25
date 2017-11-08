![CF](https://camo.githubusercontent.com/70edab54bba80edb7493cad3135e9606781cbb6b/687474703a2f2f692e696d6775722e636f6d2f377635415363382e706e67) 12: Client-side Routing w/ PageJS
===

## Submission Instructions
- Continue working in the same repository from yesterday
- Complete any feature tasks from Lab 11
- Check out a new branch for today's lab assignment, semantically named `pagejs` or something similar. It should include all of the completed code from yesterday's assignment.
- Complete your **Feature Tasks for the day**
- Create a Pull Request back to `master`
- Submit a link to your pull request on Canvas **Including the following:**
  - A question within the context of today's lab assignment
  - An observation about the lab assignment, or related 'Ah-hah!' moment
  - How long you spent working on this assignment
- Submit a link to your deployed application on Heroku

## Resources
- [PageJS Docs](https://visionmedia.github.io/page.js/)
- [Book Store Wireframe](./wireframes)

## Configuration
- `ENV VARS` - Paste the following code snippet into your terminal window:
  * _Reminder: these will be temporary while the current shell session (window) is open_
```
export PORT=3000
export CLIENT_URL='http://localhost:8080'
export DATABASE_URL='postgres://localhost:5432/books_app'
```

_Your repository must include:_
- `README.md` - with documentation regarding your lab, and it's current state of development
- `.gitignore` - with standard NodeJS configurations
- `.eslintrc.json` - with Code 301 course standards for the linter

_Your `book-list-server` repository must also include:_
- `package.json` - with all dependencies and any associated details related to configuration

```sh
. # book_app_week_3/
├── README.md
├── book-list-client
│   ├── data
│   │   └── books.json
|   ├── .eslintrc.json
|   ├── .gitignore
│   ├── index.html
|   ├── README.md
│   ├── scripts
│   │   ├── models
│   │   │   └── book.js
│   │   └── views
│   │       ├── book-view.js
│   │       ├── error-view.js
│   │       └── routes.js
│   └── styles
│       ├── base.css
│       ├── fonts
│       │   ├── icomoon.eot
│       │   ├── icomoon.svg
│       │   ├── icomoon.ttf
│       │   └── icomoon.woff
│       ├── icons.css
│       ├── layout.css
│       ├── modules
│       │   ├── book-main.css
│       │   ├── detail-main.css
│       │   ├── error.css
│       │   ├── footer.css
│       │   ├── form-main.css
│       │   └── header.css
│       └── reset.css
└── book-list-server
  ├── .eslintrc.json
  ├── .gitignore
  ├── package-lock.json
  ├── package.json
  ├── README.md
  └── server.js
```

## User Stories & Feature Tasks

#### Overview

Add functionality to the book list application for viewing a single book's details and adding a new book the to database. This includes client-side routing using PageJS.

*As a user, I want to request information about a single book so that I can view additional details.*

- Add an endpoint for a `GET` request to `/api/v1/books/:id`.
  - This should allow the client to make a request for a singular book, which returns the details of that record from the DB.
- Create a new static method to interact with your Book model, such as `fetchOne`.

*As a user, I want the ability to add new books to my app so that my collection continues to grow.*

- Add an endpoint for a `POST` request to `/api/v1/books`.
  - This should allow the client to send a new book record to the backend and persist that record in the DB.
- Create a new static method to interact with your Book model, such as `create`.

*As a user, I want my app to redirect me to the home page on any other endpoint.*

- Add an endpoint that will catch any other requests to your API and return the user to your client-side home route.

*As a user, I want my booklist to be a mobile-friendly single-page application so that I can view it on my mobile device.*

- Create a Controller file called `routes.js` and add the following endpoints:
  - `/` - List View: Books by `title` and `author` with the `image_url` displaying a rendered image of the book
  - `/books/:book_id` - Detail View of one complete book record
  - `/books/new` - Form View that will allow the user to enter a new record into the DB
    - Your form should take the following inputs: `title`, `author`, `isbn`, `image_url`, and `description`
    - On Submit: this form should `POST` a new record to the `/api/v1/books` route on the backend
- Redeploy your application.

*As a user, I want my application to be clean and free of visual distractions so that I can view my books without other content cluttering the viewport.*

- Include a hamburger menu that will allow the ability to navigate between the `/` and `/new` views
  - _NOTE: Users should be able to navigate to a `/books/:book_id` detail view by selecting that record from the main View._
- Redeploy your application.

*As a user, I want a simple, clean looking UI so that my application is easy to navigate.*

- Style your site using a *mobile-only* approach. Use the provided wireframes as a general guideline for the _minimum styling requirements_, while adding your own personal taste and color palette.
- Ensure the proper use of SMACCS principles.
  - Your `modules.css` will probably become larger today, which means that you should exercise SMACSS further by modularizing that stylesheet into a `modules/` dir with a file for each `component` of your site.
- Continue to iterate on your styles. For example, begin to include standardized styles such as a color palette and defined font families.

## Stretch Goals

*As a developer, I want to explore further functionality so that I can continue to improve the user's experience.*

- Implement the ability for your hamburger menu to operate without the use of JavaScript. You will need to research how to enable a 'pop-up/out' style menu with vanilla HTML and CSS.
- Consider any further UI/UX features which will allow a more friendly interface for your users.

## Documentation
_Your README.md must include:_
```md
# Project Name

**Author**: Your Name Goes Here
**Version**: 1.1.0 (increment the patch/fix version number up if you make more commits past your first submission)

## Overview
<!-- Provide a high level overview of what this application is and why you are building it, beyond the fact that it's an assignment for a Code Fellows 301 class. (i.e. What's your problem domain?) -->

## Getting Started
<!-- What are the steps that a user must take in order to build this app on their own machine and get it running? -->

## Architecture
<!-- Provide a detailed description of the application design. What technologies (languages, libraries, etc) you're using, and any other relevant design information. -->

## Change Log
<!-- Use this are to document the iterative changes made to your application as each feature is successfully implemented. Use time stamps. Here's an examples:

01-01-2001 4:59pm - Application now has a fully-functional express server, with GET and POST routes for the book resource.
## Credits and Collaborations
<!-- Give credit (and a link) to other people or resources that helped you build this application. -->

-->
```
