
# Data Prep Exercise

__Note: This exercise is not shared with HDS trainees. It is here simply as reference__

## Preparations & Data Loading

### Loading all libraries


```python
%matplotlib inline
%config InlineBackend.figure_format='svg'

from IPython.display import display,HTML
import pandas as pd
# import seaborn as sns
import numpy as np
import matplotlib.pyplot as plt
# sns.set_style("ticks")
# sns.set_context(context="notebook",font_scale=1)
```

### Loading the relevant file

### First inspection of the data

#  Data issue exploration

## DATA ISSUE 1: Missing values - across columns

### Count the number of NA values by column

## DATA ISSUE 2: Missing data - Income data

### Use a historigram to show the distribution of the income data

## DATA ISSUE 3: Changing Scales - Height

### Let's start with checking whether the height distribution looks normal

### From the average heights for male and female and the graph above, it looks as if part of the heights has been entered in inches, and part of the heights has been entered in cm. Let's convert all to inches.

## DATA ISSUE 4: Drugs - change scale “never”, “sometimes”, “often” to respectively 1,2,3 

### Let's start with inspecting the data

## DATA ISSUE 5: Age outliers - Ignore people "older than" 99

### We start with inspecting the data

## Height Distribution Check


```python
men_df = None
wom_df = None

# Create histograms for height of men and women with null values dropped (dropna()). Set bins to 40, alpha to 0.5, 
# normed=True


# This code move the legend, and displays the plot
plt.legend(loc='upper right')
plt.show()

# Cast 'cons_height' to numeric, set errors to 'coerce', and drop any rows with missing values for each group. 
men_height = None
wom_height = None

display("Men average {} in or {} cm".format(men_height.mean(), men_height.mean() * 2.54))
display("Women average {} in or {} cm".format(wom_height.mean(), wom_height.mean() * 2.54))


men_height = men_height[(men_height>56) & (men_height<82)]
wom_height = wom_height[(wom_height>56) & (wom_height<82)]
```

___What you should see:___

Both men and women who go online are magically 4 cm taller than average for cdc :)


```python
plt.hist(men_height, bins=23, alpha=0.5, label='Men')
plt.hist(wom_height, bins=20, alpha=0.5, label='Women')
```

___What we see___:
* Thnik we have some eager over-estimators here:
* Women peak is at 62" which is actually reasonable
* Men peak at 70 and 72" (nice round 6' ft choice)
 * Actual peak is at 68 to 70 (if we're really generous)
 * so a nice 2" bump for most men
