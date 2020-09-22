# A Comparative Study between Angular & React

## Areas of Contrast

#### [1.  Angular & React](#angular-react)

#### [2.  Data Binding](#data-binding)

#### [3.  DOM Usage](#dom-usage)

#### [4.  Language](#language)

#### [5.  Bundle Size](#bundle-size)

#### [6.  Documentation and Library support](#documentation-and-library-support)

#### [7.  Development, Speed and Productivity](#development-speed-and-productivity)

#### [8.  State Management](#state-management)

#### [9.  Flexibility and downsizing to microservices](#flexibility-and-downsizing-to-microservices)

#### [10. Version Upgradation](#version-upgradation)

#### [11. Ease of Update](#ease-of-update)

#### [12. Change Detection Mechanism](#change-detection-mechanism)

#### [13. Ease of Review](#ease-of-review)

#### [14. Internationalization-I18N](#internationalization-i18n)

#### [15. Security](#security)

#### [16. Popularity & Growth Trajectory](#popularity-growth-trajectory)

#### [17. Companies Using](#companies-using)

#### [18. Recap](#recap)



# Angular & React

**Angular** and **React** are the two main cutting-edge technologies which have their predominance in the contemporary web and mobile development.

Both Angular and React are single page applications.

***Angular*** is a fully-featured MVC framework, developed and maintained by Google.

On the other hand, ***React*** is a front-end library with lots of open source packages to integrate with and was developed by ***Facebook*** and got globalised in 2013.


# Core differences between Angular and React

## Data Binding

**Angular** allows *two-way data binding* whilst **React** allows *one-way data binding*.

> ```Two-way data binding means that any changes we make to the model affect the view, and vice versa(Bi-directional data flows).```

> ```One-way data binding means any changes we make to the model affect the view, but not the other way around. In this way, the data only flows in one direction(Uni-directional data flows)```


## DOM Usage

DOM is the Data Object Model of a web app. You can either use a regular DOM or create a virtual DOM.

 1. **Angular** updates the **browser's DOM** directly because of its **two-way data binding** which updates the MVC.

 2. **React** does not update the *Real DOM* directly but it updates the **Virtual DOM**. It performs one-way data binding which updates the view.

> ```A virtual DOM is a simplified version of the DOM. By using a virtual DOM, we can change any element very quickly and without needing to render the whole DOM.``` 

> It drastically changes the performance from good to excellent.


## Language

**Angular**

 1. **Angular** uses ***TypeScript(.ts)*** for writing the business logic. ***TypeScript*** is an object oriented language and is a *superset* of *JavaScript*.

 Angular CLI will ***transpile*** the *.ts* files into *javascript*(**.js**) and makes them into a bundle which is ready to be deployed into production.

> ***Transpilation*** is an additional overhead in production of the Angular Apps.

 2. TypeScript is a *Statically typed language*  which means that we can define the variable type (string, number, or array etc)
 
 > ``` const name: String ```
 
 3. *Statically typed* feels structured, secure, readable, and easy to collaborate with others (prevents people from passing unexpected values).
 
 4. TypeScript is simply **ES6+** with types and much more
 
**React**

 1. **React** uses JavaScript (ES6) and ***JSX*** is the recommended language for developing **React** Application. 

> ***JSX*** is a preprocessor step that adds XML syntax to JavaScript(ES6). We can definitely use React without JSX but JSX makes React a lot more elegant. 

> ***JSX*** tags have a tag name, attributes, and children. If an attribute value is enclosed in quotes, the value is a string. Otherwise, wrap the value in braces and the value is the *enclosed JavaScript expression*.

 > ``` React.createElement("div", { className: "red" }, "Children Text");```

 2. ES6 is a *Dynamically typed language* which has the flexibility and creativity to focus more on creating than thinking to much about types, interfaces and generics and so forth.
 
 3. *Dynamically typed languages* require less time to write and more flexibility to use creativity
	
 4. ES6 has implemented lots of great features such as modules, classes, spread operator, arrow functions, template literals that allows us to write less, cleaner and more structured code.

## Bundle Size

We have calculated the bundle size of the ***Bitcoin*** project in **Angular** and **React** by building the project in both Angular and React

 1. **Angular**

*Bitcoin* project has been developed in Angular version **4.2**.

> Command to build the project from the project folder

```
ng build
```

A ***dist*** folder will be created in the project folder. If we reveal it, we have found the created bundles with their calculated sizes.


 2. **React**

*Bitcoin* project has been developed in React version **16.3.1**.

> Command to build the project from the project folder

```
npm run build
```

A ***build*** folder will be created in the project folder. If we reveal it, we will find the created bundles with their calculated sizes.

> Comparatively, projects developed in Angular weigh higher than React in *size*


## Documentation and Library support

#### Angular

 1. Angular Team backed up by **Google** has provided a detailed documentation in 

 > [Angular documentation](https://angular.io/guide/quickstart) 

This documentation explains the concepts(such as Forms, dependency Injection, Routing etc) and usage of them in application.
 
 2. Angular has provided a lot of best practises in writing a code and creation of a component, besides it has provided the flexibilities for writing and maintaining the complex code.

 3. Angular CLI has set a great workflow, build process and has eased the work of a developer in *transpiling* the **.ts** files and bundle them into **JS** files to build the project.

 4. We haven't relied on any third-party packages or community libraries for developing the angular ***Bitcoin*** project except for charts(libraries used -- ***d3***) since Angular team itself has 

provided a lot of packages for *Form Validations*, *Routing*, *Angular Material* etc.
	

#### React 

 1. **React** documentation is concise and less explanatory which is backed up by **Facebook**.

 > [React documentation](https://reactjs.org/docs/getting-started.html)

 2. We haven't found much documentation on best practises for writing a code and creation of component in *React*.

 3. We have relied on many **Community Libraries** for developing the *Bitcoin* project, libraries such as *Material-UI*, *react-router-dom*(for routing through the pages), *react-d3*, *react-charts* etc.
  
 
## Development, Speed and Productivity

**Angular**

 1. ***Angular*** offers enhanced development experience because of its **Command Line Interface**(CLI) that empowers creating a workspace and design functioning applications swiftly and producing *components* and *services* with one-line commands, built-in process to solve comprehensive problems and clean coding feature of *TypeScript*.
 
 2. Plenty of *out-of-the-box* solutions make Angular a cost-effective way to build a **Minimal Viable Product (MVP)** that helps to evaluate chances of your application for market success.

> A **minimum viable product (MVP)** is a development technique in which a new product or website is developed with sufficient features to satisfy early adopters. 
> The final, complete set of features is only designed and developed after considering feedback from the product's initial users
 
 3. In addition, Angular has a built-in ability to solve large-scale problems. 
 
 4. It dictates standards that facilitate *smooth collaboration* across teams working on the same large application. 
 
 5. **TypeScript** is the language used for writing logic, which identifies the bugs at early stages of development. It's focus is on productivity and consistency, perfectly fits enterprise goals and minimizing business risks.
 
 6. Angular has a steep learning curve when compared to React.
 
 7. The Google Angular IO framework offers multiple ways to solve a particular problem, has a complex component management system, as well as demand familiarity with different concepts and languages like templates, pipes, dependency injection, RxJS, TypeScript, etc.
 
**React** 
 
 1. Reactjs allows us to easily learn and make an app in React ecosystem if we are good with JavaScript. 
 
> ```React allows the developers to reuse the existing code and apply hot reloading into the process. This approach not only improves the app performance, but also accelerates the development speed. ```
 
 2. ReactJS provides multiple useful resources for newcomers to understand the framework and look forward to developing an application, even after frequent updates are rolled out.
 
 3. React provides little functionality out-of-the-box. 
 
 4. We cannot construct an app without third-party libraries. We have to select the right architecture, along with tools from different sources, which is a time-consuming process.
 
 5. The development *speed* and *productivity* gets affected due to the involvement of *third-parties libraries*. The React js app developers have to determine the right architecture along with the tools. 
 
> **Bottom line** is that with **React**, the *preparation period* will be longer than **Angular**. Angular outshines React in terms of productivity and the ability to be used for enterprise-scale apps as well.
 
 
## State Management

#### Angular

 1. **Angular** doesn't have an official library for managing a state.

 2. Angular Team has provided flexibility for creation of *services* where in we can manage the state.

 3. **NgRx** is a third-party package which allows us to manage the application state via **Observables**. It integrates nicely into Angular apps but prior study on that concept is highly recommended.

#### React

 1. Even React doesn't have an Official Package for managing the state.

 2. ***Redux*** and ***Flux*** are third-party packages which makes managing *application state* easier. These are easy to integrate into React but prior learning is recommended.
 
 
## Flexibility and downsizing to microservices

Another factor that contributes to React vs Angular choice is flexibility. 

**React** framework provides you with the freedom to choose the tools, libraries, and architecture for developing an app. 

It let us build a highly-customized app using only the features and tech stack we require.

**Angular**, on the other side, offers a limited amount of freedom and flexibility. 

For example, the latest version of Angular IO, i.e, Angular 7 lets you use Angular components inside their own frameworks and embed codes in an HTML-based application.

 > This indicates that React offers better flexibility and freedom in comparison to Angular.

In respect to microservices and microapps, React gives us more control to size an application by selecting only the things which are really necessary. 

They offer more flexibility to shift from an SPA to microservices using parts of a former application. 

Angular works best for SPA, as it is probably too bloated to be used for microservices.  

##  Version Upgradation

 1. **Angular** has an improved ***CLI*** that contains commands like a *ng_update* which makes it possible to easily *upgrade* the app to the latest Angular version.
 
 > This makes **Angular** app development less painful, provided most of the updating process is automated.
 
 2. Similarly, **React** also offers the facility to make seamless *transitions* between two versions. 
 
	A. The front-end development library relies heavily on the external libraries which make it possible to update and migrate the third-party components.
 
	B. Besides, the developers have to check all the time if the used third-party libraries are compatible with the recent versions of the JavaScript framework or not, which increases the efforts of the developers.

## Ease Of Update	
	
A developer can identify the bugs and service failures in a project if they are isolated in the form of separate chunks like components.

In **Angular**, Logic and Mark up are different components. So, A developer can easily identify the area of bug, tracks them and can modify that particular component/service.	
	
However, in React, if components are light-weight and decoupled, developers can easily identify the bug at its corresponding component and provide required fix.

  
## Change Detection Mechanism

> ``` Change detection is the mechanism designed to track changes in an application state and render the updated state on the screen. It ensures that the user interface always stays in sync with the internal state of the program.```

**Angular**

1. When the compiler analyzes the template, it identifies properties of a component that are associated with DOM elements. For each such association, the compiler creates a binding in the form of instructions. 

 > ```A binding is the core part of change detection in Angular. ```

2. It defines an association between a component’s property (usually wrapped in some expression) and the DOM element property.

3. Once bindings are created, Angular no longer works with the template. The change detection mechanism executes instructions that process bindings. 

4. The job of these instructions is to check if the value of an expression with a component property has changed and perform DOM updates if necessary.

> ``` Processing bindings that perform dirty checks and update the relevant parts of the DOM are the core operations of change detection in Angular.``` 

**React**

React uses a completely different approach. React doesn’t use bindings.

> ```The core part of the change detection mechanism in React is Virtual DOM comparisons.```

1. All React components implement the render method that returns a JSX template

2. In React, a template is compiled into a bunch of *React.createElement* function calls. Each сall of the *React.createElement* function creates a data structure known as a **Virtual DOM node**. 

3. The Virtual DOM node properties contain the results of the evaluated expressions

4. React runs change detection, executes the **render** function that returns a new version of Virtual DOM tree.

> ```It’s very important to understand that the render function is called during each change detection cycle.```

This means that every time the function is called, it can return a completely different Virtual DOM tree.

5. React runs a **diffing algorithm** on the two Virtual DOMs to get the set of changes between them.

Once the difference is found, the algorithm produces a patch to update the corresponding DOM nodes. And then this updated version of Virtual DOM will be used for the comparisons during the next change detection cycle.

> ``` Obtaining a new Virtual DOM tree from a component, comparing it to the previous version of the tree, generating a patch to update the relevant parts of the DOM and performing updates are the core operations of change detection in React.```


**Note:** 

> ```In React we always initialize the process of change detection manually. And we do it by calling the setState function```

There’s no way to trigger change detection automatically in React. Every change detection cycle starts with the call to the setState function.

> ```But in Angular we have both options. We can use the Change Detector service to run change detection manually or we can also rely on the framework to trigger change detection automatically.```


## Ease of Review
 
**Angular**
 
*Typescript* is the recommended language for building Angular applications. So, the developer and the reviewer should have a prior knowledge on the TypeScript for developing and reviewing the code.
 
 
**React**

*React* has been developed in JavaScript(ES6). So, a developer can perform review changes to the code easily if he/she has the knowledge on JavaScript. 
 
## Internationalization-I18N

  1. **I18N** is one of the *out-of-the-box* package in *Angular* whereas in React, we need to install an additional library to avail the i18n functionalities.
  
  2. Angular simplifies the following aspects of internationalization:

    - Displaying dates, number, percentages, and currencies in a local format.
    - Preparing text in component templates for translation.
    - Handling plural forms of words.
    - Handling alternative text.

  2. *Angular* i18n requires a full page refresh when trying to switch the user locale, unlike *React*.
  
  3. Angular provides some common pipes such as number, currency, and date which handle all the locale-specific changes internally unlike *react-intl* where sometimes we need to provide custom formats based on our use case and locale.
  
  4. In the case of Angular, we need to depend on external libraries such as **ngx-translate** to provide missing functionality such as *translating strings* which are not already on the template.
  
  5. There are different libraries available to localise a **React** App. Following are few of them:
	
 - **React-intl**
		
      This library is one of the most popular solutions for i18n in React. Offered by Yahoo and it is bundled with common locale data like dates, currencies, numbers, and support for over  150+ languages.
	
 > We cannot use it for non-react components as it requires the top level component to inject the context to the children. 
		
 - **React-intl-universal**
	
      react-intl-universal is a React internationalization package developed by Alibaba Group. 
		
	  It has been built on top of React-intl by allowing non-React components use the library by providing a singleton object that can be used to load the current locale.
	
 > It can also handle locale-specific messages for Times, Dates, Decimals and Plurals.
		
 - **i18next**
	
      **i18next** aims to target high as it promises to give us a complete solution to localize our product from web to mobile and desktop. 
 
 *i18next* is a plugin-based framework and provides you with plugins to:
 
    - Detect the user language
    - Load the translations
    - Optionally cache the translations
    - Extension, by using post-processing – e.g. to enable sprintf support.

 > *i18next* is a huge framework and it supports all the major javascript frameworks 	

 
## Security

### Angular

 Angular has built-in library for protections against common web-application vulnerabilities and attacks such as cross-site scripting attacks. 
 
 It hasn't covered application-level security, such as authentication and authorization.
 
> ```Angular has provided a lot of best practises for preventing cross-site scripting(XSS) and HTTP-level vulnerabilities```
 
> ```Cross-site scripting (XSS) enables attackers to inject malicious code into web pages. Such code can then, for example, steal user data (in particular, login data) or perform actions to impersonate the user. ```
 
**Prevention of cross-site scripting(XSS)** :

 1. Angular’s cross-site scripting security model :
		
 > To systematically block XSS bugs, Angular treats all values as untrusted by default. 
 > When a value is inserted into the DOM from a template, via property, attribute, style, class binding, or interpolation, Angular sanitizes and escapes untrusted values.

 2. Sanitization and security contexts :
	
 > *Sanitization* is the inspection of an untrusted value, turning it into a value that's safe to insert into the DOM.
	
 3. Content security policy :
		
 > *Content Security Policy (CSP)* is a defense-in-depth technique to prevent XSS. To enable CSP, we need to configure our web server to return an appropriate Content-Security-Policy HTTP header.
 
**HTTP-Level vulnerabilities** :

Angular has built-in support to help prevent two common HTTP vulnerabilities, *cross-site request forgery (CSRF or XSRF)* and *cross-site script inclusion (XSSI)*.

  1. Cross-site request forgery :
		
  ``` *Cross site request forgery (CSRF)*, also known as XSRF, Sea Surf or Session Riding, is an attack vector that tricks a web browser into executing an unwanted action in an application to which a user is logged in.```
	 
  ```A successful CSRF attack can be devastating for both the business and user. It can result in damaged client relationships, unauthorized fund transfers, changed passwords and data theft—including stolen session cookies.```
 
To prevent this, the application must ensure that a user request originates from the real application, not from a different site. 
The server and client must cooperate to thwart this attack.

In a common anti-XSRF technique, the application server sends a randomly generated authentication token in a cookie. 

The client code reads the cookie and adds a custom request header with the token in all subsequent requests. 

The server compares the received cookie value to the request header value and rejects the request if the values are missing or don't match.
 
> ```Angular's HttpClient has built-in support for the client-side half of this technique. ```

  2. Cross-site script inclusion (XSSI) :
	
  ``` *Cross-site script inclusion*, also known as JSON vulnerability, can allow an attacker's website to read data from a JSON API. ```
	 
  ```The attack works on older browsers by overriding native JavaScript object constructors, and then including an API URL using a <script> tag.```
	 
This attack is only successful if the returned JSON is executable as JavaScript. 

Servers can prevent an attack by prefixing all JSON responses to make them non-executable, by convention, using the well-known string

> ``` ")]}',\n".```

> ```Angular's HttpClient library recognizes this convention and automatically strips the string ")]}',\n" from all responses before further parsing.```

### React

React apps implement a whole lot of client-side logic in JavaScript, it doesn’t seem far-fetched to assume that XSS-type attacks could be worthwhile.

ReactJS is quite safe by design as long as it is used the way it’s meant to be used. For example, string variables in views are escaped automatically.


Script injection issues can result from bad programming practices including the following:

 - Creating React components from user-supplied objects;
 
 - Rendering links with user-supplied href attributes, or other HTML tags with injectable attributes (link tag, HMTL5 imports);
 
 - Explicitly setting the dangerouslySetInnerHTML prop of an element;
 
 - Passing user-supplied strings to eval().

During the build process, the JSX code is transpiled to regular JavaScript (ES5) code. New React elements are created from component classes using the createElement() function:

   ```
   React.createElement(
  type,
  [props],
  [...children]
)
```

However, the createElement() function in ReactJS would also accept plain objects such as JSON-encoded object passed as children.
 
## Popularity & Growth Trajectory

1. **Angular**

On GitHub, at the time of writing, Angular  has **44,421 stars** and **821 contributors**. However, it also **2,270 issues** (which are to be expected, since Angular is a full-fledged framework as opposed to just a library). 

Over the last 12 months, Angular has managed to garner 35 stars/day (on average).

2. **React**

Conversely, on GitHub, React has **120,089 stars** and **1,269 contributors**. As far as issues go, React has far less than Angular, at 398 (which is to be expected since React is merely a view library). 

> ```As we can clearly see, React has more than double the amount of GitHub stars and almost double the number of contributors. ```

Of course, it could also be argued that React came out sooner than Angular (version 2+), so it’s had a longer amount of time to collect these stars/contributors. 

However, React is growing faster, as it is has collected 97 stars/day over the last 12 months.


## Companies Using

*HUGE* companies are utilizing both React and Angular.

**React**:

- Facebook
- Airbnb
- Uber
- Netflix
- Instagram
- WhatsApp
- Dropbox

**Angular**:

- Google
- Nike
- Forbes
- Upwork
- General Motors
- HBO
- Sony


## Recap

| Technology        | Angular                                                                                                                                                                             | React                                                                                                                                                                                                                                        |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Framework         | Is a full framework                                                                                                                                                                 | Just a small view library                                                                                                                                                                                                                    |
| DOM               | Has a Regular DOM, which renders updates slower than React’s Virtual DOM                                                                                                            | Has a Virtual DOM, which renders updates faster than Angular’s Regular DOM                                                                                                                                                                   |
| Rendering         | The rendered JavaScript and HTML maintains a physical separation                                                                                                                    | Uses JSX, which combines markup and logic in the same file (making components easier to read)                                                                                                                                                |
| Components        | Utilizes Components: emerging web components standard                                                                                                                               | Components: emerging web components standard                                                                                                                                                                                                 |
| Data Binding      | Data Binding: two-way                                                                                                                                                               | Data Binding: one-way                                                                                                                                                                                                                        |
| Language          | You must use TypeScript                                                                                                                                                             | You Can use ES6/7 JavaScript, although you can use Typescript or Flow if you so choose                                                                                                                                                       |
| Mobile            | Ionic and Cordova are slower than React Native                                                                                                                                      | React Native is faster than Angular’s solutions                                                                                                                                                                                              |
| Development       | Plenty of out-of-the-box solutions make Angular a cost-effective way to build a Minimal Viable Product (MVP) that helps to evaluate chances of your application for market success. | React provides little functionality out-of-the-box.                                                                                                                                                                                          |
| Change Detection  | The change detection mechanism executes instructions that process bindings.                                                                                                         | The core part of the change detection mechanism in React is Virtual DOM comparisons.                                                                                                                                                         |
| Testing           | Jasmine & Mocha                                                                                                                                                                     | Jest & Enzyme                                                                                                                                                                                                                                |
| Learning Curve    | Learning Curve is higher, but once you understand it you have an entire MVC framework                                                                                               | Learning Curve is lower, but you only get the view. Because of this, you’re going to have to learn a slew of 3rd party libraries. Ex. State management (Redux or MobX), Asynchronous calls (react-promise, react-thunk, or react-saga), etc. |
| Scalability       | easy to scale                                                                                                                                                                       | is more testable, so also easy to scale                                                                                                                                                                                                      |
| Popularity        | dropped since AngularJS (Angular 1)                                                                                                                                                 | has increased exponentially                                                                                                                                                                                                                  |
| Growth Trajectory | GitHub stars: 44,421 / Contributors: 821 / Issue: 2,270                                                                                                                             | GitHub stars: 120,089 / Contributors: 1,269 / Issues: 398                                                                                                                                                                                    |
| Size              | larger, resulting in longer load times and performance on mobile                                                                                                                    | smaller than Angular, so a bit faster                                                                                                                                                                                                        |
| companies using   | Google, Nike, Forbes, Upwork, General Motors, HBO, Sony                                                                                                                             | Facebook, Airbnb, Uber, Netflix, Instagram, Whatsapp, Dropbox                                                                                                                                                                                |