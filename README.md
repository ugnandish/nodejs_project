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

install thunder client to test HTTP request (from VS extension "Thunder Client") 

to check request in thunder client<br/>
http://localhost:5001/api/contacts

```
app.get("/api/contacts", (req, res) => {
  res.send("Get all contacts");
});
```

or to test json format

```
app.get("/api/contacts", (req, res) => {
    res.json({message: "Get all contacts"});
});
```

and to set status 200

```
app.get("/api/contacts", (req, res) => {
    res.status(200).json({message: "Get all contacts"});
});
```

create new folder "routes" and create new file "contactRoutes.js" under routes folder<br/>
add GET, POST, PUT, DELETE request in route file 

```
const express = require("express");
const router = express.Router();

router.route("/").get((req, res) => {
  res.status(200).json({message: "Get all contacts"});
});

router.route("/").post((req, res) => {
  res.status(200).json({message: "Create Contact"});
});

router.route("/:id").get((req, res) => {
  res.status(200).json({message: `Get contact for ${req.params.id}`});
});

router.route("/:id").put((req, res) => {
  res.status(200).json({message: `Update contact for ${req.params.id}`});
});

router.route("/:id").delete((req, res) => {
  res.status(200).json({message: `Delete contact for ${req.params.id}`});
});

module.exports = router;
```

and "/api/contacts" is common to all, and we use middleware as app.use("") for our API URL slash API slash context and then we are passing our contact routes

```
app.use("/api/contacts", require("./routes/contactRoutes"));
```

Create new Folder "controllers" under main folder and new file "contactController.js" under controller folder

```
//@desc Get all contacts
//@route GET /api/contacts
//@access public
const getContact = (req, res) => {
    res.status(200).json({message: "Cart all contacts"});
};

module.exports = {getContact};
```

```
cut from contactRoutes.js and paste here and update the contactController.js

(req, res) => {
    res.status(200).json({message: "Cart all contacts"});
};
```

and update the contactController.js

```
//@desc Get all contacts
//@route GET /api/contacts
//@access public
const getContacts = (req, res) => {
  res.status(200).json({message: "Cart all contacts"});
};

//@desc Create New contact
//@route POST /api/contacts
//@access public
const createContact = (req, res) => {
  res.status(201).json({message: "Create Contact"});
};

//@desc Get contact
//@route GET /api/contacts/:id
//@access public
const getContact = (req, res) => {
  res.status(200).json({message: `Get contact for ${req.params.id}`});
};

//@desc Update contact
//@route PUT /api/contacts/:id
//@access public
const updateContact = (req, res) => {
  res.status(200).json({message: `Update contact for ${req.params.id}`});
};

//@desc Delete contact
//@route DELETE /api/contacts/:id
//@access public
const deleteContact = (req, res) => {
  res.status(200).json({message: `Delete contact for ${req.params.id}`});
};


module.exports = {getContacts, createContact, getContact, updateContact, deleteContact};
```

and update the contactRoutes.js

```
const express = require("express");
const router = express.Router();
const {getContacts, createContact, getContact, updateContact, deleteContact} = require("../controllers/contactController");

// router.route("/").get(getContacts);
// router.route("/").post(createContact);
// router.route("/:id").get(getContact);
// router.route("/:id").put(updateContact);
// router.route("/:id").delete(deleteContact);

router.route("/").get(getContacts).post(createContact);
router.route("/:id").get(getContact).put(updateContact).delete(deleteContact);

module.exports = router;
```

