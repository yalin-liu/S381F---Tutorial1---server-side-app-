# Getting Started with Heroku (a cloud platform)
This tutorial demonstrates **how to deploy a simple Node.js app to Heroku**. The app you are going to deploy is **a server-side app (Node.js)** that responds to HTTP `GET` requests and returns a simple text message **Hello World!**

## Preparation
### 1. Create a **free** Heroku account at "https://www.heroku.com/".  
Write down your `login email` and `password`.

### 2. Open a terminal in local machine (Linux+Ubuntu).
Install the Heroku Command Line Interface (CLI). 

The Heroku CLI requires Git, please install Git.
```
$ sudo apt-get install git
```
Check the git version to verify your installation.
```
$ git --version
git version 2.26.0
```
### 3. Download the sample app to your **home** directory.
```
$ cd ~
$ git clone https://github.com/yalin-liu/cloudapp.git
```
### 4. Test the app in local machine. 
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
```
Open http://localhost:8099 in your web browser.
```


## Deploy the app to Heroku
### 1. Create a cloud app (where your local app will be deployed) in Heroku. 
Write down the `unique name` for your app. The App link on Heroku will be https://XXXXXXXX.herokuapp.com/ where XXXXXXXX is the name of your app.

### 2. Access the local folder containing the app.  
Remove the app's dependencies (the `node_modules` folder).
```
$ cd ~/cloudapp/helloworld
$ rm -rf node_modules
```

### 3. Login to Heroku in local machine. 
```
$ heroku login
```       
Check the Heroku version.
```
heroku --version
```

### 4. Deploy (upload) your app to the cloud app in Heroku.
Initialize git repository inside your working directory and connect that to your Heroku app using the second command with your app name.
```
$ git init
$ heroku git:remote -a unique-app-name-to-be-entered
```
Add git commit to the Heroku master branch using the following commands.
```
$ git add .
$ git commit -m "your commit message"
```
Now deploy your code:
```
$ git push heroku master
...
remote: -----> Build succeeded!
remote: -----> Discovering process types
remote:        Procfile declares types     -> (none)
remote:        Default types for buildpack -> web
remote: 
remote: -----> Compressing...
remote:        Done: 62.4M
remote: -----> Launching...
remote:        Released v3
remote:        https://cloudapp381.herokuapp.com/ deployed to Heroku
remote: 
remote: This app is using the Heroku-20 stack, however a newer stack is available.
remote: To upgrade to Heroku-22, see:
remote: https://devcenter.heroku.com/articles/upgrading-to-the-latest-stack
remote: 
remote: Verifying deploy... done.
To https://git.heroku.com/cloudapp381.git
 * [new branch]      master -> master
```
It takes 3-4 minutes to *upload* the source code, *provision* and *activate* for your app in the cloud.  If things go well, you will see the following messages at the end of deployment. 

### 5. Test your app.  Open the URL shown in `routes` above in your web broswer. 
In this tutorial, the URL is `https://cloudapp381.herokuapp.com/`.

# Other Useful Commands.
### [Switch branches of a git repository from master to main and reploy the app](https://help.heroku.com/O0EXQZTA/how-do-i-switch-branches-from-master-to-main).
```
$ git checkout -b main
$ git branch -D master
$ git push heroku main
```

## What's Next?
Follow the instructions to deploy [`express-weather`]([express-weather/README.md](https://github.com/yalin-liu/cloudapp/blob/1d4136ba314de582e6928bcb8fae830011aa37c4/express-weather/README.md)) to Heroku.
