---
layout: post
title:      "React Redux Portfolio Project"
date:       2020-07-03 02:13:01 +0000
permalink:  react_redux_portfolio_project
---

[https://github.com/shaqqour/list](https://github.com/shaqqour/list)

## To-Do, Doing, Done Lists-Part 2:
To-Do, Doing, Done is a is a continuing work for a project that was built on Ruby-Rails and plain JavaScript without the use of React and Redux. It is basically a rebuild for the entire frontend application.

I know there are many to-do list applications such as [Trello](https://trello.com/ ) exist alreay, but the simplicity of my application what makes it uniqe. Some users might be overwelmed when they act with applications that are highly customized and have many boards. So I built something a very user friendly to-do list application where all users are comfortable of using.

Users can create a new list and star a list by giving it a name. Also, they can mark a list by "star" it to view it separatly in the Starred tab. A search tab is provided if a user want to seach for a sepecific list.

A list has many tasks/items that are orgenizied within three stages, to-do, doing and done. when a user first add a task to a list, it will be added to the to-do-stage. then it can be moved to the doing and later to the done.

There are two views available for each list. a consalidated view and expanded view. They are triggered by clicking on a Expand/Consalidate button. When a user click on this button it will move all the tasks from doing and done boxes to the to-do box. Clicking again will do the oppsiit.


This application is devided into two parts, a backend and a frontend. I used Ruby on Rails for the backend and REACT-REDUX (since it is for sure the best) for the frontend.

## Rails as backend:
In this application rails is responsable of rendering APIs to the frontend. I used rails --api flag to build a backend that only renders apis which means having a rails application that doesn't have any views. the api is used later as a data provider to the the frontend.

There are few ways to render api's from Rails controller. I made use of the gem 'fast_jsonapi' that would create a Serializer class for each model you have in your application. You can pass an object from a model to this Serializer and will an api of that object will be returned. You can read more about it [here](https://learn.co/tracks/online-software-engineering-structured/front-end-web-programming/rails-as-an-api/using-the-fast-json-api-gem)

## REACT-REDUX as frontend:
This is the fun part of building this application. This application can be built using plain JS, but there is a big advantage of choosing to build it with REACT and REDUX. By using react, the application is very well orgenized when it comes to the separation of concern. As well as, using react will help the app to become more user friendly since the user doesn't like to wait on loading. React has an amazing feature that will act like it is an instance response for every user action. React application are very easy to maintain and the code is reuable in different part of the app.

An example of that is having a container where you can map your states and use them and pass them down to the children components. The same thing goes for dispatching actions.

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

In the code above which was taking from the `ListContainer.js` In this container all you need to do to access the `lists` now is `this.props.lists` which it also useful to the other components that is rendered in this container.

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
