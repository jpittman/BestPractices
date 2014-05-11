
This is going to be a little long. I've linked specific steps to Apple's documentation to provide you with more details.

'''Note''': When this doc is rendered as html, it's best to read it (and use the links) via Safari.  Silly Apple Docs. 

### Prerequisites

So let's start with the pre-requisites.  Some of this may seem obvious, but it's just helps to get this stuff cleared up before you actually sit down with the client.

So before you meet up with them, have the client do the following:

 - Sign up for an individual developer account with [Apple][4].  They can change that to a company account later if necessary.  From signup to enabled developer account can take about an hour.

 - Download [Xcode][3] through the App Store on their mac.  Best way to stay up to date and they won't have to worry about beta installs (which won't allow you to ship an app into itunes connect anyways).

 - Have them do a little bit of homework and [read][12] about the information and assets they'll need to have on hand when they submit to the store.  If you've not read this over before, it's a good time to do so.  There are a lot of details that need to be included when [creating][11] an iTunes Connect record.  Some things are required and can only be set at record creation time.

When you finally sit down with them, make sure that their xcode loads without issue and make sure they can open the project on their system.

### Xcode Developer Configuration

The first thing we'll have them do is configure the general settings of xcode to work with their developer account.

With Xcode open on their mac, have them:

 - Add their [developer account][5].

 - [Request][5] their distribution signing identity for their developer account.

### Provisioning Portal

Now we'll have them log into the [developer portal][4] and create the actual app specific information.  

In the developer portal:

 - [Add a new App ID][9] to their account. Make sure they select all of the services they need enabled for their app when it's in the store.

 - [Add a distribution provisioning profile][6] for the store for the new app id they just created.

### Itunes Connect

In order to ship to the store for review, they'll also need to [create their app record][11] in iTunes Connect.  Make sure they have all of the relevant info before completing this step.

When this is all done, the app record in iTunes Connect should have a status of "Waiting for Upload".  This is important to both validating the App build you're submitting and to the actual submission of the build to the App Store.

### App Project Configuration

Once they've created the distribution profile and set the app up in iTunes Connect, they'll need to set a couple of app project specific things in Xcode before they can attempt to build.

Back in Xcode:

 - Set the [bundle id][10] for the app in the profile setting.

 - [Refresh][8] their provisioning profiles.

 - Set the [signing identity][7] for the project.

At this point, you should be able to run a build and see if they've got everything configured correctly.  Fix any issues you run into and then try again until you get a successful build.

### Submission

Once you've got all of the kinks worked out in the build setup, it's time to archive the app and submit it to iTunes Connect.

In Xcode:

 - [Create][14] an App Archive using the build target Archive.

 - [Validate][15] the Archive via the Xcode Organizer.

 - [Submit][16] the Archive using the Xcode Organizer.

Once you've successfully submitted, you're done.

### Notes

Couple of things to be aware of.

#### Exporting Developer Profiles

Whether you do the distribution build on your machine or your client's, you can [export][2] the developer profile for shipping distribution builds.  This exported profile will contain all the things someone would need to ship another build (provisioning profile, cert and private keys).  It's usually a good idea for them to do this and have a copy someplace safe (cloud storage or usb key).  Without it, it'll be difficult for them to ship another build of the app should they lose the profile on their machine.

#### App Status and Changes

You probably also want to review the [details][13] surrounding the different states of an app's status and what can be changed inside of iTunes Connect.

[1]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW2 "Request Signing Identities"

[2]: https://developer.apple.com/library/ios/recipes/xcode_help-accounts_preferences/articles/export_signing_assets.html "Exporting Your Signing Identities and Provisioning Profiles"

[3]: https://itunes.apple.com/us/app/xcode/id497799835?mt=12 "Xcode on the App Store"

[4]: http://developer.apple.com "Apple Development Portal"

[5]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW2 "Adding Your Apple ID Account in Xcode"

[6]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW8 "Adding Your Apple ID Account in Xcode"

[7]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW45 "Choosing a Signing Identity for Apps"

[8]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW26 "Refreshing Provisioning Profiles in Xcode"

[9]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW991 "Registering App IDs"

[10]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW16 "Setting the Bundle ID"

[11]: https://developer.apple.com/library/ios/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/CreatingiTunesConnectRecord.html#//apple_ref/doc/uid/TP40011225-CH13-SW1 "Creating an iTunes Connect Record for an App"

[12]: https://developer.apple.com/library/ios/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/FirstSteps.html#//apple_ref/doc/uid/TP40011225-CH19-SW1 "Identifying Your App in iTunes Connect"

[13]: https://developer.apple.com/library/ios/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/ChangingAppStatus.html#//apple_ref/doc/uid/TP40011225-CH30-SW1 "Viewing and Changing Your App’s Status and Availability"

[14]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW26 "Creating an Archive"

[15]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW2 "Running iTunes Connect Validation Tests"

[16]: https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW27 "Submitting Your iOS App"
