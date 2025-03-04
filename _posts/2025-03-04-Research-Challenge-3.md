---
title: Research Challenge 3
published: true
---

Text can be **bold**, _italic_, ~~strikethrough~~ or `keyword`.

[Link to another page](another-page).

Getting familiar with ML basics

# [](#Challenge-3)Challenge 3

The sinking of the Titanic is one of the most infamous shipwrecks in history. This dataset is one of the first datasets introduced to any analyst in Big Data sphere and also features regularly in computational prediction competitions on [Kaggle](https://www.kaggle.com/datasets/vinicius150987/titanic3]). On April 15, 1912, during her maiden voyage from the UK to US, the widely considered "unsinkable" RMS Titanic sank after colliding with an iceberg. The lack of sufficient lifeboats for everyone resulted in the death of 1502 out of 2224 passengers and crew. Although there was some element of luck involved in surviving the sinking, some groups of people were more likely to survive than others, such as women, children, and the upper-class. The analytical tool, Python, was analyse the data and obtain usuable insights.

## [](#Cleaning-the-Data)Cleaning the Data

Initially the number of columns in the data have inconsistent number of rows. Rows with missing values were removed, and then columns with too much of a difference in the number of rows compared to the others (>500) were dropped. Following the equalisation of the number of rows of each column without losing too much data in the key columns that contained information that was pertinent to survival/death. Columns that had very little impact on this were dropped.

```python
import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)
import math  # Various math expressions
import seaborn as sns
import scipy
import matplotlib.pyplot as plt
import matplotlib.cm as cm
import matplotlib.colors as mcolors
from IPython.display import display, Math
from sympy import symbols, Eq
from sympy.printing.latex import latex
%matplotlib inline 
plt.style.use('ggplot') # just have in your script for prettier plotting
sns.set(color_codes = True)
```
The above libraries/modules were used in the analysis of this dataset. Following the cleaning of the data, in the analysis of the data, the dataframe column names key was created:


> survived --- Whether Survived or not: 0 = No; 1 = Yes
> 
> pclass --- Passenger Class: 1 = 1st; 2 = 2nd; 3 = 3rd
> 
> name --- Name of passenger
> 
> sex --- Passenger gender
> 
> age --- Passenger Age in years
> 
> sibSp --- # of siblings/spouses aboard the Titanic
> 
> parch --- # of parents/children aboard the Titanic
> 
> ticket --- Ticket number
> 
> fare --- Passenger Fare
> 
> embarked --- Port of embarkation (C = Cherboug, Q = Queenstown, S = Southampton
> 
> cabin --- Passenger cabin number
> 
> body --- Passenger Body weight
> 
> boat --- Passenger rescue boat number
> 
> home.dest --- Passenger home address


`The first 5 rows of the data returned was:`

|    |   pclass |   survived | name                                            | sex    |     age |   sibsp |   parch |   ticket |    fare | embarked   |
|---:|---------:|-----------:|:------------------------------------------------|:-------|--------:|--------:|--------:|---------:|--------:|:-----------|
|  0 |        1 |          1 | Allen, Miss. Elisabeth Walton                   | female | 29      |       0 |       0 |    24160 | 211.338 | S          |
|  1 |        1 |          1 | Allison, Master. Hudson Trevor                  | male   |  0.9167 |       1 |       2 |   113781 | 151.55  | S          |
|  2 |        1 |          0 | Allison, Miss. Helen Loraine                    | female |  2      |       1 |       2 |   113781 | 151.55  | S          |
|  3 |        1 |          0 | Allison, Mr. Hudson Joshua Creighton            | male   | 30      |       1 |       2 |   113781 | 151.55  | S          |
|  4 |        1 |          0 | Allison, Mrs. Hudson J C (Bessie Waldo Daniels) | female | 25      |       1 |       2 |   113781 | 151.55  | S 



While the summary statistics for the dataset to be used for analysis is:

|       |      pclass |    survived |       age |       sibsp |       parch |      fare |
|:------|------------:|------------:|----------:|------------:|------------:|----------:|
| count | 1043        | 1043        | 1043      | 1043        | 1043        | 1043      |
| mean  |    2.20901  |    0.407478 |   29.8132 |    0.504314 |    0.42186  |   36.603  |
| std   |    0.840685 |    0.491601 |   14.3663 |    0.91308  |    0.840655 |   55.7536 |
| min   |    1        |    0        |    0.1667 |    0        |    0        |    0      |
| 25%   |    1        |    0        |   21      |    0        |    0        |    8.05   |
| 50%   |    2        |    0        |   28      |    0        |    0        |   15.75   |
| 75%   |    3        |    1        |   39      |    1        |    1        |   35.0771 |
| max   |    3        |    1        |   80      |    8        |    6        |  512.329  |



## [](#Analysis-Results)Analysis Results

This is the results of the analysis done on the Titanic datasets and the insights gained.

### [](#Passenger-Mortality-per-Class-&-by-Gender)Passenger Mortality per class & by Gender

![Differences in Survival Rate Per Passenger Class](https://github.com/skikszilcho/Titanic/blob/master/_posts/MortalityDifferencesperclass.png)

Contradictory to Class 2 & 3, a greater number of passengers in Class 1 who survived were greater than the number of passengers that died. The difference in the number of passengers who survived is greatest in Class 3, with more passengers dying than surviving, and least in Class 2. Similarly to 3rd Class, 2nd Class also saw more passengers dying than surviving. A further analysis was conducted to observe the split in mortality between the genders.

![Mortality Differences Per Gender](https://github.com/skikszilcho/Titanic/blob/master/_posts/PassengerSurvivalbySex.png)

![Mortality Differences Between Genders Per Class](https://github.com/skikszilcho/Titanic/blob/master/_posts/PassengerMortalitybySexperClass.png)


In general, a greater number of females survived compared to the number of males who survived. Males indicated a greater mortality, or the difference in the number of passengers who survived and died, compared to females. In the `Mortality Differences Between Genders Per Class` diagram, the genders are outlined by the same colour, while the differences between surviving and dying were indicated using different linestyles. Contrary to what was seen in the `Differences in Survival Rate Per Passenger Class`, the number of males from 1st class who died is greater than the number that survived. However, the mortality of this class was the lowest and kept increasing with class number. The 1st Class results observed in the `Mortality Differences Between Genders Per Class` were offset by the number of females who survived outweighing the number of females who died, and oppositely to males, the number of females who survived decreased with consecutive classes, with 3rd Class having a greater number of females who died compared to those who survived. However, the difference between the number of female survivors in 3rd Class is the least, and 1st class being the least. First Class, for females, had the highest survival rate and lowest death rate.

### [](#Passenger-Distribution-by-Age-&-Gender)Passenger Distribution by Age & Gender

![Age Range Distribution Per Passenger Class](https://github.com/skikszilcho/Titanic/blob/master/_posts/AgeRangeDistributionperClass.png)

Aside from 1st Class passengers, the passengers in the other classes saw the greatest number of passengers in the 14-28 range, and then secondly in the 28-43 range. This especially the case for 3rd Class Passengers. First Class, however, saw the greater majority of passengers in the 28-43 range, and secondly in the 43-57 age range.


```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### [](#header-4)Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### [](#header-5)Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### [](#header-6)Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)

### Large image

![](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
