# Fraud-Analytics
NY Property Data Investigation
DSO 562 Project 1

We are looking for anomalies in the data (strange, unusual values).

Expert Variables: variables that we are focusing on
FULLVAL, AVLAND and AVTOT

Some modes of property fraud
- Assessed value too low (too high?)
- Person claiming an exemption for more than one property (requires linking by person)
- Claiming exemption on rental property (simple rule?)

In this project, we built an unsupervised fraud model for the NY property data.

Using proper methodology, we did data cleaning, constructed variables and built algorithm.

Steps in detail:
1. Build ~50 “expert variables” by various scalings of the three value fields FULLVAL, AVLAND, AVTOT

    - Create these 3 sizes
        - lotarea = LTFRONT * LTDEPTH
        - bldarea = BLDFRONT * BLDDEPTH
        - bldvol = bldarea * STORIES
    - Calculate 9 variables, each of the 3 values (FULLVAL, AVLAND and AVTOT) normalized by each of these 3 sizes (3 * 3 = 9)
    - Create the grouped averages of these 9 variables, grouped by 
      zip5, zip3, taxclass, borough, all
    - This makes 9 * 5 = 45 variables.
    - Add any additional variables you can think of that make sense.

2. Z-scale all variables
3. Perform PCA, keep the top 6 – 8 PC’s
4. Z-scale again
5. Build two separate fraud algorithms:
- Outlier detection via z-scores
- Autoencoder error
6. Combine scores via weighted quantile-scaled scores
7. Examine top records
9. Write report

*About "Fill In Missing Fields"
- For the three values, when they are missing we want to fill in with innocuous values that won’t set off the alarm. 
- Use the field averages, and you can group by any entity you think makes sense.
- For the other fields we need to scale (LTFRONT, LTDEPTH, STORIES, BLDFRONT, BLDDEPTH), 
fill in with values that make sense. 
- You can use whatever logic you want, for example:
    - If LTFRONT=LTDEPTH=0, set them to (30, 100)
    - If BLDFRONT=BLDDEPTH=0, set them to (20, 40) 
    - If STORIES=0, set it to average stories by zip code, borough, TAXCLASS, or some other entity.
