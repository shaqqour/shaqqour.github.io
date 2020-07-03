---
layout: post
title:      "React Redux Portfolio Project"
date:       2020-07-02 22:13:02 -0400
permalink:  react_redux_portfolio_project
---

[https://github.com/shaqqour/list](https://github.com/shaqqour/list)

## To-Do, Doing, Done Lists-Part 2:
"To-Do, Doing, Done" is a continuation of a project that was built on Ruby-Rails and plain JavaScript without the use of React and Redux. It is basically a rebuild of the entire frontend application.

While many to-do list applications such as [Trello](https://trello.com/ ) exist, the simplicity of my application is what makes it unique. Some users might be overwelmed when they interact with applications that are highly customized and have many boards. So I built a very user friendly to-do list application which all users could be comfortable using.

Users can create a new to-do list by giving it a name. Also, they can "star" the to-do list to view it separately in the Starred tab. A search tab is provided if a user want to seach for a specific list name.

A list has many tasks/items that are organizied within three progress stages: to-do, doing and done. When a user first adds a task to a list, it will be added to the to-do stage. Then it can be moved to the doing stage and later to the done stage.

There are two views available for each list: a consalidated view and an expanded view. They are triggered by clicking on a Expand/Consolidate button. When a user clicks on this button it will move all the tasks from doing and done boxes to the to-do box along with their status on the right. Clicking the Expand/Consolidate button again will do the opposite.

This application is divided into two parts: a backend and a frontend. I used Ruby on Rails for the backend and REACT-REDUX (since it is for sure the best) for the frontend.

## Rails as backend:
In this application rails is responsible for rendering APIs to the frontend. I used rails --API flag to build a backend that only renders APIs which means having a rails application that doesn't have any views. The API is used later as a data provider to the the frontend.

There are a few ways to render api's from Rails controller. I made use of the gem 'fast_jsonapi' that would create a Serializer class for each model you have in your application. You can pass an object from a model to this Serializer and  an api of that object will be returned. You can read more about it [here](https://learn.co/tracks/online-software-engineering-structured/front-end-web-programming/rails-as-an-api/using-the-fast-json-api-gem)

## REACT-REDUX as frontend:
This is the fun part of building this application. This application can be built using plain JS, but there is a big advantage of choosing to build it with REACT and REDUX. By using REACT, the application is very well orgenized when it comes to the separation of concerns. Additionally, using REACT will help the app to become more user friendly since the loading time is much faster. REACT has an amazing feature that will act like it is an instant response for every user action. 

REACT applications are very easy to maintain and the code is reuable in different parts of the app.  An example of that is having a container where you can map your states and use them and pass them down to the children components. The same thing goes for dispatching actions.

Below is a part of the code I used for this application:

```
const mapStateToProps = (state) => {
    return {
        lists: state.lists.lists
    }
}

const mapDispatchToProps = (dispatch) => {
    return {
        fetchLists: () => dispatch(fetchLists()),
        addList: listName => dispatch(addList(listName)),
        deleteList: listId => dispatch(deleteList(listId)),
        addItem: item => dispatch(addItem(item)),
        toggleStarred: (listId, starred) => dispatch(toggleStarred(listId, starred))
    }
}

export default connect(mapStateToProps, mapDispatchToProps)(ListsContainer);
```

In the code above which was taken from the `ListContainer.js` all you need to do to access the `lists` now is `this.props.lists` which is also useful to the other components that are rendered in this container.

On the other hand having REDUX to take care of our store comes very handy. All you have to do is to make use of the `Provider` from `react-redux` and `createStore` from `redux`

```
const store = createStore(rootReducer, composeEnhancer(applyMiddleware(thunk)));

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

And now the store is available in all of our application where dispatch action gets handled to update our state.
