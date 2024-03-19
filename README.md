# Scope

Here you will learn about scope, context and this

## Steps

- Clone this repo:
    - click the green Code button in github, copy the URL
    - open the Visual Studio Code in your learning folder and and write in terminal `git clone <paste_your_url_here>`
- create a separate branch `git switch -c "dev"`
- add html and css files and code
- in VS Code, click on html file and Go Live (plugin installed previously) to avoid refreshing the page on changes
- when you're done coding, add the changes to staging using + button in VS Code Source Control tab or type on terminal `git add .`
![VS Code staging](images/stage.png) 
- commit and push the code `git commit -am "commit message here"`, `git push -u origin dev`
- go to github and raise a pull request from your development branch to master
![Open PR](images/pullRequest.png) 

## Requirements

Exercise 1:
- create an html file which runs the following script, and add comments with your explanation
```
// exercise 1: scope
const a = 1;

const testFunction = function () {
  console.log(a);
};

testFunction(); // a. what does this output and how it does it?

const testObject = {
  a: 2,
  testFunction,
  run() {
    const a = 3;

    testFunction(); // b. what this function refers to?
    this.testFunction(); // c. what about this one, what does it refer to?
  }
};

testObject.run(); // d. what is the expected output here and why?
```

Exercise 2:
- add the following script, and add comments with your explanation
```
// exercise 2: context and a bit of scope
var outputFunction = function () {
  console.log(this);
};

outputFunction(); // a. what does this function output and why?

const contextObject = {
  outputFunction,
  run() {
    outputFunction(); // b. what function does this refer to?
    this.outputFunction(); // c. what about this one?
  },
  surrounding: this,
  arrowRun: () => {
    outputFunction(); // d. and this one?
    this.outputFunction(); // e. and this one?
  }
}

contextObject.run(); // f. what's the output here and why?
contextObject.arrowRun(); // g. what about here?

const contextObject1 = {
  run: contextObject.run,
  arrowRun: contextObject.arrowRun
};

contextObject1.arrowRun(); // h. what's happening when running this one?
contextObject1.run(); // i. what about this one?
```

Exercise 3:
- add the following script, and add comments with your explanation
```
// exercise 3: context
const fancyObject = {
  a: 1,
  b: 2,
  run() {
    const arrowFunction = () => console.log(this);
    const regularFunction = function () { console.log(this) };
    
    arrowFunction();
    regularFunction();
  }
}

fancyObject.run(); // what does this output and why?
```
