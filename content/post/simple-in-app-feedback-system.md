+++
author = "Chris"
categories = ["usability"]
date = 2020-04-08T07:01:00Z
description = ""
image = "/images/Simple-In-App-Feedback-System/1-lyku9KUYpwU9kICwsfSO1g.png"
slug = "simple-in-app-feedback-system"
title = "Simple In-App Feedback System"
type = "post"

+++
As already mentioned in my last article about [First App-Experience](https://christophwiesner.at/first-app-experience-don-t-get-too-much-in-your-user-s-way/) I’m currently trying to improve certain areas in a mobile app for e-scooter sharing.

The company is still in the building phase of  (basic) functionality of the service and therefore feedback from our first users is quite important to us.

## Problem

For now the feedback channel was basically a link in the app to a web-form, where (already signed-in) users would need to enter username/name and e-mail in order to send a message.

This message was then sent to the support mail where a help desk service integration was creating support requests upon those emails. The issue here is that by using this web-form those mails do not get the users email address as sender and therefore the support request is not issued by the users email. This means a direct reply in the help desk software is not possible. So the support agent needs to reply to the user with a email client and then comment those actions in the help desk software.

![Process flow before](/images/Simple-In-App-Feedback-System/1-PWzSqv7rOeSATyFYZIzAwQ.png "Process flow before")

## Goal

Come up with a low-effort solution to improve/ease the sending of feedback for the user and also the help desk integration in order to directly communicate with the user inside the help desk.

## Process

My role for this improvement covered research, design and development.

At first I had a look for different services that are providing user feedback abilities. Most of them are quite expensive (at least for a small startup) or lacking the ability to integrate/connect to our existing service-desk.

In terms of the capabilities we again stick to the lean approach and start with the minimum feature set, which is a plain text box to report a short message. No video recording or screenshot sharing for now.

With this simple approach we do not need to rely on features of a third party and are able to quickly implement our customized solution.

### In-app feedback ability

I wanted to make it as easy as it can get to provide feedback inside the app. Therefore I decided to place the feedback-ability directly on the home-screen.

![Feedback button in bottom left corner](/images/Simple-In-App-Feedback-System/1-6eQ7sboAyJsqpqhDT7Ex6A.png "Feedback button in bottom left corner")

Once the user has tapped on the feedback button a bottom-sheet with a simple input field will appear. Ready to type the message. No input required for user information. We can leverage the user information that we have inside the app. (name, contact info, selected scooter,…)

![Feedback-flow in the app](/images/Simple-In-App-Feedback-System/1-lyku9KUYpwU9kICwsfSO1g.png "Feedback-flow in the app")

### What happens in the background?

We decided to stick with our existing help desk service so I built an integration by using the REST API of the service to create support requests.This means I can set the user data properly on the support request which in turn enables the support agent to directly interact inside the help desk service.

![New feedback flow](/images/Simple-In-App-Feedback-System/1-1vJr06EZ5AEqNQBIwGAqjA.png "New feedback flow")

## Conclusion

With this simple integration we reduce the effort for the user to report issues or send feedback. (which should increase the likelyhood of giving feedback in the first place. We do not have numbers on that yet).Secondly we are enabling the support agent to directly interact with the user inside our service desk platform. These two improvements should result in increased and transparent  “conversation”, helping us to strengthen our Build-Measure-Learn cycle.