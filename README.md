# Ship Mode Sales Dataset

### Project overview 

The objective of this project is to analyze sales performance across various shipping modes offered by our company and identify opportunities to optimize shipping strategies, enhance customer satisfaction, and improve profitability.

### Dataset Sources
The primary dataset used for this analysis is the "sales.csv" file, containing detailed information about each sale made on the ship mode by the company. 
Python is the basic tool for the analysis, so the dataset was called using the below code.

```python
Sales=pd.read_csv('sales.csv')
Sales
```

### Tools

Python is the basic Tools used for the dataset to perform Data Manipulation in which some libraries were imported and some the manipulation that were done are:
- Data Cleaning/Preparation 
- Data Exploration/Visualization

### Data Cleaning/Preparation

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

2. Handling missing Values: After checking for missing values, the dataset was comfirmed not having a missing values
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

### Data Exploration/Visualization

We use libraries such as Matplotlib,and Seaborn to visualize the manipulated data and gain insights through plots, charts, and graphs.
```Python
import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
