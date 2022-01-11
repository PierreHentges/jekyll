---
layout: post
title:  A lockdown project that became something bigger
categories: [pollen]
---
I'm setting up this blog to document and reflect on some work I did on a dataset of aerobiological pollen measurements, to share methods I used and insights I gained.

A few weeks before last winter's lockdown, in search for a real world dataset, mainly as an exercise for time-series analysis and visualisation as well as some predictive modelling, I started looking at data from the aerobiology station in Luxembourg (publicly available at pollen.lu).

It's a great dataset, covering 30 continuous years of pollen measurements, taken at a daily frequency, of 33 different types of trees, grass and weeds. It also contains daily measurements of several types of fungal spores. The data are very clean and consistent, probably because, over the three decades, the measurements have been taken by the same team of people and the pollen trap was never moved.

The more I looked at the data, the more interested I got in it. Pollen research takes place at the unusual intersection of medicine (due to medical relevance of pollen allergies), botany (particularly [phenology](https://en.wikipedia.org/wiki/Phenology), which studies periodic events of biological life cycles), and meteorology (because pollen concentrations are largely determined by weather conditions). 
<!-- break -->
But there's also a link to climate change: since weather conditions influence pollen concentrations, climate change is reflected in pollen data. And therefore a 30 year-long time-series of pollen concentrations provides a detailed record of the impact climate change has had on vegetation.

So, when last winter's lockdown was announced, this pollen analysis project became something bigger, as I wanted to do something useful with my time.

An in-depth analysis of the data has now been accepted for publication in the [Bulletin de la Société des Sciences Médicales du Grand Duché de Luxembourg](https://ssm.lu/bulletin/). So this seems like the right moment to reflect on and document some of the work I've done for it. 

I’m going to talk about things like cleaning of these time-series data, trend analysis, getting a handle on the variability, mast seeding.

It's also very interesting from a data analysis/modelling perspective, because the data (both pollen and weather) are solid but analysis and modelling are surprsingly challenging. I learnt how to apply a number of methods, which I want to describe in this series of blog posts.


