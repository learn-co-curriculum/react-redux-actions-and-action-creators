# Actions and Action Creators

## Overview

Think of the interactions you have with any web application. You're likely clicking buttons, hovering over items, submitting forms - these are just a few of the actions you can take to interact with the application. If you've ever tried to manage all of these actions with plain old JavaScript of jQuery, you know how hard it can be to keep track of all of those different actions. In this reading, we'll look at how the Flux architecture helps us describe these actions in a large application. 

## Objectives
1. Understand the purpose of actions in a Redux application
2. Build an action creator function
3. Use an action creator with data

## Outline

1. Describe the concept of actions in general
2. Explain that actions are Plain Old JavaScript Objects an action type
3. Setup a ToDo List Application and pass an `ADD_TODO` action to the store
4. Explain the need for an action creator in case any action needs to change
5. Mention that action creators are just Plain Old JavaScript Functions that return objects. 
6. Show how the action gets passed into dispatch
