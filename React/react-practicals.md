- React TODO App Code

Basic Imports
```js
import './App.css';
import { useState } from 'react'
import { Task } from './Components/taskComponent';

```

Body Code
```js
function App() {
  let [inputValue, setInputValue] = useState("");
  let [inputStore, setInputStore] = useState([]);

  const getValue = (event) => {
    setInputValue(event.target.value);
  }

  const addTask = () => {
    if (inputValue === "") {
      alert("Type Something");
      return;
    };

    let task = {
      taskId: inputStore.length === 0 ? 1 : inputStore.length + 1,
      taskName: inputValue,
      completed: false,
    }
    setInputStore([...inputStore, task]);
  }

  const deleteTask = (taskId) => {
    setInputStore(inputStore.filter((task) => {
      if (task.taskId === taskId) {
        return false;
      } else {
        return true;
      }
    }));
  }

  const changeStatus = (taskId) => {
    setInputStore(inputStore.map((task) => {

      if (task.taskId === taskId) {
        return { ...task, completed: true };
      } else {
        return task;
      }

    }));
  }

  return (
    <div className="App" >
      
      <div>
        <input onChange={getValue}></input>
        <button onClick={addTask}>Add Task</button>
      </div>

      <div>

        {inputStore.map((task) => {
          return <Task taskName={task.taskName} taskId={task.taskId} changeStatus={changeStatus} completed={task.completed} deleteTask={deleteTask} />
        })}

      </div>
    </div>
  );
}

export default App;
```

Item Listing Component

```js
export const Task = (props) => {

    return <div>
        <h1 style={{ color: props.completed ? "green" : "red" }}>{props.taskName}</h1>
        <button onClick={() => props.deleteTask(props.taskId)}> X </button>
        <button onClick={() => props.changeStatus(props.taskId)}>Complete</button>
    </div>

}

```

- React API Call(Usign useEffect)

Basic Exports
```js
import './App.css';
import Axios from 'axios';
import { useEffect, useState } from 'react';

```
Main Code Goes Here 
```js
function App() {
  let [currFact, setCurrFact] = useState("");

  useEffect(() => {
    Axios.get("https://excuser-three.vercel.app/v1/excuse/").then((res) => {
      const excuse = res.data[0]?.excuse || "No excuse are there";
      setCurrFact(excuse)
    });
  }, []);

  const getNewExcuse = () => {
    Axios.get("https://excuser-three.vercel.app/v1/excuse/").then((res) => {
      const excuse = res.data[0]?.excuse || "No Excuse are there";
      setCurrFact(excuse)
    })
  }

  return (
    <div className="App" >
      <div>
        <button onClick={getNewExcuse}>Generate Execuss</button>
        <p>{currFact}</p>
      </div>
    </div>
  );
  
}

export default App;

```
- Axios - It is a popular library that is used to sent API requests to the HTTP end Points in React.

```js
npm install axios
```

- React Router DOM :- It is a library that is used for impliment routing in the React applications

Installing and importing the Router DOM Properties
```js
npm install react-router-dom 
import { BrowserRouter as Router, Routes, Route, NavLink } from 'react-router-dom';
import { Home } from './Pages/Home';
import { Profile } from './Pages/Profile';
import { Contact } from './Pages/Contact';

```

Main Body Code

```js
function App() {

  return (
    <div className="App" >
      <Router>
        <div className='link_div'>
          <NavLink to={"/"}>Home</NavLink>
          <NavLink to={"profile"}>Profile</NavLink>
          <NavLink to={"contact"}>Contact</NavLink>
        </div>
        <Routes>
          <Route path='/' element={<Home />} />
          <Route path='/profile' element={<Profile />} />
          <Route path='/contact' element={<Contact />} />
          <Route path='*' element={<h1>This page is not available</h1>} />
        </Routes>
      </Router>
    </div>
  );

}

export default App
```

- Link - It works like a normal anchor tag in html.It comes with the react router DOM

- NavLink - It also same as Link but in this we can get a extra property "class =active". Because of this we can know that if the link is active or not and if it's active we can give style to it.

Both Of these properties will intercept the react request to the server and load the Componenet only from the front end.So the page will not reload only the components will change.

Example of styling the NavLink 
```js
.link_div a.active {
  background-color: red;
}

```
Components
```js
export const Contact = () => {
    return <h1>This is Contact Page</h1>
}
export const Home = () => {
    return <h1>This is home page</h1>
}
export const Profile = () => {
    return <h1>This is Profile Page</h1>
}
```


- REACT FORM  
  
  This is Componet Page Code 

  Basic Imports

  ```js
  import { useForm } from "react-hook-form";
  import * as yup from "yup"
  import { yupResolver } from "@hookform/resolvers/yup";

  ```

  Main Body Code

  ```js
  
  export const Form = () => {
    
    const schema = yup.object().shape({
        fullName: yup.string().required("Your'e name is required").max(100),
        email: yup.string().email().required(),
        age: yup.number().positive().integer().min(18).required(),
        password: yup.string().min(4).max(15).required(),
        confirmPassword: yup.string().oneOf([yup.ref("password"), null], "Passwords doesn't match").required(),
    })

    const { register, handleSubmit, formState: { errors } } = useForm({
        resolver: yupResolver(schema)
    });

    const onSubmit = (data) => {
        console.log(data);
    }

    return (
        <div className="formDiv">
            <form onSubmit={handleSubmit(onSubmit)}>
                <input type="text" placeholder="Name..." {...register("fullName")} />
                <p>{errors.fullName?.message}</p>
                <input type="email" placeholder="Email..." {...register("email")} />
                <p>{errors.email?.message}</p>
                <input type="number" placeholder="Age..." {...register("age")} />
                <p>{errors.age?.message}</p>
                <input type="password" placeholder="Password..." {...register("password")} />
                <p>{errors.password?.message}</p>
                <input type="password" placeholder="Confirm Password..." {...register("confirmPassword")} />
                <p>{errors.confirmPassword?.message}</p>
                <input type="submit" />
            </form>
        </div>
    );
  }

  ```
  npm i react-hook-form - Package which is used to manage manage form in react.
  npm i yup - This is used to validate form in react.

  ```js
  import { useForm } from "react-hook-form";
  ```
  useForm provides different form managment functions

- handleSubmit - This is a function that takes the form and process's it.
- register - register will define which inputs will include the validation.If we don't give register to input fields we will not be able to get the form data.
- yup - yup provides different functions that we can use to validate the form data.

  
```js
  import { yupResolver } from "@hookform/resolvers/yup"
```

Yup resolver is used to assign the schema(validating shape of the form)to the useForm resolver Like belove :

```js
 const { register, handleSubmit, formState: { errors } } = useForm({
        resolver: yupResolver(schema)
    });

```