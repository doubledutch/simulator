DoubleDutch Extension Simulator
===============================

## Quick Start

1. Clone this repository `git clone git@github.com:doubledutch/simulator.git`
1. `cd` into cloned project folder.
1. `npm i` to install dependencies
1. Open XCode and open `ios/extensionsimulator.xcodeproj`
1. Near the top left of the XCode window, select a simulator iPhone target, e.g. `iPhone XS`.
1. Click the RUN icon.

This will build and install the DoubleDutch simulator app to your selected iPhone simulator.
You should no longer need to build the simulator project in XCode. In the future, simply open
the DoubleDutch simulator app from the iOS Simulator device.
You will at first likely see a red error screen due to not having a React Native packager running.

To launch a packager:

1. Open a DoubleDutch extension project folder that is set up for `baseBundleVersion` `0.57.5`.
1. From the `mobile` folder, run `npm start` (which simply invokes `react-native start --port 8081`)

Refresh the extension in the simulator (`command-R`), which will attempt to reload the
bundled Javascript from the packager now listening on port 8081.

### Developing multiple extensions

If you work on multiple extensions, you can switch between them by simply stopping the
React Native packager for one extension and starting it (`npm start` from the `mobile` folder)
for another extension. Refresh the simulator (`command-R`) to load this extension.

## Internal simulator implementation notes

### Updating to React Native 0.57.5

The following steps were taken to create this project.
NodeJS v11.2 was used.

1. `react-native init extensionsimulator`
1. Update iOS Info.plist with strings from DoubleDutch iOS strings: `Base.lproj/InfoPlist.strings`
   1. NSCameraUsageDescription
   1. NSPhotoLibraryUsageDescription
   1. NSPhotoLibraryAddUsageDescription: `This allows us to add the photos you take to your camera roll.`
1. Install [react-native-camera](https://www.npmjs.com/package/react-native-camera)
   1. Follow setup steps for this module.
   1. `npm i --save react-native-camera`
   1. `react-native link react-native-camera`
   1. Pin version in `package.json` (remove ^, e.g. `"react-native-camera": "1.4.3"`)
1. Install [rn-fetch-blob](https://www.npmjs.com/package/rn-fetch-blob)
   1. `npm i --save rn-fetch-blob`
   1. `RNFB_ANDROID_PERMISSIONS=true react-native link rn-fetch-blob`
   1. Pin version in `package.json`
1. Install [react-native-video](https://www.npmjs.com/package/react-native-video)
   1. `npm i --save react-native-video`
   1. Pin version in `package.json`
1. Install [react-native-youtube](https://www.npmjs.com/package/react-native-youtube)
   1. `npm i --save react-native-youtube`
   1. `react-native link react-native-youtube`
   1. `cp ./node_modules/react-native-youtube/assets/YTPlayerView-iframe-player.html ios/extensionsimulator.xcodeproj/`
   1. Pin version in `package.json`
1. Run on iOS: `react-native run-ios`
1. Update @doubledutch/cli
   1. Versions in bundles/make/package.json
   1. Review bundles/make/base.js

### Updated from React Native 0.57.5 to 0.59.1

1. Apply diffs from https://github.com/react-native-community/rn-diff-purge/compare/version/0.57.5...version/0.59.1