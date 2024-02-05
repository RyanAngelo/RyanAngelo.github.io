---
layout: post
title:  "Instant MBTA"
date:   2022-01-22 09:17:00 -0500
categories: projects
tags: raspberry pi, pHAT, MBTA,
author: Ryan Angelo
read_time: true
---

I recently finished up a small project as a gift that provides train schedules on a small-form factor Raspberry Pi Zero W using an eInk display.

<span class="icon icon--github">{% include icon-github.svg %}</span> [View on GitHub](https://github.com/RyanAngelo/InstantMBTA){:target="_blank"}

InstantMBTA is a project that is designed to leverage a Raspberry Pi Zero W for acquiring and displaying MBTA train schedules on an Inky pHAT display.

This project retrieves the latest train schedules and finds the latest predicted time for arbitrary inbound and outbound trains, leveraging the MBTA's API.

## The Hardware
This project runs on a [Raspberry Pi Zero W](https://www.raspberrypi.com/products/raspberry-pi-zero-w/){:target="_blank"}. I chose it primary because of the small form factor, the wireless LAN capability and the low energy consumption.

The display piece is an [inky pHAT](https://shop.pimoroni.com/products/inky-phat?variant=12549254217811){:target="_blank"} which is made by PIMORONI. I find eInk/ePaper really interesting and wanted to experiment with it. That, coupled with it's low energy footprint made it a fun choice. I find the eInk a really interesting technology, I hope it finds its way into more applications and becomes more affordable. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/Oqu1--AzM7U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

I went with a [simple acyrlic case](https://www.c4labs.com/product/zero-heatsink-case-raspberry-pi-zero-w/){:target="_blank"} from C4 Labs. Having purchased a few C4 labs cases over the years, I like their simplicity and the fact that you get both form and function.

![Image of back of the system](/assets/images/InstantMBTA/back.png)

## The Software
The MBTA provides [an API](https://www.mbta.com/developers/v3-api){:target>="_blank"} for getting up-to-date transit information. In particular, their Swagger API documentation was really useful and easy to navigate. Their API documentation also lets you experiment with parameters within the documentation.

The software piece is written in Python and simply goes out and collects the schedule for the given line and looks at stops of interest. If the stops of interests have predictions (real-time expected arrivals) they are used instead of the pre-determined schedule.

The inky pHAT display has a [python library called inky](https://github.com/pimoroni/inky){:target="_blank"} maintained by PIMORONI that makes it easy to display content on the display using PIL. The Inky pHAT is 250x122 so there is limited space for displaying text. I decided to start from the top and work down getting everything lined up. Selecting a font size and determining the height of each line of text, you can move from the top coordinate to the bottom coordinate.

![Image of front of the system](/assets/images/InstantMBTA/front.png)

#### Optimization
The Inky pHAT takes a relatively long time to refresh, so to reduce the amount of refreshes, the display will only refresh if something has actually changed. I'm looking forward to experimenting with other ways of drawing on the Inky pHAT that might reduce the refresh time.

#### For the Future
The MBTA API supports Last-Modified caching, so to further optimize the load, a future improvement would be to add support for checking the header for when the data was last modified and only continuing if it has been updated.

One aspect that was a bit more complex than anticipated was getting the predictions. The predictions provided as part of the schedule endpoint only return a prediction ID. I had to go and retrieve all of the predictions, then find the prediction information by the ID. I haven't figured out a way to get a prediction by ID without getting all of the predictions, as it doesn't seem like the prediction ID can be used as a filter for the request.

This doesn't seem like a good solution, I would like to find a better way of getting the prediction data:

```python
def find_prediction_by_id(self, prediction_id, predictions):
    prediction = None
    for prediction in predictions['data']:
        if prediction['id'] == prediction_id:
            return prediction
    self.logger.warn("There should have been a prediction found, but there wasn't.")
    return prediction
```

A better setup for the case might also be in the cards, as the display would look more polished with a covering.