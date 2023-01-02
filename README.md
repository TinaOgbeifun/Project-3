# Project-3

SIMPLE TO-DO APPLICATION ON MERN WEB STACK

In this project, we will implement a web solution based on MERN stack in AWS Cloud

Make a research what types of Database Management Systems (DBMS) exist and what each type is more suitable for. Be able to explain the difference between Relational DBMS and NoSQL (of a different kind)

[database management system](https://en.wikipedia.org/wiki/Web_framework)

[RESTful API](https://restfulapi.net/)

# BACKEND CONFIGURATION

To update ubuntu, we would run

sudo apt update

![To update ubuntu](./images/sudo-apt-update.png)

To upgrade ubuntu, again we run

sudo apt upgrade

![To upgrade ubuntu](./images/sudo-apt-upgrade.png)

Lets get the location of Node.js software from Ubuntu repositories.

curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -

![installing the nodesource](./images/nodesource-installation.png)


Install Node.js on the server

Install Node.js with the command below

sudo apt-get install -y nodejs

![install nodejs on the server](./images/install-nodejs.png)

Note: The command above installs both nodejs and npm. NPM is a package manager for Node like apt for Ubuntu, it is used to install Node modules & packages and to manage dependency conflicts

Verify the node installation with the command below

node -v 
Verify the node installation with the command below

![verifying the node installation](./images/node-v.png)

npm -v 

![verifying the npm installation](./images/npm-v.png)

Application Code Setup

Create a new directory for your To-Do project:

mkdir Todo

Run the command below to verify that the Todo directory is created with ls command

ls

![todo directory is created with ls command](./images/todo-directory.png)

Now change your current directory to the newly created one:

cd Todo

![changing your current directory to the newly created one](./images/cd-todo.png)

Next, you will use the command npm init to initialise your project, so that a new file named package.json will be created. This file will normally contain information about your application and the dependencies that it needs to run. Follow the prompts after running the command. You can press Enter several times to accept default values, then accept to write out the package.json file by typing yes.

npm init

![using npm init command to initialise my project](./images/npm-init.png)

Run the command ls to confirm that you have package.json file created

![To confirm that i have package.jason file created](./images/confirm-package-jason-file.png)

# INSTALL EXPRESSJS

Express is a framework for Node.js, therefore a lot of things developers would have programmed is already taken care of out of the box. Therefore it simplifies development, and abstracts a lot of low level details. For example, Express helps to define routes of your application based on HTTP methods and URLs.

To use express, install it using npm:

npm install express

![installing express using npm](./images/npm-install-express.png)

Now create a file index.js with the command below

touch index.js

Then run ls to confirm that your index.js file is successfully created

![confirm that your index.js file is successfully created](./images/index-js-file.png)

Install the dotenv module

npm install dotenv

![Install the dotenv module](./images/dotenv-module.png)

Open the index.js file with the command below

vim index.js

Type the code below into it and save then paste the code into the file.

![Open the index.js file](./images/paste-code-into-the-file.png)

Notice that we have specified to use port 5000 in the code. This will be required later when we go on the browser.

Use :w to save in vim and use :qa to exit vim

Now it is time to start our server to see if it works. Open your terminal in the same directory as your index.js file and type:

node index.js

If every thing goes well, you should see Server running on port 5000 in your terminal

![start our server to see if it works](./images/node-index-js.png)

Now we need to open this port in EC2 Security Groups to create inbound rule to open TCP port 5000

![creating inbound rule for port 5000](./images/inbound-rule-for-port-5000.png)

Open up your browser and try to access your server’s Public IP or Public DNS name followed by port 5000:

http://<PublicIP-or-PublicDNS>:5000

![accessing server's public IP](./images/public-server.png)

Again, create a folder routes by running  the below command

mkdir routes

Change directory to routes folder.

cd routes
Now, create a file api.js with the command below

touch api.js

![create folder routes](./images/folder-routes.png)

Open the file with the command below

vim api.js

![open the file](./images/vim-api-js-file.png)

# MODELS

A model is at the heart of JavaScript based applications, and it is what makes it interactive

We will also use models to define the database schema 

To create a Schema and a model, install mongoose which is a Node.js package that makes working with mongodb easier

npm install mongoose

![npm install mongoose](./images/install-mongoose.png)

Create a new folder models :

mkdir models
Change directory into the newly created ‘models’ folder with

cd models
Inside the models folder, create a file and name it todo.js

touch todo.js

![create new folder models](./images/create-new-folder-models.png)

All three commands above can be defined in one line to be executed consequently with help of && operator by running the command below

mkdir models && cd models && touch todo.js

Then Open the file created by running this command

vim todo.js

![Open the file created with vim todo.js](./images/vim-todo-js.png)

Now we need to update our routes from the file api.js in ‘routes’ directory to make use of the new model.

In Routes directory, open api.js with vim api.js, delete the code inside with :%d command and paste there code below into it then save and exit

![open api.js with vim api](./images/vim-api-js-code-file.png)

# MONGODB DATABASE

We need a database where we will store our data. For this we will make use of mLab. mLab provides MongoDB database as a service solution (DBaaS)

![adding new database user](./images/new-database-user.png)

Allow access to the MongoDB database from anywhere

Also, In the image below, change the time of deleting the entry from 6 Hours to 1 Week

![change the time of deleting the entry from 6 Hours to 1 Week](./images/mongo-db-database.png)

Create a MongoDB database and collection inside mLabreate a MongoDB database and collection inside mLab

![create mongoDB database and collection](./images/mongoDB-database-and-collection.png)

Create a file in your Todo directory and name it .env.

touch .env
vi .env

![Todo directory](./images/creating-file-in-todo-directory.png)

Add the connection string to access the database in it, just as below:

DB = 'mongodb+srv://<username>:<password>@<network-address>/<dbname>?retryWrites=true&w=majority'

Ensure to update <username>, <password>, <network-address> and <database> according to your setup 

![select connecting your application](./images/connect-application.png)

![connecting to cluster](./images/connect-to-cluster.png)

![adding connection string](./images/connection-string.png)

Now we need to update the index.js to reflect the use of .env so that Node.js can connect to the database

![connect to database on vim](./images/connect-to-database-on-vim.png)

Now we need to update the index.js to reflect the use of .env so that Node.js can connect to the database.

Simply delete existing content in the file, and update it with the entire code below.

To do that using vim, follow below steps

Open the file with vim index.js
Press esc
Type :
Type %d
Hit ‘Enter’

![deleting existing content in file](./images/content-file.png)

The entire content will be deleted, then,

Press i to enter the insert mode in vim
Now, paste the entire code below in the file.

![paste code in vim file](./images/vim-file.png)

Using environment variables to store information is considered more secure and best practice to separate configuration and secret data from the application, instead of writing connection strings directly inside the index.js application file.

Start your server using the command:

node index.js

You shall see a message ‘Database connected successfully’, if so – we have our backend configured. Now we are going to test it.

![database connected successfully](./images/database-connected.png)

# Testing Backend Code without Frontend using RESTful API

we will use Postman to test our API

how perform CRUD operartions on Postman  [title](https://www.example.com)

![alt text](image.jpg)
![alt text](image.jpg)
![alt text](image.jpg)
![alt text](image.jpg)











