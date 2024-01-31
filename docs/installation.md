---
sidebar_position: 1
---

# Installation

### Configure Reanimated

React native reanimated progress bar depends on `react-native-reanimated` library.
So make sure to first install reanimated library for your project

#### For Expo Projects

```bash
npx expo install react-native-reanimated
```

#### For Bare Projects

```bash
npm install react-native-reanimated
```

### Add reanimated's Babel Plugin

Add `react-native-reanimated/plugin` plugin to your `babel.config.js`. Make sure to add it as the last entry in the array.

```js
  module.exports = {
    presets: [
      ... // don't add it here :)
    ],
    plugins: [
      ...
      'react-native-reanimated/plugin',
    ],
  };

```

### Clear cache and restart development server

#### For Expo Projects

```bash
npx expo start -c
```

#### For Bare Projects

```bash
npm start -- --reset-cache
```

### Install the library

```bash
npm install react-native-reanimated-progress-steps
```
