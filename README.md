# Airbnb Project
## Data Description and Technical Analysis

### Data:
 _Our data was collected from Inside Airbnb_
_This data was taken from Airbnb and we assume that is was computer generated_
_We referenced websites such as Zillow and Hospitable to find information about long term rentals and the added costs of short term rentals_
_We referenced reports from the City of Dallas to understand their HOT or Occupancy Tax_

### Deleted columns:
* ~~Listing UR~~
* ~~Scrape ID~~
* ~~Last Scraped~~
* ~~Source~~
* ~~Picture URL~~
* ~~Host URL~~
* ~~Host Name~~
* ~~Host About~~
* ~~Host Thumbnail URL~~
* ~~Host Picture URL~~
* ~~Host Profile Picture~~
* ~~Host Identity~~
* ~~Host Verifications~~
* ~~Latitude~~
* ~~Longitude~~
* ~~Minimum Minimum Nights~~
* ~~Maximum Minimum Nights~~
* ~~Maximum Maximum Nights~~
* ~~Minimum Nights Average~~
* ~~Maximum Nights Average~~
* ~~Calendar Updated~~
* ~~Has Availability~~
* ~~Availability 30~~
* ~~Availability 60~~
* ~~Availability 90~~
* ~~Availability 365~~
* ~~Calendar Last Scraped~~
* ~~Calculated Host Listings~~

### Added/Updated Columns:
* Filtered for just two bedroom listings
* Filtered room_type to Entire Home/Apt
* Filtered for District 1 only
* Filled blanks on review scores with the median score, as there was some skewness
* Added occupancy rate
* With an assumed occupancy rate of 50%, we multiplied number of reviews by 2, and then we multiplied that value by the minimum nights to get an estimate of occupancy over the lifetime of the listing
* Added revenue column
* Using an estimate of $143, based on similar rentals
* Added host region column
* Host region was found by classifying hosts as inside or outside of the city of Dallas by using the neighborhood column

Access original datasources and my updated datasources [here](https://drive.google.com/drive/folders/1eI0hxKTkzH3s82YG6-dMvt-D15b98He1?usp=sharing "Dallas Airbnb Data")

### Analysis Description
       
In order to make a recommendation for Sara’s property we needed an understanding of long term and short term rentals in the city of Dallas and an analysis of host involvement for each type of property to find the option that would ask the least of Sara and allow her to appropriately cover the costs of the property while she is in her program.
When looking at host involvement we considered the information that we had about host response time, host location, booking options such as instant booking, and reviews. Due to lack of information occupancy and revenue, our initial analysis relied heavily on the assumption that higher review ratings were associated with higher rates of booking. Once we were able to calculate an estimated occupancy rate using the San Francisco model cited on Inside Airbnb’s website, we were able to test this relationship. With the initial calculation, we took the number of reviews and multiplied this by 2 to account for a 50% review rate. We then multiplied this value by the minimum night stay value. When running a regression analysis between the two variables: average review rating and occupancy rate, our R^2 value was less than 0.5. We decided that an estimated occupancy rate was a more reliable key metric because it was an indicator of customer action, instead of opinion. 
We compared estimated occupancy rate for the lifetime of the listing to host response time and found strong associations between quick host response times and higher rates of occupancy. This was a key insight into our recommendation because we assume that Sara is a full time nurse while she is in school, and that time will be her most precious resource. We do not believe that she will have capacity to respond to each airbnb message in a timely manner, which would impact her occupancy rates. In addition, we also found strong associations with the average occupancy rate and the host’s location. We created a host location column that classified if a host was located within the city of Dallas or outside. When looking at average occupancy, hosts that lived inside the city of Dallas were associated with higher rates of average occupancy: 319 nights compared to 70 nights for hosts who lived outside of the city. This is relevant, as our host will be based in New York while she is managing the property. Lastly, we looked at instant booking as a way to see if this would impact occupancy rates, as this might be a viable option for Sara who is limited on time. When looking at District 1 in Dallas where Sara’s house is located, we discovered that properties without instant booking had higher overall rates of occupancy. All of these metrics on host involvement allow us to conclude that higher host involvement is associated with higher rates of booking, which is difficult for our client.
We came to the $145 nightly rate, as there were a few outliers in our data that skewed our average rate ($245.35). For the short term yearly costs, we took the nightly rental income, multiplied it by 21 (based on the 70% occupancy cap that Inside Airbnb provided), then multiplied it again by 12 months. We also deducted costs for a property manager, booking fees, HOT taxes, maintenance and repair costs, and furnishing costs to come to the final yearly revenue number. 
Our strategy to find the most commonly used amenities was to take all of the individual amenities and separate them into their own cells. Then, aggregate all of the cells into one column, find all of the unique values, and use a =COUNTIF function to populate the number of times each unique value was used.
To break down the long term analysis we had to gather data outside the inside airbnb website.To find the average home price in Dallas we looked up the average sale price of homes within the last 2 years and came up with $450,000 via redfin. The next question was what would be the month to month cost on mortgage. We retrieved a mortgage calculator and put $450,000 with a down payment of 20% which came out to $90,000.With those specifications our mortgage on a 30 year loan came up to $3067/month with taxes and insurance.Our next step was finding out where to price our home in that market. To do that we went on to Zillow.com and Rent.com, where we took every listing available on 12/18/2022 and came up with the average rent of $2200.
