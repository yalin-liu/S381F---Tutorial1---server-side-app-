# Learn to test *server.js* apps locally and deploy it to the cloud (Heroku)
This tutorial demonstrates **how to deploy a simple server.js app to Heroku**. You are going to deploy two app samples, one is **helloworld** that responds to HTTP `GET` requests and returns a simple text message **Hello World!**; and another is **express-weather** that also responds to a HTTP web and returns the weather in global regions.

## Preparations
### Local System: Virtual Machine + Ubuntu
For lab computer, do the following operations:
i) Boot into the VMOS partition, 
ii) run VMWare Workstation Player, 
iii) play virtual machine, and 
iv) run **the Ubuntu**.

For your PC, do the followering operations:
i) Copy **the Ubuntu image** in lab computer (C:\VM_Image\Ubuntu 64-bit 19.04.vmwarevm), 
ii) [Install VMware WorkStation Player](www.vmware.com/asean/products/workstation-player/workstation-player-evaluation.html) in your PC, 
iii) put the Ubuntu image in your PC, and 
iv) Run the Ubuntu.

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

## Task 1 - Learn the basic Linux command in local system 
### Create folder 
> Access the home directory, show the path, and list all files in current folder
```
cd ~
pwd
ls
```
> Create the follower folder hierarchy 

![image](https://user-images.githubusercontent.com/42903384/185931911-18732174-0343-46f3-8bd3-5966f667b76b.png)

```
mkdir comps381f cd comps381f
mkdir lecture tutorial cd tutorial
mkdir t01 t02
```
> Download `primer-dataset.json` at the following URL using your web browser. Right click and save the json file.
"https://raw.githubusercontent.com/mongodb/docs-assets/primer-dataset/primer-dataset.json"
> Write down the linux command to place `primer-dataset.json` into the `t02` folder.
```
mv ~/Downloads/primer-dataset.json ~/comps381f/tutorial/t02
```
> Writen down the single linux command to delete the `comps381f` folder (and its subfolder).
```
rm -rf ~developer/comps381f
```


### Updade `npm` in local system
```
npm install npm@latest
```


## Test the app locally
# Getting Started with Heroku (a cloud platform)

### 2. Open a terminal in local machine (Linux+Ubuntu).
Install the Heroku Command Line Interface (CLI). 
The Heroku CLI requires Git, please install Git.
```
$ sudo apt-get install git
```
Check the git version to verify your installation.
```
$ git --version
```
Install with Ubuntu / Debian apt-get
```
$ curl https://cli-assets.heroku.com/install-ubuntu.sh | sh
```
This version doesn’t autoupdate. Update it manually via `apt-get`. 
Check the heroku version to verify your installation.
```
$ heroku --version
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
[Switch branches of a git repository from master to main and reploy the app](https://help.heroku.com/O0EXQZTA/how-do-i-switch-branches-from-master-to-main).
```
$ git checkout -b main
$ git branch -D master
$ git push heroku main
```
# What's Next?
Follow the instructions to deploy [express-weather/README.md](https://github.com/yalin-liu/cloudapp/blob/1d4136ba314de582e6928bcb8fae830011aa37c4/express-weather/README.md) to Heroku.
