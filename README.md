## EXPRESS-JS DOCUMENTATION

Thanks for visiting my GitHub account!

<img src ="https://ajeetchaulagain.com/static/7cb4af597964b0911fe71cb2f8148d64/87351/express-js.png" height = "200px" width = "120px"/> **Express-js**, or simply **Express**, is a back end web application framework for building RESTful APIs with Node.js, released as free and open-source software under the MIT License. It is designed for building web applications and APIs. It has been called the de facto standard server framework for Node.js. [more](https://www.geeksforgeeks.org/express-js/)

## Source Code (Download)

[Click Here](https://mega.nz/folder/RGFiUApD#PoKIVCwF8IkQhE2PHw1XxQ)

## Required Software (Download)

- VS Code, Download ->https://code.visualstudio.com/download
- Node, Download-> https://nodejs.org/en/download
- MongoDB Shell(msi) , Download-> https://www.mongodb.com/try/download/shell
- MongoDB Compass (msi), Download-> https://www.mongodb.com/try/download/community
- Postman, Download-> https://www.postman.com/downloads/

**Or Online Database (MongoDB Atlas)**

- Register -> https://www.mongodb.com/cloud/atlas/register

## ========== Environment Setup ==========

1. Install Node.js
2. To verify installation into command form by node -v
3. For initialization npm write the query in the command window as npm init -y
4. Setup the opening file into the package.json and change the file with main:'server.js'
5. To create a server using the express package then write a query into the command window as npm install express.
   Write code in the server file for initialization
   const express = require("express");
   const app = express();
   app.listen(3000, () => {
   console.log("Server is running at http://localhost:3000");
   });

6. Install the nodemon package for automatically running the server as- npm i --save-dev nodemon (For Developing purpose)
7. setup the package.json file in the scripts key, write
   "scripts": {
   "start": "node ./resources/backend/server.js",
   "dev": "nodemon ./resources/backend/server.js",
   "test": "echo \"Error: no test specified\" && exit 1"
   },
8. use the Morgan package for automatic restart. Hence install the morgan package as npm install --save-dev morgan (Development purpose)
   Write code in the server file for initialization
   const morgan = require("morgan");
   app.use(morgan("dev")); --> Middlewire.
9. Install Postman software for API testing by the URL endpoint.
10. Install Mongobd + MongobdCompass and Mongoshell (For Database)

## ========== Connect MongoDB Database ==========

1. Install Mondodb + Mongodb Compass and Mongodb Shell download from the google.
2. Set up Environment Variable in drive:c/program file
3. Create a directory in the base path of the c drive named data. Inside the data directory create another folder db.
4. Write the command in the CMD window as Mongod. And write the other command in the other CMD window as mongosh.
5. Then Check the version as mongod --version and mongosh --version.
6. Install mongoose package as npm i mongoose
7. Create an atlas account. In the atlas account create a cluster that have a user(as atlas admin) and network access with any access IP address.
8. Connect the database using URL from the atlas cluster or local Mongodb compass using the mongoose package as mongoose. connect('mongodb://localhost:27017/database-name);

## Total Chapters are following

2. Express.js
   1. introduction to express.js
   2. express server
   3. http methods and postman
   4. Express Router
   5. HTTP Response
   6. HTTP Request part-1
   7. HTTP Request part-2
   8. HTTP Request part-3
   9. send and receive from data
   10. Area Calculator
   11. How to set .env variables
   12. Middlewares
   13. express static Middlewares
   14. MVC pattern

## Chapter 2: Express.js

### [2.1 Introduction to express.js](https://youtu.be/1Max9huISzA)

- always check the documentation of [express.js](https://www.npmjs.com/package/express)
- Express.js is a node.js framework which makes life easier
- no more hassle of setting Content-Type
- easy to learn and time saving facilitites available because we have ready made stuff in express.js
- MERN Stack, NERD stack, PERN stack

### [2.2 creating express server](https://youtu.be/t9GVn5j1Hsw)

- first initialize npm : `npm init -y`
- install express: `npm install express`
- example

  ```js
  const express = require("express");

  const PORT = 3000;

  const app = express();

  app.get("/", (req, res) => {
    res.send("<h1> Welcome to express server </h1>");
  });

  app.listen(PORT, () => {
    console.log(`server is running at http://localhost:${PORT}`);
  });
  ```

### [2.3 http methods and postman](https://youtu.be/AnCkn--EAas)

- HTTP methods - get, post, put, patch, delete ...
- get methods helps to get a resource or data
- post method helps to create new resource
- put method helps to update a resource
- patch method helps to update single item of a resource
- delete method helps to delete a resource
- example

  ```js
  // index.js

  const express = require("express");

  const PORT = 3000;

  const app = express();

  // http://localhost:3000/user

  // this will work for all http methods: get, post so use app.get() or anything specific
  app.use("/user", (req, res) => {
    res.send("<h1> Welcome to get request of express server </h1>");
  });

  app.get("/user", (req, res) => {
    res.send("<h1> Welcome to get request of express server </h1>");
  });

  app.post("/user", (req, res) => {
    res.send("<h1> Welcome to post request of express server </h1>");
  });

  // put is for updating multiple property
  // patch is for updating one property

  app.put("/user", (req, res) => {
    res.send("<h1> Welcome to put request of express server </h1>");
  });

  app.patch("/user", (req, res) => {
    res.send("<h1> Welcome to patch request of express server </h1>");
  });

  app.delete("/user", (req, res) => {
    res.send("<h1> Welcome to delete request of express server </h1>");
  });

  app.listen(PORT, () => {
    console.log(`server is running at http://localhost:${PORT}`);
  });

  // error handling
  app.use((req, res) => {
    res.send("<h2>Page not found 404</h2>");
  });

  app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send("Something broke!");
  });
  ```

### [2.4 Express Router](https://youtu.be/S7oFcdUiF1k)

- use morgan package for getting more info about routing on console

  ```js
     step1 : npm install morgan
     step2 : const morgan = require("morgan");
     step3 : app.use(morgan("dev"));
  ```

- example

  ```js
  // step1: creates a routes folder
  // setp2: create a file name as user.routes.js
  // step3: write the following code inside user.routes.js
  const express = require("express");

  const router = express.Router();

  // /users
  router.get("/", (req, res) => {
    res.send("I am get method of user route");
  });

  router.post("/", (req, res) => {
    res.send("I am post method of user route");
  });

  router.put("/", (req, res) => {
    res.send("I am put method of user route");
  });

  router.patch("/", (req, res) => {
    res.send("I am patch method of user route");
  });

  router.delete("/", (req, res) => {
    res.send("I am delete method of user route");
  });

  module.exports = router;

  //step4: write following code inside index.js
  const express = require("express");

  const userRoutes = require("./routes/user.routes");

  const PORT = 3000;

  const app = express();

  app.use("/users", userRoutes);

  app.listen(PORT, () => {
    console.log(`server is running at http://localhost:${PORT}`);
  });
  ```

- example 2

  ```js
  const express = require("express");
  const router = express.Router();

  // how to get the path
  const path = require("path");

  const getFileLocation = (fileName) => {
    return path.join(__dirname, `../views/${fileName}`);
  };

  router.get("/", (req, res) => {
    res.sendFile(getFileLocation("index.html"));
  });
  router.get("/register", (req, res) => {
    res.sendFile(getFileLocation("register.html"));
  });
  router.get("/login", (req, res) => {
    res.sendFile(getFileLocation("login.html"));
  });
  module.exports = router;
  ```

### [2.5 regular expression & wild card Router]()

```js
//regular expression
// we can use 0-9 but maximum 4 digits combination
router.get("/search/:id([0-9]{4})", (req, res) => {
  res.status(200).send("serach user by id" + req.params.id);
});

// only letters allowed with maximum 5 characters
router.get("/search-username/:name([a-zA-Z]{5})", (req, res) => {
  res.status(200).send("serach user by name" + req.params.name);
});

// wild cart
router.get("*", (req, res) => {
  res.status(404).send({
    message: "url not found",
  });
});
```

### [2.6 Express generator]()

- package `npx espress-generator`
- create a basic standard scalable folder structure with necessary codes

### [2.7 HTTP Response](https://youtu.be/S7oFcdUiF1k)

- response can be text, html, json
- res.send("some text here");
- res.status(statuscode).json({...});
- res.sendFile(fileName);
- res.cookie(key, value);
- res.clrarCookie(key);
- res.writeHead()
- res.write()
- res.end()
- res.append(key, value); this will set as response header

### [2.8 HTTP Request part-1](https://youtu.be/141Q7XhGGS8)

- request with query parameter - req.query.parameterName
- request with route parameters - req.params.parameterName
- request with headers - req.header(key)
- request with json data / form data inside body - req.body.parameterName
- query parameter has question mark; search something on google.

  - example of query parameter - http://localhost:3000?id=101&name=anisul islam

    - we can get the value using req.query.id and req.query.name

    ```js
    router.post("/", (req, res) => {
      console.log(req.query);
      console.log(req.query.id);
      console.log(req.query.name);
      res.send("I am get method of user route");
    });
    ```

### [2.9 HTTP Request part-2](https://youtu.be/141Q7XhGGS8)

- example of routes parameter

  - http://localhost:3000/101
  - we can get the value using req.params.id

    ```js
    router.post("/:id", (req, res) => {
      console.log(req.params.id);
      res.send("I am get method of user route");
    });
    ```

- example of how to get data header requests

  ```js
  router.post("/", (req, res) => {
    console.log(req.header("id"));
    res.send("I am get method of user route");
  });
  ```

### [2.10 HTTP Request part-3](https://youtu.be/141Q7XhGGS8)

- example of request with json data

  - first add `app.use(express.json())`; for form data use `app.use(express.urlencoded({extended: true}))`
  - then access the data using `req.body.parameterName`

  ```js
  // sending json or from data when making request
  {
    "name" : "anisul"
  }

  router.post("/", (req, res) => {
    res.status(201).json({
      message: "user is created",
      name: req.body.name,
    });
  });
  ```

### [2.11 send and receive from data](https://youtu.be/GXkth_xoG64)

- create a index.html file inside views folder

  ```html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <title>home</title>
    </head>
    <body>
      <nav>
        <ul>
          <li><a href="/">Home</a></li>
        </ul>
      </nav>
      <main>
        <h1>welcome to home page</h1>
        <form action="/users" method="post">
          <label for="name">Name</label>
          <input type="text" id="name" name="name" />
          <button type="submit">Register</button>
        </form>
      </main>
    </body>
  </html>
  ```

- load a html file

  ```js
  // Inside user.routes.js file
  const express = require("express");
  const path = require("path");

  const router = express.Router();

  router.get("/", (req, res) => {
    res.sendFile(path.join(__dirname, "../views/index.html"));
  });

  router.post("/", (req, res) => {
    res.status(201).json({
      message: "user is created",
      name: req.body.name,
    });
  });

  module.exports = router;

  // inside index.js
  const express = require("express");

  const userRoutes = require("./routes/user.routes");

  const PORT = 3000;

  const app = express();

  app.use(express.json());
  app.use(express.urlencoded({ extended: true }));
  app.use("/users", userRoutes);

  app.listen(PORT, () => {
    console.log(`server is running at http://localhost:${PORT}`);
  });
  ```

### [2.12 Area Calculator](https://youtu.be/u1BgJg6YzYM)

### [2.13 How to set .env variables](https://youtu.be/dxwUjw2Jyfc)

- Step 1: create an .env file in the root directory

- Step 2: define environment variable(S) using uppercase letters and underscore if more than one word. Example -
  PORT
  DATABASE_URL

- Step 3: Assign the values without double quotation and space
  PORT=3000
  DATABASE_URL=mongodb+srv://medo:demo1234@cluster0.0tl3q.mongodb.net/test?retryWrites=true&w=majority

- Step 4: you can make a comment using #

  ```js
  # server port
  PORT=3000
  ```

- Step 5: install dotenv package - npm install dotenv

- Step 6: require dotenv - require('dotenv').config();

- Step 7: Access the env variables from anywhere using process.env.VARIABLE_NAME. Example – process.env.PORT;

- Optional: DotENV Extension - nice syntax highlighting in your .env files.

### [2.14 Middlewares](https://youtu.be/byiRZfg2JaE)

- what is middleware?
  - middleware is a function; it contains request obejct, response object and next function
- why middleware?
  - execute any code inside middleware
  - we can make changes to the request and response object
  - we can end the request and response cycle.
  - we can call the next middleware in the stack.
- some common usage of middleware

  - user is authenticated or not
  - check user is active or not
  - data is correct / all data available

- Types of middleware

  - Application Level middleware: app.use(), app.METHOD(); here METHOD can be get, put, post, delete, patch
  - router Level middleware: router.use(),router.METHOD()
  - built-in Level middleware: express.json(), express.urlencoded(), express.static()
  - third-party Level middleware: body-parser
  - error handling middleware

    ```js
    // routes not found error
    app.use((req, res, next) => {
      res.status(404).json({
        message: "resource not found",
      });
    });

    // server error
    app.use((err, req, res, next) => {
      console.log(err);
      res.status(500).json({
        message: "something broke",
      });
    });
    ```

### [2.15 express static Middlewares](https://youtu.be/lqRIy6d6D48)

- `app.use(express.static());` helps us to use static resources such as css and image inside our server

### [2.16 MVC Architecture](https://youtu.be/BDeBB9b2L9I)

- MVC Architecture means Model View Controller Architecture
- Model holds all the database related codes
- View is what users see
- Controller is the connection point between Model and View. basically It deals with all the logic.
- example of mvc file structure: setup a project and install necessary packages ( npm init -y && npm install nodemon express body-parser cors)

  <img width="203" alt="Screenshot 2022-04-26 at 05 13 08" src="https://user-images.githubusercontent.com/28184926/165205917-0b83ecc1-9145-40ac-b92f-b8e8cb7511b4.png">

- controllers - user.controller.js

  ```js
  const path = require("path");
  const users = require("../models/user.model");

  const getUser = (req, res) => {
    res.status(200).json({
      users,
    });
  };

  const createUser = (req, res) => {
    const user = {
      username: req.body.username,
      email: req.body.email,
    };
    users.push(user);
    res.status(201).json(users);
  };

  module.exports = { getUser, createUser };
  ```

- models

  - user.model.js

    ```js
    const users = [
      {
        username: "anisul islam",
        email: "lalalal@yahoo.com",
      },
      {
        username: "rakibul islam",
        email: "lalalal@yahoo.com",
      },
    ];
    module.exports = users;
    ```

- routes

  - user.route.js

    ```js
    const express = require("express");
    const { getUser, createUser } = require("../controllers/user.controller");
    const router = express.Router();

    router.get("/", getUser);
    router.post("/", createUser);

    module.exports = router;
    ```

- views

  - index.html

    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
      </head>
      <body>
        <nav>
          <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/api/users">Register</a></li>
          </ul>
        </nav>
        <h1>Home Page</h1>
      </body>
    </html>
    ```

    - user.html

    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=], initial-scale=1.0" />
        <title>Document</title>
      </head>
      <body>
        <nav>
          <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/api/users">Register</a></li>
          </ul>
        </nav>
        <h1>User Registration</h1>
        <form action="/api/user" method="post">
          <input type="text" name="username" placeholder="username" />
          <input type="email" name="email" placeholder="email" />
          <button type="submit">register</button>
        </form>
      </body>
    </html>
    ```

- .env
  - `PORT=4000`
- app.js

  ```js
  const express = require("express");
  const cors = require("cors");
  const app = express();
  const bodyParser = require("body-parser");
  const userRouter = require("./routes/user.route");
  // CORS
  app.use(bodyParser.urlencoded({ extended: true }));
  app.use(bodyParser.json());
  app.use(cors());

  app.use("/api/users", userRouter);

  app.get("/", (req, res) => {
    res.sendFile(__dirname + "/views/index.html");
  });

  // routes not found error
  app.use((req, res, next) => {
    res.status(404).json({
      message: "resource not found",
    });
  });

  // server error
  app.use((err, req, res, next) => {
    console.log(err);
    res.status(500).json({
      message: "something broke",
    });
  });

  module.exports = app;
  ```

- index.js

  ```js
  require("dotenv").config();
  const app = require("./app");
  const PORT = process.env.PORT || 5000;
  app.listen(PORT, () => {
    console.log(`server is running at http://localhost:${PORT}`);
  });
  ```

### [2.17] Validation with express-validator

- install express-validator

## Version-2 Express server with a project

## Express tutorial

## 1. Create an express server

- initialize npm and install packages
- nodemon montior the changes of our code and update the server

```js
npm init -y && npm install express
npm install -D nodemon
```

```js
// index.js
const express = require("express");

const app = express();

const port = 3001;

app.listen(port, () => {
  console.log(`server is running at http://localhost:${port}`);
});
```

```json
//package.json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node src/index.js",
    "start-dev": "nodemon src/index.js"
  },
```

## 2. setting environment variables

## 3. Handle GET Request -> GET all products

- routing plan using HTTP methods for RESTful Services
- HTTP Verbs -> GET, POST, PUT, PATCH, DELETE helps us to CRUD operations

```js
GET /products - get all the products -> 200 (ok) / 404 (not found)
GET /products/:id - get a single product -> 200 / 404
POST /products/ - create a single product -> 201 (Created) / 404 (Not Found) / 409 (Conflict -> Already Exist)
PUT /products/:id - update/replace every resource in a single product -> 200 (Ok) / 404 (Not Found) / 405 (Method Not Allowed)
PATCH /products/:id - update/Modify product itself -> 200 (Ok) / 404 (Not Found)  / 405 (Method Not Allowed)
DELETE /products/:id - delete a single product -> 200 (Ok) / 404 (Not Found) / 405 (Method Not Allowed)

```

```js
// app.use()
app.use("/", (req, res) => {
  res.send("home page");
});

// now use ThunderClient extension for testing the API; you will see app.use() accept all http methods

// app.get() - will only accept get method
app.get("/", (req, res) => {
  res.send("home page");
});
```

```js
let products = [
  {
    id: 1,
    title: "Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops",
    price: 109.95,
  },
  {
    id: 2,
    title: "Mens Casual Premium Slim Fit T-Shirts ",
    price: 22.3,
  },
];

app.get("/products", (req, res) => {
  res.send(products);
});
```

## 4. Middleware

## 5. Handling error

```js
// client error
app.use((req, res) => {
  res.send("<h2>Page not found 404</h2>");
});

// server error
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.send("Something broke!");
});
```

## 6. Response Object

- text, HTML, JSON

```js
res.send("hello");
res.send({
  success: true,
  user: { id: 1, name: "anisul" },
});
res.sendFile("hello.html");
```

## 7. [Status codes](https://devhints.io/http-status)

```js
app.get("/", (req, res) => {
  res.status(200).send("home page");
});

app.get("/products", (req, res) => {
  res.status(200).send(products);
});

app.use((req, res) => {
  res.status(404).send("<h2>Page not found 404</h2>");
});

app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send("Something broke!");
});
```

## 8. Request Object

- request with query parameter - req.query.parameterName

- request with route parameters - req.params.parameterName

- request with headers - req.header(key)

- request with json data / form data inside body - req.body.parameterName

- query parameter has question mark; search something on google.

- example of query parameter - http://localhost:3000?id=101&name=anisul islam

- we can get the value using req.query.id and req.query.name

```js
router.post("/", (req, res) => {
  console.log(req.query);
  console.log(req.query.id);
  console.log(req.query.name);
  res.send("I am get method of user route");
});
```

## 9. Handle GET Request -> get a single product

```js
// route parameter
app.get("/products/:id", (req, res) => {
  const singleProduct = products.find(
    (product) => product.id === Number(req.params.id)
  );
  res.status(200).send(singleProduct);
});

// query parameter
const sortItems = (sortBy, items) => {
  if (sortBy === "ASC") {
    return items.sort((a, b) => a.price - b.price);
  } else if (sortBy === "DESC") {
    return items.sort((a, b) => b.price - a.price);
  }
};

const sortItems = (sortBy, items) => {
  if (sortBy === "ASC") {
    return items.sort((a, b) => a.price - b.price);
  } else if (sortBy === "DESC") {
    return items.sort((a, b) => b.price - a.price);
  }
};

app.get("/products", (req, res) => {
  const maxPrice = Number(req.query.maxPrice);
  const sortBy = req.query.sortBy;
  let result;
  if (maxPrice) {
    result = products.filter((product) => product.price <= maxPrice);
    result = sortBy ? sortItems(sortBy, result) : result;
    res.status(200).send(result);
  } else {
    res.status(200).send(products);
  }
});
```

## 10. Handle POST Request -> create a single product

```js
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

app.post("/products", (req, res) => {
  const newProduct = {
    id: Number(req.body.id),
    title: req.body.title,
    price: req.body.price,
  };
  products.push(newProduct);
  res.status(200).send(newProduct);
});
```

## 11. Handle DELETE Request -> delete a single product

```js
app.delete("/products/:id", (req, res) => {
  products = products.filter((product) => product.id !== Number(req.params.id));
  res.status(200).send(products);
});
```

## 12. Handle PUT Request -> update a single product

```js
app.put("/products/:id", (req, res) => {
  products
    .filter((product) => product.id === Number(req.params.id))
    .map((product) => {
      product.title = req.body.title;
      product.price = req.body.price;
    });
  res.status(200).send(products);
});
```

## 13. MVC Structure - Routing with express Router

- Separation of Concerns
- Model, View, Controllers
- create a router folder and then create a product file where we will move all our routes

```js
//routes -> product.js
const express = require("express");
const router = express.Router();

let products = [
  {
    id: 1,
    title: "Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops",
    price: 109.95,
  },
  {
    id: 2,
    title: "Mens Casual Premium Slim Fit T-Shirts ",
    price: 22.3,
  },
  {
    id: 3,
    title: "Mens Cotton Jacket",
    price: 55.99,
  },
  { id: 4, title: "Mens Casual Slim Fit", price: 15.99 },
];

const sortItems = (sortBy, items) => {
  if (sortBy === "ASC") {
    return items.sort((a, b) => a.price - b.price);
  } else if (sortBy === "DESC") {
    return items.sort((a, b) => b.price - a.price);
  }
};

router.get("/products", (req, res) => {
  const maxPrice = Number(req.query.maxPrice);
  const sortBy = req.query.sortBy;
  let result;
  if (maxPrice) {
    result = products.filter((product) => product.price <= maxPrice);
    result = sortBy ? sortItems(sortBy, result) : result;
    res.status(200).send(result);
  } else {
    res.status(200).send(products);
  }
});

router.get("/products/:id", (req, res) => {
  const singleProduct = products.find(
    (product) => product.id === Number(req.params.id)
  );
  res.status(200).send(singleProduct);
});

router.post("/products", (req, res) => {
  const newProduct = {
    id: Number(req.body.id),
    title: req.body.title,
    price: req.body.price,
  };
  products.push(newProduct);
  res.status(200).send(newProduct);
});

router.put("/products/:id", (req, res) => {
  products
    .filter((product) => product.id === Number(req.params.id))
    .map((product) => {
      product.title = req.body.title;
      product.price = req.body.price;
    });
  res.status(200).send(products);
});

router.delete("/products/:id", (req, res) => {
  products = products.filter((product) => product.id !== Number(req.params.id));
  res.status(200).send(products);
});

module.exports = router;

// inside index.js
const productRouters = require("./router/products");
app.use(productRouters);
```

- remove all the products and in index.js use `app.use("/products", productRouters);`

## 14. MVC Structure - Controller part

```js
// routes -> products.js
const express = require("express");
const {
  getAllProducts,
  getSingleProduct,
  createProduct,
  updateProduct,
  deleteProduct,
} = require("../controller/products");
const router = express.Router();

router.get("/", getAllProducts).get("/:id", getSingleProduct);

router.post("/", createProduct);

router.put("/:id", updateProduct);

router.delete("/:id", deleteProduct);

module.exports = router;

// controller -> products.js
let products = [
  {
    id: 1,
    title: "Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops",
    price: 109.95,
  },
  {
    id: 2,
    title: "Mens Casual Premium Slim Fit T-Shirts ",
    price: 22.3,
  },
  {
    id: 3,
    title: "Mens Cotton Jacket",
    price: 55.99,
  },
  { id: 4, title: "Mens Casual Slim Fit", price: 15.99 },
];

const sortItems = (sortBy, items) => {
  if (sortBy === "ASC") {
    return items.sort((a, b) => a.price - b.price);
  } else if (sortBy === "DESC") {
    return items.sort((a, b) => b.price - a.price);
  }
};

const getAllProducts = (req, res) => {
  const maxPrice = Number(req.query.maxPrice);
  const sortBy = req.query.sortBy;
  let result;
  if (maxPrice) {
    result = products.filter((product) => product.price <= maxPrice);
    result = sortBy ? sortItems(sortBy, result) : result;
    res.status(200).send(result);
  } else {
    res.status(200).send(products);
  }
};

const getSingleProduct = (req, res) => {
  const singleProduct = products.find(
    (product) => product.id === Number(req.params.id)
  );
  res.status(200).send(singleProduct);
};

const createProduct = (req, res) => {
  const newProduct = {
    id: Number(req.body.id),
    title: req.body.title,
    price: req.body.price,
  };
  products.push(newProduct);
  res.status(200).send(newProduct);
};

const updateProduct = (req, res) => {
  products
    .filter((product) => product.id === Number(req.params.id))
    .map((product) => {
      product.title = req.body.title;
      product.price = req.body.price;
    });
  res.status(200).send(products);
};

const deleteProduct = (req, res) => {
  products = products.filter((product) => product.id !== Number(req.params.id));
  res.status(200).send(products);
};

module.exports = {
  getAllProducts,
  getSingleProduct,
  createProduct,
  updateProduct,
  deleteProduct,
};
```

## 15. MVC Structure - Model part

```js
// model -> products.js
let products = [
  {
    id: 1,
    title: "Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops",
    price: 109.95,
  },
  {
    id: 2,
    title: "Mens Casual Premium Slim Fit T-Shirts ",
    price: 22.3,
  },
  {
    id: 3,
    title: "Mens Cotton Jacket",
    price: 55.99,
  },
  { id: 4, title: "Mens Casual Slim Fit", price: 15.99 },
];

module.exports = products;
```

## 15. EJS

## 16. Deploy on Heroku

- `const port = process.env.PORT || 3001;`
- Procfile -> `web: node index.js`
- add .gitignore file -> `node_modules_`

## 17. Database

- save(), find(), findOne(), deleteOne(), updateOne()

```js
const mongoose = require("mongoose");
mongoose
  .connect("mongodb://localhost:27017/testProduct")
  .then(() => console.log("DB is connected"))
  .catch((error) => {
    console.log(error.message);
    process.exit(1);
  });

// schema & model
const { model } = require("mongoose");
const mongoose = require("mongoose");

const productsSchema = new mongoose.Schema({
  id: Number,
  title: String,
  price: Number,
});

module.exports = model("Product", productsSchema);

// controller
const Products = require("../model/products");

// Create
const createProduct = async (req, res) => {
  try {
    const newProduct = new Products({
      id: Number(req.body.id),
      title: req.body.title,
      price: req.body.price,
    });
    await newProduct.save();
    res.status(200).send(newProduct);
  } catch (error) {
    res.status(500).send(error.message);
  }
};

// Read
const getAllProducts = async (req, res) => {
  try {
    const products = await Products.find();
    res.status(200).send(products);
  } catch (error) {
    res.status(500).send(error.message);
  }
};

// read all the products
const getAllProducts = async (req, res) => {
  try {
    const products = await Products.find();
    const maxPrice = Number(req.query.maxPrice);
    const sortBy = req.query.sortBy;
    let result;
    if (maxPrice) {
      result = await Products.find({ price: { $lt: maxPrice } });
      result = sortBy ? sortItems(sortBy, result) : result;
      res.status(200).send(result);
    } else {
      res.status(200).send(products);
    }
  } catch (error) {
    res.status(500).send(error.message);
  }
};

// read single product by id
const getSingleProduct = async (req, res) => {
  try {
    // const id = parseInt(req.params.id);
    const singleProduct = await Products.findOne({ req.params.id });
    res.status(200).send(singleProduct);
  } catch (error) {
    res.status(500).send(error.message);
  }
};

// delete one product by id
const deleteProduct = async (req, res) => {
  try {
    const id = parseInt(req.params.id);
    const singleProduct = await Products.deleteOne({ id });
    res.status(200).send({ success: true });
  } catch (error) {
    res.status(500).send(error.message);
  }
};

// update a product by id
const updateProduct = async (req, res) => {
  try {
    await Products.updateOne(
      { id: req.params.id },
      {
        $set: {
          title: req.body.title,
          price: req.body.price,
        },
      }
    );
    res.status(200).send({ success: true });
  } catch (error) {
    res.status(500).send(error.message);
  }
};
```

## 18. cors setup

- cors setup

```js
npm install cors
app.use(cors())
```

## 19. connection from front end

```js
import "./App.css";
import React, { useEffect, useState } from "react";
import NewProduct from "./components/NewProduct";

const URL = "http://localhost:4000/products";
function App() {
  const [products, setProducts] = useState([]);
  const [isLoading, setIsLoading] = useState(true);
  const [error, setError] = useState(null);

  // update
  const [selectedProduct, setSelectedProduct] = useState({
    title: "",
    price: "",
  });
  const [updateFlag, setUpdateFlag] = useState(false);
  const [selectedProductId, setSelectedProductId] = useState("");

  const getAllProducts = () => {
    fetch(URL)
      .then((res) => {
        if (!res.ok) {
          throw Error("could not fetch");
        }
        return res.json();
      })
      .then((result) => {
        setProducts(result);
      })
      .catch((err) => {
        setError(err.message);
      })
      .finally(() => {
        setIsLoading(false);
      });
  };
  useEffect(() => {
    getAllProducts();
  }, []);

  const handleDelete = (id) => {
    fetch(URL + `${id}`, {
      method: "DELETE",
    })
      .then((res) => {
        if (!res.ok) {
          throw Error("could not delete");
        }
        getAllProducts();
      })
      .catch((err) => {
        setError(err.message);
      });
  };

  const addProduct = (product) => {
    fetch(URL, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(product),
    })
      .then((res) => {
        if (res.status === 201) {
          getAllProducts();
        } else {
          throw new Error("could not create new product");
        }
      })
      .catch((err) => {
        setError(err.message);
      });
  };

  const handleEdit = (id) => {
    setSelectedProductId(id);
    setUpdateFlag(true);
    const filteredData = products.filter((product) => product.id === id);
    setSelectedProduct({
      title: filteredData[0].title,
      price: filteredData[0].price,
    });
  };

  const handleUpdate = (product) => {
    console.log(selectedProductId);
    fetch(URL + `/${selectedProductId}`, {
      method: "PUT",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(product),
    })
      .then((res) => {
        if (!res.ok) {
          throw new Error("failed to update");
        }
        getAllProducts();
        setUpdateFlag(false);
      })
      .catch((err) => {
        setError(err.message);
      });
  };

  return (
    <div className="App">
      <h1>Products</h1>
      {isLoading && <h2>Loading...</h2>}
      {error && <h2>{error}</h2>}

      {updateFlag ? (
        <NewProduct
          btnText="Update Product"
          selectedProduct={selectedProduct}
          handleSubmitData={handleUpdate}
        />
      ) : (
        <NewProduct btnText="Add Product" handleSubmitData={addProduct} />
      )}

      {products.length > 0 &&
        products.map((product) => (
          <article key={product.id}>
            <h3>{product.title}</h3>
            <p>{product.price}</p>
            <button
              onClick={() => {
                handleEdit(product.id);
              }}
            >
              Edit
            </button>
            <button
              onClick={() => {
                handleDelete(product.id);
              }}
            >
              Delete
            </button>
          </article>
        ))}
    </div>
  );
}

export default App;


// NewProduct.js
import React, { useState, useEffect } from "react";
import { v4 as uuidv4 } from "uuid";

const NewProduct = ({ handleSubmitData, selectedProduct, btnText }) => {
  const [product, setProduct] = useState({
    title: "",
    price: "",
  });

  const { title, price } = product;

  useEffect(() => {
    setProduct({
      title: selectedProduct.title,
      price: selectedProduct.price,
    });
  }, [selectedProduct]);

  const handleChange = (e) => {
    const selectedField = e.target.name;
    const selectedValue = e.target.value;
    setProduct((prevState) => {
      return { ...prevState, [selectedField]: selectedValue };
    });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    const newProduct = {
      id: Number(uuidv4()),
      title: product.title,
      price: product.price,
    };
    handleSubmitData(newProduct);
    setProduct({
      title: "",
      price: "",
    });
  };

  return (
    <form onSubmit={handleSubmit}>
      <div className="field-group">
        <label htmlFor="title">Title: </label>
        <input
          type="text"
          id="title"
          name="title"
          value={title}
          onChange={handleChange}
          required
        />
      </div>
      <div className="field-group">
        <label htmlFor="price">Price: </label>
        <input
          type="text"
          id="price"
          name="price"
          value={price}
          onChange={handleChange}
          required
        />
      </div>
      <button type="submit" className="btn">
        {btnText}
      </button>
    </form>
  );
};

NewProduct.defaultProps = {
  selectedProduct: {
    title: "",
    price: "",
  },
};

export default NewProduct;

```

## CORS Setup

## REST API

- basically we are going to return some data
- Reperesentational State Transfer
- Response data -> text, html, xml, json
- HTTP methods -> GET, POST, PUT (CREATE/OVERRIDE A RESOURCE) /PATCH, DELETE
- Routing

## Necessary Code

```bash
const express = require("express"); // Create Express server
const morgan = require("morgan"); // For automatically run server
const cookieParser = require("cookie-parser"); // For set Cookie
const createError = require("http-errors"); // For create HTTP Error
const xssClean = require("xss-clean"); // For  Secure API
const bodyParser = require("body-parser"); // For Get/ Set data into body
const cors = require("cors"); // To set access for client-side URL
```

/_
|--------------------------------------------------------------------------
| Initialize Middleware
|--------------------------------------------------------------------------
_/

```bash
app.use(cookieParser()); // For set Cookie
app.use(morgan("dev")); // For automatically run server
app.use(xssClean()); // For  Secure api
app.use(bodyParser.json()); // For Set, Read data into the body and display JSON Format Text
app.use(bodyParser.urlencoded({ extended: true })); // Get HTML Form Data
app.use(setRefreshToken); // For set Refresh Token [Automatically call this middleware for all route]
// To get access to Client side URL
app.use(cors(
 {
   origin: BASE_URL, // Frontend Base URL
   credentials: true
 }
));
app.use(express.static("public")); // To Display Server site image
```

/_
|--------------------------------------------------------------------------
| Socket IO
|--------------------------------------------------------------------------
_/

```bash
const io = require("socket.io")(8080, {
 cors: {
   origin: BASE_URL
 },
});
io.on("connection", (socket) => {
 console.log("User connected", socket.id);

 setInterval(() => {
   io.emit("refresh", {});
 }, 500)

 // socket.on("disconnect", function () {
 //   console.log("Disconnect");

 // })

});
```

## Follow Me

<img src ="https://www.edigitalagency.com.au/wp-content/uploads/Facebook-logo-blue-circle-large-transparent-png.png" height="15px" width="15px"/> [Facebook](http://facebook.com/learnwithfair), <img src ="https://image.similarpng.com/very-thumbnail/2021/10/Youtube-icon-design-on-transparent-background-PNG.png" height="20px" width="20px"/> [Youtube](http://youtube.com/@learnwithfair), <img src ="https://i.pinimg.com/originals/fa/ea/02/faea02f412415becfb4939d2b6431c28.jpg" height="15px" width="15px"/> [Instagram](http://instagram.com/learnwithfair)
