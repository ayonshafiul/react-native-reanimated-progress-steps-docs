---
sidebar_position: 1
title: useProgressStepperContext
description: Hook for controling Progress Stepper States
---

Hook for controling Progress Stepper States

| Property                                  | Type                                           | Description                                                          |
| ----------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------------- |
| [currentPosition](#currentposition)       | number                                         | The current position of the active step within the progress stepper. |
| [setCurrentPosition](#setcurrentposition) | `React.Dispatch<React.SetStateAction<number>>` | A function to update the current position of the active step.        |
| [goToNext](#gotonext)                     | () => void                                     | A function to move to the next step in the progress stepper.         |
| [goToPrevious](#gotoprevious)             | () => void                                     | A function to move to the previous step in the progress stepper.     |
| [steps](#steps)                           | string[]                                       | Array of step labels.                                                |
| [width](#width)                           | number                                         | Width of the progress stepper.                                       |
| [initialPosition](#initialposition)       | number                                         | Initial position of the active step.                                 |
| [animationDuration](#animationduration)   | number                                         | Duration of the animation for step transitions.                      |
| [animationDelay](#animationdelay)         | number                                         | Delay before starting the animation.                                 |
| [stepStyle](#stepstyle)                   | ViewStyle                                      | Custom styles for each step.                                         |
| [showLabels](#showlabels)                 | boolean                                        | Whether to display step labels.                                      |
| [activeColor](#activecolor)               | string                                         | Color of the active step.                                            |
| [inactiveColor](#inactivecolor)           | string                                         | Color of inactive steps.                                             |
| [trackHeight](#trackheight)               | number                                         | Height of the track.                                                 |
| [containerHeight](#containerheight)       | number                                         | Height of the container.                                             |
| [stepWidth](#stepwidth)                   | number                                         | Width of each step.                                                  |
| [trackActiveColor](#trackactivecolor)     | string                                         | Color of the active track.                                           |
| [trackInactiveColor](#trackinactivecolor) | string                                         | Color of inactive track.                                             |
| [labelOffset](#labeloffset)               | number                                         | Offset for step labels.                                              |
| [labelStyle](#labelstyle)                 | TextStyle                                      | Custom styles for step labels.                                       |
| [innerLabelStyle](#innerlabelstyle)       | TextStyle                                      | Custom styles for inner step labels (if `extended` is true).         |
| [extended](#extended)                     | boolean                                        | Indicates if the progress stepper is in extended mode.               |

### [currentPosition](#currentposition)

- `number`
- The current position of the active step within the progress stepper.

### [setCurrentPosition](#setcurrentposition)

- `React.Dispatch<React.SetStateAction<number>>`
- A function to update the current position of the active step.

### [goToNext](#gotonext)

- `() => void`
- A function to move to the next step in the progress stepper.

### [goToPrevious](#gotoprevious)

- `() => void`
- A function to move to the previous step in the progress stepper.

### [steps](#steps)

- `string[]`
- Array of step labels.

### [width](#width)

- `number`
- Width of the progress stepper.

### [initialPosition](#initialposition)

- `number`
- Initial position of the active step.

### [animationDuration](#animationduration)

- `number`
- Duration of the animation for step transitions.

### [animationDelay](#animationdelay)

- `number`
- Delay before starting the animation.

### [stepStyle](#stepstyle)

- `ViewStyle`
- Custom styles for each step.

### [showLabels](#showlabels)

- `boolean`
- Whether to display step labels.

### [activeColor](#activecolor)

- `string`
- Color of the active step.

### [inactiveColor](#inactivecolor)

- `string`
- Color of inactive steps.

### [trackHeight](#trackheight)

- `number`
- Height of the track.

### [containerHeight](#containerheight)

- `number`
- Height of the container.

### [stepWidth](#stepwidth)

- `number`
- Width of each step.

### [trackActiveColor](#trackactivecolor)

- `string`
- Color of the active track.

### [trackInactiveColor](#trackinactivecolor)

- `string`
- Color of inactive track.

### [labelOffset](#labeloffset)

- `number`
- Offset for step labels.

### [labelStyle](#labelstyle)

- `TextStyle`
- Custom styles for step labels.

### [innerLabelStyle](#innerlabelstyle)

- `TextStyle`
- Custom styles for inner step labels (if `extended` is true).

### [extended](#extended)

- `boolean`
- Indicates if the progress stepper is in extended mode.
