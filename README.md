# Property Search

#### Problem Statement:

#### Assumptions made:

- Since it is not mentioned that the valid budget +/- 25% has to be taken from min/max budget value, I assumed the average value to calculate the +/- 25% and the added both sides.
- Assuming all the data will be provided
- Created 1000 properties mock data in database to match with the requirements.
  - assumed bedrooms & bathrooms between 1 to 6
  - assumed price between $ 1k to 10k
- Using [Haversine formula](https://en.wikipedia.org/wiki/Haversine_formula) to calculate distance between two points in miles
   


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
2	3	3	opharrow1@time.com	2	45.262508	17.427272	64.0	Murray-Schaden	8911.71
3	4	4	abadrick2@nba.com	3	-7.325472	108.207356	58.0	Mante Inc	7741.58
4	5	5	snorthover3@baidu.com	4	14.674129	120.511291	44.0	Bruen, Goldner and Bednar	7171.20
5	5	5	esigfrid9@shinystat.com	10	56.578971	85.102674	44.0	Walter, Herman and Murray	7239.76
6	1	1	bcampo5@yahoo.com	6	12.564028	123.730411	40.0	Auer Group	1526.33




```


