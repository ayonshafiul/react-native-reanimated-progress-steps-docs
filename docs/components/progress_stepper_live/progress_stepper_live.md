---
sidebar_position: 1
title: ProgresStepperLive
description: ProgressStepperLive
---

## ProgressStepperLive

### Usage

ProgressStepperLive is a single page progress stepper component where the main emphasis is showing an ongoing sequence of events.

`App.js`

```js
import React, { useState } from "react";
import { View, StyleSheet, Button } from "react-native";

import { ProgressStepperLive } from "react-native-reanimated-progress-steps";

function App() {
  const [current, setCurrent] = useState(0);
  return (
    <View style={styles.container}>
      <ProgressStepperLive
        allSteps={["Step 1", "Step 2", "Step3"]}
        showLabels
        stepGap={10}
        trackBackgroundColor="white"
        progressColor="red"
        trackCompletedColor="green"
        currentStep={current}
        animationVariation="live"
        animationDuration={2000}
        trackHeight={8}
      />
      <Button onPress={() => setCurrent(current + 1)} title="Next" />
      <Button onPress={() => setCurrent(current - 1)} title="Prev" />
    </View>
  );
}

export default App;

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
    gap: 16,
  },
});
```

The above code produces the following

<p>
<img src="/img/progress_stepper_live.gif" width="250"/>
</p>

### Animation Presets

Currently two types of animation variations are supported. `animationVariation` could either be `live` or `scaleToFill`

#### `scaleToFill` variation with `animationDuration` set to 1000

<p>
<img src="/img/progress_stepper_live_scale.gif" width="250"/>
</p>
