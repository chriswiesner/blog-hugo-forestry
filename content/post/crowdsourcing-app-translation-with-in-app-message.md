+++
author = "Chris"
categories = ["remote-config", "development"]
date = 2017-11-16T23:00:00Z
description = ""
slug = "crowdsourcing-app-translation-with-in-app-message"
title = "Crowdsourcing App-Translation with in-app message"
type = "post"

+++
Inspired by a mention in a book of a very simple Timer application I started building an [Android Timer App](https://play.google.com/store/apps/details?id=at.cwiesner.android.visualtimer&referrer=utm_source%3Dmedium%26utm_medium%3Dpost) on that principle. The first version was published in two Languages (English and German) which i could provide without external help.

![main-screen](/images/Crowdsourcing-App-Translation-with-in-app-message/1-rS0zwni23ZnbJCD-hyJtLQ.png "Mainscreen of the app — easy setup by just dragging to desired duration")

I was already looking for translation possibilities when I started publishing the first version but couldn’t find any free services that offer human translations. I didn’t want to spend money on it as this was just a side project and free for all users. At first I created a public translation project on [poeditor.com](https://poeditor.com/) and was hoping that random translators would join the project. Unfortunately without promoting the project nobody was joining. Next I asked a co-worker to help out with a language and soon added the third one. As there where still no other contributors I started again looking for other possibilities of acquiring voluntary translators. Luckily I found a [thread](https://forum.xda-developers.com/showthread.php?t=2069390) in the [xda-developers.com](http://xda-developers.com) board where I could acquire three additional translators.

With that I could offer my app (+ store listings) in 5 Languages which was quite good for a small hobby project. Still it lacked some major languages like Spanish, Chinese or Japanese.I got the idea to get in touch with already existing users in those areas to contribute for a “native” version of the app. As there is no registration required the only way to contact users is via Notifications or In-App messages.

## Utilizing Firebase Remote-Config

With the capabilities of Firebase Remote-Config I had the plan to add an In-App message to acquire volunteers for the missing languages.

![bottom-sheet](/images/Crowdsourcing-App-Translation-with-in-app-message/1-Z7RUsEuhfpBecBNGsft12w.png "Bottom sheet shown on second app start")

The first Idea was to define the missing locales in a remote parameter so that I can show the contribution message on devices with those specific languages. Once a contributor is found for a specific locale I simply can remove it from that list and the In-app message won’t show up for that language. This is done without touching the apps code and there’s no need to redeploy an update in the app store.

![config](/images/Crowdsourcing-App-Translation-with-in-app-message/1-lLDXfl2S5GFvAAMahxRgLQ.png "Using a Remote Config parameter to trigger the contribution Screen")

When I got to define the parameter in the Firebase console, I realized that it’s even possible to add conditions for the parameter also on a device language level. This made the attribution implementation even simpler. I just can have a flag whether to show the screen or not and alter the condition right in the console.

![condition](/images/Crowdsourcing-App-Translation-with-in-app-message/1-1VRYfiR0CUUrk4hz25gDww.png "Adding a condition to a Remote Config parameter")

With some additional Tracking in place I started the rollout. I was happy about the decent setup and looking forward to acquire new Translators in the coming days/weeks.

## Results

Within nearly two months now, around 10 new contributors joined the translation project. Two of those finished the translation work and I could already publish those translations along some other improvements.

With the basic tracking I added before we can do further analysis on funnel of contributors.

Here we can again utilise Firebase to create a funnel for those users.

![funnel](/images/Crowdsourcing-App-Translation-with-in-app-message/1-ar0MGd4jm3NGoScrd3euYg.png "Funnel view in Firebase Analytics")

The “opt-in”-sheet had a “click”-rate of 25,6%, which is quite good actually. So 80 users decided to help with the translation.

**So why did this 80 users not end up as translators?**In terms of tracking it’s hard to tell as this “opt-in”-Button is redirecting to the public Page of the translation project in the Browser where I can’t track any longer.

If we take a look at the steps the users have to perform until they end up as a contributor there are some flaws.

Currently the only way people can join a translation project on poeditor.com is to sign up on the [public page](https://poeditor.com/join/project/DAV4srMQ0q) of the project. Alltough this public page is a responsive Webpage on a mobile phone it looks like this:

![translation-project](/images/Crowdsourcing-App-Translation-with-in-app-message/1-9ukfP7QZQhHmfwl2S8H02w.png "Public page of translation project shown on a mobile Phone")

I think the first issue here is that there’s a lot of heading on this screen, which will hide the actual list of languages on smaller phones already.Next big thing is that users have to search for their language in this list. There’s no way of directly opening the Join-Page with a preselected language. Once they selected the proper language they are prompted with a sign-up form.

![sign-up](/images/Crowdsourcing-App-Translation-with-in-app-message/1-9hmSEqV-FaILYADlQ7rT2g.png "Sign-up form of translation project")

After the sign-up they need to confirm their e-mail address first before they can actively contribute.

There were also users how could manage to end up in the project (they even verified their account) but then never started the actual translation work.

## Conclusion

Overall I’m happy that I could get new translators for my project and could try new capabilities to reach out to users.With that system in place I can always “turn-on” the opt-in screen if I see that certain languages don’t get updated any longer and I would need new translation contribution for those.

Next steps would be to further investigate on how I could improve the actual sign-up process in order to ease the experience for the users who are willing to help.