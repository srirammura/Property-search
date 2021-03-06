# Property Search

#### Problem Statement:

Write the most efficient algorithm that helps s determine a list of matches with match percentages for each match between a huge set of properties (sale and rental) and buyer/renter search criteria as and when a new property or a new search criterion is added to our network by an agent. This algorithm should match these properties and search criteria as they come in based on 4 parameters such that each match has a  match percentage.
The 4 parameters are : 
 - Distance - radius (high weightage)
 - Budget (high weightage)
 - Number of bedrooms (low weightage)
 - Number of bathrooms (Low weightage)


#### Assumptions 

- Since it is not mentioned that the valid budget +/- 25% has to be taken from min/max budget value, I assumed the average value to calculate the +/- 25% and the added both sides.
- Assuming all the data will be provided
- Created 1000 properties mock data in database to match with the requirements.
  - assumed bedrooms & bathrooms between 1 to 6
  - assumed price between $ 1k to 10k
- Using Haversine Formula to calculate distance between two points in kilometers
```
def distance(lat1, lon1, lat2, lon2):
    p = 0.017453292519943295
    a = 0.5 - cos((lat2 - lat1) * p) / 2 + cos(lat1 * p) * \
        cos(lat2 * p) * (1 - cos((lon2 - lon1) * p)) / 2
    return 12742 * asin(sqrt(a)) # in kms
```
   


#### Algorithm used:

I used linear proportion conversion algorithm to generate results.
Here's the formula for it:
```
OldRange = (OldMax - OldMin)  
NewRange = (NewMax - NewMin)  
NewValue = (((OldValue - OldMin) * NewRange) / OldRange) + NewMin
```

Here's the steps for one data: 
(example of price - budget matching):
- given min & max budget and price of a property
- calculate the average budget 
- define boundaries for valid to 100% matching condition
- using above expression to find the matching percentage
- returning data

#### Calculations:
After indivisually calculating matching of every field, I'm then merging them according to the provided weightage:
```
DISTANCE_WEIGHT = 0.3
BUDGET_WEIGHT = 0.3
BATHROOM_WEIGHT = 0.2
BEDROOM_WEIGHT = 0.2

Result(in %age)  = distance_match * DISTANCE_WEIGHT
        + budget_match * BUDGET_WEIGHT
        + bedroom_match * BEDROOM_WEIGHT
        + bathroom_match * BATHROOM_WEIGHT
```

###  Results



| Bathrooms | Bedrooms | Emailid                | id | Latitude | Longitude | Match | Name             | Price      |
|-----------|----------|------------------------|----|----------|-----------|-------|------------------|------------|
| 2	       | 2        | mheaviside0@symantec.com | 1 | 18.372139 | 121.511128 | 100.0  | Jerde Group       | 8305.39    |
| 2 |	2 |	ddybbe6@dell.com |	7	 | 59.917331 |	10.818031 |	70.0 |	Altenwerth Inc |	8435.96 |
|	3 |	3 |	opharrow1@time.com |	2	 | 45.262508 |	17.427272 |	64.0 |	Murray-Schaden |	8911.71 |
|	4 |	4  |	abadrick2@nba.com	 | 3 |	-7.325472 |	108.207356 |	58.0 |	Mante Inc |	7741.58 |
|	5  |	5 |	snorthover3@baidu.com |	4 |	14.674129 |	120.511291 |	44.0 |	Bruen, Goldner and Bednar |	7171.20 |
|	5 |	5 |	esigfrid9@shinystat.com |	10 |	56.578971 |	85.102674 |	44.0 |	Walter, Herman and Murray |	7239.76 | 
|	1 |	1 |	bcampo5@yahoo.com |	6 |	12.564028 |	123.730411 |	40.0 |	Auer Group |	1526.33 |







