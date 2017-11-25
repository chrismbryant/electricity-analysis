# Analysis of Electricity Consumption (using Moving Averages)

Here, I perform a brief graphical analysis of my family's home power consumption, using data collected by our power company, Southern California Edison (SCE). 

Every 15 minutes, SCE measures the amount of energy consumed by our household (in kWh) over that 15-minute interval. By dividing each of these measurements by 15 minutes (0.25 hour), we can obtain the average power consumed during each 15-minute window. Power, i.e. the _rate of energy consumption_, is a sensible quantity to plot against time because we can calculate the energy consumed during a given interval of time by integrating the power curve over that interval. To get a sense of the trends present in our electricity consumption, as well as smooth out some of the noise in the data, we can plot a [_moving average_](https://en.wikipedia.org/wiki/Moving_average). The particular form of moving average I chose to use is an [exponentially weighted average](https://en.wikipedia.org/wiki/EWMA_chart) of the following form: v<sub>t</sub> = βv<sub>t-1</sub> + (1 - β)θ<sub>t</sub>, where **θ** is the list of raw measurements, β is a bias representing the smootheness of the averaging procedure, and **v** is the new smoothed list of measurements. Below, I have plotted the raw data in red, a short-term average in blue (β = 0.9), and a long-term average in gray (β = 0.999).  

![plot-1]

At this scale, while the raw data (which is ~35000 data points) is unweildy, we can start to glean some useful information from the moving averages. From the long-term average, we can see that around January 2017, the power consumption rose above average, likely due to persistent use of the heater. Likewise, in blue, we can see large spikes toward the end of May 2017 and the beginning of September 2017, indicating the use of air conditioning. To get a better idea of what the power consumption looks like during one of those air-conditioning spikes, lets's zoom in: 

![plot-2]

Above, we see that the power spike of September 3 actually separates into two distinct spikes, one in the night leading up to Sep 3, and the other peaking in the daytime around 6 pm. This makes sense, because we likely only had the air conditioner running while we were awake. It is also important to note that the energy consumed on this air-conditioning-day reached roughly 5 times our average daily energy consumption! To save on electricity, we see, it's a very good idea to limit the use of air conditioning.

To get an idea of what a more typical week for our household looks like, let's shift our view to the few days before and after Halloween of 2016. In the plot below, we see a clear daily trend of night-time power peaks roughly twice the height of the baseline power consumption, as well as smaller peaks around 7 am each morning. This pattern reflects the fact that we turn on most of the house lights when the sun sets, turn them off when we sleep, then turn a subset of the lights on in the morning when we get ready for the day. From around 7 am to 6 pm each day, the power consumption rests at its baseline (refrigerators contributing the most to that baseline) both because most of the members of the household are not at home, and because the ambient daylight removes the need for the house lights to be on.      

![plot-3]

Lastly, we can plot the SCE data in a histogram to view the distribution of power measurements. 

![hist-1]

[plot-1]: https://raw.githubusercontent.com/chrismbryant/electricity-analysis/master/Plots/plot_1.png
[plot-2]: https://raw.githubusercontent.com/chrismbryant/electricity-analysis/master/Plots/plot_2.png
[plot-3]: https://raw.githubusercontent.com/chrismbryant/electricity-analysis/master/Plots/plot_3.png
[hist-1]: https://raw.githubusercontent.com/chrismbryant/electricity-analysis/master/Plots/hist_1.png
