# Getting Started with Heroku (a cloud platform)
This tutorial demonstrates **how to deploy a simple Node.js app to Heroku**. The app you are going to deploy is `a server-side app (Node.js)` that responds to HTTP `GET` requests and returns a simple text message **Hello World!**

## Preparation
### 1. Create a **free** Heroku account at "https://www.heroku.com/".  
Write down your `login email` and `password`.
### 2. Install the Heroku Command Line Interface (CLI) in local machine. 
The Heroku CLI requires Git, please [install Git](https://git-scm.com/download/linux).
```
$ such apt-get install git
[sudo] password for developer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version (1:2.26.0-1~ppa1~ubuntu19.04.1).
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```
Check the git version.
```
$ git --version
git version 2.26.0
```
### 3. Download the sample app to your **home** directory
```
$ cd ~
$ git clone https://github.com/yalin-liu/cloudapp.git
```
### 4. Verify the app in local machine 
Go into the folder containing the server-side app.
```
$ cd ~/cloudapp/helloworld
```
Install the app's dependencies.
```
$ npm install
```
Run the server app in local machine.
```
$ npm start
```
Test your app by sending to it a HTTP `GET` request.  

Open http://127.0.0.1:8099 in your web browser.

## Deploy the app to Heroku
### 1. Create a cloud app (where your local app will be deployed) in Heroku. 
When prompted to **Select a region**, selet `us-south`
Write down the `unique name` for your app. The App link on Heroku are named XXXXXXXX.mybluemix.net where XXXXXXXX is the name of your app.
I use `rs202009011306` as the name of my app in this tutorial.  If the deployment is successful, you will be able to see your app running at `http://rs202009011306.mybluemix.net`.
### 2. Access the local folder containing the app.  
Remove the app's dependencies (the `node_modules` folder).
```
$ cd ~/cloudapp/helloworld
$ rm -rf node_modules
```
### 3. Login to Heroku in local machine. 
```
$ heroku login
heroku: Press any key to open up the browser to login or q to exit
 ›   Warning: If browser does not open, visit
 ›   https://cli-auth.heroku.com/auth/browser/***
heroku: Waiting for login...
Logging in... done
Logged in as me@example.com
```       
Check the Heroku version.
```
heroku --version
```

### 4. Deploy (upload) your app to the cloud app in Heroku
Initialize git repository inside your working directory and connect that to your Heroku app using the second command with your app name.
```
$ git init
$ heroku git:remote -a unique-app-name-to-be-entered
```
It takes 3-4 minutes to *upload* the source code, *provision* and *activate* for your app in the cloud.  If things go well, you will see the following messages at the end of deployment.

Add and commit to the Heroku master branch using the following commands.
```
$ git add .
$ git commit -m "your commit message"
```
Now deploy your code:
```
$ git push heroku master
```
You can also change your main deploy branch from "master" to "main" for both manual and automatic deploys, please follow the instructions here.
```
$ git checkout -b main
$ git branch -D master
```
Then re-deploy the application using the new default branch:
```
$ git push heroku main
```
### 4. 5. Test your app.  Open the URL shown in `routes` above in your web broswer. 
In this tutorial, the URL is `http://rs202009011306.mybluemix.net`.

# Other Useful Commands

## What's Next?
Follow the instructions to deploy [`express-weather`](https://github.com/leungmanfai/ibmcloud/tree/master/express-weather#express-weather---a-simple-server-side-app) to Heroku.
# ibmcloud
