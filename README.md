# Actions and Action Creators

## Overview

Think of the interactions you have with any web application. You're likely clicking buttons, hovering over items, submitting forms - these are just a few of the actions you can take to interact with the application. If you've ever tried to manage all of these actions with plain old JavaScript or jQuery, you know how hard it can be to keep track of all of those different actions. In this reading, we'll look at how Redux helps us describe these actions in a large application. 

## Objectives
1. Understand the purpose of actions in a Redux application
2. Build an action creator function
3. Use an action creator with data

## Life Before Actions

As we've seen in the past, keeping track of user interactions is hard. Figuring out when and where we're firing web requests and updating our views can get confusing very quickly. Imagine you're making a twitter clone using only vanilla JavaScript. It's really confusing.

## Time for Some Actions

In Redux, we have a simple way to describe our actions. We simply create plain old JavaScript objects with a `type` property. The type property may be something like `ADD_TODO`, `CREATE_TWEET`, or `INCREMENT_COUNT`. 

```javascript
const incrementCountAction = {type: 'INCREMENT_COUNT'}
const addTodoAction = {type: 'ADD_TODO'}
const createTweetAction = {type: 'CREATE_TWEET'}
```

Imagine that we have a `store` object who's job it is to keep track of different pieces of data for our application. We'll refer to those pieces of data as our `state`. 

```javascript
store.getState() // returns the current state
```

We can pass actions to our store using a method called dispatch. We'll then depend on our store to update the state of our application and update any views. 

```
store.dispatch({type: 'INCREMENT_COUNT'})
```

We can safely assume now that our store will know how to deal with this action and what to do with it. The point is, we've now separated out what an action is from what an action should do. This will make our applications much easier to maintain. 

## Passing Additional Data

For a simple application like a counter, our actions won't need to tell the store too much. We can let the store figure out that `INCREMENT_COUNT` action should up our count by one, and `DECREMENT_COUNT` should decrease our count by one. However, some actions will require more pieces of data. With Redux, we can pass other data along with our actions. Imagine we have an action to create a new tweet. We'd also need to pass along the content of that tweet into the store. 

```javascript
let createTweetAction = {
  type: 'CREATE_TWEET',
  tweet: {
    content: "Here's a picture of some food",
    userId: 1
  }
}
```

When we dispatch the action, our store can now update the state using the data we've attached onto our `createTweet` action.

## Action Creators

As we talked about earlier, actions are getting created all the time in our applications. It's kind of a pain to have to create these action objects each time we want to dispatch one to the store. In Redux, we typically create functions, called "Action Creators". These are just normal JavaScript functions that return normal JavaScript Objects. 

```javascript
function incrementCount(){
	return {
	 type: 'INCREMENT_COUNT'
	};
}
```

Now, we can use this action creator function to dispatch an action to the store. 

```javascript
let incrementCountAction = incrementCount();
store.dispatch( incrementCountAction ) ;
```

This is helpful - if we ever want to change what type of action we use to increment the count, this will be way easier. We can do the same thing for actions that need some data associated with them.

```javascript
function createTweet(tweet) {
  return {
    type: 'CREATE_TWEET',
    tweet: tweet
  }
}
```

Now, we just pass the tweet into our action creator function.

```javascript
let createTweetAction = createTweetAction({ content: "Here's a picture of some food", userId: 1});
store.dispatch( createTweetAction ) ;
```

Finally, you can imagine that many actions don't just affect the state of our application. We may also need to be able to do other things, like send requests to our API to update our database. Our Action Creator functions give us a great place to make these requests. 

```javascript
function createTweet(tweet) {
  // Here, we could make a post request to our API to actually save our tweet...
	
  return {
    type: 'CREATE_TWEET',
    tweet: tweet
  }
}
```

## Conclusion/So What?

By using actions and action creators, we've given ourselves a consistent way to describe the different behaviors our users can take for our application. This approach will scale really well as our applications continue to grow. 

<p class='util--hide'>View <a href='https://learn.co/lessons/react-redux-actions-and-action-creators'>Actions And Action Creators</a> on Learn.co and start learning to code for free.</p>
