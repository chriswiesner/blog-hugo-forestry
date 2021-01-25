+++
author = "Chris"
categories = ["development", "app"]
date = 2020-04-22T22:00:00Z
description = ""
image = "/images/dayTrace---effortless-activity-journal/1-EzHVIJ1xGMlyybLySm2Bzg.png"
slug = "daytrace---effortless-activity-journal"
title = "dayTrace — effortless activity journal"
type = "post"

+++
When I switched to my last job my commute got quite long and I was facing a lot of traffic on my route on specific times. Next to the plan of avoiding peak hours I wanted to see if there were better or worse times besides the peak.

So I wanted to track my commuting over a period of time to see those patterns. I didn’t want to create a logbook for that or having to manually start an activity tracker.Therefore I built an app that would recognize the rides automatically by utilizing activity recognition.

***

### Activity recognition

The smartphone can detect certain activities (movements) by using its motion sensor.Using this approach has several benefits:

* fully automatic (no manual action required)
* no GPS needed → privacy by design
* minimal battery impact

***

At first, I was only interested in the activity type `IN VEHICLE` . As this was needed to track my car rides.

### Prototype

For this first use case, I built a very basic app to have just a list of the rides and their durations.I was using this on a regular basis and reviewing my rides. But at some point I found myself commuting at rather fixed times and not spending too much effort to optimize further or analyze for maybe seasonal trends.The project came to a halt.

### Another use-case — the idea grows

In my new job, I had no form of time-tracking obligated. Still, I wanted to know how much time I was spending at work and so another use case was born.

By expanding the tracking principle from above I could also capture the time between the rides and generate “stays”.This was I was able to see how long I spent at a place (without knowing the location).

This addition also caused a general app overhaul and it was clear that the application should get an activity journal where you could see a timeline of your activities and their durations. Next to tracking rides in a vehicle, I added the activity recognition of `BIKING`. In this way, more people should be able to track their commutes and stays as well.

![overview](/images/dayTrace---effortless-activity-journal/1-61_tIWp4h2dCDBk4BjIBww.jpeg "daily overview — adding a manual activity — monthly calendar view")

**Why no geo-fencing?**

Although tracking your stays would be also possible with geo-fencing. It comes with some downsides:

* **setup**: you need to declare a geo-fence for your areas where you want to track stays
* **battery impact**: using geo-fences primarily relies on GPS which results in higher battery consumption
* **no tracking outside fences**: there are other use cases where the activity journal comes in handy. For example, to answer questions like “When did we leave yesterday at our friends?” or “How long did we stay in the mall?”. This would not be possible otherwise.

### What comes next?

The journal currently can answer questions around those outlined use-cases but I’m sure there’s a lot of opportunity for other insights.

By tagging activities, it would be possible to give insights about which days certain activities take to most or least time (e.g. for commuting). Also, you could set goals on those activities and track the progress with minimal effort.

I’m happy to get feedback and open to your suggestions.

Get the app on [Google Play](https://play.google.com/store/apps/details?id=at.cwiesner.daytrace).Add feedback [here](https://feedback.userreport.com/0b441bc1-7c79-4a54-88a7-725ac7fb17ed#ideas/popular)