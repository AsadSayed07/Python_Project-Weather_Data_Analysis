# Python Project - Weather Data Analysis

## OVERVIEW
In this project, we will work on the "Weather Dataset", a time series data set with per-hour information about the weather conditions at a particular location. It covers an end-to-end process of understanding the dataset, uploading the file on **Jupyter Notebook** and using **Pandas** library for analysis .The primary goals of this project are to practice Pandas Library skills and generate valuable insights from the dataset.

## STEPS TAKEN TO DO THE PROJECT

### 1. DATA EXPLORATION
Before working on the dataset, it is important to understand the data thoroughly. The dataset contains attributes such as:
- `Date-Time`, `Temperature`, `Dew point temperature`, `Relative Humidity`, `Wind Speed`, `Visibility`, `Pressure`, and `Weather Conditions`.

### 2. UPLOADING THE CSV FILE
After seeing the attributes, I uploaded the CSV file to Jupyter Notebook.

### 3. IMPORTING 'PANDAS' LIBRARY
Imported the 'Pandas' Library for analysing the dataset and completing the project.
- This project includes 15 questions.

## 15 PROBLEMS SOLVED BELOW USING PANDAS

Q1. **Find all the unique "Wind Speed" Values in the data ?**
```sql
print("No. of unique values in 'Wind Speed km/hr':", df["Wind Speed_km/h"].nunique())
```
Q2. **Find the number of times when the "Weather" is "Exactly Clear"**
```vim
#Value Counts
print("The weather was clear", df["Weather Condition"].value_counts()["Clear"],"times")

#Filtering
print("The weather was clear",len(df[df["Weather Condition"] == "Clear"]),"times")

#Group by
print("The Weather was exactly clear",len(df.groupby("Weather").get_group("Clear")),"times")
```
Q3. **Find the number of times when the "Wind Speed" was exactly 4 km/hr.**
```vim
print("The Wind Speed was 4km/h,", len(df[df["Wind Speed_km/h"]==4]),"times")
```
Q4. **Find all the null values in the data.**
```vim
print(df.isnull().sum())
```
Q5. **Rename the column, "Weather" in the dataframe to "Weather Condition".**
```vim
df.rename(columns = {"Weather" : "Weather Condition"}, inplace = True)
df.head(2)
```
Q6. **What is the mean "Visibility"?**
```vim
print("The mean value of 'Visibility_km/h' is", df["Visibility_km"].mean().round(2))
```
Q7. **What is the standard deviation of "Pressure" in this data?**
```vim
print("The standard deviation of 'Pressure' is",df["Press_kPa"].std().round(2))
```
Q8. **What is the variance of "Relative Humidity" in this data?**
```vim
print("The Variance of 'Relative Humidity' is", df["Rel Hum_%"].var().round(2))
```
Q9. **Find all instances when snow was recorded**
```vim
#Method 1 : Value Counts
print("Snow was recorded",df["Weather Condition"].value_counts()["Snow"],"times")

#Method 2: Filtering
print("Snow was recorded",len(df[df["Weather Condition"]=="Snow"]),"times")

#Method 3: Group By
print("Snow was recorded", len(df.groupby("Weather Condition").get_group("Snow")), "times")

#Method 4 Str.contains
print("With 'str.contains' method, snow has been recorded",len(df[df["Weather Condition"].str.contains("Snow")]),"times, since it considers all the rows where snow is mentioned irrespective of other conditions along with it, for example: Freezing drizzle, Snow")
```
Q10. **Find all instances when "Wind Speed" is about 24 and "Visibility" is 25.**
```vim
s = len(df[(df["Wind Speed_km/h"] == 24) & (df["Visibility_km"] == 25)])
print("The above instance has occured", s, "times")
```
Q11. **What is the mean value of each column against each "Weather Condition"?**
```vim
s = df.groupby("Weather Condition").mean(numeric_only = True)
print("Following are the mean values of each column against each 'Weather Condition':","\n")
s
```
Q12. **What is the minimum and maximum value of each column against each "Weather Condition"?**
```vim
#Minimum
a = df.groupby("Weather Condition").min()
print("Following are the minimum values ofeach column against each weather condition:","\n")
a

#Maximum
b = df.groupby("Weather Condition").max()
print("Following are the maximum values ofeach column against each weather condition:","\n")
b
```
Q13. **Show all the record where weather condition is fog.**
```vim
a = df[df["Weather Condition"].str.contains("Fog")]
print("Below are all the records where weather condition was 'Fog':","\n")
a
```
Q14. **Find all instances when "Weather is clear" or "Visibility" is above 40**
```vim
a = df[(df["Weather Condition"] == "Clear") | (df["Visibility_km"] > 40)]
print("The following records show all the instances where the weather was clear and visibility was 40:","\n")
a
```
Q15. **Find all instances when:**
a) ***"Weather is Clear" and "Relative Humidity is greater than 50"***
**OR**
b) ***"Visibility" is above 40"***
```vim
s = df[((df["Weather Condition"] == "Clear") & (df["Rel Hum_%"] > 50)) | (df["Visibility_km"] > 40)]
print("Below records show the records where Weather condition is clear and Relative Humidity is greater than 50 or where visibility is greater than 40:","\n")
s
```




