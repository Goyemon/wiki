# Release Process
How to test and release the new Goyemon apps. 

- merge feature branches into a develop branch
- test in the develop ropsten
- test in simulators
- test in real devices
- merge the develop into a master
- change the three config files for the mainnet
- test in the master mainnet
- test in simulators
- build new iOS and android version with fastlane. *update the version code in iOS and android
- download the previous version from the google play console in android and update that with the new android build
- download the previous version from the app store in iOS and update that with the new iOS build
- make sure update of the apps works
- test in real devices
- create a new release in google play console and review
- create a new release in App Store connect and submit for a review

