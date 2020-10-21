# Property Search

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


```

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


- - -
