![CF](https://camo.githubusercontent.com/70edab54bba80edb7493cad3135e9606781cbb6b/687474703a2f2f692e696d6775722e636f6d2f377635415363382e706e67) 14: REST & APIs
===

## Overview

This is an individual stand-alone assignment and does not apply to the books app you have been working on this week. You will be obtaining a unique token from GitHub and making a secure proxied request to the GitHub API using an npm package called superagent. You will be  _Note: You may have already completed some of these steps if you followed along with the demo in class._

## Assignment Tasks

- Fork the [lab repository](https://github.com/codefellows/301-14-github-api) and clone it to your local machine. Don't forget to `npm i` to install the dependencies and set your `PORT` as a local environment variable.
- Obtain a token from GitHub, as demonstrated in class. Make sure to copy and save your token somewhere because this is the *only* time you are able to view it. If you forget to copy and save your token, you can delete it and generate a new one.
- Use the token to make an AJAX request to GitHub for a list of your repositories, following the steps as demonstrated in class:
  - Use the command `npm install -S superagent` to bring in this new package for making proxies to the GitHub API. Don't forget to include superagent in server.js.
  - Create a new `GET` route in your server to the `/github/*` endpoint.
  - Use superagent to proxy the correct url. _Hint: req.params[0] will be used!_ Your proxy will also need to include your token for authorization.
  - Refactor your client-side route into a `$.get` request to the correct endpoint.
  - To test locally, export the `GITHUB_TOKEN` as a local environment variable and confirm that your repositories are displaying in the browser.
  - Add and commit your changes.
  - Deploy your app on Heroku from the command line using `heroku create <name-of-your-app>` and then `git push heroku master`.
  - Store your token as a `config var` on Heroku. Your deployed application should not have your token exposed in your AJAX request and should not be in a separate file that you list in your `.gitignore`. You are welcome to practice these processes on your own, but should not do so in your submitted lab assignment.
- Submit a link to your deployed site in Canvas.
