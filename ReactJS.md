# ReactJS

## Contents

#### [1.  Definition of ReactJS](#definition-of-react)

#### [2.  Create React App](#create-react-app )

#### [3.  Project Creation](#project-creation)

#### [4.  Project folder structure](#project-folder-structure)

#### [5.  JSX](#jsx)

#### [6.  Components](#components)

#### [7.  Styling React Components](#styling-react-components)

#### [8.  Props & State](#props-state)

#### [9.  Component Lifecycle](#component-lifecycle)

#### [10. Event Handling](#event-handling)

#### [11. Lists](#lists)

#### [12. React Keys](#react-keys)

#### [13. Web Connectivity](#web-connectivity)

#### [14. Routing](#routing)

#### [15. Charts](#charts)


### Definition of React

 React (Or  ReactJS, React.js) is an open source  Javascript library to build reusable interface components. It was developed by Facebook.

### Environment setup 

> Kindly ensure that we have the following softwares to create and run a react app.

[Node.js](https://nodejs.org/en/download/)   
[Visual studio Code Editor](https://code.visualstudio.com/download)

	
### Create React App

Open command prompt and type in the following line of code


 > npm install -g create-react-app


### Project Creation  

React project can be created at any desired folder by inputting the following lines of code


 > create-react-app react-bitcoin


![***react-bitcoin*** project creation!](/assets/images/philly-magic-gardens.jpg "react-bitcoin project creation")


 > cd *react-bitcoin*

  Start the application
 
 > npm start


### Project folder structure

Open the project **react-bitcoin** in *Visual Studio code*.

The project folder structure is as follows

![***react-bitcoin*** folder structure!](/assets/images/philly-magic-gardens.jpg "react-bitcoin folder structure")


### JSX

*JSX* stands for JavaScript XML.

*JSX* is a preprocessor step that adds XML syntax to JavaScript.  *JSX* is the alternative of **React.createElements**.

We can declare a variable or expression inside JSX by wrapping them around *curly braces* > {}

JSX is actually closer to JavaScript, not HTML, so there are a few key differences to note when writing it.

> - ***className*** is used instead of **class** for adding CSS classes, as class is a reserved keyword in javascript
>
> - Properties and methods in JSX are **camelCase** such as onclick will become onClick.
>
> - Self-closing tags must end in a slash such as \<img />
 

syntax of ***JSX*** is as follows

```JSX

const companyName= 'Fujitsu';
const element = <h1>Hello, {companyName}</h1>; //JSX

```
The above example illustrates JSX. 

In the first line, we declared a constant – *companyName*, which is a String. It is not a JSX.

In the second line, we declared a constant by *element*. This syntax is neither a string nor HTML. It is a JSX. CompanyName is been enclosed within *curly braces* in HTML element h1 with opening and closing tags.

It will render the message ***Hello Fujitsu*** in the web page.

Therefore, we can say that *JSX* syntax helps us *render* content in the *UI*.

When we *compile react*, it *transpiles* the code into **ES5** because the *browser doesn’t support* **ES6**. 

Therefore, **Babel** is a transpiler which  *compiles* **JSX** down to *React.createElement()* calls.

#### JSX in a Component

**JSX** can also be used in the React Component.

```JSX

1. import React from 'react';

2. class Layout extends React.Component {

3. render() {

4.	return (
	
5.	<div>

6.		<h1>Welcome to Fujitsu</h1>

7.		<Users region="BAS">Name:Fujitsu- Region</Users>

8.		<Users region="MIS">Name:Fujitsu- Region</Users>

9.	</div>
	
10.		)

11.   }
12. }

13. export default Layout;

```

The above example shows how *JSX* is used in React. 

We can see that there are a group of tags from line number 6 to 8 which are enclosed in a div tag. 

> This entire code from line number 6 to 8 is JSX.

**\<Users>** is a *user defined component*. As we can see, we have used it a couple of times.

*JSX* has provided the greater option for **Reusablility** of a component.


> \<Users> component

We have defined <Users> Component as:
```
const User = (props) => {
return (
	<div>{props.children} - {props.region}</div>
	)
}
```

The above code will be ***transpiled*** to **ES5** as below

```ES5
var User = function User(props){
return React.createElements("div", null, props.children, "- ", props.region)
}
```

> *JSX* looks clean and readable but we need a transpiler called ***Babel*** which converts the JSX to browser readable mode(i.e ES5)


### Components

A **Component** is one of the core building blocks of React and these usually takes the form of JavaScript classes. 

**Components** make the task of building UIs much easier.

React separates concerns with loosely coupled units called “components” that contains both markup language and business logic.

A typical React app therefore could be depicted as a component tree - having one root component **App** and then an potentially *infinite amount* of **nested child components**.

![***Component Tree structure*** folder structure!](/assets/images/philly-magic-gardens.jpg "Component Tree structure")

Components split the UI into *independent* and *reusable* pieces

Components are of two types

 **1. Functional Component**   
 **2. Class Component**
	
#### Functional Component
	
**Functional component** is simply a javascript function.
	
*Functional Component* is a React component, it accepts a single “props” (which stands for properties) object argument with data and returns a React element.

*Functional Components* are purely referred as *Functional*, *Stateless*, *Presentational* because they all do is output *UI* elements and they do not hold or manage the *state*.

```jsx
function Welcome(props) {
	return <h1>Hello, {props.name}</h1>;
	}
```
> or

**Functional component** (called *chartComponent*) written using *ES6’s arrow* function syntax that may/may not takes *props* argument and returns a div tag with the text 

```jsx
const chartComponent = (props) => {
	return <div> This is {props.name}</div>

	}
```

#### Class Component

Components can also be written using **ES6 classes** instead of functions. Such components are called **class components**>

**Class Components** have some additional features such as the ability to contain logic (for example methods that handle *onClick* events), *local state management*.

**Class Component** are also called as ***stateful components*** because they can hold and/or manage local state.

**Class Component** are usually referred to as a ***Container*** because they hold or contain numerous other (mostly **Functional**) components.

> Class components have a considerably larger amount of markup. Using them excessively and unnecessarily can negatively affect performance as well as code readability, maintainability and testability.

> We can create a component by extending the  ***React.Component*** class


```jsx

class Layout extends React.Component {
    render() {
        return <h1>Page Layout</h1>;
    }
}

```

**Note:**

**Class Component** are *advisable* to use if and only if we 

- need to manage local state

- need to add lifecycle methods to your component

- need to add logic for event handlers

Otherwise, **always** use a *Functional Component*


### Styling React Components

We have applied css styles to the React components in our application to differentiate components and to produce aesthetic look.

We have implemented two different ways of styling in our Application.

- External CSS

- Inline CSS

#### External CSS

We have created a separate css file for each component and imported that css into the JS file.

> Example

![***.css file creation*** folder structure!](/assets/images/philly-magic-gardens.jpg ".css file creation")

> ***BodyContent.css***

```JSX

.gridContainer {
  display: grid;
  grid-template-columns: auto;
 
}
.gridItem {
  font-size: 17px;
  text-align: center;
}
```

> ***BodyContent.js***

```JSX

import React from 'react';
import classes from './BodyContent.css';

const BodyContent = (props) => {
  const { t, tReady } = props;
  return (

    <div className={classes.gridContainer}>
      <div className={classes.gridItem}>Bitcoin</div> 
      </div>
    

  );
}

```

#### Inline CSS

In Inline styling, we will write the css inside a JSX/JS file.

We will create a constant object and write all the css properties inside the constant object as follows:

> Example:

> ***BodyContent.js***

```JSX
import React from 'react';


const styles = {
  fontSize: '42px',
  color: "#ff2c0e",
  position: 'relative',
  top: '14px'
}

const BodyContent = (props) => {
  const { t, tReady } = props;
  return (
    <p style={styles}> BTC01.234567/$9,876</p>

  );
}

```

In the above example, we have assigned the ***styles*** object to the ***style*** property as *'style={styles}'*.
So, the css properties from the *styles* object are made available dynamically to the style property.

### Props & State

props and state are the core concepts of React.

### Props

React allows us to pass information to a Component using a special property called **props** (stands for properties). **Props** are basically a kind of global variable or object. 

props allow you to pass data from a parent(wrapping) component to a child(embedded) component.

 Example:

> **Layout component:** (Parent component)

```JSX

import React from 'react';

class Layout extends React.Component {

 render() {
 
        return (

            <div className={classes.Wrapper}>
                <div className={classes.WrapperItem}> <ExchangeCurrency valueData= 1234.58$  /></div>
            </div>
        )

    }

}
```

> Here, *valueData* is the custom property(prop) set up on the custom **ExchangeCurrency** component.

> **ExchangeCurrency component:** (Child component)

```JSX
import React from 'react';

const exchangeCurrency = (props) => {
 
return (

	<div className={classes.ExchangeCurrencyContainer}>
	  <div className={classes.ExchangeCurrencyItem1}>{props.valueData}</div>  
	</div>

	);
}
```
*ExchangeCurrency* component receives the props argument. 

*{props.valueData}* then dynamically outputs the *valueData* property of the props object, which is available since we have set the *valueData* property for **ExchangeCurrency** component inside the parent component called **Layout component**.

Note: 
 To access the ***valueData*** property inside the *Class Component*, we need to declare it in the following way.
 
>  **{this.props.valueData}**

#### defaultProps

The **defaultProps** is a *method* which we can use to store as much information as we want and can be accessed from anywhere inside of a particular class.

Every piece of information we add inside the *defaultProps*, that will be added as the prop of that class. 

Example 1:

```JSX

import React from 'react'; 
import ReactDOM from 'react-dom'; 

// Component 
class DefaultPropsTest extends React.Component{ 
	render(){ 
		return( 
				<div> 
					{/* using default prop - title */} 
					<h1>This is {this.props.title}'s Website!</h1> 
				</div> 
			); 
	} 
} 

// Creating default props for 
// DefaultPropsTest Component 
DefaultPropsTest.defaultProps = { 
	title: "NextGen Banking"
} 

ReactDOM.render( 
	<DefaultPropsTest />, 
	document.getElementById("root") 
); 

```

Example 2:

> We can also pass *arrays* as props, instead of passing single elements. 

```JSX

import React from 'react'; 
import ReactDOM from 'react-dom'; 

// Component 
class DefaultPropsTest extends React.Component{ 
	render(){ 
		return( 
				<div> 
					{/* accessing array prop directly */} 
					<h1>The names of students are: {this.props.names}</h1> 
				</div> 
			); 
	} 
} 

// Passing an array as prop 
DefaultPropsTest.defaultProps = { 
	names: ['Fujitsu 1', 'Fujitsu 2', 'Fujitsu 3'] 
} 

ReactDOM.render( 
	<DefaultPropsTest />, 
	document.getElementById("root") 
); 

```

#### PropTypes

In the above examples, we have seen how to pass information from one component to another component through **props**. But, we have not verified the ***type*** of property value, we are passing.

**prop-types** are used to document the intended types of properties passed to components. 

React will *check props passed* to the components against those definitions, and warn in development if they don’t match.

So, *propTypes* is ***Runtime type checking*** for React props and similar objects.

> Installation

```
npm install --save prop-types
```

> Import

```
import PropTypes from 'prop-types'; // ES6
```

```JSX

import PropTypes from 'prop-types'; 
import React from 'react'; 
import ReactDOM from 'react-dom'; 

// Component 
class PropTypesTest extends React.Component{ 
	render(){ 
		return( 
				<div> 
					{/* printing all props */} 
					<h1> 
						{this.props.arrayProp} 
						<br /> 

						{this.props.stringProp} 
						<br /> 

						{this.props.numberProp} 
						<br /> 

						{this.props.boolProp} 
						<br /> 
					</h1> 
				</div> 
			); 
	} 
} 

// validating prop types 
PropTypesTest.propTypes = { 
	arrayProp: PropTypes.array, 
	stringProp: PropTypes.string, 
	numberProp: PropTypes.number, 
	boolProp: PropTypes.bool, 
} 

// creating default props 
PropTypesTest.defaultProps = { 
	arrayProp: ['Fujitsu 1', 'Fujitsu 2', 'Fujitsu 3'], 
	stringProp: "NextGen Banking", 
	numberProp: "10", 
	boolProp: true, 
} 

ReactDOM.render( 
	<PropTypesTest />, 
	document.getElementById("root") 
); 
```

#### Composition(*Children* property)

React has a powerful composition model to reuse code between components.

Few components use the special ***children*** prop to pass children elements directly into their output

```JSX

function Person(props) {
  return (
    <div>
      {props.children}
    </div>
  );
}

function WelcomeDialog() {
  return (
    <Person>
      <h1 className="Dialog-title">
        Welcome
      </h1>
      <p className="Dialog-message">
        Thank you for visiting our spacecraft!
      </p>
    </Person>
  );
}

ReactDOM.render(
  <WelcomeDialog />,
  document.getElementById('root')
);

```

#### State

**State** of a React Component Class can be defined as an object of a set of observable properties that control the behavior of the component. 

In other words, *State* of a component is an object that holds some information that may change over the lifetime of the component. 

*state* can change the data in your application based on user interaction and it is mutable. Changes to *state* also trigger an UI update.

Only class based components( i.e., the class which extends *React.Component*) can define and use *state*.

We can access *state* via ***this.state*** in our class JSX code( i.e., in render() method).

Whenever *state* changes, the component will re-render and reflect the new state.


```JSX
class Layout extends React.Component {

     state = {
            purchasePrice: '',
        }

    componentDidMount() {
        axios({
            method: 'get',
            url: 'http://localhost:8080/purchaseprice',
        })
            .then(response => {
                this.setState({ purchasePrice: response.data });              
            })
            .catch(error => {
                console.log(error);
                if(error.response === undefined){
                    alert(error);
                }
                else if(error.response) {
                    console.log(error.response.data);
                        alert(error.response.data.error + '\n' + 'Status code is ' + error.response.data.status)
                }              
            })
    }

    render() {
        const purchasePrice = this.state.purchasePrice;
        return (

            <div className={classes.Wrapper}>
                <div className={classes.WrapperItem}> <ExchangeCurrency valueData={purchasePrice}/></div>
            </div>
        )
    }
}

export default Layout;

```

**state** should never be updated explicitly as below.

> this.state.purchasePrice = "new-value";

Instead, React provides its own method called **setState()**.

**setState()** method takes a single parameter and expects an object which should contain the set of values to be updated. 

Once the update is done, the method implicitly calls the **render()** method to reload the page. 

Hence the correct method of updating the value of a state is as below.

> this.setState({ purchasePrice: response.data });

#### Props v/s State


| Props                                                          | State                                        |
|----------------------------------------------------------------|----------------------------------------------|
| Props are immutable i.e.. Once set the props cannot be changed | State is mutable                             |
| Props can be used in Functional or class components            | State can only be used in class components   |
| Props are set by Parent component                              | State is generally updated by event handlers |

### Component Lifecycle

React Component Lifecycle has various methods which are invoked at different phases of the lifecycle of a component.

Lifecycle methods has provided flexibility to the user to perform operations before or after the component rendered or mounted.

React Component Lifecycle methods has been split into 4 different phases:

- 1. Initialization
- 2. Mounting
- 3. Updating
- 4. Unmounting

##### 1. Initialization

The initialization phase is where we define defaults and initial values for this.props and this.state.

The component is setting up the initial state in the constructor, which can be changed later by using thesetState method

The defaultProps is defined as a property of Component to define all the default value of props, which can be overridden with new prop values.

##### 1. Mounting

Mounting is the process that occurs when a component is being inserted into the DOM.

This phase has two methods that we can hook up with  

- ***componentWillMount()***
- ***componentDidMount()***

**componentWillMount()**

The componentWillMount() is the first method to be called in this phase.

It will be invoked once and immediately before the initial rendering occurs, hence before React inserts the component into the DOM.

**render()**

*render* mounts the component onto the browser.

**componentDidMount()**

componentDidMount() is the hook method which is executed after the component was mounted on the dom.

This method is executed once in a lifecycle of a component and after the first render.

> We have invoked the ***API*** calls in this method to access the DOM and to modify the state object 

```JSX

import React from 'react';
import axios from 'axios';

class Layout extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            purchasePrice: '',
            sellPrice: ''
        }
    }
    componentDidMount() {
        axios({
            method: 'get',
            url: 'http://localhost:8080/purchaseprice',
        })
            .then(response => {
                this.setState({ purchasePrice: response.data });              
            })
            .catch(error => {
                console.log(error);
                if(error.response === undefined){
                    alert(error);
                }
                else if(error.response) {
                    console.log(error.response.data);
                        alert(error.response.data.error + '\n' + 'Status code is ' + error.response.data.status)
                }                   
    }
    render() {
        const purchasePrice = this.state.purchasePrice;
        return (
            <div >
                <div className={classes.WrapperItem}> <ExchangeCurrency valueData={purchasePrice} /></div>
            </div>
        )
    }
}

export default Layout;


```

##### 3. Updating

There are other methods that will allow us to execute code relative to when a component’s state or properties get updated.

1. When receiving new props from the parent, the following methods are executed.

![***Component Updating Methods on receiving new props*** folder structure!](/assets/images/philly-magic-gardens.jpg "Component Updating Methods")

2. When the state changes via this.setState(), the following methods are executed.

![***Component Updating Methods on state change*** folder structure!](/assets/images/philly-magic-gardens.jpg "Component Updating Methods")

During this phase a React component is already inserted into the DOM. Thus these methods are not called for the first render().

- ***componentWillReceiveProps()***

This method will be invoked when a component is receiving new props. Sometimes state depends on the props, hence whenever props changes, the state should also be synced. This is the method where it should be done.


- ***shouldComponentUpdate()*** tells the React that when the component receives new props or state is being updated, should React re-render or it can skip rendering?

This method returns a boolean value, and accordingly the component would be re-rendered or skipped. By default, this method returns ***true***.

> We can use ***shouldComponentUpdate()*** method if performance is a bottleneck . Especially with dozens or hundreds of components where the re-render is particularly expensive. 


- ***componentWillUpdate()*** is executed only after the ***shouldComponentUpdate**** returns *true* and immediately before rendering, when new props or state are being received.

- ***render()*** And then the component gets rendered.

- ***componentDidUpdate()*** is executed when the new updated component has been updated in the DOM. This method is used to re trigger the third party libraries used to make sure these libraries also update and reload themselves.



##### 4. Unmounting

In this phase, the component is not needed and the component will get unmounted from the DOM.

The methods called in this phase is:

**componentWillUnmount()**

This method is the last method in the lifecycle. This is executed just before the component gets removed from the DOM.

In this method, we do all the cleanups related to the component.

### Illustration of Component Lifecycle:

![***Component Lifecycle Phases*** folder structure!](/assets/images/philly-magic-gardens.jpg "Component Lifecycle Phases")


### Event Handling

Event handlers are used to determine what action has to be taken when an event has fired. This could be a mouse click or a change in a text input.

Handling events with *React elements* is very similar to handling events on DOM elements.

Syntax of Event handlers in React:

- React events are named using camelCase, rather than lowercase.
- With JSX you pass a function as the event handler, rather than a string.

React events are primarily targeted at altering the *state* information based on the events triggered.

```JSX

class CurrencyChart extends React.Component {

    constructor(props) {
    super(props);
 
    var now = new Date();
    this.state = {
      currentTime: now.toString()
    };
  }
 
  refreshCurrentTime() {
    var now = new Date();
    this.setState({ currentTime: now.toString() });
  }
  
  render() {
    return (
      <div>
        <h4>Current Time:</h4>
        <p>{this.state.currentTime}</p>
        <button onClick={() => this.refreshCurrentTime()}>
          Refresh Current Time
        </button>
      </div>
    );
  }

}


```

In the example above, the **onClick** attribute is our event handler and it is added to the target element in order to specify the function to be executed when that element is clicked.

The **onClick** attribute is set to the **refreshCurrentTime** function which displays the current time.

React supports different types of events such as **Mouse events**, **Form events**, **UI events** etc.

[React Supported Events](https://reactjs.org/docs/events.html)   

### Lists

#### React Lists:
In  Javascript, if you want to create a new array from an available array by converting each element of the original array to create the corresponding element of the new array, you can use map() method.  
please see the example, you have an array of integer numbers, such as [1, 2, 5], and you want to create another array by multiplying each element of the initial array by 10. 

```JSX
var arr1 = [1, 2, 5];
 
console.log(arr1); // --> [1, 2, 5]
 
var arr2 = arr1.map( e  => e * 10 );
 
console.log(arr2); // --> [10, 20, 50]
```

In  JSX, you also may do the same, from an array of objects, create a new array containing tags: 

```JSX
var array1 = [        
  { empId: 1, fullName: "Trump", gender: "Male" },        
  { empId: 2, fullName: "Ivanka", gender: "Female" },        
  { empId: 3, fullName: "Kushner", gender: "Male" }        
];
 
var array2 = array1.map (
    e =>
    <Emloyee fullName={e.fullName} gender={e.gender} />  
);
```

### React Keys

***Keys*** help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity:

```JSX

const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li key={number.toString()}>
    {number}
  </li>
);

```

> A ***Key*** can be * String* or an *Id* from the data.

```JSX

const todoItems = todos.map((todo) =>
  <li key={todo.id}>
    {todo.text}
  </li>
);

```

#### Extracting Components with Keys

If we want to extract a ListItem component, we should keep the key on the <ListItem /> elements in the array rather than on the <li> element in the ListItem itself.

```JSX

function ListItem(props) {
  // Correct! There is no need to specify the key here:
  return <li>{props.value}</li>;
}

function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    // Correct! Key should be specified inside the array.
    <ListItem key={number.toString()}
              value={number} />

  );
  return (
    <ul>
      {listItems}
    </ul>
  );
}

const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList numbers={numbers} />,
  document.getElementById('root')
);

```

### React conditional rendering methods:

1. **if else**

IF is the most basic approach of all and probably the one you will mostly see, but it is restricted to the total block of the component. You use an IF with your condition and return the element to be rendered

```JSX
function List({ list }) {
  if (!list) {
    return null;
  }

  return (
    <div>
      {list.map(item => <ListItem item={item} />)}
    </div>
  );
}

```

2. **Ternary operator**

You can make your if-else statement more concise by using a ternary operation.
Syntax:	condition ? expr1 : expr2

```JSX
function Item({ item, mode }) {
  const isEditMode = mode === 'EDIT';

  return (
    <div>
      { isEditMode
        ? <ItemEdit item={item} />
        : <ItemView item={item} />
      }
    </div>
  );
}
```

3. **logical &&**

In React you can make use of that behaviour. If the condition is true, the expression after the logical && operator will be the output. If the condition is false, React ignores and skips the expression.

```JSX
function LoadingIndicator({ isLoading }) {
  return (
    <div>
      { isLoading && <p>Loading...</p> }
    </div>
  );
}
```

4. **switch case**

Now there might be cases where you have multiple conditional renderings. For instance, the conditional rendering could apply based on different states. Let’s imagine a notification component that can render an error, warning or info component based on the input state. You can use a switch case operator to handle the conditional rendering of these multiple states.

```JSX
function Notification({ text, state }) {
  switch(state) {
    case 'info':
      return <Info text={text} />;
    case 'warning':
      return <Warning text={text} />;
    case 'error':
      return <Error text={text} />;
    default:
      return null;
  }
```

### Web Connectivity 

There are many libraries available for connecting the React application to the backend server through AJAX calls

Backend server will provide the Rest API endpoints for accessing the resources or for creating the resources.

In our React app, we have made a rest call to fetch the JSON data from the server through ***Axios***, a third party Javascript library.

***Axios*** is a *Promise based HTTP client* for the browser and node.js.

The interesting features of the *Axios* are

- It supports the *Promise* API

- Make *http* requests from node.js

- Callback props for onSuccess, onError, and onLoading etc.

***componentDidMount()*** is the component lifecycle method where we have populated data with AJAX calls.

This is so we can use ***setState*** to update the component when the data is retrieved.


> Installation of *Axios*

```
npm install axios --save
```
> Import the *Axios* library in to the component 

```
import axios from 'axios';
```


```JSX


import React from 'react';

import axios from 'axios';

class Layout extends React.Component {

     state = {
            purchasePrice: '',
        }

    componentDidMount() {
        axios({
            method: 'get',
            url: 'http://localhost:8080/purchaseprice',
        })
            .then(response => {
                this.setState({ purchasePrice: response.data });              
            })
            .catch(error => {
                console.log(error);
                if(error.response === undefined){
                    alert(error);
                }
                else if(error.response) {
                    console.log(error.response.data);
                        alert(error.response.data.error + '\n' + 'Status code is ' + error.response.data.status)
                }              
            })
    }

    render() {
        const purchasePrice = this.state.purchasePrice;
        return (

            <div className={classes.Wrapper}>
                <div className={classes.WrapperItem}> <ExchangeCurrency valueData={purchasePrice}/></div>
            </div>
        )
    }
}

export default Layout;

```

### Routing

React router(V4) is a routing library built on top of the react which is used to create the routing in react apps.

> Installation

React Router has been broken into three packages 

- react-router

> ***react-router*** package provides the core routing components and functions for React Router applications

- react-router-dom

- react-router-native 

***react-router-dom*** and ***react-router-native*** are environment specific components and they exports all the core features of the ***react-router*** package.

***react-router-dom*** is a web browser specific component. So, we have installed this package and developed routing to create a single page application ***Bitcoin***.
 
```
npm install --save react-router-dom
```

#### Router

**<BrowserRouter>**

We have wrapped our ***\<App>*** component in ***<BrowserRouter>*** component to handle the dynamic requests and respond to any URI produced from server.

```
import { BrowserRouter } from 'react-router-dom'
import React, { Component } from 'react';
class App extends Component {
  render() {
    return (

      <BrowserRouter>
		  <div className="App">
		  </div>
      </BrowserRouter>
    );
  }
}
export default App;
```

#### Routes

The **<Route>** component is the main building block of React Router.

This component is used to render the content of a calling component based on the location's pathname via ***<Route>*** element.

A ***<Route>*** expects a ***path*** prop, which is a string that describes the pathname that the route matches.


In our application, we have created routes for each component and configured them in the following way.

> **App.js**

```JSX


import {BrowserRouter, Route} from 'react-router-dom'
import React, { Component } from 'react'

class App extends Component {
  render() {
    return (

      <BrowserRouter>
      <div className="App">   
		<Route path="/"  exact  component={DashBoard}/>
       {<Route  exact path="/layout" component={Layout}/>}		
      </div>

      </BrowserRouter>
    );
  }
}
export default App;

```
> **DashBoard.js** component


```JSX


import React from 'react';
import { withRouter } from "react-router-dom";
class DashBoard extends React.Component {
  
    navigateLayout = () =>{
        this.props.history.push('/layout')
    }
    render() {
        const { value } = this.state;
        return (
   <div>	
	<div onClick={this.navigateLayout}> <a>BTC/JPY<br /><br /></a> <a >20,000</a></div>
   </div>               
        );
    }
}
export default withRouter(DashBoard);

```


### Charts

#### React Stockcharts

**React Stockcharts** were built with React JS and d3.

**React Stockcharts** provides a flexible API to create charts that represent ***time series data***. We can

- add custom chart components
- add custom indicators
- access the svg elements and styling with CSS(when using svg)
- Get fast performance to pan and zoom actions, when using the hybrid mode.

### Installation

```
npm install  --save react-stockcharts
```

### LineChart

> Custom Line chart

> Following are the imports required for creating a *Line Chart* through React Stock charts


```

import { format } from "d3-format";
import { timeFormat } from "d3-time-format";

import { ChartCanvas, Chart } from "react-stockcharts";
import { LineSeries, ScatterSeries, CircleMarker } from "react-stockcharts/lib/series";
import { XAxis, YAxis } from "react-stockcharts/lib/axes";
import { discontinuousTimeScaleProvider } from "react-stockcharts/lib/scale";
import { OHLCTooltip } from "react-stockcharts/lib/tooltip";
import { fitWidth } from "react-stockcharts/lib/helper";
import { last } from "react-stockcharts/lib/utils";
import { HoverTooltip } from "react-stockcharts/lib/tooltip";

```

**X Axis** uses a time scale. A time scale converts a date/time domain to a range, this is used as the xScale, the xDomain is calculated from the input data and the xExtents prop, and the range is calculated as width - margin.left - margin.right.

**Y Axis** uses a linear scale. A Linear scale converts a domain say 10 - 45 to a range say 0 to 300 pixels. Like the name represents the data in between is interpolated linear.

**xAccessor** is self explanatory

**xScale** knowledge of d3 scales will certainly help. This is a function which *converts* a domain say 2011-01-01 to 2013-01-02 to a range say 0 to 500 *pixels*. 

This scale can now interpolate an input date to a value in pixels. d3.scaleTime() is a linear time scale.

*xExtents* is the start and end points to show on initial render. This is an optional property.

**seriesName** this does not add value to this simple chart, you will see its use explained better later in the zoom and pan section

```
<XAxis axisAt="bottom" orient="bottom" {...xGrid}/>
```
*axisAt* takes on possible values as top, middle, bottom for advanced cases, you can also pass in a number indicating the pixel position where the axis has to be drawn.

*orient* takes on possible values as top, bottom, this orients the axis ticks on the top/bottom

```
<YAxis axisAt="left" orient="left"  ticks={3}  {...yGrid} stroke="#000000"/>
Similar to XAxis except left/right instead of top/bottom
```

**LineSeries** is the component responsible for producing *LineChart*.

```
<LineSeries yAccessor={d => d.assets} strokeDasharray="Solid"
stroke={strokeColor} />
```

**yAccessor** displays the *assets* data values on the *Y-Axis*.


**HoverTooltip** is a component used to display the data content, when the mouse is hovered on the particular point.

```
<HoverTooltip
                    tooltipContent={tooltipContent()}
                    fontSize={15}
                />
```

```
function tooltipContent() {
    return ({ currentItem, xAccessor }) => {
        return {
            x: [dateFormat(xAccessor(currentItem))],
            y: [
                {
                    label: "assets",
                    value: currentItem.assets && numberFormat(currentItem.assets)
                }

            ]

        };
    };
}
```

**Zoom and Pan**

*mousemove*, *pan* and *zoom* are enabled by default. To disable them we can use *mouseMoveEvent*, *panEvent* and *zoomEvent* props.

### Candlestick chart

```JSX
import { CandlestickSeries } from "react-stockcharts/lib/series";
class CandleLib extends React.Component {

	
	render() {
		let { type, data: initialData, ratio, timeFormat } = this.props;		
		
		const margin = { left: 50, right: 10, top: 10, bottom: 20 };
		const width = .95 * window.innerWidth;
		const height = .7 * window.innerHeight;
		const gridHeight = height - margin.top - margin.bottom;
		const gridWidth = width - margin.left - margin.right;
		const xScaleProvider = discontinuousTimeScaleProvider.inputDateAccessor(
			d => new Date(d.date)
		);

		const yGrid = { innerTickSize: -1 * gridWidth, tickStrokeOpacity: 0.1 };
		const xGrid = { innerTickSize: -1 * gridHeight, tickStrokeOpacity: 0.1 };
		
		const { data, xScale, xAccessor, displayXAccessor }	 = xScaleProvider(initialData);
		const start = xAccessor(last(data));
		const end = xAccessor(data[Math.max(0,data.length-150)]);
		const xExtents = [ start, end ];
		const candlesAppearance = {
			fill: d=>{
				return d.close>d.open?"#2ca02c" : "#d62728"
			},
			stroke: d=>{
				return d.close>d.open?"#2ca02c" : "#d62728"
			},
			opacity: 1,
			widthRatio:0.3,
		};
		
		return (
			<ChartCanvas height={height}
					width={width}
					ratio={ratio}
					margin={margin}
					type={type}
					seriesName="MSFT"
					data={data}
					xScale={xScale}
					xAccessor={xAccessor}
					displayXAccessor = {displayXAccessor}
					xExtents={xExtents}
					>

				<Chart id={1} yExtents={[d => [d.high, d.low],
				]}
				padding={{ top: 10, bottom: 20 }}>
					<XAxis axisAt="bottom" orient="bottom" {...xGrid}/>
					<YAxis axisAt="left" orient="left" ticks={5} {...yGrid}/>
					<CandlestickSeries{...candlesAppearance}/>

						
					<HoverTooltip
						tooltipContent={tooltipContent(timeFormat)}
						fontSize={15}
					/>
				</Chart>
			</ChartCanvas>
		);
	}
}

```
**xScale** is replaced with **xScaleProvider**.

**discontinuousTimeScaleProvider** is a function which takes some pre calculated values and the data array to return a scale that removes the discontinuity and to show a linear scale.

```
xScaleProvider={discontinuousTimeScaleProvider}
```

<Chart id={1} yExtents={d => [d.high, d.low]}>

**yExtents** can accept a function which returns a number / an object / an array of numbers. The min and max value of these are used to calculate the y domain.

<XAxis axisAt="bottom" orient="bottom" {...xGrid}/>
<YAxis axisAt="left" orient="left" {...yGrid}/>

**<CandlestickSeries />** is responsible for producing candlestick charts.


**Customizing Candles**

We can change the looks of the candles by adding this to the top of your file:

const candlesAppearance = {
  wickStroke: "#000000",
  fill: function fill(d) {
    return d.close > d.open ? "rgba(196, 205, 211, 0.8)" : "rgba(22, 22, 22, 0.8)";
  },
  stroke: "#000000",
  candleStrokeWidth: 1,
  widthRatio: 0.8,
  opacity: 1,
}
``

Then, make sure to render the CandlestickSeries component as such:

```
<CandlestickSeries {…candlesAppearance} />
```