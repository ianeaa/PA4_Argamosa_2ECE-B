# EXPERIMENT 3 - Python Data Analysis

This is for my Programming Assignment 4 containing my codes for Experiment 4 - Data Wrangling and Visualization

**ECE BOARD EXAM PROBLEM**: Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given

**1**. Create the following data frames based on the format provided:

&emsp; a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant asInstrumentation and hometown Luzon

&emsp; b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

**2**. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?


# Codes *(Outputs can be seen in the PA4-Codes.ipynb file)*

## **ECE BOARD EXAM PROBLEM**

Access the Pandas Library and load the given file 'board2.xlsx'

Make sure the file is at the same folder as your notebook

```python
import pandas as pd

# load the excel file
df = pd.read_excel('board2.xlsx')
df

```
## *1a* - Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant asInstrumentation and hometown Luzon
```python
# store the needed data frame to Instru
# filter the 'Track' column with only instrumentation below it. The same goes for 'Hometown', which is Luzon
# pick out also the column of 'Electronics' containing grades > 70, 'Name', and 'GEAS'
Instru = df[(df['Track'] == 'Instrumentation')
            &(df['Hometown'] == 'Luzon')
            &(df['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']]
Instru
```
Save the file 
```python
# save the file as .xlsx
Instru.to_excel('Instru.xlsx', index = False)
```

## *1b* - Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female
```python
# create a different column for Average, computing for the mean of Math, Electronics, GEAS, and Communication
df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis = 1)

# store the needed data frame to Mindy
# just like what was done in 1A, filter out and pick the required parameters
Mindy = df[(df['Hometown'] == 'Mindanao')
            &(df['Gender'] == 'Female')
            &(df['Average'] >= 55)][['Name', 'Track', 'Electronics', 'Average']]
Mindy
```
Save the file 
```python
# save the file as .xlsx
Mindy.to_excel('Mindy.xlsx', index = False)
```

## *2*. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?
I divided it into three barplots

1. Average grade by Hometown
```python
# FIGURE 1

import pandas as np
import matplotlib.pyplot as plt
import seaborn as sns

# create a bar plot regarding how Hometown contributes to the average
# declare the colors
color = ['#8D988d','#9AA0A3','#C1B1A6']
# configure the figure size
plt.figure(figsize=(6, 9))
# input the appropriate values for the barplot
sns.barplot(x='Hometown', y='Average', data=df, hue='Hometown', palette=color)
# rotate the variables in the x-axis for aesthetics and so that it would fit
plt.xticks(rotation = 45)

plt.show()
```
2. Average grade by college Track
```python
# FIGURE 2

import pandas as np
import matplotlib.pyplot as plt
import seaborn as sns

# create a bar plot regarding how the college track contributes to the average
# declare the colors
color = ['#016764','#014848','#00312F' ]
# configure the figure size
plt.figure(figsize=(9, 7))
# input the appropriate values for the barplot
sns.barplot(x = 'Track', y ='Average', data = df, hue ='Track', palette = color)
# rotate the variables in the x-axis for aesthetics and so that it would fit
plt.xticks(rotation = 45)

plt.show()
```
3. Average grade by Gender
```python
# FIGURE 3

import pandas as np
import matplotlib.pyplot as plt
import seaborn as sns

# create a bar plot regarding how the college track contributes to the average
# declare the colors
color = ['#9799BA','#FEADB9']
# configure the figure size
plt.figure(figsize=(6, 6))
# input the appropriate values for the barplot
sns.barplot(x='Gender', y='Average', data=df, hue='Gender', palette=color)
# rotate the variables in the x-axis for aesthetics and so that it would fit
plt.xticks(rotation = 45)

plt.show()
```
Conclusion for *Number 2*

After observing the figures above *(Figures 1,2 and 3)*, it can be said that Hometown, Track, and Gender have significant effects on the average. In *Figure 1*, it is observed that exam takers who live in Luzon have the highest average grade, then followed by those who live in Mindanao. Lastly are those that live in Visayas. When it comes to their Track *(Figure 2)*, it can be seen that the track that got the highest average grade is Communication, followed by Microelectronics, and lastly, Instrumentation. For Gender *(Figure 3)*, it can be seen that the Male gender obtained a higher grade average than the Female gender.


## The experiment is focused on Data Wrangling and Data Visualization. If there are any problems, inquiries, or recommendations about the experiment, please to let me know!
# Author
Argamosa, Gabriel Ian E.




