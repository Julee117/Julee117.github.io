---
layout: post
title:      "React Redux Project"
date:       2018-03-02 03:31:01 +0000
permalink:  react_redux_project
---


My project was built using a Rails API back-end and React Redux front-end. It allows user to add a post, which includes a title, image, and content. The user can also leave a comment and like a post. 

I had a bit of difficulty understanding the flow of using Redux with React. I looked through different resources to get a better understanding. It also helped to look at diagrams.


![Async Redux Flow](http://www.thegreatcodeadventure.com/content/images/2016/09/async-redux-flow.png)


In Redux, there is only a single store, which is a JavaScript object that manages the application’s state. State can be modified through actions, which sends data to the store. Action creators are functions that create actions. It just returns an action.

Here is my code to fetch all the posts.

```
/*Action Creator*/
const setPosts = posts => {
  return {
    type: 'GET_POSTS',
    posts
  }
}

/*Async Action*/
export const getPosts = () => {
  return dispatch => {
    return fetch(`${API_URL}/posts`)
      .then(response => response.json())
      .then(posts => dispatch(setPosts(posts)))
      .catch(error => console.log(error));
  }
}
```

Reducers take in actions and output a new state, which is saved in the store. Note that we should never mutate the state. The reducer contains a switch statement. 

```
export default (state = [], action) => {
  switch(action.type) {
    case 'GET_POSTS':
      return action.posts;
	default:
      return state;
  }
}
```

The new state is available to any component subscribed to the store via `connect` function provided by Redux. 

Components can be divided into two categories: Presentational and Container. Presentational components are concerned with how things look. Container components are concerned with how things work and are often stateful. They provide data and behavior to presentational components and to other container components. It will be alerted when a change occurs to the state by the reducer. Then, it would re-render with the changes. 

I’m happy that I was able to get over the hump and have a working app. There is more that I can do with this app like adding user authentication and when a user creates a post or a comment, it would show who created it. I want to build more apps to become more familiar with using React Redux. 

It’s been a long journey getting to where I am now and as I’m writing this blog, I realize I’m nearing the conclusion of this curriculum. It’s bittersweet in the sense that I’m proud of what I’ve accomplished, I enjoyed the course but yet I know that I myself have to pursue even more to become adept in coding. 





