# PA4 - Data Wrangling and Data Visualization
##### This repository includes Python code to solve a programming problem titled "ECE Board Exam Problem." The solution utilizes data wrangling and data visualization to analyze the provided dataset.

##### The code preview is available below, and you can find a detailed Jupyter notebook in the files section.

## ECE Board Exam Problem
### Overview
* Using data wrangling and visualization, the task is to analyze the dataset and create various (i) data frames and (ii) visualizations to tell a compelling story.

### What to do?
* DataFrame 1: Instru = ["Name", "GEAS", "Electronics >70"] with the track set to Instrumentation and hometown to Luzon.
* DataFrame 2: Mindy = ["Name", "Track", "Electronics", "Average >=55"] with hometown set to Mindanao and gender to Female.

### Data Frame Creation: 
* This task involves creating specific data frames by filtering a larger dataset. It focuses on students from particular tracks, hometowns, or genders who meet certain academic criteria. This approach makes it easier to analyze and understand specific groups within the data.

### Code Implementation and its Output
``` python
import pandas as pd
```

``` python
# Load the data from the Excel
board = pd.read_excel('board2.xlsx')
board
```

<img width="422" alt="Screenshot 2024-09-19 at 10 33 45 AM" src="https://github.com/user-attachments/assets/55e19c5a-b39f-4d0e-bb98-5c736c75413f">


``` python
# Filter rows where 'Track' is 'Instumentation') & 'Hometown' is 'Luzon', and 'Electronics' sore is above 70.
Instru = board[(board['Track'] == 'Instrumentation') 
        & (board['Hometown'] == 'Luzon') 
        & (board['Electronics'] > 70)]


# Select and display the relevant columns: 'Name', 'GEAS', 'Electronics' 
Instru [['Name', 'GEAS', 'Electronics']]
```

<img width="221" alt="Screenshot 2024-09-19 at 10 34 18 AM" src="https://github.com/user-attachments/assets/ad50d219-e67b-4ce1-b303-f4e97085e31c">


``` python
# Filter rows where 'Hometown' is 'Mindanao' & 'Gender' is 'Female'
Mindy = board[(board['Hometown'] == 'Mindanao') 
        & (board['Gender'] == 'Female')].copy()

# Calculate for the average of 'Math', 'Electronics', 'GEAS', and 'Communication' for each row.
Mindy['Average'] = Mindy[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

# Simply keep the rows where the calculate average is 55 or above
Mindy = Mindy[Mindy['Average'] >= 55]

# Select and print the relevant columns: 'Name', 'Track', 'Electronics', and 'Average'.
Mindy[['Name', 'Track', 'Electronics', 'Average']]
```

<img width="343" alt="Screenshot 2024-09-19 at 10 34 42 AM" src="https://github.com/user-attachments/assets/6dadc976-f14d-4c14-90a5-94dc84ef7ba1">

## Data Visualization
* The goal is to create a visualization that shows how various factors, such as college track, gender, and hometown, affect students' average grades. The analysis aims to see how each of these factors affects students' grades.

### What to do? 
* Develop a visualization showcasing how the different features affect the average grade. Analyze whether factors such as chosen track, gender, or hometown influence a higher average score.

### Code Implementation and its Output

#### Gender Bar Chart:
* The bar chart below displays the average scores for male and female students, allowing for a comparison of their performance. This chart shows if one gender generally performs better than the other.

``` python
# Use matplotlib.pyplot library as it is required to make different graphs
import matplotlib.pyplot as plt

# Calculate the average score for each student (on the fly)
board['Average'] = board[['Math', 'GEAS', 'Electronics', 'Communication']].mean(axis=1)

# Create a bar plot for Average Score by Gender
plt.figure(figsize=(10, 4))  # Set the size of the figure
plt.bar(board['Gender'], board['Average'])  # Plot the average scores calculated above
plt.title('Average Score by Gender')  # Add a title
plt.xlabel('Gender')  # Label the x-axis
plt.ylabel('Average Score')  # Label the y-axis
plt.show()  # Display the plot

```
<img width="643" alt="Screenshot 2024-09-19 at 10 36 47 AM" src="https://github.com/user-attachments/assets/2e086b4e-fbb8-4c16-bd59-c1b772e33a91">

#### Track (College) Bar Chart:
* The bar chart below shows the average scores across different academic tracks, such as Instrumentation, Communication, and Electronics. This chart allows for an easy comparison of student performance in various fields and can reveal if certain tracks tend to have higher or lower average scores. 

``` python
#Create a bar plot for Average Score by Track
plt.figure(figsize=(10, 4))  #Set figure size
plt.bar(board['Track'], board['Average'])  #Plot average scores with Track on x-axis
plt.title('Average Score by Track')  #Add title
plt.xlabel('Track')  #Label x-axis
plt.ylabel('Average Score')  #Label y-axis
plt.tight_layout()  #Adjust layout to prevent clipping
plt.show()  #Display the plot
```
<img width="648" alt="Screenshot 2024-09-19 at 10 37 32 AM" src="https://github.com/user-attachments/assets/db05a6c4-9039-46d4-9d84-a03cee8f3b67">

#### Hometown Bar Chart:
* The bar chart below illustrates the average scores for students from different regions (Visayas, Luzon, Mindanao). It helps to see how performance varies by location, showing if students from a particular region tend to score higher on average than those from other areas.
```python
#Create a bar plot for Average Score by Hometown
plt.figure(figsize=(10, 4))  #Set figure size
plt.bar(board['Hometown'], board['Average'])  #Plot average scores with Hometown on x-axis
plt.title('Average Score by Hometown')  #Add title
plt.xlabel('Hometown')  #Label x-axis
plt.ylabel('Average Score')  #Label y-axis
plt.tight_layout()  #Adjust layout to prevent clipping
plt.show()  #Display the plot
```
<img width="655" alt="Screenshot 2024-09-19 at 10 38 01 AM" src="https://github.com/user-attachments/assets/e05322b8-f730-44ff-b577-19d1fec5a7a1">

### Data Observation
* Female students generally achieve higher average grades than male students.
* Microelectronics students have the highest average grades, with Communication next, and Instrumentation students have the lowest.
* Luzon students show the highest average grades, followed by Visayas, while Mindanao students have the lowest average grades.

# Author
### Ginger Fiona R. Ignacio
### 2ECE-B










