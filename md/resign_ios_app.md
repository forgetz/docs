# How to Resign an iOS App

Let's say you receive an app (e.g. MyApp.ipa) from another developer, and you want to be able to install and run it on your devices (by using ideviceinstaller, for example).

Or your certificates and provision profiles have expired and you want to provide a new build to your clients without having to make a new build on the latest XCode or iOS SDK.

## Prepare New Signing Assets

The first step is to attain a Provisioning Profile which includes all of the devices you wish to install and run on. Ensure that the profile contains a certificate that you have installed in your Keychain Access (e.g. iPhone Developer: Some Body (XXXXXXXXXX) ). Download the profile (MyProfile.mobileprovision) so you can replace the profile embedded in the app.

Next, we are going to prepare an entitlements file to include in the signing. Open up your terminal and run the following.

    $ security cms -D -i path/to/MyProfile.mobileprovision > provision.plist

This will create an xml file describing your Provisioning Profile. Next, we want to extract the entitlements into a file.

    $ /usr/libexec/PlistBuddy -x -c 'Print :Entitlements' provision.plist > entitlements.plist



## Replace The Provisioning Profile and Resign App

If you are working with a .ipa file, first, unzip the app (if you have a .app instead, you can skip this step).

    $ unzip MyApp.ipa

Your working directory will now contain Payload/ and Payload/MyApp.app/. Next, remove the old code signature files.

    $ rm -rf Payload/MyApp.app/_CodeSignature

Replace the existing provisioning profile (i.e. embedded.mobileprovision) with your own.

    $ cp path/to/MyProfile.mobileprovision Payload/MyApp.app/embedded.mobileprovision
Now sign the app with the certificate included in your provisioning profile and the entitlements.plist that you created earlier.

    $ /usr/bin/codesign -f -s "iPhone Developer: Some Body (XXXXXXXXXX)" --entitlements entitlements.plist Payload/MyApp.app

IMPORTANT: You must also resign all frameworks included in the app. You will find these in Payload/MyApp.app/Frameworks. If the app is written in Swift or if it includes any additional frameworks these must be resigned or the app will install but not run.

    $ /usr/bin/codesign -f -s "iPhone Developer: Some Body (XXXXXXXXXX)" --entitlements entitlements.plist Payload/MyApp.app/Frameworks/*

You can now rezip the app.

    $ zip -qr MyApp-resigned.ipa Payload

Done

You may now remove the Payload directory since you have your original app (MyApp.ipa) and your resigned version (MyApp-resigned.ipa). You can now install MyApp-resigned.ipa on any device included in your provisioning profile.