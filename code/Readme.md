# Code
- The Python code processes a dataset named "heart.csv" using the pandas library. The dataset contains information related to heart health, including attributes such as age, sex, chest pain type, and various medical measurements. The script extracts specific columns from the dataset and transforms the data into a JSON format, which is then saved in a file named "data.json." The code iterates through the rows of the dataset, creating a list of dictionaries, with each dictionary representing an individual's health record. The generated JSON file can be utilized for further analysis or data sharing. To enhance readability, consider adding comments to describe each section of the code, explaining its purpose and functionality. Additionally, provide information on how to interpret the resulting JSON structure and its potential applications.
```
# Import necessary libraries
import pandas as pd
import json

# Read the CSV file into a DataFrame
df = pd.read_csv("heart.csv")

# Display the first few rows of the DataFrame
df_head = df.head()

# Uncomment the following lines to display summary statistics and information about the DataFrame
# df.describe()
# df.info()

# Select specific columns for processing
temp = ["Age", "Sex", "ChestPainType", "RestingBP", "Cholesterol", "FastingBS", 
        "RestingECG", "MaxHR", "ExerciseAngina", "Oldpeak", "ST_Slope", "HeartDisease"]

# Create an empty list to store dictionaries
temp1 = []

# Loop through each row in the DataFrame
for i in range(len(df)):
    # Create a dictionary for each row with selected columns
    record_dict = {
        temp[0]: int(df["Age"][i]),
        temp[1]: df["Sex"][i],
        temp[2]: df["ChestPainType"][i],
        temp[3]: int(df["RestingBP"][i]),
        temp[4]: int(df["Cholesterol"][i]),
        temp[5]: int(df["FastingBS"][i]),
        temp[6]: df["RestingECG"][i],
        temp[7]: int(df["MaxHR"][i]),
        temp[8]: df["ExerciseAngina"][i],
        temp[9]: int(df["Oldpeak"][i]),
        temp[10]: df["ST_Slope"][i],
        temp[11]: int(df["HeartDisease"][i])
    }
    # Append the dictionary to the list
    temp1.append(record_dict)

# Write the list of dictionaries to a JSON file
with open("data.json", "w") as f:
    json.dump(temp1, f)
```
