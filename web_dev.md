# <u>*Github*</u>

## How to create a simple Github Pull Request

1. **fork the project**
2. it will appear at your repository.
3. it means you have a brand-new copy of it.
4. you are going to clone it :  **git clone {git@github.com:projectPath/projectName.git}**
5. **cd to the directory**
6. take a look at what stuff you want to change and **change it.**
7. **create a new branch: git checkout -b fix-readme-typo**
8. to change it, type "**emacs README.md" or type emacs -nw README.md**  to open a new window.  
9. **modify it**
10. **git status**  --> to look at the status
11. to the differences  , type ---> **git diff**
12. **git add README.md**
13. **git commit -m "Fix type in README"**
14. **git push origin fix-readme-typo**
15. you will see "**compare & pull request**"

### Practical Guidance for cloning and pushing 

download the file

git clone [url]

git add

git status 

git commit -m "created the very 1st web portfolio"

git push

### How to change the username and email in git?

nano .git/config   **I can modify the user.name and user.email in the config file**

git config --list    **to check the status of the situation through a list**

git config --global user.name "xxxxx"

git config --global user.email "xxxxx"

### Create a new repository on the CLI

1. git init
2. git add README.md
3. git commit -m "first commit"
4. git remote add origin git@github.com:cobimr/my-new-website.git
5. git push -u origin main




## Course note from 0-master

1. source control allows a team work on the same project

   we have one place instead of our own computer, instead of each of us having a copy of the project, with source control, we have a copy of the project, but there is centralized location up somewhere, maybe owned by a company, like github, that has the ultimate version that we each talk to to make sure that we each have the same version.  Getting Github is a way to be able to use source control.  

2.  What Github will do is to notice if there is a merge conflict, and then inform the people who are involved with the conflict and allow colleagues to discuss about that and figure out which version is final one. 

3. getting used to the terminal is important instead of getting a desktop app

4. 

# <u>*Problems to solve*</u>

## solving COR Issues with heroku server

heroku CLI, npm and node.js is required

1. heroku login
2. open vscode's terminal
3. git clone [whatever the shit you got just to Js reverse proxy which adds CORS headers to the proxied request]
4. cd into that git file
5. npm install
6. heroku create
7. git push heroku master/main
8. open that heroku app and use that url as proxyUrl
9. usage: proxyUrl + apiUrl, it will add CORS Headers to the proxied request.



# Get a cheap domain name

Domain Name Server: namecheap.com



# Debug guidelines

remember a few tips:

1. check the top of js file first, to find any typo variables.

2. if top of the js file is not wrong, then check the html typo.

3. finally css.

   Can't find any bug? Use web dev tool in browser pressing F12 and pinpoint the source code to check

# Projects that I think will help me get a job: 

1. Build many fucking UI and projects.
2. Create my own resume website.
3. contribute on the github as much as possible

# To optimize the website

1. reduce the amount of lines in code

2. reduce the amount of time spent in algorithm, using big O notion.

3. put **navbar** at the bottom of the code because it is not that important yet before audience saw the html.

4. let users see the top of the website first, and then let the rest of the website slowly fading in to produce an illusion that the site is ready for them in shorter time.  

5. use **defer** or **async** to optimize the website: 

    **defer** is used to defer some codes or files that are not as important as others like script.js, html or others.    Usually, we use it to defer navbar.js, since users don't usually use navbar first when they first visit the website.

reference: https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/loading-third-party-javascript#use_async_or_defer

# Color Pattern

# font choice

Nunito   -- Regular 400 italic

font-family: 'Comfortaa', cursive;

Pattern 1: Allura, Gochi Hand, Biryani

# Use of push in Javascript

using PUSH can help us to populate the bookmarks on webpage altogether.

The array can store all the data that are not deleted yet.  



# the URL to scrape the web's favicon and use it

const favicon = document.createElement('img');

favicon.setAttribute('src', `https://s2.google.comusercontent.com/s2/favicons?domain=${url}`);

favicon.setAttribute('alt', 'Favicon');

https://s2.google.comusercontent.com/s2/favicons?domain=



# Consider how data structure can help to optimize the web's operation.

things like an object has a better way to search the data 

bookmarks = {};



Object.keys(bookmarks).forEach(id) => {

const { name, url } = bookmarks[id];

};



bookmarks[id] = {

​	name: 'abc',

​	url: 'https://abc.design',

};



if (bookmarks[id]) {

delete bookmarks[id];

}



Objects search data by their id, not by looping index number

We need to organize data for proficiency of the web development



# <u>*web dev Future*</u>

'**web assembly**' can be a way to standardize the machine code format so that there is no need for interpreter, but only use compiler directly.

We can use "blazor" - which is a library, makes web performance run faster without actually reading assembly code.

# 

# **<u>*Web dev Library*</u>** suggestion

tailwindcss for css just like Babel in React for html and javascript 

recommend: tailwindcss + React.

# <u>*Problems to avoid*</u>

## Stack Overflow and Memory Leak

stack overflow: e.g. recursion will crash the website in the old days

memory leak: e.g. whenever you use setInterval(), remember to clear it using clearInterval(); 



## Hidden classes

When js object is built, if you want to add more data to an object, you need to add it in an top-to-bottom order or it will slow down the execution speed.



## Don't block the event loop

don't put shitty slow code on the stack, especially when you try to render image processing or animation, 

 when you do that, the browser won't do anything that you want it to do.

Slow code like 'delay();'

# <u>***During web development***</u>

## 	Don't type every single code yourself

### 		HTML

learn emmet

### 		CSS

#### 				autoprefixer(google the website if i don't know it)

learn to use autoprefixer at the final stage of the development, because css file would so big that you will feel overwhelm to check the prefix of the property,  the prefix is used to make sure the css property can be rendered in certain type of brower like firefox.

# 

### D3 (data-driven javascript library)

// it is to make input value show up in the p element,  but the data is not saved, once refresh the page, the data will be gone. 

`d3.select("#new-note").on("submit", function() {`
    `d3.event.preventDefault();`
    `var input = d3.select("input");`
    `d3.select("#notes")`
      `.append("p")`
         `.classed("note", true)`
         `.text(input.property("value"))`
    `input.property("value", "")`
`})`

## asynchronous methods / functions

#### `promise, .then`  

`var counter = 0;`
`let promise = new Promise( (resolve, reject) => {`
`setTimeout( () => {`
    `counter++;`
    `console.log("Counter: ", counter);`
    `resolve(counter);`
    `}, 1000);`
    `}    
);`

`promise.then((counter) => {`
    `console.log("counter passed to resolve: ", counter);`
    `return new Promise( (resolve, reject) => {`
        `setTimeout( () => {`
            `counter++;`
            `console.log("Counter: ", counter);`
            `resolve(counter);`
        `}, 2000);`
    `});`
`}).then((counter) => {`
    `console.log("counter passed to resolve: ", counter);`
    `return new Promise( (resolve, reject) => {`
        `setTimeout( () => {`
            `counter++;`
            `console.log("Counter: ", counter);`
            `resolve(counter);`
        `}, 3000);`
    `});`
`});`

**<u>====================================================</u>**

`var counter = 0;`
`function incCounter() {`
    `counter++;`
    `console.log('Counter: ', counter);`
`}`

`function runLater(callback, timeInMs) {`
    `var p = new Promise((resolve, reject) => {`
        `setTimeout(() => {`
            `var res = incCounter();`
            `resolve(res);`
        `}, timeInMs);`
    `});`
    `return p;`
`};`

`runLater(incCounter, 1000).then(() => {`
    `return runLater(incCounter, 2000);`
`}).then(() => {`
    `return runLater(incCounter, 3000);`
`}).then (() => {`
	`Final .then is not necessary, says the lectuerer.`
`});`



## array method

forEach, filter, map, some, every, reduce

## Closure and 'this'

call, apply, bind

### Call

<u>*To select all the divs that contain 'Hello'*</u>

`var divs = document.getElementsByTagName('div');`

`var divsArray = [].slice.call(divs);`

`divsArray.filter( (value) => {`

​			return value.innerText === 'Hello'

`});`

### Apply

If you can't carry array using "call", then use "apply" instead.

### Bind

var colt = {

​		firstName: "Colt",

​		sayHi: () => {

​				setTimeout( () => {

​						console.log("Hi " + this.firstName);

​				}.bind(this), 1000);

​		}

}



## Back-end 

### MongoDB

to connect MongoDB, you need to 

`var mongoose = require('mongoose');`  

`mongoose.connect('mongodb://localhost/todo-api');`   // we need "todo-api" to specify the database name, so that we can create database.

## API

use `res.json()` when you build an API, so that user can access the data in json format easily.



### deal with json data format from API

node.js version  (check: D:\udemy\web dev project\openWeatherMap\index.js)

`// importing https library from npm first`

`const https = require('https');`

`https.get(apiUrl, (res) = >{`

​	`res.on('data', (data) => {`

​		`const weatherData = JSON.parse(data);`

​		`var wea-temp  = weatherData.main.temp;`

​	`});`

`});`



vanilla js version (check: D:\udemy\advanced_web_dev\promise_practise(octokitAPI)\app.js)

`// need to define Get function`

`function Get(yourUrl){`

​	`var Httpreq = new XMLHttpRequest(); // a new request`

​    `Httpreq.open("GET",yourUrl,false);`

​    `Httpreq.send(null);`

​    `return Httpreq.responseText;`     

`}`

`let urls = usernames.map(`

​		`username => JSON.parse( Get( baseUrl + username ) )` //get the Url and then use JSON.parse to access the data

`);`



to load images

`require("BMPLoader").load(bmpString);`

## 



## React

### package

###### unpkg

 is a fast, global content delivery network for everything on [npm](https://www.npmjs.com/)

unpkg.com/:package@:version/:file

###### JSX --> JS  (Babel)

cdn : go check cloudflare

Normally use Babel transpiler/Library to transpile the JSX to vanilla JS

the transpiling process of JSX is a bit longer than vanilla js.

remember to use the tool to optimize the the loading process so that it can be run faster.

###### @material-ui/icons

https://next.material-ui.com/

```bash
npm install @material-ui/icons
```

###### @material-ui/core

```bash
npm install @material-ui/core
```

https://www.appbrewery.co/p/web-development-course-resources/

## ALGORITHM

### for JSON format data from API,  

assume type of the '**data**' is **[{key: value},{key: value},{key: value}]**

firstly, you make sure **'data'** you get is **an array that contains object**, which is I believe, a typical JSON format data.

**The outcome of this algorithm will be an object that contains the most followers**

​     

```js
 var arrLikeObj = data.sort((a,b) => a.followers > b.followers); 
```

//'data' and 'arrLikeObj' is the same type of data, so we can ignore 'arrLikeObj', it is useless in this case.      

```js
      var arr = []

​      var obj = {}

​      data.forEach((value, index) => {

​        arr.push(value.followers)

​        obj[index] = value;

​      })

​      let max_followers = Math.max(...arr)

​      var max_obj = {}

​      for( var i = 0; i < arr.length; i++) {

​        if (obj[i].followers == max_followers){

​          max_obj = obj[i];

​        }

}
```



### **Sorting out letter frequency: **

**the most frequent letter would be at the middle**

```js
function getFrequencies(str) {

  var sorted = str.split("").sort()) // [1,2,3,4]

  var data = []

  for (var i = 0; i < sorted.length; i++) {

​    var last = data[data.length - 1];     

​    if (last && last.character === sorted[i]) last.count++;

​    else data.push({ character: sorted[i], count: 1});

  }

  return data;

}
```

// getFrequencies("hello world!")

// will output an array containing objects

### Get the median of an array of numebrs

//#Source https://bit.ly/2neWfJ2  

```js
const median = arr => { 

		const mid = Math.floor(arr.length / 2),    

					nums = [...arr].sort((a, b) => a - b);
		return arr.length % 2 !== 0 ? nums[mid] : (nums[mid - 1] + nums[mid]) / 2;

};



console.log(median([5, 6, 50, 1, -5]));

console.log(median([1, 2, 3, 4, 5]));
```



Sample Output:

```
5
3
```

## DATA STRUCTURE



# Python Flask



```python
from flaskblog import db
db.create.all()

from flaskblog import User, Post

user_1 = User(username='kt', email='123@123.com', password='123123')
db.session.add(user_1)
user_2 = User(username'bt', email='admin@123.com', password='123123')
db.session.add(user_2)
db.session.commit()
User.query.all()

User.query.first()   --> e.g.  to check if the username is taken

User.query.filter_by(username)

================================
from flaskblog.models import User, Post

```
