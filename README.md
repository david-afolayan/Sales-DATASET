# **Ship Mode Sales Dataset**

## Table of Contents

-[Project Overview](#project-overview)

-[Dataset Sources](#dataset-sources)

-[Data Manipulation and Tools](#data-manipulation-and-tools)


### Project Overview 

The objective of this project is to analyze sales performance across various shipping modes offered by our company and identify opportunities to optimize shipping strategies, enhance customer satisfaction, and improve profitability.

### Dataset Sources
The primary dataset used for this analysis is the "sales.csv" file, containing detailed information about each sale made on the ship mode by the company. 
Python is the basic tool for the analysis, so the dataset was called using the below code.

```python
Sales=pd.read_csv('sales.csv')
Sales
```

### Data Manipulation and Tools

Python is the basic Tools used for the dataset to perform Data Manipulation in which some libraries were imported and some the manipulation that were done are:
- Data Cleaning/Preparation 
- Data Exploration/Visualization

#### *Data Cleaning/Preparation*

In the initial data preparation phase, we performed the following tasks under Data cleaning and formatting:

1. Data Loading and Inspection: import of Librabries and Dataset
```Python
import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

pd.options.display.max_rows = 9999

Sales=pd.read_csv('sales.csv')
Sales
```

2. Handling missing Values:
After checking for missing values, the dataset was comfirmed not having a missing values
```python
Sales.info()
Sales.isnull()
```
   
3. Rearranging the columns
```python
Sales.columns=Sales.columns.str.replace(' ','_')
```

4. Checking for Duplicates
```python
Sales=Sales.drop_duplicates()
```

5. Data Transformation/Data Aggregation
```python
Sales.describe()
Sales.groupby('Ship Mode').Sales.agg(['mean','max','median','min'])
Sales.groupby('Order Date').Sales.agg(['mean','max','median','min'])
Sales.groupby('Segment').Sales.agg(['mean','max','median','min'])
```

#### *Data Exploration/Visualization*

We use libraries such as Matplotlib,and Seaborn to visualize the manipulated data and gain insights through plots, charts, and graphs.
```Python
import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

**Relplot:**
 is a function in the Seaborn library, which is commonly used for creating relational plots. Relational plots are used to visualize the relationship between two or more variables in a dataset.
 in this dataset Relplot was used to Segment sales. 
 ```python
sns.relplot(x = 'Segment', y = 'Sales', data=Sales, hue='Segment')
```

**Countplot:**
 is a function in the Seaborn library used to create bar plots that show the counts of observations in each category of a categorical variable.

   - countplot on ship mode sales
 ```python
sns.countplot(x='Ship_Mode',data=Sales, hue='Ship_Mode')
plt.title('Countplot of Ship Mode Sales', c='Green', size= 15,fontweight='bold')
plt.xlabel('Ship Mode', size= 13,c='grey',fontweight='bold')
plt.ylabel('Count of Sales', size= 13, c='grey',fontweight='bold')
plt.grid(True)
```

   - countplot on segment sales
```python
sns.countplot(x='Segment',data=Sales, hue='Segment')
plt.title('Countplot of Segment Sales', c='Green', size= 15,fontweight='bold')
plt.xlabel('Segment', size= 13,c='grey',fontweight='bold')
plt.ylabel('Count of Sales', size= 13, c='grey',fontweight='bold')
plt.grid(True)
```

**Scatterplot:**
is a type of plot that displays the relationship between two numerical variables. It is often used to visualize the correlation or association between two variables and identify any patterns or trends in the data.
```Python
plt.figure(figsize=(8, 6))
sns.scatterplot(x='Segment', y='Sales', data=Sales, color='green',hue='Segment')
plt.title('Scatter Plot of Total Sales vs Sales Segment', c='Green', size= 15,fontweight='bold')
plt.xlabel('Sales Segment', size= 13,c='grey',fontweight='bold')
plt.ylabel('Total Sales(Naira)', size= 13, c='grey',fontweight='bold')
plt.grid(True)
plt.show()
```

**Boxplot:**
also known as a box-and-whisker plot, is a type of plot that provides a graphical summary of the distribution of numerical data through quartiles. It is particularly useful for visualizing the spread and variability of data, identifying outliers, and comparing distributions between different groups or categories.

```python
plt.figure(figsize=(6, 4))
sns.boxplot(x='Ship_Mode', y='Sales', data=Sales, hue='Ship_Mode')
plt.title('Evaluation of Ship Mode and Amount of Sales', c='blue', size='20',fontweight='bold')
plt.ylabel("Amount of Sales", c='green', size=15,fontweight='bold')
plt.xlabel("Ship Mode", c='red', size=15,fontweight='bold')
plt.grid(False)
plt.show()
```
