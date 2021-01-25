+++
author = "Chris"
date = 2020-12-08T08:57:52Z
description = ""
draft = true
slug = "guiding-customers---improving-a-onboarding-experience"
title = "Guiding customers — Improving a onboarding experience"
type = "post"
+++


Recently I was spending time on improving the onboarding exprience of [autologg.com](http://www.autologg.com)

## The domain

AutoLogg is a digital logbook solution to track trips of cars. The product exists currently of a hardware box that sits in the car an reports milages to the software system which then generates trips based on the actual milage of the car. Next to the dongle there’s currently an open beta phase for Tesla owners who can connect their car which sends it’s data without relying on the box.

Customers are able to use a web-portal to sign-up and manage their boxes/tesla vehicles and manage their logbook. Next to the web solution there are apps for iOS and Android to assign trips on the go.

## The problem

The current onboarding experience is lacking guidance in order to give customers a sense of the next steps.

![client-overview](/images/Guiding-customers---Improving-a-onboarding-experience/1-8jhKCTIdiJiME4KH9ahEAw.png "Client overview")

The mobile client is basically reduced to the functionality of user login, statistics and assigning trips whereas features like user registration and setup of boxes and tesla connection is only available in the web-application. Customers who enter the funnel from the app(store) are redirected to the registration in the web. After registering an account the customers are obligated to register a box or connect a tesla. Once this setup is done the recording of a first trip is necessary in order to be able to assign a trip or view statistics.This is where the customers are currently lacking information.

![client-overview](/images/Guiding-customers---Improving-a-onboarding-experience/1-9V-tknpu9tHGw2FyuKDs8w.png "Task flow for first app usage")

With the existing onboarding flow outlined above I see a few issues.

If we look at the boxes outlined, we see that customers might need to switch platforms two times in order to complete their setup. A customer that enters the funnel from the app store needs to switch to the web for user registration and registration of the box/car.After the registration customers are left without notice that a first ride is necessary to initialize the mileage of the car.In behavioural analytics we saw that users start to explore the web client and are actively looking for next steps, but they are left with empty screens of statistics.

Due to the viarity of cars and their protocols it might be necessary to adjust/initialize the milage once after the first trip. This can only be done on the mobile client right now. Customers that came from the web-funnel might not know about this fact and are left with wrong mileages.

## The solution

### Mobile experience

The mobile client is currently lacking the features of user registration and registering box or connecting a tesla. Bringing those two capabilities to the mobile client would create a more cohesive experience to customers that are using the mobile client in the first place.

The setup of a box/vehicle would enable a onboarding experience that could be done without the need of switching platforms (app vs. web). This comes of course with additional development effort, so that a forward-link (from app to web) to the box/vehicle registration (without the need of login in the web) and then a link back to the app would be an alternative solution.

### **Web experience**

After registering a box/vehicle it is necessary to outline the next steps for the customer. Showing empty states of charts might not be helpful in that case. The capability of adjusting the mileage after the first trip needs to be presented in the web too  in order to avoid showing trips to customers  where the mileage is to initialized yet.

