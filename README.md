# 🚗 Fuel Economy Data Exploration and Analysis with Pandas

This project explores fuel economy data of various car models using **Pandas** in **Python** and executed via **Google Colab**. It focuses on DataFrame creation, transformation, filtering, and performing insightful statistical operations on real-world data.
---

## 📘 Project Overview

This notebook-based project introduces you to working with structured datasets using `pandas`.It guides learners through reading data, selecting columns, computing new variables, and filtering with boolean logic.
The dataset includes **234 car models** with various specifications such as engine displacement, fuel type, drive, and city/highway mileage. This exercise demonstrates foundational data manipulation skills with a focus on fuel economy, subcompact identification, and transmission types.

---

## 🎯 Objectives

* 📥 Import and explore a dataset using Pandas
* 🔍 Select and summarize relevant columns
* 📊 Calculate new columns such as average mileage
* ✅ Use Boolean masks to filter and count specific observations
* 🧹 Perform basic data cleaning and transformations

---

## 🛠️ Tools Used

| Tool                | Purpose                                      |
| ------------------- | -------------------------------------------- |
| **Python** 🐍       | Programming language                         |
| **Pandas** 📊       | Data analysis and manipulation               |
| **Google Colab** 💻 | Cloud-based development and notebook sharing |

---

## 📊 Dataset Overview

* **Name**: `mpg.csv`
* **Rows**: 234
* **Columns**: 11

  * `manufacturer`, `model`, `displ`, `year`, `cyl`, `trans`, `drv`, `cty`, `hwy`, `fl`, `class`

Each row represents a vehicle with its specifications and fuel economy stats.

---

## 🧠 Key Steps & Code Examples

### 1️⃣ Load and Inspect the Dataset


```python
```
![image](https://github.com/user-attachments/assets/696be008-f7ce-4067-af64-d3f3770db095).

import pandas as pd
mpg = pd.read_csv("mpg.csv")
```

mpg.tail(3)
```
  ![image](https://github.com/user-attachments/assets/327a1617-1110-4cfa-9fd6-6a0f8faf2a64)

---

### 2️⃣ Select Specific Columns

```python
columns_of_interest = ["displ", "cty", "hwy"]
mpg[columns_of_interest].head()
```
  ![image](https://github.com/user-attachments/assets/05b836ef-ee4e-4ca7-9c50-202568064512)

---

### 3️⃣ Compute Average Mileage

```python
mpg[["cty", "hwy"]].mean(axis=0)
```
  ![image](https://github.com/user-attachments/assets/b9b4aef8-a9da-492a-9ca5-089dd4ffac2c)

---

### 4️⃣ Frequency Count of Cylinders

```python
mpg.cyl.value_counts()
```
![image](https://github.com/user-attachments/assets/bd9d4a55-f2fc-4ece-81a3-cb4d878ede19)

---

### 5️⃣ Boolean Filtering: How Many Audis?

```python
(mpg.manufacturer == "audi").sum()
```
![image](https://github.com/user-attachments/assets/3976dae4-321b-488d-a850-dedd58032941)


---

## 🧾 Key Results

* ✅ **Average mileage column** created successfully
* ✅ Count of specific brands (like `audi`) calculated using boolean series
* ✅ Dataset insights obtained using `.value_counts()` and `.mean()`
* ✅ Created a clean and sorted DataFrame with relevant variables

---

## 🧠 Conclusion

This exercise demonstrated how Pandas makes it simple to:

* Import real-world data
* Transform and analyze DataFrames
* Use Boolean logic to filter and count
* Create new features like average mileage



## 🧪 Extended Task on mpg

### 1. Create a new column named is_automatic that holds a Boolean if that given vehicle is an automatic transmition or not.
mpg["is_automatic"] = mpg["trans"].str.contains("auto", case=False)
mpg
![image](https://github.com/user-attachments/assets/3af02dc8-15ca-475b-9b71-a6f00aeb9d10)

### 2. Use the is_automatic column to sum up the number of automatic vehicles in this dataset.

num_automatic =mpg["is_automatic"].sum()
num_automatic

![image](https://github.com/user-attachments/assets/41fd24d6-9a3c-4d2d-8e3e-6a0ffc0735c5)


### 3. Write the pandas code to determine what percentage of the vehicles are subcompacts?
are_subcompact = mpg["class"] == "subcompact"
percentage_subcompact = are_subcompact.mean()*100
percentage_subcompact

![image](https://github.com/user-attachments/assets/5e9b06b0-ed52-41a9-a8f7-fc9f730f638e)


### 4. Combined fuel economy is a weighted average of the city value by 55% and the highway value by 45%. Use arithmetic operators to add a new column named fuel_economy to the mpg dataframe.
mpg["fuel_economy"]=mpg["cty"]*0.55 + mpg["hwy"]*.45
mpg
![image](https://github.com/user-attachments/assets/079d2d17-b8fc-4b8d-a786-862614947dd7)


### 5. Use Boolean masking to find all of the vehicles with a fuel_economy above the median fuel_economy.
median_fe= mpg["fuel_economy"].median()
median_fe
![image](https://github.com/user-attachments/assets/74f4af94-b66a-4d56-bfe7-7670b9daf484)

mask=mpg["fuel_economy"]>median_fe
mask
![image](https://github.com/user-attachments/assets/63d5f719-8317-4895-bdef-725c68d17d27)


median_fe=mpg["fuel_economy"].median()
above_median_cars=mpg[mpg["fuel_economy"]>median_fe]
above_median_cars
![image](https://github.com/user-attachments/assets/4f2d36f4-6a69-44f6-b25f-3a6e136e4bb7)

---

## 📌 Conclusion

This hands-on exercise introduced multiple core capabilities of the Pandas library such as:

* Column selection & aggregation
* Creating calculated fields
* Boolean logic for filtering
* Counting and grouping operations

These foundational techniques are essential for any data analysis task using Python.

---

