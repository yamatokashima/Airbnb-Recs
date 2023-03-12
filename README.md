# Airbnb Project
## Data Description and Technical Analysis

### Data:
Introduction
The goal of this project was to create a rental recommendation for Sara’s property in Dallas, Texas  while she is in a nurse practitioner program in Buffalo, New York. With Airbnb being a popular way to earn passive income, the team decided to look into both short term and long term rental options for Sara’s two bedroom home, while keeping in mind that Sara will have limited capacity to manage the rental from afar. The overarching goal was to find a rental recommendation for the house that would allow Sara to cover as many of the baseline costs including mortgage, taxes, and insurance  as possible while requiring the least of her involvement. 

### Background 
 Sara recently placed a 20% down payment on a two bedroom home in Dallas, Texas for $450,000. In recent years many people have generated passive income on short term rentals through Airbnb. Turning a profit on these properties requires the right property and significant amounts of work from the host. As Airbnb has become more popular, more people have started to examine the impacts of short term rentals on the housing and long term rental market, and many cities including the city of Dallas, have started to apply short term occupancy taxes and create new regulations to account for these challenges.
 Our analysis looked at all of the market trends outlined above and was structured around examining what type of profit was possible for Sara to generate on a short term basis given the style and location of her home. We also decided to examine what type of involvement Sara would need to make the property as profitable as possible. We then did an analysis of the long term housing possibilities for the home and the rental market in Dallas and did a comparison between the two. 

### Technical Details
Our key metric for this project was to use occupancy rate, as later detailed on how we ended up on this metric and how we went about measuring it. Some of the analysis for this included a comparison of host response time and occupancy, host location and occupancy as well as occupancy rate associated with many aspects of the home details. To do our calculations and visualizations, our main tools used were Microsoft Excel and Microsoft Power BI. We also utilized index searches to find most of our long-term rental data, since we could not find this information on InsideAirbnb’s site, which could pose as an issue, as the method of collecting data may be different.

Our presentation highlighted many of the associations that we perceived as significant. These results mainly comprised of one-to-one comparisons. We used a variety of pivot tables, pivot graphs, and many of Power BI’s variety of charts and graphs to use in our presentation to clearly ad accurately display of findings within Google Slides. We were able to import all our data from Excel directly into Power BI. Once we finished the visualizations, we imported them to Slides by grabbing screenshots and uploading them as images.

A challenge for us was trying to figure out a way to implement the amenities data and find the best way to clean the information. The way we went about this was to first use the ‘Find & Replace’ tool to get rid of the unnecessary open/close brackets, single quotes, and spaces. We then copied all the column information, pasted it into its own excel sheet, used the text-to-columns function to put each amenity into its own cell, highlighted all rows and columns with amentities data, renamed the highlighted box to “Amenities”, input the function: 

	=INDEX(Amenities,1+INT((ROW(A1)-1)/COLUMNS(Amenities)),MOD(ROW(A1)-1+COLUMNS(Amenities),COLUMNS(Amenities))+1
to put all of the cells into one row. After, we input the =UNIQUE function in a new column to find all unique cells from the amenities, then did the =COUNTIF function to see how many occurrences of each unique amenity appears. We were able to find the top amenities by number of occurrences so that we could make a recommendation for Sara on what’s important to Airbnb guests.
 
### Implementation
In order to make a recommendation for Sara’s property we needed an understanding of long term and short term rentals in the city of Dallas and an analysis of host involvement for each type of property to find the option that would ask the least of Sara and allow her to appropriately cover the costs of the property while she is in her program.

When looking at host involvement we considered the information that we had about host response time, host location, booking options such as instant booking, and reviews. Due to lack of information occupancy and revenue, our initial analysis relied heavily on the assumption that higher review ratings were associated with higher rates of booking. 
When using average reviews as a key metric, we ran into several challenges including how to categorize reviews as low, medium, or high. 

### Descriptive Statistics for Average Reviews

| Aggregation| Value|
| ----------- | ----------- |
| Median     | 4.85 |
| Mean       | 4.72 |
| Mode       |  5   |
| Minimum    |  0   |
| Maximum    |  5   |

Majority of the reviews were above 4.0 which made it very difficult to classify something as a good or bad review. In addition, it was very difficult to know how many people actually left a review and we had no real proof that a higher review resulted in higher rates of booking.
Once we were able to calculate an estimated occupancy rate using the San Francisco model cited on Inside Airbnb’s website, we were able to test the relationship between reviews and occupancy rate. With the initial calculation, we took the number of reviews and multiplied this by 2 to account for a 50% review rate. We then multiplied this value by the minimum night stay value. When running a regression analysis between the two variables: average review rating and occupancy rate, our R2 value was less than 0.5 as seen below. While this linear regression model does not show correlation, we are able to see that there is some sort of positive relationship between the two variables, possibly an exponential relationship. We decided that an estimated occupancy rate was a more reliable key metric because it was an indicator of customer action, instead of opinion. 

### Regression Analysis: 

![regression](https://user-images.githubusercontent.com/101782618/224577157-076f63c0-3896-4961-ac16-675adb9df845.png)

Once we confirmed our key metric as occupancy rate, we outlined our analysis as follows:

* Host Involvement and Occupancy rate:
* Compare occupancy rate and booking option instant book or non instant book
* Compare occupancy rate and host response time
* Compare occupancy rate and host location (inside or outside the city of Dallas) 

### Short Term Rental Analysis
* Compare amenities and rates of occupancy
* Compare  occupancy rate and number of beds
* Compare occupancy rate and number of guests
* Find the average cost per night based on location

### Long Term Rental Analysis
* Find long term rental costs
* Examine long term rental market in Dallas Texas


### Results
The findings of the research were interesting to say the least. We found that the number Sara needed to cover every month to break even was going to be $3,067 which comes to a grand total of $36,804. We examined the short term Airbnb data and found out that the gross income would be around $3,045 monthly. The downside of that option was the enormous fees: the 30% property fee accompanied by a couple other fees brought the net revenue between $8,697 and $11,197. The long term data revealed that the average price in Dallas for a 2 bedroom house was around $2,200, with the gross income totaling $26,400. The advantage that the long term option had over the short term was avoiding a lot of the fees. By going long term the property manager fee is cut down from 30% to 10% and would also avoid the HOT/booking fees. This brought our net revenue down to between $21,460 and $22,360 which was much more than the long term option.

### Conclusion 
After everything was said and done we realized both routes lead to a loss, the only thing we can do is try to cut our losses shorter. Our initial prediction was right and wrong at the same time; we initially speculated that the short term would bring Sara more revenue but wouldn't be the ideal due to her circumstances at the moment. To our surprise not only did the long term outperform the short term revenue , but it doubled the amount of revenue we would see. This further strengthens our suggestion to go with the long term route because the short term has no logical benefits.

## References
### Data and information:
* Inside Airbnb
* DallasCityHall  
* Hospitable
* US Census
* Rent
* Zillow
* Redfin
* SmartAsset

### Technologies:
* Microsoft Excel
* Microsoft PowerBI
* Trello
* Google Slides
* Google Drive
* Google Sheets
* Slack

### Techniques:
•	Harry McKaig and team (Evan Meyer and Adam Klesitz) for helping us with the idea of using Occupancy Rate as our key metric

Access original datasources and my updated datasources [here](https://drive.google.com/drive/folders/1eI0hxKTkzH3s82YG6-dMvt-D15b98He1?usp=sharing "Dallas Airbnb Data")
