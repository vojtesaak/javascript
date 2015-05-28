# Storyous developers bootstrap() {

## Table of Contents

  1. [Technology](#technology)
  1. [Newbie dictionary](#newbie-dictionary)
  1. [Code style](#code-style)
  1. [Git flow](#git-flow)
  1. [Quick tips](#quick-tips)

## Technology

  - [1.1](#1.1) <a name='1.1'></a> **Node.js**: To serve be able to handle http+sockets requests.

    + [Node.JS API](https://nodejs.org/api/)

  - [1.2](#1.2) <a name='1.2'></a> **Can.js**: Simple, Angular like clientside MVC framework 

    + [Can.JS guide](http://canjs.com/guides/Tutorial.html)

  - [1.3](#1.3) <a name='1.3'></a> **Express.js**: Simpliest HTTP framework for Node.js

    + [Express.JS guide](http://expressjs.com/guide/routing.html)

  - [1.4](#1.4) <a name='1.4'></a> **{{Handlebars/mustache}} templates**: 

    + Server side: [Handlebars](http://handlebarsjs.com)
    + Client side: [can.Stache](http://canjs.com/docs/can.stache.html)

**[⬆ back to top](#table-of-contents)**

## Newbie dictionary

  - [2.1](#2.1) <a name='2.1'></a> **POS**: Point of sale, an Android application for restaurants. They use it to print and track bills.

  - [2.2](#2.2) <a name='2.2'></a> **PRO**: Storyous for PROffesionals. Our sales page. ([pro.storyous.com](http://pro.storyous.com))

  - [2.3](#2.3) <a name='2.3'></a> **WWW**: Social network and magazine for foodies. ([storyous.com](http://storyous.com))

  - [2.4](#2.4) <a name='2.4'></a> **PAY**: Backend for POS system (APIs and web application). 

  - [2.5](#2.5) <a name='2.5'></a> **WIKI**: Every project is documented on it's Github wiki.

  - [2.6](#2.6) <a name='2.6'></a> **JIRA**: Our project tracking and bug reporting SW. [here](http://storyousjira.atlassian.net).

**[⬆ back to top](#table-of-contents)**

## Code style

  - [3.1](#3.1) <a name='3.1'></a> **ES5 style like AirBNB**: [for the ES5-only guide click here](es5/). 
  
  - [3.2](#3.2) <a name='3.2'></a> **ES5 Examples**: [example of class and service](es5-sample/).

  - [3.3](#3.3) <a name='3.3'></a> **Can.JS pro-tips**: [some advices, how to use Can.js](can/).

**[⬆ back to top](#table-of-contents)**

## Git flow

  - [4.1](#4.1) <a name='4.1'></a> **Keep git clean**: We use a Gitflow workflow to manage projects on git.

    + Never commit to master/alpha/beta/dev branches directly
    + Each "feature" should have own branch
    + Make a pull request when the work is done 

![Gitflow](http://nvie.com/img/git-model@2x.png)

**[⬆ back to top](#table-of-contents)**

## Quick tips

  - [5.1](#5.1) <a name='5.1'></a> **Avoid callback hell.** Keep the app clear. 
  
    + Use Promisses and Deferreds to keep an order.
    + But it's not a silver bullet!
    
  > We use [Q module](https://www.npmjs.com/package/q) 

    ```javascript
    
    publicMethod: function(foo, bar, callback) {
        this.doSomethink(foo)
            .then(this._nextMethod(bar))
            .then(callback);
    }

    ```

  - [5.2](#5.2) <a name='5.2'></a> **Keep the code simple and self descriptive:** It's good to keep methods, classes and files short and self descriptive. 

    + keep file 500 lines max. (300 is good)
    + keep methods 40 lines max. (25 is good)
    + max. 4-5 arguments in method (use instance of a Class, when u need more)
    + max 3-4 nested blocs (ifs/cycles/functions) in a method

**[⬆ back to top](#table-of-contents)**

## Quick tips

  - [2.1](#2.1) <a name='2.1'></a> Use `const` for all of your references; avoid using `var`.

  > Why? This ensures that you can't reassign your references (mutation), which can lead to bugs and difficult to comprehend code.

    ```javascript
    // bad
    var a = 1;
    var b = 2;

    // good
    const a = 1;
    const b = 2;
    ```


**[⬆ back to top](#table-of-contents)**

# };
