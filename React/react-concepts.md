# React

React is an open source javascript library used for building user interface for web applications. It was developed and maintained by facebook. React is mainly known for its component based architecture. We can compose complex UIs from small and isolated pieces of code called “components”.
Instead of manipulating the browser's DOM directly, React creates a virtual DOM in memory, where it does all the necessary manipulating, before making the changes in the browser DOM.

> React only changes what needs to be changed!

### Advantages of react

-    Effortless Maintenance  
     Creating large applications with multiple integrations is a complex task; however, maintaining it with changing business requirements can be more complicated and expensive.modular and flexible architecture, leading to modernizing each component independently without affecting others. In addition, objects defined for a particular element can be reassigned to other components to reduce the developer’s effort.

-    Fast Rendering  
     React JS comprises the in-built functionality of virtual DOM, making the rendering faster and enhancing the overall user experience. In addition, it makes the application lightweight, leading to boost performance and productivity.

     ![Alt text](https://positiwise.com/blog/wp-content/uploads/2023/08/rending-in-react.png)

-    Search Engine Friendly  
     Many websites cannot reach the top search pages, as JavaScript pages are complex to read and rank across search engines. But, the Virtual DOM feature of ReactJS renders the application more accurate and returns the web app as a typical web page.
     Due to this, search bots are able to crawl through the React JS website and effortlessly analyze the relevance and rank the website on the search engine.

-    Mobile app developement  
     We can develop web application as well as mobile applications. React Native is a popular framework for developing mobile apps

-    Component reusability  
     React JS provides the architecture and ecosystem to build business software based on components and reuse each component multiple times.

## DOM concepts in Javascript

Dom is a way to represent the webpage in a structured hierarchial way so that it wil become easier to access and modify the document.

### Why DOM is important

Javascript can't understand the HTML document directly. So when the web page loads in the browser it creates a tree like structure composed with objects of the webpage. So js can easily interact with the DOM. JS can't understand the `<h1>` tag but it can understand the object h1 in the DOM.

### Applications of DOM

-    Dynamic web pages : DOM enables interactive and responsive web experience, Such as updating content without reloading the entire page or responding to the user acion instantly.
-    Cross browser capability : DOM provides a standard way to interact with the webpage elements.
-    Single Page Applications : Applications build with React or Angular heavily relay on the DOM for efficient rendering and updating of content within a single HTML page without reloading the entire page.

### Difference between actual DOM and virtual DOM

-    The actual DOM is a tree like structure that represent the structure of the html document.
-    When we are changing the structure or the content of the web page we are actually interacting with the actual DOM.
-    Manipulating the Actual DOM directly will leads to performance bottlenecks. It will slow down the performance. And it will creates a new DOM if the element updates.
-    The vitual DOM is a abstraction of the actual DOM and it is used by some frameworks like React to optimize the process of updating the user interface.
-    Instead of directly updating the actual DOM, these framework creates a virtual representation of the DOM in memory.
-    When any changes occures the changes will first applied to the virtual DOM . This process is much faster than modifing the real DOM.
-    After changes occured in the virtual DOM a process called reconciliation will perform. This involves comparing the current virtual DOM with the previous version to identify the differences(diffing).
-    Only the differences are then applied to the actual dom.

## Single page applications

-    In single page applications there is only single html page and whenever user interacts with the website it will dynamically rewrite the content rather than loading an entire new page from the server.
-    Navingation within the application is done by javascript.
-    Javascript will manipulate the DOM to show or hide content. without triggering a full page reload.

#### Advantages

-    Enhanced user experience due to faster transition between views.
-    Reduce the server reloads . Only the data is exchanged during interactions.

#### Disadvantages

-    Initial page load might take some time because the entire application need to loaded.
-    SEO can be a challenge. But techniques like serverside rendering can help. \

### Difference between single-page applications and multi-page applications

#### Loading approach

-    SPA loads a single page and dynamically updates the contents.
-    MPA loads a new HTML page from the server in each interactions.

#### User Experience

-    Due to fewer full page reloads SPA provides a smoother user experience .
-    MPA's initial fast page reload.

#### Server interactions

-    SPA interact with the server for fetch data and updates the contents without reloading the entire page.
-    MPA loads a new HTML page from the server in each interactions.

#### SEO

-    SPA faces challenges with SEO, But techniques like serverside rendering can help.
-    MPA is more SEO friendly, as each page has a separate url.

## CSR vs SSR

### Client side rendering

-    It is the process of rendering the web pages on the client side using javascript.
-    Server sends a initial HTML file and client then uses javascript to dynamically update the page as needed.
-    Client can update a specific part of the web page without reloading the whole page.
-    commonly used for web applications that require high amount of user interactivity

#### Advantages

-    More dynamic and interactive web applications
-    Smoother user experience
-    reduce the need of additional server requests.

#### Disadvantages

-    Slower initial load time
-    Less SEO friendly

### Server side rendering

-    The process of rendering the web pages on the server side and sending the fully rendered HTML to the client.
-    commonly used for content heavly applications.

#### Advantages

-    Faster initial page laod
-    improved SEO optimization

#### Disadvantages

-    Require more server resource and maintenance
-    slower subsequent page loads

## Concept of reusability

Reusability allows developers to create modular and maintainable code. React provides a component based architute. It allows to create small reusable ui elements, this can be combosed to create larger and more complex UI's.

### Key aspect of reusability in react

-    Components : A component is a small and reusable ui element. It can be a button or cards etc.
-    Props : It is a way to pass data from parent component to child component.
-    composition : It is a practice of combining small and simple component to create large and complex ui.
-    Higher order component : Higher order components take a components and return another component with additional functionality.
-    Custom hooks : Custom hooks are functions that encapsulate reusable logic and can be shared across components.

## Javascript XML (JSX)

-    JSX allows us to write html code inside javascript and place them into the DOM without any createElement and appendChild.
-    browsers can't understand JSX. So it converts jsx to plain JavaScript using the tool babel.

### Difference between JSX and HTML

-    html will directly interpret by browser. JSX needs to convert to javascript before it can be rendered in a browser. \
-    JSX uses className instead of class
-    Attribute name should be in camelCasing format.
-    Inline styles are specified using objects.

## Components

-    A component is a independent reusable piece of ui.
-    We can create large and complex UI's by combining these components.
-    It returns a piece of JSX code which tells what should be rendered on the browser.

Types of components

### Functional component

Functional components are javascript functions this function may or may not receive props and return react elements.

### Class component

Class components are ES6 classes that extend from React.Component. They can have local state and lifecycle methods.


### Life cycle methods Class Components

Mounting Phase

- constructor() - First the constructor method is called and inside this constructor method it calls the parent constructor method with the propers as argument.
- GetDerivedStateFromProps() - If any new props are received, this will call before rendering the component.It returns null if there is no update is neccessary.
- render() - It renders the component.
- componentDidMount() - Called after the component rendered into the DOM. We can define data fetching code logic here.

Updating Phase

- getDerivedStateFromProps() - This method is called before rendering the component to check if there is any new states. Just like in mounting phase.
- shouldComponentUpdate() - Returns a boolean value. By checking this value we can specify react should countinue with the render or not.
- render() - Renders the component based on the changes.
- getSnapshotBeforeUpdate() - It called just before changes from the render is applied to the DOM. It allow us to get the information in the DOM before it changes.The value returned from this method is passed to the the next method.
- componentDidUpdate() - It is called after the update of the component in the DOM.

Unmount Phase

- componentWillUnmount() - It will call when the component is ready to remove from the DOM.


#### Life cycle methods Functional Components

Mounting

-    constructor : When a component is initialised the constructor function will call first. The initial state and other initial vlaues will setup here. It will have an argument called props.

-    getDerivedStateFromProps : This method will call right before rendering the element in DOM. Here we can set the initial state based on the initial props. It takes state as argument and returns an object with changes to the state.
-    render : It is a required method. It will render the html to the DOM.
-    componentDidMount : It is called after the component is rendered.

Updating

-    getDerivedStateFromProps : This method will call right before rendering the element.
-    shouldComponentUpdate : This method will return a boolean value. we can specify whether react continue with the render or not.
-    render : It will render the HTML to the DOM.
-    getSnapshotBeforeUpdate : We have access to the previous props and states after the update if we are using this method we should use componentDidUpdate.
-    ComponentDidUpdate : This method will call right after the component is updated.

Unmount

-    componentWillUnmount : It will call when the component is about to remove from the DOM.

## Dynamic rendering

Dynamic rendering is the process of generating and displaying content on website or application based on user interaction.In the context of web development, this often involves updating the user interface (UI) in response to user input or changes in the underlying data.

## Hooks

-    Hooks allows functional components to have access to states and life cycle features in functional components.  
  
### Hook rules  
- Hooks can only be called inside the React functional component. 
- hooks can only called at the top level of a React component. 
- hooks cannot be conditional. 

### useState

allows functional components to have local states. it takes an initial value as argument and returns an array with two elements.current state and other is the function to update the state.

### useEffect

The useEffect hook in React is used to handle the side effects in React such as fetching data, and updating DOM. This hook runs on every render but there is also a way of using a dependency array using which we can control the effect of rendering
It has two arguments, function and dependency.

useEffect [] - Only run once when the component mounts.
useEffect [count] - When ever the count changes the useEffect will execute.
useEffect - It will execute for all the renders. 


### useRef

It can be used to store mutable values that does not cause a re-render. Like if we want to know how many times our application renders using the useRef hook.

### useNavigate 

It is used to navigate between different pages in react. It cames with the react router dom library. This is introduced as an alternative for the older method useHistory.

### Custom Hooks

We can create our own Hooks. Custom hooks are created when have to use a logic multiple time we can create a hook for that logic.

### Other Concepts

- Bundling - Combining multiple CSS and Javascript files into a single file to increase the perfomance. Webpack is used for bundling in react applications.

- Error Boundary - It is a special component that is used catch the javascript errors anywhere in its component tree, log those errors and render a fallback UI insted of crashing the component tree.

### Controlled Elements 
These elements are controlled in react using a state.The state will fully control the element, and any changes to the element is controlled by the state.

### Un-Controlled elements 
Here the element is not controlled by a state, insted DOM handles the input directly.

### Axios 
Axios is a modern library to make data fetch requsts to servers in react. It has a built in cancellation and automatic JSON parsing. It is a more advanced way than the fetch.

### Fetch 
Fetch is a light weight built in Javascript API for making HTTP requestes. It  does not have automatic json-parsing or cancellation features. For a simple request we can use Fetch.

### Reconsilation 
It is the process of updating the DOM. It updates the parts where it has changes and only those parts are updated in the DOM.


### useMemo
useMemo is a hook that takes a function and a list of dependencies as arguments, and returns a value that is the result of calling the function. The value is stored in a cache and is only re-computed if one of the dependencies has changed. useMemo caches the result of the function.


### useCallback Hook
In react if we change the state of a component it also re-renders all the other components also.

useCallback will cache the function and return that cached function if nothing is changed. If any dependancy of the function changed then only it will re-render the component.

It accepts two parameters. One is a callback function and a array of dependancys.
 
We have to use this with React.memo()

### React.Memo
In react when a parent component is re-rendered it will automatically render the child component unnecessarily. To prevent this we can use React.memo

What is the Difference between useMemo and React.memo ?

useMemo is a hook which is used to cache the result of a function. It is used for avoiding operations that don't need to be executed on every render.

But React.memo is a Higher Order component. It can be used to memoize a functional component to avoid unnecessary renders.


## Context API and useContext Hook


### Context API 
Contezt API helps us to put all our functions and variables in one place and then all of the component inside that context can access the variables and functions inside it.useContext hook is used to create context in react.

### useContext Hook
useContext Hook allows us to consume the context in a efficient way.

- React.createContext - Used to create a context.
- Provider - context provides function and variables that can be used by the child components.
- Comsumer - Using the values provided in the Context.

### useReducer 

useReducer is a hook that is used to manage states in react. It accepts two parameters a REDUCER function and a INITIAL STATE.
Use reducer returns the current value of the state and a "dispatch" that we can use to change the reducer state.

## Lazy loading

It is technique used to improve the perfomance of react application by loading only the component that is needed. It can help to reduce the initial load time.

We need to use default export for lazy load Components in order to apply lazy loading.

## Code Splitting
Code splitting in React is a technique used to optimize the performance of our application by splitting your bundle into smaller chunks. This allows you to load only the code that is necessary for the current view or functionality, reducing the initial load time.


## Erro Boundary 
It is used to catch the error comes when the lazy component is loading. For creating error boundary we can use the npm library "react-error-boundary".

