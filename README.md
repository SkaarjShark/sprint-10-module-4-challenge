# RTK Query Module Project

## ✨ Requirements

1. Node >= 18.x
2. Git Bash (Windows users)
3. Redux Dev Tools Chrome extension

## ✨ Usage

1. Fork and clone repo
2. Run `npm install`
3. Run `npm run dev`
4. Load app in `http://localhost:3003`

## ✨ Prototype

[Link to a working prototype.](https://bloominstituteoftechnology.github.io/W_S10_M1_Project/)

## ✨ Instructions

Welcome to your Module Project! In this module you learned to use RTK Query to sync the state of the server with the state of the client, all handled with Redux. Make sure to code alongside your Guided Project before attempting this challenge!

In this project you will keep working on the Quotes app. Right now the application is not fetching information from a server, but using information that's hard-coded on the frontend instead: it's up to you to get this Redux app talking to a real API!

### 🥷 Tasks

**❗ Preliminary notes about your tasks:**

- Watch the first minutes of the **Solution Video** if you need help getting situated.
- There is no need to install any extra NPM dependencies.
- You will make changes to four files - roughly in this order:
  1. [quotesApi.js](./frontend/state/quotesApi.js)
  2. [store.js](./frontend/state/store.js)
  3. [Quotes.js](./frontend/components/Quotes.js)
  4. [QuoteForm.js](./frontend/components/QuoteForm.js)

#### 👉 TASK 1 - Study the prototype

The general functionality of the app will approximately match the one in [this prototype](https://bloominstituteoftechnology.github.io/W_S10_M1_Project/). Note that the prototype is not using RTK Query. Your finished app will use Redux and RTK Query to sync its state with the server via GET, POST, PUT and DELETE requests, and also display messages informing the user when the requests are in progress or when they have errored.

#### 👉 TASK 2 - Study the API with Postman

When your app is running it exposes an API on `http://localhost:9009/api/quotes` with the endpoints below. You should test them out in Postman to understand how they work. If you delete all the quotes, you can reset your server by running `npm run dev` again.

1. GET `/quotes` **returns all quotes from the server**
    - Expects no parameters nor a request body

2. POST `/quotes` **posts a new quote to the server**
    - Expects a `{ "quoteAuthor": "example author", "quoteText": "example text" }` as the request body
    - Both properties must be longer than two characters or a 422 error response is returned

3. DELETE `/quotes/:id` **removes a quote from the server**
    - Expects an actual quote ID at the end of the URL (instead of the ":id")

4. PUT `/quotes/:id` **updates the apocryphal key of a given quote**
    - Expects an actual quote ID at the end of the URL
    - Expects a `{ "apocryphal": true (or false) }` as the request body

#### 👉 TASK 3 - Wire RTK Query to the application

1. Inside [quotesApi.js](./frontend/state/quotesApi.js) **create a `quotesApi`** containing 4 endpoints: a `getQuotes` query, and `createQuote`, `toggleFake` and `deleteQuote` mutations. Do not flesh these out completely yet. We just want to scaffold and export this API so we can plug it to Redux in the next step.

2. Inside [store.js](./frontend/state/store.js) import the `quotesApi` and **connect** its reducer and its middleware to the existing Redux store.

3. Check the Redux tab of Chrome Dev Tools to make sure that RTK Query is working.

#### 👉 TASK 4 - Implement the getQuotes query, fetch a list of quotes, render the quotes to the screen

1. Inside [quotesApi.js](./frontend/state/quotesApi.js) build the `getQuotes` endpoint completely. Make sure to set a "Quotes" tag on the data returned by the server.

2. Inside [Quotes.js](./frontend/components/Quotes.js) use the `useGetQuotesQuery` hook exposed by `quotesApi` to GET the quotes from the server and render the retrieved data, instead of the hard-coded quotes found in the module.

#### 👉 TASK 5 - Implement the mutations

1. Inside [quotesApi.js](./frontend/state/quotesApi.js) build the rest of the endpoints, which are all mutations as opposed to queries.

2. Inside [QuoteForm.js](./frontend/components/QuoteForm.js) use the `useCreateQuoteMutation` hook to POST a new quote to the server.

3. Inside [Quotes.js](./frontend/state/Quotes.js) build the functionality needed to DELETE a quote and PUT a change to its `apocryphal` status.

❗ Note that this task and the next ones can be done in parallel.

#### 👉 TASK 6 - Create messages to show that requests are in progress

Inside [Quotes.js](./frontend/components/Quotes.js) and [QuoteForm.js](./frontend/components/QuoteForm.js), render messages to the screen to inform the user that requests are in flight, and test them out by throttling the speed of the requests in the Network Tab in Chrome (by selecting `Fast 3G` or `Slow 3G` from the dropdown). Design and style these messages however you like!

#### 👉 TASK 7 - Display validation problems

Inside [QuoteForm.js](./frontend/components/QuoteForm.js) render an error message to the screen if the new quote does not pass server-side validation. This is the scenario that plays out when a user sends a POST request attaching a "quoteText" (or a "quoteAuthor") shorter than 3 characters in length. The frontend purposely lacks any validation other than preventing the submission of a totally empty form.

#### 👉 TASK 8 - Watch the Solution Video

This step is only required if you need help getting started or get stuck at any point. HAVE FUN!

## FAQ

<details>
  <summary>I feel very stuck. What can I do?</summary>

Redo the Guided Project for the module, or check out the Solution Video for this project. In these recordings, an industry expert walks you through their thinking in detail, while they solve the tasks.

</details>

<details>
  <summary>I am getting errors when I run npm install. What is going on?</summary>

This project requires Node >= V18 correctly installed in order to work. Sometimes Node can be misconfigured. Try deleting `node_modules` and running `npm install`. If this fails, try deleting both `node_modules` and `package-lock.json` before reinstalling. If all fails, please request support!

</details>

<details>
  <summary>Do I need to install extra libraries with NPM?</summary>

No. Everything you need should be installed already.

</details>

<details>
  <summary>Can I edit the HTML or the CSS?</summary>

You can edit the CSS of the project to give it a personal touch so you can add it to your portfolio, but only after you've finished your tasks!

</details>

<details>
  <summary>My page does not work! How do I debug it?</summary>

Remember to use console.logs and breakpoints to troubleshoot your code. Do not panic if you see errors in the console, just read them carefully looking for clues. Also keep an eye on the Redux DevTools.

</details>

<details>
  <summary>How do I run tests against my code?</summary>

There are no automatic tests in this project. Feel free to write some, though! All necessary libraries are installed.

</details>

<details>
  <summary>I messed up and want to start over! How do I do that?</summary>

Do NOT delete your repository from GitHub! Instead, commit frequently as you work. This in practice creates restore points. If you find yourself in a mess, use git reset --hard to simply discard all changes to your code since your last commit. If you are dead-set on restarting the challenge from scratch, you can do this with Git as well. Research how to reset --hard to a specific commit.

</details>
