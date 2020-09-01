
<h2 align="center">
  React Native Shimmer Placeholder
</h2>
<p align="center">
  <a href="https://www.npmjs.com/package/react-native-shimmer-placeholder"><img src="https://img.shields.io/npm/v/react-native-shimmer-placeholder.svg?style=flat-square"></a>
  <a href="https://www.npmjs.com/package/react-native-shimmer-placeholder"><img src="https://img.shields.io/npm/dm/react-native-shimmer-placeholder.svg?style=flat-square"></a>
  <a href="https://packagephobia.now.sh/badge?p=react-native-shimmer-placeholder@1.0.29"><img src="https://packagephobia.now.sh/badge?p=react-native-shimmer-placeholder@1.0.29"></a>
</p>
<h5 align="center">
Placeholder for both IOS and Android
</h5>

<p align="center">`
<img src="https://github.com/tomzaku/react-native-shimmer-placeholder/blob/master/example.gif?raw=true">
</p>`
<!-- <p align="center">
<img src="https://github.com/tomzaku/react-native-shimmer-placeholder/blob/master/example2.gif?raw=true">
</p> -->

## Get Started
![install size](https://packagephobia.now.sh/badge?p=react-native-shimmer-placeholder@1.0.29)

### Installation

`npm i react-native-shimmer-placeholder --save`

or

`yarn add react-native-shimmer-placeholder`


### Usage

#### Simple
``` js
import { LinearGradient } from 'expo-linear-gradient';
import { createShimmerPlaceholder } from 'react-native-shimmer-placeholder'
const ShimmerPlaceholder = createShimmerPlaceholder(LinearGradient)

<ShimmerPlaceHolder />
<ShimmerPlaceHolder visible={isFetched}>
  <Text>
    Wow, awesome here.
  </Text>
</ShimmerPlaceHolder>

```
or
``` js
import { LinearGradient } from 'expo-linear-gradient';
...
<ShimmerPlaceHolder
  LinearGradient={LinearGradient}
/>

```

#### Connect more components

``` js
import { createShimmerPlaceholder } from 'react-native-shimmer-placeholder'

const ShimmerPlaceholder = createShimmerPlaceholder(LinearGradient)
const FacebookContent = () => {

  // Handle animation
  const avatarRef = React.createRef()
  const firstLineRef = React.createRef()
  const secondLineRef = React.createRef()
  const thirdLineRef = React.createRef()

  React.useEffect(() => {
    const facebookAnimated = Animated.stagger(400, [avatarRef.current.getAnimated(), Animated.parallel([
      firstLineRef.current.getAnimated(),
      secondLineRef.current.getAnimated(),
      thirdLineRef.current.getAnimated()
    ])])
    Animated.loop(facebookAnimated).start();
  }, [])

  return (
    <View>
      <View style={{ flexDirection: "row" }}>
        <ShimmerPlaceholder
          ref={avatarRef}
          stopAutoRun
        />
        <View style={{ justifyContent: "space-between" }}>
          <ShimmerPlaceholder
            ref={firstLineRef}
            stopAutoRun
          />
          <ShimmerPlaceholder
            ref={secondLineRef}
            stopAutoRun
          />
          <ShimmerPlaceholder
            ref={thirdLineRef}
            stopAutoRun
          />
        </View>
      </View>
    </View>
  )
}
```

More Detail see [this](https://github.com/tomzaku/react-native-shimmer-placeholder/blob/master/example/App.js)

### Props

| Prop                      | Description                                                                                            | Type     | Default                                           |
| ------------------------- | ------------------------------------------------------------------------------------------------------ | -------- | ------------------------------------------------- |
| **`visible`**             | Visible child components                                                                               | boolean  | false                                             |
| **`style`**               | Container Style                                                                                        | Style    | `{backgroundColor: '#ebebeb',overflow: 'hidden'}` |
| **`shimmerStyle`**        | Shimmer Style only                                                                                     | number[] | *[0.3, 0.5, 0.7]*                                 |
| **`location`**            | Locations of shimmer                                                                                   |          | `{backgroundColor: '#ebebeb',overflow: 'hidden'}` |
| **`width`**               | Width of row                                                                                           | number   | 200                                               |
| **`duration`**            | Duration of shimmer over a row                                                                         | number   | 300                                               |
| **`height`**              | Height of row                                                                                          | number   | 15                                                |
| **`shimmerWidthPercent`** | Percent of shimmer width                                                                               | number   | 1.0                                               |
| **`isReversed`**          | Reverse direction of animation                                                                         | boolean  | `true`                                            |
| **`stopAutoRun`**         | Stop running shimmer animation at beginning                                                            | boolean  | `false`                                           |
| **`isInteraction`**       | Defines whether or not the shimmer animation creates an interaction handle on the `InteractionManager` | boolean  | `true`                                            |
| **`shimmerColors`**       | Colors of the shimmer.                                                                                 | string[] | *['#ebebeb', '#c5c5c5', '#ebebeb']*               |

### Methods
| Method            | Description                 | Type     |
| ----------------- | --------------------------- | -------- |
| **`getAnimated`** | get Animated of Placeholder | Animated |

### Contribute

Welcome to help me build this awesome lib.

### License

[MIT](https://github.com/tomzaku/react-native-shimmer-placeholder/blob/master/LICENSE)
