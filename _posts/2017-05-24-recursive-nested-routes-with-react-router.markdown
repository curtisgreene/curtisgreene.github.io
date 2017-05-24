---
layout: post
title:  "Recursive Nested Routes with React Router"
date:   2017-05-24 08:16:01 -0600
categories: javascript react router reactjs
---

React Router provides a tremendous amount of power to the already supercharged Reactjs library. With React you can recursively create nested child components. Using a component to create another instance of itself can get confusing easily, but with intelligent route design it becomes much easier.

![master of none](https://media.giphy.com/media/LQEJf2akHAddm/giphy.gif?response_id=59259007d2b11a0bbd9ba92b "Really")

 React Router helps us do just that. With it's functionality, specifically the ```match``` object, we have the ability to write recursive routes for nested child components.

Let's first look at what tools we will be using:
```javascript
import React from 'react'
import {
  BrowserRouter as Router,
  Route,
  Link
} from 'react-router-dom'
```
And here is some data for us to think about:
```javascript
const PEOPLE = [
  { id: 0, name: 'Dev', friends: [ 1, 2, 3, 4 ] },
  { id: 1, name: 'Arnold', friends: [ 0, 2, 4 ] },
  { id: 2, name: 'Denise', friends: [ 0, 1, 3 ], },
  { id: 3, name: 'Brian', friends: [ 1, 2, 4 ] },
  { id: 4, name: 'Francesca', friends: [ 0, 1 ] }
]
```

Now lets start building some components:
```javascript
const MasterOfFun = () => (
  <Router>
    <Person match={ params: { id: 0 }, url: '' }/>
  </Router>
)
```

Here we see the mysterious ```match ``` appearing as a prop being passed to the Person component. Let's now check out that component to see how its being used:

```javascript
const find = (id) => PEOPLE.find(p => p.id == id)

const Person = ({ match }) => {
  const person = find(match.params.id)

  return (
    <div>
      <h3>{person.name}’s Friends</h3>
      <ul>
        {person.friends.map(id => (
          <li key={id}>
            <Link to={`${match.url}/${id}`}>{find(id).name}</Link>
          </li>
        ))}
      </ul>
      <Route path={`${match.url}/:id`} component={Person}/>
    </div>
  )
}
```


```match``` has a ```url``` prop, which is also paramount to this exercise, which is a matched portion of the URL.



By using ```match``` we are sending updated and current URL information to each of our people. The part of this that is recursive is the ```Route``` at the end of the ```Person``` component. A Person is creating more people inside of it. This miracle of life could be dangerous if it creates an infinite loop, but luckily we have some conditional logic to help us.


That route is awaiting a path that is the current match's URL plus a new id. Once it has that, it renders a new instance of the Person component within the component it sits. Here we are creating nested components


And as we watch the path update, we are seeing our routes being written recursively.



![recursive routes](https://media.giphy.com/media/3oKIPA6dGYwBihfWPC/giphy.gif "Watch those routes go!")
