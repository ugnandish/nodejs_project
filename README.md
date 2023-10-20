In this project you will learn below topics

First Step: Express Project Setup

Second Step: Create Express Server 

Third Step: Thunder Client Setup - to test our api's

Fourth Step: Express Router Setup

Fifth Step: Error Handling & Async Handler

Sixth Step: Express Middleware

Seventh Step: MongoDB Setup

Eighth Step: Mongoose Schema

Ninth Step: CRUD API

Tenth Step: User Authentication

Eleventh Step: Registration & Login API

Twentieth Step: Controllers & DB Operations

Thirteen Step: Password Hashing & Comparing

Fourteenth Step: Sign/Verify JWT Token

Sixteenth Step: Handle Relationships

Seventeenth Step: User Authorization

Eighteenth Step: API Testing


<h1>Contact Manager App</h1>

Overview REST API Convention

<table>
  <tr>
    <th>CRUD Actions</th>
    <th>HTTP Method</th>
    <th>Endpoints</th>
  </tr>
  <tr>
    <td>Get all contacts</td>
    <td>GET</td>
    <td>/api/contacts</td>
  </tr>
  <tr>
    <td>Get contact</td>
    <td>GET</td>
    <td>/api/contacts/:id</td>
  </tr>
  <tr>
    <td>Create contact</td>
    <td>POST</td>
    <td>/api/contacts</td>
  </tr>
  <tr>
    <td>Update contact</td>
    <td>PUT</td>
    <td>/api/contacts/:id</td>
  </tr>
  <tr>
    <td>Delete contact</td>
    <td>DELETE</td>
    <td>/api/contacts/:id</td>
  </tr>
</table>

<h3>Install Nodejs</h3>
<h3>Install Visual Studio</h3>

<h3>Open Terminal</h3>
<p>mkdir mycontacts-backend</p>
<p>cd mycontacts-backend</p>
<p>install init - npm init</p>
<p>install express - npm install express</p>
<p>install nodemon - npm i -D nodemon</p>
<p>install dotenv - npm i dotenv (create new file .env)</p>
<p>run dev - npm run dev</p>

<h4>Update the server.js</h4>
```
const express = require("express");
const dotenv = require("dotenv").config();

const app = express();

const port = process.env.PORT || 5000;

app.listen(port, () => {
    console.log(`server running on port ${port}`);
});
```

<h4>Update the .env</h4>
```
PORT=5001
```