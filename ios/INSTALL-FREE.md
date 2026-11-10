# TJS MHSS (Matric) on your iPhone - free, no Mac, no paid account

Two parts: (A) get the `.ipa` file (the iPhone version of an APK) from a free cloud Mac, (B) install it on your phone with a free tool.

## A. Get the .ipa (about 15 minutes, once; repeat only when the app changes)
1. Make a free GitHub account (github.com) and create a NEW repository. Choose **Private** (private repos get 2,000 free minutes a month; one build takes about 10 Mac minutes x10 = 100 minutes).
2. Put the contents of `TJS-MHSS-iPhone-4.0.2.zip` into the repository. Easiest on Windows with Git installed, in the unzipped folder:
   ```
   git init
   git add -A
   git commit -m "iPhone app"
   git branch -M main
   git remote add origin https://github.com/<your-name>/<repo>.git
   git push -u origin main
   ```
   (The zip includes the hidden folder `.github/workflows` that holds the build recipe. Do not drag-and-drop in the browser: it skips hidden folders.)
3. In the repository open the **Actions** tab > **iPhone app (.ipa for sideloading)** > **Run workflow**.
4. When it turns green (about 10 minutes), open the run and download the artifact **TJS-MHSS-iPhone-ipa** (a zip with `TJS-MHSS-4.0.2-unsigned.ipa` inside). Unzip it.
   If the run fails, open it and send me the red step's text.

## B. Install on the iPhone (free Apple ID)
Use **Sideloadly** (sideloadly.io, free, Windows) - or AltStore (altstore.io), same idea.
1. On the PC install iTunes and iCloud from apple.com (the web versions, not the Microsoft Store ones), then Sideloadly.
2. Plug the iPhone in with the cable, tap Trust on the phone.
3. Drag `TJS-MHSS-4.0.2-unsigned.ipa` into Sideloadly, type your Apple ID (a spare free Apple ID is a good idea), press **Start**.
4. On the phone: Settings > General > VPN & Device Management > your Apple ID > **Trust**. On iOS 16 and newer also turn on Settings > Privacy & Security > **Developer Mode** and restart.
5. Open **TJS MHSS** from the Home Screen.

## What a free Apple ID allows (Apple's rule, not ours)
- The app stops opening after **7 days**. Open Sideloadly again (or leave AltStore's AltServer running on the PC on the same Wi-Fi, which renews it by itself) and press Start once more; your data and sign-in stay.
- Maximum 3 sideloaded apps at a time per Apple ID.
- If your phone is jailbroken or on iOS 14.0 - 17.0 you can instead install the same .ipa with **TrollStore**, which keeps it permanently with no weekly renewal.

## Updating
Raise the version, run the workflow again, install the new .ipa the same way (it replaces the old one and keeps your data).
