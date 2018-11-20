DoubleDutch Extension Simulator
===============================

## Updating to React Native 0.57.5

The following steps were taken to create this project.
NodeJS v11.2 was used.

1. `react-native init extensionsimulator`
1. Update iOS Info.plist with strings from [DoubleDutch iOS strings](https://ddgit.me/Flock/flock4-iOS/blob/master/Flock/Base.lproj/InfoPlist.strings)
   1. NSCameraUsageDescription
   1. NSPhotoLibraryUsageDescription
   1. NSPhotoLibraryAddUsageDescription: `This allows us to add the photos you take to your camera roll.`
1. Install [react-native-camera](https://www.npmjs.com/package/react-native-camera)
   1. Follow setup steps for this module.
   1. `yarn add react-native-camera`
   1. `react-native link react-native-camera`
   1. Pin version in `package.json` (remove ^, e.g. `"react-native-camera": "1.4.3"`)
1. Install [react-native-fetch-blob](https://www.npmjs.com/package/react-native-fetch-blob)
   1. `yarn add react-native-fetch-blob`
   1. `RNFB_ANDROID_PERMISSIONS=true react-native link react-native-fetch-blob`
   1. Pin version in `package.json`

```javascript
const nativeModules = ['react-native-camera@0.10.0', 'react-native-fetch-blob@0.10.8', 'react-native-video@2.0.0', 'react-native-youtube@1.0.1']
```