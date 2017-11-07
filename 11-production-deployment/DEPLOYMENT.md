![CF](https://camo.githubusercontent.com/70edab54bba80edb7493cad3135e9606781cbb6b/687474703a2f2f692e696d6775722e636f6d2f377635415363382e706e67) Lab 11: Book App Deployment Instructions
===

1. Create an organization on GitHub and add your partner(s) as collaborator(s).
1. Create a corresponding folder in your `/codefellows/301` directory.
1. Create a new repository named `book-list-client`. This will contain your frontend code.
1. Create a new repository named `book-list-server`. This will contain your backend code.
1. Clone both of these repositories into your folder. If you type the command to open the code in your code editor, such as `atom .` or `code .`, you can view both repositories together in your code editor.
1. Scaffold a basic "Hello World" app and make sure that both the frontend and backend are communicating with each other. Open up two terminal windows: from your server directory, run your server with `nodemon` and from your client directory, run `live-server`. You will need to terminate both of these processes before moving on to deployment.
1. From the command line, navigate into your server repository and enter the command `heroku create <partner 1 initials>-<partner 2 initials>-booklist`. For example, Allie and Sam would create their instance with the following command: `heroku create ag-sh-booklist`.

  - You will see your URL in the terminal, such as `https://ag-sh-booklist.herokuapp.com`.
  - Your AJAX requests should hit this Heroku application at specific endpoints. In the to-do demo, the endpoint is `https://ag-sh-booklist.herokuapp.com/books`
  - In your model file (in the to-do demo, it is `task.js`), declare a variable named `__API_URL__` and assign it the value of your new URL.
  - Note that this variable has two underscores at the beginning and the end of its name.
  - For example, `var __API_URL__ = https://ag-sh-booklist.herokuapp.com`.
  - This `__API_URL__` will be used in the AJAX requests within this file.
  - Your endpoint should follow the same pattern as the one listed above, so either remove the last `/` in the `__API_URL__` or remove the `/` in your AJAX requests, so it would appear as `${__API_URL__}books`. Keeping the `/` in the `__API_URL__` and the AJAX request will result in `//` as part of your endpoint and will cause an error.

1. Return to your terminal and make sure to add and commit your changes. Then enter the command `git push heroku master` to push your instance to Heroku.
  - Look for a completion message and the bottom that says "Verifying deploy... done."
1. Navigate to your Heroku Dashboard and confirm that your Application instance appears.
1. Click on your booklist app and go to the Resources tab. Search for "Postgres" and provision the free version to your app. This will automatically populate the `DATABASE_URL` config var in the Settings tab. Navigate to the Settings tab to verify.
1. You will also need to manually enter the `CLIENT_URL` as a config var on Heroku. Return to your terminal and navigate into your frontend code. Create a new branch called "gh-pages" with the command `git checkout -b gh-pages`. This is the branch that will deploy your site to gh-pages when it is pushed to your repo. This is the deployed version of your frontend that Heroku will be pointing to.
1. Add, commit, and push your frontend code. On GitHub, go to the frontend repo and click on Settings. Scroll down to see your deployed site. It should be in the format of: `https://todo-app-demo.github.io/todo-app-client/`.
1. Return to Heroku and paste this URL as the VALUE of the `CLIENT_URL` config var.
1. Migrate your local database to Heroku using one of the following methods.

##### Method 1:

- If your local database exists, manually push your local database to Heroku.
  - Use the following format for your command: `heroku pg:push books\_app DATABASE\_URL --app <partner 1 initials>-<partner 2 initials>-booklist`

##### Method 2:

- If your local database does not exist, manually connect your database using the `DATABASE_URL` that Postgres populated as a Heroku config var.
- This takes the format of: `postgres://knqrpsybxlro:f01eb57a1a1ad9309925fc4eec2554710ecf79d8ff3987218dd78835103@ec2-107-22-187-21.compute-1.amazonaws.com:5432/d4as4k2ei1di0`
    - In this URL, the host is `ec2-107-22-187-21.compute-1.amazonaws.com`
    - The PORT is `5432`
    - The username is `knqrpsybxlro`
    - The database is `d4as4k2ei1di0`
    - The password (if needed) is `f01eb57a1a1ad9309925fc4eec2554710ecf79d8ff3987218dd78835103`
- Use the following command format in your terminal to connect your Heroku database to your local shell: `psql -h <host> -p <port> -U <username> -W <password> <database>`
  - For this example, the command is: `psql -h ec2-107-22-187-21.compute-1.amazonaws.com -p 5432 -U knqrpsybxlptro d4as4k2ei1di0` and the password is not needed
  - The psql prompt should now appear as `d4as4k2ei1di0=>`, in this example. Now you can create your table and insert records.
