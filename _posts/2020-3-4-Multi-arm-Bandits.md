---
layout: post
title: 'Realized Volatility '
published: true
---
Combine trade with book data. Some merge. 
Trade data: avg_size = size/order
Trade data: average time between orders: .diff() -> mean()


My changes: 300, 150.
Avg order size
Avg time between trades
Early stopping from 30 to 300

If missing values, replace by the mean for each stock id. 

Add time_id represents the bucket in the day. 
Fill nan values

time_id we can probably reverse engineer the time id to get the U-shaped curve. 

shocks propagate between stocks, correlation between stocks.

Create a few models for clusters of stocks. 

RV by 1 min or 2min. 

time_id x bin empty what to do? ok

add log_return2 see if it improves performance or not

try 2min bins to see if we see better performance. 

Cluster the same stocks together. 