# Fraud-Analytics
NY Property Data Investigation
DSO 562 Project 1

We are looking for anomalies in the data (strange, unusual values).

Expert Variables:
FULLVAL, AVLAND and AVTOT

Some modes of property fraud
- Assessed value too low (too high?)
- Person claiming an exemption for more than one property (requires linking by person)
- Claiming exemption on rental property (simple rule?)

In this project, we built an unsupervised fraud model for the NY property data.

Using proper methodology, we did data cleaning, constructed variables and built algorithm.

Steps:
1. Build ~50 “expert variables” by various scalings of the three value fields FULLVAL, AVLAND, AVTOT
2. Z-scale all variables
3. Perform PCA, keep the top 6 – 8 PC’s
4. Z-scale again
5. Build two separate fraud algorithms:
- Outlier detection via z-scores
- Autoencoder error
6. Combine scores via weighted quantile-scaled scores
7. Examine top records
9. Write report

