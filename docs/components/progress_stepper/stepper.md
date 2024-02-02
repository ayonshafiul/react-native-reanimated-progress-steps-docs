---
sidebar_position: 1
title: ProgressStepper
description: Progress Stepper
---

# ProgressStepper

ProgressStepper in itself gets all the necessary details from `ProgressStepperProvider`. This helps to avoid passing same props to each screen.

In terms of single page usage, it doesn't provide much benefit but for multi page usage, this keeps the codebase clean.

Use this to simply indicate where the ProgressStepper should appear in a screen.

### Example Usage

```js
function HomeScreen({ navigation }) {
  return (
    <View style={styles.container}>
      <ProgressStepper />
      <Button onPress={() => navigation.navigate("Cart")} title="Go To cart" />
    </View>
  );
}
```
