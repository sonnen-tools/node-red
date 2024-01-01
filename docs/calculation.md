# Calculation 

## What is a cheap hour?

There are many ways to calculate what "cheap" is. Tibber even provides a "PriceLevel" in its API [https://developer.tibber.com/docs/reference#price](https://developer.tibber.com/docs/reference#price)
![](../images/pricelevel.png)

However, I wanted a bit more flexibility and granularity (I have to take the conversion loss into account, also)... 

## Key node

The key node for the calculation is the getCheapestHours node:

![](../images/SB-flow-overview_getcheapestHours.png)

Based on its calculation, it stores the "cheap hours" in an array in the flow context. Other nodes (e.g. the "`shouldIBeCharging`" node) read this and then determine if they are in a "cheap Window" and what the the current cost is:

![](../images/cheapHours-context.png)

## How does it work ?

The "algorithm" (if it deserves that name) is rather simple:

1) I get all available prices (that's either just today or today _and_ tomorrow)
2) I calculate the average price over that time horizon (24 or 48 hours)
3) I'm factoring in the "conversion loss factor" (see [Background](./background.md)) - the effective average price after the charging/discharging cycle is higher than the "real" price.
4) I also have a "userMaxPrice" to override calculation - I use whichever is lower (the factoredAverage or the userMaxPrice). So, if the price level is really high (the factored average would be higher than your set maxPrice) you can avoid charging above a certain level (even if the average tells you that it is cheap compared to the overall period).
5) All hours with a price lower that the result are considered "cheap Hours".

So, I get all hours that are below the factored average or the maxPrice.

**Example:**  
If the average price for today and tomorrow is 25ct/kWh, with a conversion loss factor of 20% (factor: 1.2) the "factored" average would be 20ct/kWh (or, 80% of 25ct).  
So, all hours equal or below 20ct would be considered "*_cheap enough for charging the battery_*"


# Next Step: Charging/Discharging

The process for charging/discharging (based on our "cheapHours") is explained in the [Charging / Discharging](./charging-discharging.md) chapter.
