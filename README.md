---
services: cosmos-db
platforms: mongoose
author: viviswan
---

# Using Mongo ReadPreference with Azure Cosmos DB's MongoDB API
Azure Cosmos DB is a globally distributed multi-model database. One of the supported APIs is the MongoDB API, which provides a document model and support for client drivers in many platforms. This sample shows you how to use MongoDB ReadPreference against Azure Cosmos DB with MongoDB API using Mongoose framework.

## Running this sample

* Before you can run this sample, you must have the following prerequisites:

   * An active Azure account. If you don't have one, you can sign up for a [free account](https://azure.microsoft.com/free/). Alternatively, you can use the [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) for this tutorial.
   * Node JS installation

* Then, clone this repository.

* Next, substitute the `remoteUrl` in *config/database.js* with your Cosmos DB account connection string. 

* `npm install` to install dependencies (mongo driver)

* `npm start`

* The application starts at `http://localhost:8080`. Visit this Url to access the application.

## About the code
The code included in this sample is intended to illustrate using ReadPreference and tags with Azure Cosmos DB with the MongoDB API for performing reads across geo replicated read regions. This application is a fork of this [TODO application](https://github.com/scotch-io/node-todo) and modified to add read preference setting.

## Read preference Settings

* Refer `getTodos` method in `app\routes.js` for setting Read preference. Find the snippet below:

```javascript
    Todo.find(function (err, todos) {

        // if there is an error retrieving, send the error. nothing after res.send(err) will execute
        if (err) {
            res.send(err);
        }

        res.json(todos); // return all todos in JSON format
    }).read('secondary');
```

## More information

- [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)
- [Azure Cosmos DB : MongoDB API](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [Mongoose framwork documentation](http://mongoosejs.com/docs/api.html)
- [MongoDB NodeJS ReadPreference documentation](http://mongodb.github.io/node-mongodb-native/2.2/api/ReadPreference.html)