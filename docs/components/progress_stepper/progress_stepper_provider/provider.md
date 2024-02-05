---
sidebar_position: 1
title: Guides
description: Progress Stepper Usage Guides
---

# ProgressStepperProvider

Progress stepper provider is a Context Provider that holds all of the styles and states of ProgressStepper.

This makes it possible to declare styles in one place and have it applied in every screen progress stepper is used.

## Single Page

### Usage

Declare `ProgressStepperProvider` in root level to use `ProgressStepper` and access `useProgressStepperContext` hooks

`App.js`

```js
import { ProgressStepperProvider } from "react-native-reanimated-progress-steps";
import ProgressStepperExample from "./ProgressStepperExample";

export default function App() {
  return (
    <ProgressStepperProvider>
      <ProgressStepperExample />
    </ProgressStepperProvider>
  );
}
```

`ProgressStepperExample.js`

```js
import {
  ProgressStepper,
  useProgressStepperContext,
} from "react-native-reanimated-progress-steps";

const ProgressStepperExample = () => {
  const { goToNext, goToPrevious } = useProgressStepperContext();

  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button title="Previous" onPress={goToPrevious} />
      <Button title="Next" onPress={goToNext} />
    </View>
  );
};

export default ProgressStepperExample;
```

### Default Styles

<p>
<img src="/img/progress_stepper.gif" width="250"/>
</p>

### `extended` mode and `width` set to full screen

```js
<ProgressStepperProvider width={Dimensions.get('window').width} extended>
```

<p>
<img src="/img/progress_stepper_extended.gif" width="250"/>
</p>

### Round progress steps with `stepStyle` and `innerLabelStyle`

In the default diamond shapes, the inner label styles are rotated to -45 deg to match the style. So to override, simply use `stepStyle` and `innerLabelStyle` together.

```js
<ProgressStepperProvider
  width={Dimensions.get('window').width}
  extended
  stepStyle={{
    height: 30,
    width: 30,
    borderRadius: 15,
    justifyContent: 'center',
    alignItems: 'center',
  }}
  innerLabelStyle={{
    color: 'white',
    fontWeight: 'bold',
  }}
  trackActiveColor="green"
  activeColor="green"
>

```

<p>
<img src="/img/progress_stepper_round.gif" width="250"/>
</p>

### `renderInnerStep` to render any valid component as steps

In the default diamond shapes, the inner step styles are rotated to match the style. So to override, simply use `stepStyle` and `renderInnerStep` together.

```js
<ProgressStepperProvider
        width={Dimensions.get('window').width}
        extended
        renderInnerStep={() => {
          return <Image source={require('./checkbox.png')} />;
        }}
        stepStyle={{
          width: 30,
          height: 30,
          borderRadius: 15,
          justifyContent: 'center',
          alignItems: 'center',
          backgroundColor: '#E44949',
        }}
        activeColor="#E44949"
        trackActiveColor="#E44949"
        trackHeight={2}
      >
```

<p>
<img src="/img/progress_stepper_custom.gif" width="250"/>
</p>

## Multi Page

### Setup

Let's assume we have a simple stack navigator in our app with `Home`, `Cart` and `Checkout` Screens.

Each screen has a button that navigates to the next screen.
Our goal is to animate the ProgressStepper steps automatically as we navigate to or away between these pages.

**First**, let's wrap our Stack Navigator with `ProgressStepperProvider` so that we can use `ProgressStepper` in each screen.

`App.js`

```js
import React from 'react';
import { View, StyleSheet, Button } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import {
  createNativeStackNavigator
} from '@react-navigation/native-stack';

import {
  ProgressStepperProvider,
  ProgressStepper
} from 'react-native-reanimated-progress-steps';


function HomeScreen({ navigation }) {

  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button onPress={() => navigation.navigate('Cart')} title="Go To cart" />
    </View>
  );
}

function CartScreen({ navigation }) {

  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button
        onPress={() => navigation.navigate('Checkout')}
        title="Go To checkout"
      />
    </View>
  );
}

function CheckoutScreen({ navigation }) {
  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button onPress={() => navigation.navigate('Home')} title="Go To Home" />
    </View>
  );
}


const Stack = createNativeStackNavigator<RootStackParamList>();

function App() {
  return (
    <NavigationContainer>
      <ProgressStepperProvider>
        <Stack.Navigator>
          <Stack.Screen name="Home" component={HomeScreen} />
          <Stack.Screen name="Cart" component={CartScreen} />
          <Stack.Screen name="Checkout" component={CheckoutScreen} />
        </Stack.Navigator>
      </ProgressStepperProvider>
    </NavigationContainer>
  );
}

export default App;

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    gap: 16,
  },
});


```

Now you may notice that we can navigate between these pages and our `ProgressStepper` component shows up but the steps do not change!

In order for the steps to change automatically, let's write a hook that tells `ProgressStepper` to change steps whenever a new screen is in focus.

`useFocusedPosition.js`

```js
import React, { useEffect } from "react";
import { useProgressStepperContext } from "react-native-reanimated-progress-steps";
import { useIsFocused } from "@react-navigation/native";

export default function useFocusedPosition(position) {
  const isFocused = useIsFocused();
  const { setCurrentPosition } = useProgressStepperContext();
  useEffect(() => {
    if (isFocused) {
      setCurrentPosition(position);
    }
  }, [isFocused, setCurrentPosition, position]);
}
```

Note that, this hook takes a position as a number, and sets the current step position to that number whenever that screen is in focus.

Now, all that we need to do is call this hook with our desired position on each screen.

For example, Home screen should represent Step 1 so we will call `useFocusedPosition(1)` inside `HomeScreen`

```js
function HomeScreen({ navigation }) {
  useFocusedPosition(1);
  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button onPress={() => navigation.navigate("Cart")} title="Go To cart" />
    </View>
  );
}
```

Similarly, for other screens we will call this hook with their respective step numbers.

```js
function CartScreen({ navigation }) {
  useFocusedPosition(2);
  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button
        onPress={() => navigation.navigate("Checkout")}
        title="Go To checkout"
      />
    </View>
  );
}

function CheckoutScreen({ navigation }) {
  useFocusedPosition(3);
  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button onPress={() => navigation.navigate("Home")} title="Go To Home" />
    </View>
  );
}
```

### Summary

**In summary,** to go from a simple single page setup, where we could change the steps manually or via button clicks, to an automatically changing multi page stepper, we had to do the following -

- Declare a custom hook to change the position dynamically
- Call the hook with appropriate position on each screen

### Boilerplate

To create this same setup. Create `App.js` and `useFocusedPostion.js` with the following code to get started quickly.

`App.js`

```js
import React from 'react';
import { View, StyleSheet, Button } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import {
  createNativeStackNavigator
} from '@react-navigation/native-stack';

import {
  ProgressStepperProvider,
  ProgressStepper
} from 'react-native-reanimated-progress-steps';
import useFocusedPosition from './useFocusedPosition';

function HomeScreen({ navigation }) {
  useFocusedPosition(1);
  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button onPress={() => navigation.navigate("Cart")} title="Go To cart" />
    </View>
  );
}

function CartScreen({ navigation }) {
  useFocusedPosition(2);
  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button
        onPress={() => navigation.navigate("Checkout")}
        title="Go To checkout"
      />
    </View>
  );
}

function CheckoutScreen({ navigation }) {
  useFocusedPosition(3);
  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button onPress={() => navigation.navigate("Home")} title="Go To Home" />
    </View>
  );
}

const Stack = createNativeStackNavigator<RootStackParamList>();

function App() {
  return (
    <NavigationContainer>
      <ProgressStepperProvider>
        <Stack.Navigator>
          <Stack.Screen name="Home" component={HomeScreen} />
          <Stack.Screen name="Cart" component={CartScreen} />
          <Stack.Screen name="Checkout" component={CheckoutScreen} />
        </Stack.Navigator>
      </ProgressStepperProvider>
    </NavigationContainer>
  );
}

export default App;

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    gap: 16,
  },
});

```

`useFocusedPosition.js`

```js
import React, { useEffect } from "react";
import { useProgressStepperContext } from "react-native-reanimated-progress-steps";
import { useIsFocused } from "@react-navigation/native";

export default function useFocusedPosition(position) {
  const isFocused = useIsFocused();
  const { setCurrentPosition } = useProgressStepperContext();
  useEffect(() => {
    if (isFocused) {
      setCurrentPosition(position);
    }
  }, [isFocused, setCurrentPosition, position]);
}
```

This should produce the following behavior

<p>
<img src="/img/multi_page.gif" width="250"/>
</p>
