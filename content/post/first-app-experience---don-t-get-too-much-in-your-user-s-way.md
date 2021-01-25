+++
author = "Chris"
categories = ["app", "usability"]
date = 2020-03-18T08:01:00Z
description = ""
slug = "first-app-experience---don-t-get-too-much-in-your-user-s-way"
title = "First app experience — don’t get too much in your user’s way"
type = "post"

+++
In fall last year  I joined a startup as user experience engineer which is operating in the competitive market of micromobility —  more specifcally — its building an e-scooter sharing-system.Next to wrapping my head around the business area and the challenges the whole market is facing, it was my responsibility to improve the app experience.The startup is quite new on the market and operating based on  the “Lean Startup” Methodology by Eric Ries. That being said, the company is still in it’s infancy and the app covers currently only the fundamentals of booking and returning a scooter.

The main goal for now is to find areas of the app that can be improved with little to moderate effort in order to open the funnel for future customers.

During the last weeks/months there were some experiments run on how much data users are willing to provide in order to get free rides. This is resulting in a sign-up process which is producing some usability issues.

**Goal**

Therefore the goal is to design/implement a new sign-up flow that reduces the cognitive load of this standard task in order to leave more focus on experience of actual porpuse of the app.

## Current user flow

At first I mapped out the current user flow to outline how many steps need to be performed until the user lands on the mainscreen.

![flow](/images/First-app-experience---don-t-get-too-much-in-your-user-s-way/1-RSJ7STH9z25GrCWXmcweOQ.png "Current user flow for registration")

First questions popped in my head around the data that we retrieve and also verify in this process:-  Which data we **need** to have?-  What would be nice to have?

As a next step I had a look at other apps in the vertical to see how they approached this cirtical part of the funnel.

![competitors](/images/First-app-experience---don-t-get-too-much-in-your-user-s-way/1-dQV8Sdzi9UP4_XA-aujr_A.png "Screenflow from competitor apps")

I made a matrix to condense the information shown here

![registration-analysis](/images/First-app-experience---don-t-get-too-much-in-your-user-s-way/1-xHHuqWj2qrJKAHKwZ_6yyw.png "Overview registration analysis")

That beiing outlined it was now time to answer the questions above. What data do we actually need from the user?After some discussions with the team we agreed on reducing it to the bare minimum that is necessary.

### What is necessary?

As a company it is necessary to be able to get in contact with our riders, e.g. if we see problems with the system or faulty rides. Additionally it is important to have a direct contact, when it comes to damaged or stolen scooters.

So we agreed on using the phone number for user login/identification.And that would be the only information we ask in order to get into the app.

![signup-flow](/images/First-app-experience---don-t-get-too-much-in-your-user-s-way/1-RuPgxC-NrBRECg9NzKcseA.png "New sign-up flow")

By adding also the capability of auto-verifying the One-time-passcode the user is down to two steps logging in. No need to remember usernames or passwords.

Here in Austria we have a mandatory registration of SIM cards since beginning of this year. Which means that in case of legal actions we are able to obtain personal information about the riders which is I guess superior to email adresses.

### One-time passcode

Using the phone number we have the ability to contact riders if we see problems with their rides. Additionally we can auto-fill the passcode removing interaction steps for the user. Also compared to email verification the SMS code mostly will land on the current phone. Some users might not have their e-mail account setup on their phone (e.g. when using not their primary mail for sign-up). This would lead to a list of steps (browsing e-mail provider, logging in,…) that is not necessary with the phone number. Of course users can enter a phone number of a different device, so they still would need to enter the code manually, but that should apply only to a minority of our users. (we will keep an eye on the auto-verify rate)

Beginning with iOS 12 there is the new [AutoFill](https://developer.apple.com/documentation/security/password_autofill) capability which allows (personal) information to be suggested for certain input types. This allows us to suggest the users phone number or get the one-time password from messages suggested for the input.

On Android there is an [SMS verification API](https://developers.google.com/identity/sms-retriever/choose-an-api) that allows you to read certain message content and that enables the capability of auto-filling the one-time password and do the verification without any user input needed.

![new-flow](/images/First-app-experience---don-t-get-too-much-in-your-user-s-way/1-vAi1WwjUa1X_u0qy-YCLUA.png "New sign-in flow")

### Whats left?

The goal was to reduce the steps for the user to get to the mainscreen of the app. With our current concept we have achieved taking that down to 1–2 interactions (depending on Platform).

We will monitor our registration rate in order to also get numbers on the impact of the new flow.