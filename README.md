![Dashboard Items](https://raw.github.com/BatchLabs/cordova-plugin/master/readme_logo.png)

# Batch Sample Apps
These samples are minimal examples demonstrating a proper integration of the Batch SDK and implementation of Batch Unlock and Batch Push functionality.

## App

1. Clone or download the repository, which contains the SDK and the sample app

2. Go into the BatchSample folder and use standard cordova commands to run the app (ex: "cordova emu ios" or "cordova run android")

## Dashboard

### 1. Login to your [Batch.com](https://batch.com/) account or create a new one.

### 2. Add your new sample app
Add a new app on the [dashboard](https://dashboard.batch.com/app/new) using the manual option, as your sample app doesn't have an App Store or Play Store URL to autopopulate.

### 3. Retrieve the dev API key
Within your newly-created app, find the dev API key either here on step 1 of the wizard screen under `API KEY`, or in the settings menu under *API Keys*. 

Place the dev API key in your sample app's AppDelegate didFinishStartingWithOptions function, in the startWithAPIKey method call.

At this point, feel free to launch your app. If you select `Unlock`, you should see that you haven't yet redeemed any *features* or *items*.

> Note: The app starts with 10 `Lives`, as shown below.

![No Redeeemed Items](https://raw.github.com/BatchLabs/cordova-plugin/master/readme_noredeem.png)

If you are using the wizard, you can now click `Test` and should receive a confirmation of your integration if you launched the app with your API key.

### 4. Add items for Batch Unlock
The samples are configured with three static items: `No Ads`, `Pro Trial`, and `Lives`.

![Dashboard Items](https://raw.github.com/BatchLabs/cordova-plugin/master/readme_items.png)

While the names can vary in the *NAME* field, the *REFERENCE* is the case-sensitive value used in the sample code.

*No Ads* is used to demonstrate restorability. It is recommended to set this to *Always restore*.

*Pro Trial* demonstrates a time-to-live (TTL) for expiring offers. Set the option to *trial (days)* and choose a valid amount of days for the feature to be active.

*Lives* is an example of a resource, or consumable item. You can define the given quantity in the campaign.  

### 5. Create campaign
In the campaign screen of your dashboard, create a new *Unlock* campaign. You can use any of the wizard options, or choose a *Custom Offer* for manual setup. 

As long as the conditions (time, user targeting, URL scheme, capping) match when you launch the app, you will recieve whatever configuration of features and resources you specify. You will also recieve the `reward_message` custom parameter, sent as alert, to give feedback to the user about the offer redeemed.

In this example, `No Ads` is given in the offer with *restore* enabled, `Pro Trial` is given with a 9 day trial set, and 5 `Lives` are given, adding to the previously-mentioned default of 10.

![Redeemed Items](https://raw.github.com/BatchLabs/cordova-plugin/master/readme_redeem.png)

> Note: If you set a campaign targeting only new users, ensure that you're running the app for the first time on the device, otherwise it will be considered an existing user. Delete and reinstall to be considered new.

### 6. Testing Restore

To test the restore functionality, delete the app from your testing device and then reinstall it. Upon relaunch you see that your inventories have been reset to defaults. Within *Unlock*, select *Restore* and you will see a confirmation of the restore. Your inventory will now reflect any content you have enabled for restoration.
 
## Resources
* [Full Batch documentation](https://dashboard.batch.com/doc)
* [support@batch.com](support@batch.com)