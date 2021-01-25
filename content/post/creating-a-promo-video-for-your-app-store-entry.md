+++
author = "Chris"
categories = ["ab-test", "aso"]
date = 2018-04-19T22:00:00Z
description = ""
slug = "creating-a-promo-video-for-your-app-store-entry"
title = "Creating a promo-video for your app-store entry"
type = "post"

+++
How to create a simple video that might boost your installs

In order to increase the app-store conversion of my [**Visual Timer app**](https://play.google.com/store/apps/details?id=at.cwiesner.android.visualtimer) I thought of adding a promo-video. It should be a simple showcase of the app to give the visitors a better understanding of the simple setup mechanism and other main features.

![main-screen](/images/Creating-a-promo-video-for-your-app-store-entry/1-UuzKnG3Iz3idXZydQQZFTg.png "Main-screen of the App")

Additionally I wanted to also measure the impact of this video on the conversion with an **A/B-Test** in order to proof my assumption that it actually would boost installs.

As it only should be a “proof-of-concept” and this is only a hobby-project I didn’t want to spent too much time and money on making this video.

## Recording

I started off by doing some screen-recordings of interactions within the app using Android Studio. I split it into smaller/shorter recordings which then can be combined again in a later stage. I think it was a good idea to not script a longer interaction flow which might need a few attempts of recording. Before recording I enabled the [Demo-Mode](https://android.googlesource.com/platform/frameworks/base/+/master/packages/SystemUI/docs/demo_mode.md) of the Android system to “clean” the Status-Bar of the device in order to have a streamlined video.

Having the recordings in place (which took me just a couple of minutes) I was looking for an easy option to add captions to the videos.

## iMovie — not really helpful

One of my first ideas was to use iMovie as I was working on my Macbook and its comes for free with MacOS.

I wanted to display the video clips inside a device frame and have the captions/description next to it.

![video](/images/Creating-a-promo-video-for-your-app-store-entry/1-ts4fgvf2cxqenwpB0ZZQAw.png "Screenshot of the final video")

In order to use the recorded clips (.webm) I had to convert them into some format that could then be used in iMovie. After conversion I had troubles to place the video clip inside a device frame image. You need to use “picture-in-picture” mode in order to achieve that but are **limited in the placement** of the background (device frame). Next I tried to add text descriptions to it and discovered another restriction of iMovie. It is only capable of placing **texts on pre-defined positions**. This was then the point where I started again looking for alternative tools to create the video.

### Other tools

While doing some research on the web I discovered a few services which either offer the creation of a video (like an agency) or tools which where too expensive for this use case.

## Keynote — somehow a Swiss Army Knife

Having seen Powerpoint being (mis-)used as “design” tool I got the Idea of using Keynote to produce the video clip.The export function let’s you create a video clip of your presentation which comes in handy in that case.

Using Keynote you’re able to place media-content freely on your slide and by leveraging the basic animation options you can even have transitions for text and fading between scenes.

For each scene/feature I created a separate slide, added some fading animations in between and adapted the transition to happen automatically after a certain amount of time.

![keynote](/images/Creating-a-promo-video-for-your-app-store-entry/1-soFNrI2yTXkvE2BQbnhbRg.png "By using Keynote you eliminate also the learning curve for a new video editing tool")

After spending one hour I could already export two videos (different languages) and add them to my store entry.This is the result:

<iframe src="https://www.youtube.com/embed/l3CefYVWcdE?feature=oembed" width="700" height="393" frameborder="0" scrolling="no"></iframe>

## Conclusion

I found it pretty cool to “reuse” an existing tool without much effort to achieve my goal. Of course with Keynote you are limited in terms of post-processing and if you need to have a more complex/longer video the timing can get out of handy quickly. But for a promo-video which anyhow should only be a few seconds that perfectly worked for me.

Having the video ready I started an A/B-Test for my Play-Store entry.

![last](/images/Creating-a-promo-video-for-your-app-store-entry/1-cS1rxfiVbL1fpivoCflkqQ.png)

The result currently does not really proof my assumption that it will boost the installs, but I guess there are some improvements possible by adjusting the preview-image of the video and also maybe shorten the video a bit.

Glad to hear any suggestions or tips on that matter!