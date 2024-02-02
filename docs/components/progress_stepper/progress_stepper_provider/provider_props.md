---
sidebar_position: 1
title: props
description: Progress Stepper Provider Props
---

# Props

| Name               | Optional | Type                                                         | Description                                                | Default Value                                                                                                                  |
| ------------------ | -------- | ------------------------------------------------------------ | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| children           | -        | React.ReactNode                                              | React components to be rendered as children.               | -                                                                                                                              |
| width              | ✓        | number                                                       | Width of the progress stepper.                             | `windowWidth - 100`. Assuming ` windowWidth = Dimensions.get('window').width;`                                                 |
| steps              | ✓        | string[]                                                     | Array of step labels.                                      | `['Menu', 'Cart', 'Checkout']`                                                                                                 |
| initialPosition    | ✓        | number                                                       | Initial position of the active step.                       | `0`                                                                                                                            |
| animationDuration  | ✓        | number                                                       | Duration of the animation for step transitions.            | `300`                                                                                                                          |
| animationDelay     | ✓        | number                                                       | Delay before starting the animation.                       | `700`                                                                                                                          |
| stepWidth          | ✓        | number                                                       | Width of each step.                                        | `60`                                                                                                                           |
| stepStyle          | ✓        | ViewStyle                                                    | Custom styles for each step.                               | `{ width: 30, height: 30, transform: [{ rotate: '45deg' }], borderRadius: 4, justifyContent: 'center', alignItems: 'center' }` |
| trackHeight        | ✓        | number                                                       | Height of the track.                                       | `6`                                                                                                                            |
| containerHeight    | ✓        | number                                                       | Height of the container.                                   | `60`                                                                                                                           |
| activeColor        | ✓        | string                                                       | Color of the active step.                                  | `'#FF0000'`                                                                                                                    |
| inactiveColor      | ✓        | string                                                       | Color of inactive steps.                                   | `'#DEDEDE'`                                                                                                                    |
| showLabels         | ✓        | boolean                                                      | Whether to display step labels.                            | `true`                                                                                                                         |
| trackActiveColor   | ✓        | string                                                       | Color of the active track.                                 | `activeColor`                                                                                                                  |
| trackInactiveColor | ✓        | string                                                       | Color of inactive track.                                   | `inactiveColor`                                                                                                                |
| labelOffset        | ✓        | number                                                       | Offset for step labels.                                    | `-15`                                                                                                                          |
| labelStyle         | ✓        | TextStyle                                                    | Custom styles for step labels.                             | `{ color: 'black', fontSize: 12, fontWeight: 'bold' }`                                                                         |
| innerLabelStyle    | ✓        | TextStyle                                                    | Custom styles for inner step labels (if extended is true). | `{ color: 'white', fontWeight: 'bold', transform: [{ rotate: '-45deg' }] }`                                                    |
| extended           | ✓        | boolean                                                      | Indicates if the progress stepper is in extended mode.     | `false`                                                                                                                        |
| renderInnerStep    | ✓        | ((stepLabel: string, stepNumber: number) => React.ReactNode) | Custom function to render inner step content.              | null                                                                                                                           |

### [children](#children)

React components to be rendered as children.

### [width](#width)

Width of the progress stepper. Default value: `windowWidth - 100`. Assuming ` windowWidth = Dimensions.get('window').width;`

### [steps](#steps)

Array of step labels. Default value: `['Menu', 'Cart', 'Checkout']`

### [initialPosition](#initialposition)

Initial position of the active step. Default value: `0`

### [animationDuration](#animationduration)

Duration of the animation for step transitions. Default value: `300`

### [animationDelay](#animationdelay)

Delay before starting the animation. Default value: `700`

### [stepWidth](#stepwidth)

Width of each step. Default value: `60`

### [stepStyle](#stepstyle)

Custom styles for each step. Default value: `{ width: 30, height: 30, transform: [{ rotate: '45deg' }], borderRadius: 4, justifyContent: 'center', alignItems: 'center' }`

### [trackHeight](#trackheight)

Height of the track. Default value: `6`

### [containerHeight](#containerheight)

Height of the container. Default value: `60`

### [activeColor](#activecolor)

Color of the active step. Default value: `'#FF0000'`

### [inactiveColor](#inactivecolor)

Color of inactive steps. Default value: `'#DEDEDE'`

### [showLabels](#showlabels)

Whether to display step labels. Default value: `true`

### [trackActiveColor](#trackactivecolor)

Color of the active track. Default value: `activeColor`

### [trackInactiveColor](#trackinactivecolor)

Color of inactive track. Default value: `inactiveColor`

### [labelOffset](#labeloffset)

Offset for step labels. Default value: `-15`

### [labelStyle](#labelstyle)

Custom styles for step labels. Default value: `{ color: 'black', fontSize: 12, fontWeight: 'bold' }`

### [innerLabelStyle](#innerlabelstyle)

Custom styles for inner step labels (if extended is true). Default value: `{ color: 'white', fontWeight: 'bold', transform: [{ rotate: '-45deg' }] }`

### [extended](#extended)

Indicates if the progress stepper is in extended mode. Default value: `false`

### [renderInnerStep](#renderinnerstep)

Custom function to render inner step content. Default value: `null`
