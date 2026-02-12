# Learning-Vue.js

The source is based from Traversy Media's Vue.js Crash course

## Why Vue?

- Simplicity & Approachability
- Flexibility
- Performance & Size
- Component-Based Architecture
- Active community & Rich Ecosystem

## Vue Components

- Reusable, self-contained pieces of code
- Includes the logic/JS, dynamic HTML output & scoped styling
- Options API vs Composition API

![Vue Components](/Images/components.png)

Within the `<template>` this is where HTML will be rendered, and you can also include Dynamic elements within this template (Loops, Variables, Conditionals)

**2 Ways to build Vue components**

- Options API - Kind of traditional way of doing things where everything is in objects or options. More straightforward, good for smaller projects
- Composition API - Released with Vue3, more flexible and allows you to create more complex components.

## Getting Setup

- CDN - Include with script tag with the CDN url
- Vue CLI - Command line interface for setting up Vue projects. **No longer recommended**
- Create Vue - Uses Vite, which includes features like hot-reloading, out of the box TypeScript and an ecosystem of plugins.
- Nuxt.js & Gridsome - SSR & SSG frameworks that use Vue

## Lifecycle Methods

- onBeforeMount - called before mounting begins
- onMounted - called when component is mounted
- onBeforeUpdate - called when reactive data changes and before re-render
- onUpdated - called after re-render
- onBeforeUnmount - called before the Vue instance is destroyed
- onActivated - called when a kept-alive component is activated
- onDeactivated - called when a kept-alive component is deactivated
- onErrorCaptured - called when an error is captured from a child component

## Setting Up Router

Run this line to setup router of Vue

```
npm i vue-router
```

Then in the `src` folder, create another folder called `router`. Create a file `index.js`
Inside index.js insert the following line

```
import { createRouter, createWebHistory } from 'vue-router';
```

Create another folder inside `src` called `views`.
