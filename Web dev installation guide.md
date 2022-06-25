# Web dev installation guide

## Back-end dev

### 	*For node.js development and relevant database* 

1. install node.js https://nodejs.org/en/download/current/ first.
   1. tried install in the default destination location if it doesn't work
   2. tried install 32-bit
   3. Finally, a command line saved me "npx -p npm@6 npm i --legacy-peer-deps" in https://www.programmersought.com/article/20808365240/
2. remember to install those additional tools as well if you can, as we are going to play around with them 
3. then run "curl -qL https://www.npmjs.com/install.sh | sh" written in https://www.npmjs.com/package/npm  or no need to run it because you've installed it.

## MongoDB

You'd better use the default download directory, it helps you setup the environment faster.  

After the download, remember to cd ~, so that you can be directed to the c://users/ralap, and then create a file called '.bash_profile',   -->  vim .bash_profile --->   copy the code below and paste them in the file,  remember to modify the version number to match the one you download or it won't work

`alias mongod="/c/Program\ files/MongoDB/Server/4.0/bin/mongod.exe"`
`alias mongo="/c/Program\ Files/MongoDB/Server/4.0/bin/mongo.exe"`

### 	*For php development and relevant database*





# web dev Library

## 4 ways to access to API json data:

XHR

Fetch  (front-end library for XHR == XMLHttpRequest)

jQuery (library)

Axios --> (lightweight library) aiming for less code to make request  ( cdn, npm )



## React

npm install -g create-react-app

create-react-app helloworld

cd helloworld

npm start

==================

if not successful

npm uninstall -g create-react-app

npx create-react-app helloworld

cd helloworld

npm start

=====================

sometimes, god is dumb, so you need to work a way out yourself

e.g. npm update -g npm

npm install -force

npm cache clean --force

npm install --global --production windows-build-tools

```js
npm config set python /path/to/python2.7
```

npm config set cache "C:\\Users\\Ralap\\AppData\\Roaming\\npm-cache" --global



# setup web dev env on WSL2

check wsl version 

```powershell
wsl -l -v
```

```powershell
wsl --set-version Ubuntu-20.04 2
```

```powershell
wsl --set-default-version 2
```

```powershell
wsl --shutdown
```



## fixing-Errors

### if "sudo apt update" brings errors

##### case 1: 

The `date` command reports a wrong date and time. I used the following:

```
sudo apt install ntp 
sudo service ntp restart 
```

Then the `date` command reports the correct data and time. `sudo apt update` now can work.



##### case 2:

Run:

```
sudo hwclock --hctosys 
```

This command gets the latest time from your Windows machine’s RTC and sets the system time to that.

https://askubuntu.com/questions/1096930/sudo-apt-update-error-release-file-is-not-yet-valid
