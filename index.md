---
title       : WiFi Latency
subtitle    : A Shiny App for evaluating a Sensor Network
author      : K. Pavelock
job         : Developing Data Products Coursera Class Project
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]       # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## WiFi Latency - Introduction

     Purpose: "To evaluate WiFi Latency for a sensor network based on several network parameters"  


### Network parameters
     - surveillance area
     - network hub range
     - wifi throughput
     - message size
     - number of major network transactions


### Selectable parameters       
     - Surveillance area (feet); "slider bar (60 - 5280*2)"       
     - Network node range (feet); "slider bar (25 - 200)"
     - WiFi throughput speed (Mbps); "slider bar (30 - 100)"

--- 

## WiFi Latency - Notes/Assumptions

- Average building area is 760 feet; Average area for a small city is 2 miles
- WiFi throughput for for 802.11n is 40-50 Mbps. From http://www.speedguide.net/faq/
- Message sizes (kilobytes-KB): small-50KB, medium-500KB, large-5000KB
- Requires 3 sensors per node; Alert Sensor with two Confirming Sensors
- Required main Network Messaging Transactions

     - Sensor discovery initiation via a status request;
     - Sensor discovery response via a status message;
     - Sensor(s) alert via alert message;
     - Detailed detection data request;
     - Detailed detection data transmittal;
     - Additional detailed detection data request;

---

## WiFi Latency - Formula

Network Processing Time (NP) is measured as Network Delay. 

Total Network Processing time $ NP_T $ is the sum of all NPs for each transaction:

$$ NP_T = \sum_{t=1}^n NP_t $$
$ n $ is the number of main transactions and $ NP_t $ is the network processing time for one major transaction:

$$ NP_t = NL * \left( d_r + d_p + d_c \right) $$
$ NL $ is the number of nodes (network routers + 1)
- Transmission Delay $ d_r $ average message size /Rate (WiFi Speed)
- Propagation Delay $ d_p $ distance/wave propagation speed. WiFi wave propagation speed = speed of light (186,000 miles per second)
- Processing Delay $ d_c $  time for routers to process packet headers.  This is negligible (set to 0)

---

## WiFi Latency - Outputs

A graph (plot) is displayed showing the latency versus number of sensors.  Calculated values are displayed as text labels:  Number of sensors, Surveillance area (Distance), and Latency.  The sample plot below is a replica from the Shiny App with WiFi speed of 45 Mbps and 100 ft hub range.
- Try it for yourself.  My WiFi Latency App is deployed at https://kathpave.shinyapps.io/Shiny/

