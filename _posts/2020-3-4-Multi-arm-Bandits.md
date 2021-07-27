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