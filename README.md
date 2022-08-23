# Learn to deploy *server.js* apps to the cloud (Heroku)
This tutorial demonstrates **how to deploy a simple server.js app to Heroku**.

## Preparations

### Heroku Cloud Platform: account + app
> Create a free account at "https://www.heroku.com/".  
- Write down your `login email` and `password` for later use.

> Create your own heroku app in Heroku platform.
- Write down your `app-name` for later use. 
- Heroku will generate a Web link "https://app-name.herokuapp.com/" for your app.

### OpenWeather: account + API key
> Create a free account at "https://home.openweathermap.org/users/sign_up"
- Write down your `login email` and `password` for later use.
- Get `an API key` for later use.

## Test the app samples in local machine
### Open a terminal in local machine (Ubuntu system).
> Access the home directory and download the sample app to your **home** directory.
```
$ cd ~
$ git clone https://github.com/yalin-liu/cloudapp.git
```

### Test the `helloworld` app in local machine. 
- Go into the folder containing the `helloworld` app.
```
$ cd ~/cloudapp/helloworld
```
- Install the app's dependencies.
```
$ npm install
```
- Run the server app in local machine.
```
$ npm start
```
- Test your app by sending to it a HTTP `GET` request.  
- Open "http://localhost:8099" in your web browser.

### Test the `express-weather` app in local machine. 
- Go into the folder containing the `express-weather` app.
```
$ cd ~/cloudapp/express-weather
```
- Open `server.js` files
```
$ gedit server.js
```
- Add Open Weather `API` key to the `server.js` file
- Install the app's dependencies.
```
$ npm install npm@latest
```
- Run the server app in local machine.
```
$ npm start
```
- Test your app by sending to it a HTTP `GET` request.  
- Open "http://localhost:8099" in your web browser.


## Deploy the `express-weather` app to Heroku 
> Access the local folder containing the app.  

> Login to Heroku in local machine. 
```
$ heroku login
```       
Check the Heroku version.
```
$ heroku --version
```
> Deploy (upload) your app to the cloud app in Heroku.
Initialize git repository inside your working directory and connect that to your Heroku app using the second command with your app name.
```
$ git init
$ heroku git:remote -a unique-app-name-to-be-entered
```
> Add git commit to the Heroku master branch using the following commands.
```
$ git add .
$ git commit -m "init"
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
> Test your app.  Open the URL shown in `routes` above in your web broswer. 
In this tutorial, the URL is `https://cloudapp381.herokuapp.com/`.




# Other Useful Commands.
[Switch branches of a git repository from master to main and reploy the app](https://help.heroku.com/O0EXQZTA/how-do-i-switch-branches-from-master-to-main).
```
$ git checkout -b main
$ git branch -D master
$ git push heroku main
```
