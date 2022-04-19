# :zap: PERN Full Stack Todo

* PostgreSQL Express React Node (PERN) full-stack app, integrates React frontend with Node.js backend. Tutorial code from [The Stoic Programmers](https://www.youtube.com/channel/UCAPuqvFWmUg_gc_AZHUBPsA) (see 'Inspiration' below)
* **Note:** to open web links in a new window use: _ctrl+click on link_

![GitHub repo size](https://img.shields.io/github/repo-size/AndrewJBateman/pern-stack-auth?style=plastic)
![GitHub pull requests](https://img.shields.io/github/issues-pr/AndrewJBateman/pern-stack-auth?style=plastic)
![GitHub Repo stars](https://img.shields.io/github/stars/AndrewJBateman/pern-stack-auth?style=plastic)
![GitHub last commit](https://img.shields.io/github/last-commit/AndrewJBateman/pern-stack-auth?style=plastic)





<h1 align="center">Hi 👋</h1>

<p align="center">
- 🌱 I’m currently learning How to create a 3-tier architecture
</p>

<p align="center">
- 💬 About : This repository contains my work from the course called Concepteur Développeur d'Applications.
</p>

<h3 align="center">Languages, Technologies and Environments:</h3>

<p align="center">
    <img src="https://img.shields.io/badge/Babel-F9DC3e?style=for-the-badge&logo=babel&logoColor=black">
    <img src="https://img.shields.io/npm/v/electron?color=blue&label=electron&logo=electron&style=for-the-badge">
    <img src="https://img.shields.io/npm/v/bootstrap?color=purple&label=bootstrap&logo=bootstrap&style=for-the-badge">
    <img src="https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white">
    <img src="https://img.shields.io/badge/figma-%23F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white">
    <img src="https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white">
    <img src="https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white">
    <img src="https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white">
    <img src="https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E">
    <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black">
    <img src="https://img.shields.io/npm/v/mongodb?color=green&label=mongodb&logo=mongodb&style=for-the-badge">
    <img src="https://img.shields.io/npm/v/mysql?color=blue&label=msql&logo=mysql&style=for-the-badge">
    <img src="https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white">
    <img src="https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white">
    <img src="https://img.shields.io/npm/v/react?color=blue&label=react&logo=react&style=for-the-badge">
    <img src="https://img.shields.io/npm/v/redux?color=purple&label=redux&logo=redux&style=for-the-badge">
    <img src="https://img.shields.io/npm/v/sass?color=pink&label=sass&logo=sass&style=for-the-badge">
    <img src="https://img.shields.io/npm/v/webpack?color=blue&label=webpack&logo=webpack&style=for-the-badge">
    <img src="https://img.shields.io/npm/v/express?color=yellow&label=express&logo=express&style=for-the-badge">
</p>





## :page_facing_up: Table of contents

* [General info](#general-info)
* [Screenshots](#screenshots)
* [Technologies](#technologies)
* [Setup](#setup)
* [Features](#features)
* [Status](#status)
* [Inspiration](#inspiration)
* [Contact](#contact)

## :books: General info

### Backend

* PostgreSQL needs to be installed and running - I started it from my Windows 10 PostgreSQL 12 dropdown option 'SQL shell (psql)'
* Postman used to test the backend before frontend was available

### Frontend

* React frontend includes a simple todo list with a user input field and a table of todos below. User can edit and delete todos.
* [JavaScript XML (JSX)](https://reactjs.org/docs/introducing-jsx.html) used to write HTML elements in Javascript
* [React Fragments](https://reactjs.org/docs/fragments.html) used to show table of todos as a row with columns in the DOM

## :camera: Screenshots

![Backend screenshot](./img/postgresql.png)
![Frontend & backend screenshot](./img/todos.png)
![Frontend screenshot](./img/edit.png)

## :signal_strength: Technologies - Backend

* [PostgreSQL v14](https://www.postgresql.org/)
* [PostgreSQL Installer for Windows](https://www.postgresqltutorial.com/install-postgresql/)
* [Express.js middleware v4](https://expressjs.com/)
* [Node.js v16](https://nodejs.org/es/)
* [Nodemon v2](https://www.npmjs.com/package/nodemon) npm module so backend server will automatically restart after code changes
* [Postman API](https://www.postman.com/downloads/) to simulate a frontend

## :signal_strength: Technologies - Frontend

* [React framework v16](https://reactjs.org/)
* [Bootstrap v4](https://getbootstrap.com/) component library

## :floppy_disk: Setup - Backend

* Change to `/server` directory
* Install dependencies using `npm i`
* Install [nodemon](https://www.npmjs.com/package/nodemon) globally if you don't already have it
* Install [PostgreSQL](https://www.postgresql.org/) & run it (requires the password you created during installation)
* Add database access credentials to `db.js` - recommend installing [npm dotenv](https://www.npmjs.com/package/dotenv) & using .env to hide credentials if commiting to Github
* Postgresql shell commands: `\l` list all databases. `\c` database1 connect to database1. `\dt` inspect tables. `\d+` inspect table & show relation information. `\q` to quit.
* Run `nodemon server` for a dev server
* `http://localhost:5000/` can be accessed for CRUD operations such as POST, GET, PUT, DELETE etc. using Postman

## :floppy_disk: Setup - Frontend

* Change to `/client` directory
* Install dependencies using `npm i`.
* run `npm start`. Frontend will open at `http://localhost:3000/`

## :computer: Code Examples - Backend

* backend `index.js`: express post method used to add new todo [description] to postgreSQL database using SQL INSERT INTO statement

```javascript
// create a todo
app.post('/todos', async (req, res) => {
  try {
    const { description } = req.body;
    const newTodo = await pool.query(
      "INSERT INTO todo (description) VALUES($1) RETURNING *",
      [description]
    );

    res.json(newTodo.rows[0]);
  } catch (err) {
    console.error(err.message);
  }
})
```

## :computer: Code Examples - Frontend

* function that runs when user presses 'Add' button: the input body (description) is converted from a JavaScript object to a JSON string & POSTed to the todo database

```javascript
  const onSubmitForm = async e => {
    e.preventDefault();
    try {
      const body = { description };
      const response = await fetch("http://localhost:5000/todos", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(body)
      });

      console.log("Successfully added todo: ", response);
      window.location = "/";
    } catch (err) {
      console.error(err.message);
    }
  };
```

## :cool: Features - Backend

* All data stored in PostgreSQL database that can also be viewed and changed from the PostgreSQL shell (psql)

## :cool: Features - Frontend

* React app created from the command prompt using [Create React App](https://reactjs.org/docs/create-a-new-react-app.html)
* Uses the [Bootstrap basic table](https://www.w3schools.com/bootstrap/bootstrap_tables.asp) to list todos
* [Bootstrap 4 Modal](https://www.w3schools.com/bootstrap4/bootstrap_modal.asp) dialog box

## :clipboard: Status & To-Do List

* Status: error in registration
* To-Do: Fix errors and complete testing

## :clap: :wrench: Inspiration/General Tools

* [PERN Stack Course - PostgreSQL, Express, React and Node](https://www.youtube.com/watch?v=ldYcgPKEZC8&t=116s)
* [Youtube video: Learn Database Design by combining our JWT and PERN stack Todo List app together Part 1](https://www.youtube.com/watch?v=l3njf_tU8us)
* [Youtube video: Learn Database Design by combining our JWT and PERN stack Todo List app together, part 2](https://www.youtube.com/watch?v=25kouonvUbg)
* [Youtube video: How to Deploy a PERN application on Heroku](https://www.youtube.com/watch?v=ZJxUOOND5_A)
* [React documentation](https://reactjs.org/docs/getting-started.html)
* [Enable Emmet support for JSX in Visual Studio Code | React](https://medium.com/@eshwaren/enable-emmet-support-for-jsx-in-visual-studio-code-react-f1f5dfe8809c)
* [js-beautify for VS Code](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)

## :file_folder: License

* N/A

## :envelope: Contact

* Repo created by [ABateman](https://github.com/AndrewJBateman), email: gomezbateman@yahoo.com
