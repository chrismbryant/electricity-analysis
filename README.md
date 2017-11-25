# Analysis of Electricity Consumption (using Moving Averages)

Here, I perform a brief graphical analysis of my family's home power consumption, using data collected by our power company, Southern California Edison (SCE). 

Every 15 minutes, SCE measures the amount of energy consumed by our household (in kWh) over that 15-minute interval. By dividing each of these measurements by 15 minutes (0.25 hour), we can obtain the average power consumed during each 15-minute window. Power, i.e. the _rate of energy consumption_, is a sensible quantity to plot against time because we can calculate the energy consumed during a given interval of time by integrating the power curve over that interval. To get a sense of the trends present in our electricity consumption, as well as smooth out some of the noise in the data, we can plot a [_moving average_](https://en.wikipedia.org/wiki/Moving_average). The particular form of moving average I chose to use is an [exponentially weighted average](https://en.wikipedia.org/wiki/EWMA_chart) of the following form: v<sub>t</sub> = βv<sub>t-1</sub> + (1 - β)θ<sub>t</sub>, where *θ* is the list of raw measurements, β is a bias representing the smootheness of the averaging procedure, and *v* is the new smoothed list of measurements. Below, I have plotted the raw data in red, a short-term average in blue (β = 0.9), and a long-term average in gray (β = 0.999).  

![plot-1]

At this scale, the raw data (which is ~35000 data points) is unweildy. From the long-term average, we can see that around January 2017, the power consumption rose above average, likely due to persistent use of the heater. Likewise, in blue, we can see large spikes toward the end of May 2017 and the beginning of September 2017, indicating the use of air conditioning. To get a better idea of what the power consumption looks like during one of those spikes, lets's zoom in: 

![plot-2]

Above, we have a 

![plot-3]
![hist-1]

[plot-1]: https://raw.githubusercontent.com/chrismbryant/electricity-analysis/master/Plots/plot_1.png
[plot-2]: https://raw.githubusercontent.com/chrismbryant/electricity-analysis/master/Plots/plot_2.png
[plot-3]: https://raw.githubusercontent.com/chrismbryant/electricity-analysis/master/Plots/plot_3.png
[hist-1]: https://raw.githubusercontent.com/chrismbryant/electricity-analysis/master/Plots/hist_1.png
