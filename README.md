# Prediction-of-Housing-Price

R script of my project on prediction of housing price in king county

## Research Question
1.  Interpret how price of houses in King County is affected by a myriad of variables such as number of bedrooms, number of bathrooms, location, square feet of house and etc. What's the likely range for the difference in prices between houses that have different features and locations? Does houses in seattle tend to have higher price than houses in other regions? How much higher?

2. Is there any evidence that the association between prices of houses and any feature of house differs by region? If so, characterize those differences.

## Methodology

Multiple regression is used to predict house price as log price demonstrates a linear relationship with most of the dependent variables.

## Data Overview

* Data Time Period: Houses sold 2014-2015
* 19 House Features
* 21613 Observations

|   Variable Name    |                  Meaning                   | Type of Variable |                 Transformation                  |
| :----------------: | :----------------------------------------: | :--------------: | :---------------------------------------------: |
|       Price        |                House price                 |    Dependent     |                       Log                       |
|      Bedrooms      |             Number of Bedrooms             |    Continuous    |                        -                        |
|     Bathrooms      |            Number of Bathrooms             |    Continuous    |                        -                        |
|       Floors       |           Total floors in house            |   Categorical    |                        -                        |
|     Waterfront     |      House with a view to waterfront       |   Categorical    |                        -                        |
|        View        | Number of times the house has been viewed  |   Categorical    |                        -                        |
|     Condition      |         How good the condition is          |    Continuous    |                        -                        |
|       Grade        | Overall grade based on King County grading |    Continuous    |                        -                        |
|    Sqft_Living     |           Square footage of home           |    Continuous    |                     Square                      |
|      Sqft_Lot      |           Square footage of lot            |    Continuous    |                     Square                      |
|     Sqft_Above     |    Square feet of house except basement    |    Continuous    |        Not used due to high correlation         |
|   Sqft_Basement    |       Square footage of the basement       |   Categorical    |  Convert to have_basement categorical variable  |
|   Yr_built, date   |           Built year, date sold            |    Continuous    |             Convert to age of house             |
|    Yr_renovated    |       Year when house was renovated        |   Categorical    |    Convert to have_reno categorical variable    |
| Zipcode, Lat, Long |            Location information            |   Categorical    | Convert to city and region categorical variable |
|   Sqft_Living 15   |          Living room area in 2015          |    Continuous    |        Not used due to high correlation         |
|    Sqft_Lot 15     |           Lot size area in 2015            |    Continuous    |        Not used due to high correlation         |
|                    |                                            |                  |                                                 |

## Key Findings

### Understand Housing Types in King County

1. **Bedroom** - 3 and 4 bedrooms are the most common types among all houses across regions, followed by 2 and 5 bedrooms. Bedrooms above 6 are really rare compared with other types. Seattle has the highest number of 2 bedrooms among all regions.

2. **Bathroom** - 3 bathrooms is the most common among all regions, followed by 2 and 1 bathrooms. Bathrooms above 5 is really rare compared with other types.

3. **Condition** - Condition 3 is the most common across all regions. Bellevue & Renton and Seattle have the highest number of condition level above 4.

4. **Floor** - Floor 1 is the most common across all regions, follOwed by floor 2. Seattle and Shoreline have a significant amount of 3 floors whereas the other regions don’t.

5. **View/Waterfront/Renovation**- no view, have waterfront and have renovated are the norms across regions.

6. **Basement** - most of houses in most of regions don't have basement. In Seattle we observe the highest amount of houses having basement.

7.  **Square Feet Living** - seems Gold Bar has the lowest square feet living median whereas Issaquah has the highest.

8. **Square Feet Lot** - seems Island has the highest square feet lot median whereas Seattle has the lowest.

9. **Square Feet basement** - basement across all regions seem to be the same. 

10. **Grade** - Gold Bar has the lowest grade median whereas Issaquah has the highest.

11. **Age** - Seattle has the highest age median whereas Issaquah has the lowest.

### How is Price affected by different dependent Variables

* All variables are statistically significant. The price of other types of house comparing with a house in Seattle when all other variables held constant is as below (all 95% CI), I am only highlighting the interesting findings here:

* The increase in every 1 bedrooom will cause the median price to drop by 2.33%-3.40%, but increase in every 1 bathroom will cause the median price to increase by 4.20% - 5.76%. The house of 3 floor will have median price around 12.22%-18.46% higher than 1 floor. That has shown people maybe valuing house of 3 floors more. The house that has a waterfront view will have median price around 35.14%-48.53% higher. With every 1 increase in condition grade, the median price of the house increases by 4.65%-5.99%. The house that has renovation will have median price increased by 3.37%-7.51%. The house that has basement will have median price increased by 0.76%-2.73%. With every 1 year increase in age, the median price increases by 0.38%-0.42%. 

* If the house is in Bellevue and Renton region, the median price would increase by 0.73%-3.07%. If the house is in Federal Way and Kent, the median price would decrease by 31.18%-33.08%. If the house in Gold Bar, the median price would decrease by 25.44%-43.24%. If the house is in Island , the median price would decrease by 0.73%-10.67%. If the house is in Issaquah, the media price would increase by 3.43%-6.57%. If the house is at shoreline, the median price would increase by 0.69%-3.16%. If the house sqft_living increases by 50%, the median price would increase by 0.40^1.5 - 0.44^1.5 which is 25.3%-29.2%. The house sqft_lot increases by 50%, the median price would increase by -0.0235^(1.5) - (-0.0127)^(1.5) which is 0.143% to 0.36% which is close to no change.

* **Among all insights, the interesting ones are when all other variables held constant, more bedrooms will cause median price to drop and higher age will cause median price to increase. We can infer that when all other variables are the same for 2 houses, people in general prefer houses with fewer bedrooms. This may be because people prefer house area to be used for other purpose rather than bedrooms. For the fact that people prefer older houses, it may be due to predictors that are not explained in this model. For example, older houses may have some other features that are attractive to buyers.**

### Evidence of Relationship between Price and House Features Differ by Region

* Different region of people appreciate buying houses that renovated before differently.  

* Comparing with houses that do not have renovation in Seattle, houses that are in Bellevue & Renton and have renovation, are exp(-0.0011+0.0042+0.170)-1=18.9% more expensive; houses that are in Federal Way & Kent and have renovation, are exp(-0.4+0.0042+0.04)-1=29.9% less expensive; houses that are in Gold Bar and have renovation, are exp(-0.31+0.0042-0.534)-1=56.8% less expensive; houses that are in Island and have renovation, are exp(-0.084+0.0042-0.144)-1=20.1%; houses that are in Issaquah and have renovation, are exp(0.0545+0.0042-0.06)-1=0.12% less expensive (can be seen as same price); houses that are in Shoreline andhave renovation, are exp(-0.0004+0.0042-0.00180)-1=0.2% more expensive (can be seen as same price)

