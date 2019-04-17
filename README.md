# Bokeh visualizations with Cargo 2000
This is my bokeh practices using Cargo 2000 dataset downloaded from kaggle https://www.kaggle.com/crawford/cargo-2000-dataset

I re-constructed the dataset based on my needs:

1. I removed two shippments in the incoming transport leg and the outgoing transport legs. As stated in the related paper Comparing and Combining Predictive Business Process Monitoring Techniques, the data "represents the structure of the business processes of a freight forwarding company, in which up to three smaller shipments from suppliers are consolidated and in turn shipped together to customers in order to benefit from better freight rates or increased cargo security." The legs in the header are actually shippments, not flight legs. I removed the data I don't need.

2. Since the dataset is sanitized and the depart/arrival airports are replaced with three-digit numbers, I manually mapped 29 most frequent airports (three-digit numbers) to real airports (airport codes). Note that the real airports are inferred from the flight time durations, distances between airports, and the geographical relations of airports. It's very likely the airports are not right as in the unsanitized data. But I just need a dataset to visualize logistic data so it doesn't matter.

3. I added risk of flight leg based on the number of runways that the airports have. The airport dataset I used is from https://github.com/krlawrence/graph/tree/master/sample-data

4. I added random values, weights, cargo_price_units, order_dates of the shippments. Other attributes such as cargo_price, risk_all, planned_date, deliver_date are generated from the above data wrangling.
