---
sidebar_position: 2
title: Quick Example
description: Example App.js for quickly getting started
---

### Example App.js

```js
import React, { useState } from "react";

import { Button, StyleSheet, View } from "react-native";

import {
  ProgressStepperProvider,
  ProgressStepper,
  useProgressStepperContext,
  ProgressStepperLive,
} from "react-native-reanimated-progress-steps";

export default function App() {
  return (
    <>
      <ProgressStepperProvider>
        <ProgressStepperLiveExample />
        <ProgressStepperExample />
      </ProgressStepperProvider>
    </>
  );
}

const ProgressStepperLiveExample = () => {
  const [current, setCurrent] = useState(0);

  return (
    <View style={styles.container}>
      <ProgressStepperLive currentStep={current} />
      <Button title="Previous" onPress={() => setCurrent((p) => p - 1)} />
      <Button title="Next" onPress={() => setCurrent((p) => p + 1)} />
    </View>
  );
};

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

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
    gap: 16,
  },
});
```

Running this code you should see a screen like the following.

<p>
<img src="/img/demo.gif" width="250"/>
</p>
