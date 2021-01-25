+++
author = "Chris"
categories = ["app", "aso"]
date = 2019-12-20T23:00:00Z
description = ""
slug = "app-pricing-with-gdp-in-mind"
title = "App pricing with GDP in mind"
type = "post"

+++
This week I got a review for my app [Visual Timer](https://play.google.com/store/apps/details?id=at.cwiesner.android.visualtimer) from an Indian user who suggested to add a cheaper product, that would enable more purchases for their market.

That got me thinking about my pricing and I had a look how it was configured in the first place.

![config-play](/images/App-pricing-with-GDP-in-mind/1-jr_ZNn6M78wIInyPbh3gLg.png "In-app product pricing configuration in Google Play Console")

In the Google Play Console you just specify an amount (e.g. $1) and it takes the current exchange rate and converts the amount in the target currency. That was it for the global payment setup i thought — until that review.

This pricing does not take the **differences in GPD** (per capita) for the countries into account. Which means that an Indian user is most likely not able or willing to purchase a product of $1.

I was quite surprised that I didn’t pay attention to that earlier. So I thought I’d share this learning here.

### Calculate pricing

In order to configure adjusted prices I’d need to calculate them for every country where the app is available.I’ve used the GDP of my country and relate it to the GDP of the countries in order to adjust pricing.

For that I’ve created a spreadsheet with all countries and their GDP per capita (there are two different models: nominal/PPP) and their currencies to calculate GDP adjusted prices. You can [get it here](https://docs.google.com/spreadsheets/d/13Uq7DpctKCn_XC1n6nOtyLOxG3-ZrxCDIBLso1Rd_sU/edit?usp=sharing).

![spreadsheet](/images/App-pricing-with-GDP-in-mind/1-wRJucDzqZKHP3jO23MSKgg.png "Spreadsheet for calculating GDP adjusted pricing")

### Minimal price

While the calculations would suggest to use a very low price for countries like Jordan Google is having a minimum price limit (I guess even individually defined for currencies). Still these limits are not very transparent and for some countries to high compared to my calculations.

### What remains?

I adjusted now my products pricings and I’m eager to see if those changes will drive purchases in countries where I lowered prices up to 10x. Will share findings if there is some impact.

Thanks for reading and let me know if you have a different opinion or I got something wrong.