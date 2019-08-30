# redux-intercept [![npm version](https://badge.fury.io/js/%40jeemyeong%2Fredux-intercept.svg)](https://badge.fury.io/js/%40jeemyeong%2Fredux-intercept)

`redux-intercept` is a Redux middleware for user to control specific actions

### Features

- Written in TypeScript.

## Installation

```sh
$ npm i @jeemyeong/redux-intercept
```

## Configuration

```js
import { applyMiddleware, compose, createStore } from 'redux';
import reduxIntercept from '@jeemyeong/redux-intercept';

import reducer from './store/reducer';

const interceptOption = {
  filter: (action) => {
    return !action.type.match(PERMIT_REGEX)
  }
}


// Create the Redux store.
const store = createStore(
  reducer,
  applyMiddleware(reduxIntercept(interceptOption))
);
```

You should pass options to the `reduxIntercept` function.

#### Available options

```typescript
interface Options {
  filter: (action: Action) => boolean | Promise<boolean>;
  rejectedCallback?: (action: Action) => void;
}
```
