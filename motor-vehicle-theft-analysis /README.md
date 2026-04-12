
---

# 🚗 Motor Vehicle Theft Analysis – SQL Project

---

## 📑 Table of Contents

## 📌 Introduction

## 📊 Dataset Description

## 🔍 Recommended Analysis

## 🛠 Approach

## 📋 List of Questions

## 🔗 Relevant Links
---

## 📌 Introduction

In this project, the objective is to analyze a **Motor Vehicle Theft dataset** using SQL to uncover patterns, trends, and key risk factors associated with vehicle theft.

The analysis focuses on:

* Identifying high-risk regions
* Understanding vehicle characteristics most targeted
* Analyzing theft trends over time
* Comparing vehicle categories (Luxury vs Standard)

The goal is to generate **data-driven insights** that can support decision-making in areas such as **security strategies, policy development, and crime prevention**.

---

## 📊 Dataset Description

This project uses a structured relational dataset consisting of **three main tables**:

### 📁 1. `stolen_vehicles`

Contains detailed records of stolen vehicles:

* `vehicle_id` – Unique identifier
* `vehicle_type` – Type of vehicle (e.g., Saloon, Hatchback)
* `make_id` – Foreign key linking to make details
* `model_year` – Year of manufacture
* `color` – Vehicle color
* `date_stolen` – Date of theft
* `location_id` – Foreign key linking to location

---

### 📁 2. `make_details`

Contains information about vehicle brands:

* `make_id` – Unique identifier
* `make_name` – Brand name (e.g., Toyota, Nissan)
* `make_type` – Classification (Luxury or Standard)

---

### 📁 3. `locations`

Contains geographic and demographic data:

* `location_id` – Unique identifier
* `region` – Region name
* `country` – Country name
* `population` – Regional population
* `density` – Population density

---

## 🔍 Recommended Analysis

### 🚗 Vehicle Analysis

* Identify most stolen vehicle types and makes
* Analyze vehicle characteristics (color, age, model year)
* Compare theft between luxury and standard vehicles

---

### 🌍 Location Analysis

* Determine regions with highest theft rates
* Analyze the impact of population and density
* Identify theft hotspots

---

### 📅 Time-Based Analysis

* Analyze theft trends by year and month
* Identify peak theft periods
* Evaluate seasonal patterns

---

### ⚖️ Comparative Analysis

* Compare theft across vehicle categories
* Identify high-risk vehicle segments

---

## 🛠 Approach

### 🔹 Data Preparation

* Imported CSV datasets into a relational database
* Created tables: `stolen_vehicles`, `make_details`, `locations`
* Verified data integrity and handled missing values

---

### 🔹 Data Transformation

* Performed joins across tables using foreign keys
* Derived new insights such as:

  * Vehicle age (`current year - model_year`)
  * Time-based features (month, year)

---

### 🔹 Exploratory Data Analysis (EDA)

* Used SQL queries to:

  * Aggregate theft counts
  * Identify trends and patterns
  * Compare categories
  * Generate meaningful insights

---

## 📋 List of Questions

### 🚗 Vehicle Characteristics & Target Patterns

* How many vehicles were stolen overall?
* How many vehicles were stolen by vehicle type?
* What are the top 5 most stolen makes?
* What colors are most commonly stolen?
* Which make and model year combination is most targeted?
* What is the breakdown of vehicle types by make type (Luxury or Standard)?
* How many unique makes are affected by vehicle theft?

---

### 🌍 Location-Based Analysis

* How many vehicles were stolen in each region?
* Which country has the highest number of vehicle thefts?
* Which regions have the highest thefts for luxury vehicles only?
* Which regions with the highest population density experience the most thefts?

---

### 📅 Time-Based Analysis

* What is the trend of vehicle thefts by model year?
* Which month has the highest number of thefts?
* What is the trend of thefts over time by year?

---

### ⚖️ Comparative & Statistical Analysis

* Are luxury vehicles stolen more than standard vehicles?
* What is the average age of stolen vehicles?
* What is the average population of regions where vehicles are stolen?

---


## 🔗 Relevant Links

🔗 **GitHub Repository:**
[https://github.com/Presh-Hub-pixel/motor-vehicle-theft-analysis](https://github.com/Presh-Hub-pixel/motor-vehicle-theft-analysis)

---

## 🤝 Contributing

Contributions are welcome!

If you'd like to improve this project:

* Fork the repository
* Make your changes
* Submit a pull request

---

## 📩 Support

If you have any questions, suggestions, or feedback:

**Rotimi Precious Eniola**
Data Analyst | SQL Developer | BI Enthusiast

📧 [rotimipreciousenny04@gmail.com](mailto:rotimipreciousenny04@gmail.com)
🔗 LinkedIn: Rotimi Precious Eniola

---

## ⭐ Support the Project

If this project helped you or inspired you:

👉 Please give it a **⭐ on GitHub**

---
