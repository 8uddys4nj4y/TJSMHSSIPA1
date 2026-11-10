# TJS MHSS (Matric school) for iPhone - build on a Mac

The iPhone project in this folder is ready (bundle id `in.tjs.mhss`, name "TJS MHSS", version 4.0.2 / build 40002, minimum iOS 15).
An iPhone app can only be compiled and signed on a Mac with Xcode, so these steps are done once on a Mac.

## You need
- A Mac with Xcode 16 or newer (free from the Mac App Store) and Node.js 20+.
- An Apple Developer account (US$99 a year) to install on iPhones other than your own test phone, and for TestFlight / the App Store. A free Apple ID can run the app on your own iPhone for 7 days at a time.

## Steps
1. Copy `TJS-MHSS-iPhone-4.0.2.zip` to the Mac and unzip it. It holds the `ios` folder (the Matric app is already built into it), `package.json`, `package-lock.json` and `capacitor.config.json`.
2. In Terminal, inside the unzipped folder, install the three plugins the iPhone project uses (this takes a minute):
   ```
   npm install --ignore-scripts
   ```
   (Only if you change the web app: copy the full project instead, then `npm run ios:sync` builds the Matric web app again, copies it into `ios/App/App/public` and puts the version into Xcode.)
3. Open `ios/App/App.xcodeproj` in Xcode (double-click). Xcode downloads the Swift packages by itself (no CocoaPods).
4. Click the blue **App** project in the left list > **Signing & Capabilities** > tick *Automatically manage signing* and choose your **Team**. If Xcode says the bundle id is taken, change `in.tjs.mhss` to your own, e.g. `com.yourname.tjsmhss`.
5. Plug in the iPhone (trust the computer, and on the phone turn on Settings > Privacy & Security > Developer Mode), choose it at the top of Xcode and press **Run** (the play button).
6. For TestFlight / the App Store: choose **Any iOS Device (arm64)**, then **Product > Archive**, then **Distribute App** in the window that opens.

## Updating later
After any change to the web app, run `npm run ios:sync` again on the Mac, then Run / Archive in Xcode. Raise the version in `package.json` first (the sync copies it into Xcode). The iPhone app does not update itself like the Android and Windows apps; new versions arrive through TestFlight or the App Store.

## Notes
- The login, bills, fee collection and reports are the same screens as the Matric Android app. Printing is hidden on phones, as on Android.
- The app icon is the Matric icon enlarged to 1024 px. Replace `ios/App/App/Assets.xcassets/AppIcon.appiconset/AppIcon-512@2x.png` with a 1024 x 1024 PNG (no transparency) for a sharper icon.
- The camera is not used by this app, so no camera permission text is needed.
