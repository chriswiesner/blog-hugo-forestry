+++
author = "Chris"
categories = ["development", "app"]
date = 2018-06-01T22:00:00Z
description = ""
slug = "putting-my-app-on-a-diet--android-app-bundle-to-the-rescue-"
title = "Putting my app on a diet: Android App Bundle to the rescue."
type = "post"

+++
### _How a even simple app can benefit from the new build type._

Google introduced Android App Bundle at [IO this year](https://www.youtube.com/watch?v=bViNOUeFuiQ&index=31&list=PLOU2XLYxmsIInFRc3M44HUTQc3b_YJ4-Y). As there are already a few articles about the bundle system itself I just want to share my experience applying it to my side-project [**Visual Timer**](https://play.google.com/store/apps/details?id=at.cwiesner.android.visualtimer).

When I started building the app in 2016 I went for [realm-java](https://github.com/realm/realm-java) to easily store data. It is a [known “issue”](https://github.com/realm/realm-java/issues/3662) that realm adds up to 4 MB to your APK by adding different native libraries. This also applied to my rather minimalistic timer app which ended up with an APK size of 7.2 MB.

![Realm taking 76% of the APK size](/images/Putting-my-app-on-a-diet--Android-App-Bundle-to-the-rescue-/1-vVIVkQ_9BIDSOOGayRaEig.png "Realm taking 76% of the APK size")

Aiming to build a minimalistic, yet useful app it somehow hurts to ship a bloated APK to users. Additionally it is proven that app-size has direct impact on install-rates as shown [by Google several times](https://youtu.be/flU42CTF3MQ?t=511). This, I think, is especially crucial in my use case as nobody wants to install a simple timer app that takes up a lot of download traffic and disk space.

There is a proposed solution from Realm to minimise that “overhead” by building split-APKs (building multiple APKs each tailored to a specific hardware/resource configuration). This is rather tedious to handle when it comes to releases, therefore I stuck with the (single) universal APK.

In order to reduce the APK size a bit I applied a resource config filter on languages to only ship the supported language files and omit any unnecessary resources. This is done by a configuration setting in the app’s _build.gradle_ file:

    android {
       defaultConfig {
          ...
          resConfigs "en", "de", "fr", "ru", "vi", "pt-rBR", "it", ...
          ...
       }
    }

This reduced the APK by roughly 200kb, which isn’t much but if you put Realm aside it would be nearly 10% saving though. Definitely a low-hanging fruit for a universal APK. But this step could soon be unnecessary when using App Bundle.

## Android App Bundle to the rescue (almost)

With that it was quite good to hear that this situation can be improved by using the Android App Bundle. Building an Android App Bundle is done pretty easily without changing code inside the app.

You just need to update your Android Gradle Plugin to the latest canary version (if you build your app with Android Studio you should also upgrade that as well). Having that in place it is just a few clicks to produce the App Bundle.

After uploading the Bundle to the Play Store I was eager to see how much it could save in my case. Without further ado here’s the banner I saw:

![Size saving after uploading the App Bundle](/images/Putting-my-app-on-a-diet--Android-App-Bundle-to-the-rescue-/1-ho09h55yUSXUZxzN7_ddsw.png "Size saving after uploading the App Bundle")

I was already expecting a huge benefit but still was happy about the number. It was around 2–3 MB depending on configuration of the phone.The App Bundle system is still in Alpha state. It is not recommended to be used for production apps. But the size-savings were too tempting for me and I did a staged rollout with the App Bundle. I wasn’t expecting any bigger issues and tested with Emulator and 2 other phones.

After some time in the staged rollout I had to face an issue tough.

![Stacktrace: Missing Library for Realm](/images/Putting-my-app-on-a-diet--Android-App-Bundle-to-the-rescue-/1-76JgsHjpx_zDe6yDk_uO9g.png "Stacktrace: Missing Library for Realm")

There were only two users affected by it but keeping in mind that it was a staged rollout it still was a major issue as the app would not work at all for the affected users.

After a short research it turned out that I’m not the only one who has [issues with Realm](https://github.com/realm/realm-java/issues/5977) in that case. It’s currently not clear to me if the App Bundle system is producing this issue or the Realm library is not providing the native libs for all configurations. It could be that the app is now shipped to configurations which are not supported by Realm and would not be able to install it with a universal APK. This needs still some further investigation.

## Bottom Line

The App Bundle system is definitely a good tool to reduce app-sizes and eases the process of delivering a “tailored” app to the users.

To see that this is even (or especially) beneficial for small apps is a good learning here and should encourage many developers to adopt this new capability. I’m looking forward to use it in production once the Realm-issue is resolved.

Let me know if you have further questions!