```bash
npx react-native init <ProjectName>
```


# Basics
```bash
yarn add react-native-gesture-handler react-native-haptic-feedback react-native-localize react-native-safe-area-context react-native-safe-area-view react-native-svg react-native-device-info react-native-reanimated @react-native-clipboard/clipboard react-native-json-tree react-native-linear-gradient react-native-shadow-2
```

#### Reanimated

add to file ```babel.config.js```

```bash
  plugins: ['react-native-reanimated/plugin']
```

# DEV
```bash
yarn add googleapis yarn-upgrade-all
```



# Redux
```bash
yarn add @react-native-async-storage/async-storage react-redux redux redux-persist
```



# ADS
```bash
yarn add @sparkfabrik/react-native-idfa-aaid react-native-google-mobile-ads react-native-tracking-transparency
```

# Firebase
```bash
yarn add @react-native-firebase/app @react-native-firebase/analytics @react-native-firebase/remote-config
```


#IAP
```bash
yarn add react-native-iap
```



# Blur
add to package.json
```bash
"@react-native-community/blur": "https://github.com/dankocher/react-native-blur.git"
```


# React Native Visio Camera
If in android is black screen open file ```node_modules/react-native-cision-camera/src/useSkiaFrameProcessor.ts``` and add next code to function ```withRotatedFrame``` in line 93
```js
    switch (orientation) {
      case 'portrait':
        if (Platform.OS === "android") {
          canvas.translate( 0,frame.height / 2)
        }
        // do nothing
        break
      case 'landscape-left':
        if (Platform.OS === "ios") {
          // rotate two flips on (0,0) origin and move X + Y into view again
          canvas.translate(frame.height, frame.width)
          canvas.rotate(270, 0, 0)
        } else {

          // rotate two flips on (0,0) origin and move X + Y into view again
          canvas.translate(0, frame.width)
          canvas.rotate(270, 0, 0)
        }
        break
      case 'portrait-upside-down':
        if (Platform.OS === "ios") {
          // rotate three flips on (0,0) origin and move Y into view again
          canvas.translate(frame.width, frame.height)
          canvas.rotate(180, 0, 0)
        } else {
          // rotate three flips on (0,0) origin and move Y into view again
          canvas.translate(frame.width, frame.height * 1.5)
          canvas.rotate(180, 0, 0)
        }
        break
      case 'landscape-right':
        // rotate one flip on (0,0) origin and move X into view again
        canvas.translate(frame.height, 0)
        canvas.rotate(90, 0, 0)
        break
      default:
        throw new Error(`Invalid frame.orientation: ${frame.orientation}!`)
    }
```

and in ```node_modules/react-native-cision-camera/src/Camera.ts``` in styles in line 690

```js
  customPreviewView: {
    flex: 1,
    transform: [
      {scaleX: Platform.OS === "android" ? -1 : 1}
    ]
  },
```
