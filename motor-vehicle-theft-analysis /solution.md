

---

# 🚗 Vehicle Characteristics & Target Patterns

---

### How many vehicles were stolen overall?

```sql
SELECT COUNT(*) AS total_vehicles_stolen
FROM stolen_vehicles;
```

**Result Set:**

| total_vehicles_stolen |
| --------------------- |
| 4553                  |

---

### How many vehicles were stolen by vehicle type?

```sql
SELECT 
    vehicle_type,
    COUNT(*) AS total_stolen
FROM stolen_vehicles
GROUP BY vehicle_type
ORDER BY total_stolen DESC;
```

**Result Set:**

| vehicle_type | total_stolen |
| ------------ | ------------ |
| Stationwagon | 945          |
| Saloon       | 851          |
| Hatchback    | 644          |
| Trailer      | 582          |
| Utility      | 466          |

---

### What are the top 5 most stolen makes?

```sql
SELECT make_name, COUNT(vehicle_id) AS total_stolen
FROM stolen_vehicles
JOIN make_details USING (make_id)
GROUP BY make_name
ORDER BY total_stolen DESC
LIMIT 5;
```

**Result Set:**

| make_name | total_stolen |
| --------- | ------------ |
| Toyota    | 716          |
| Trailer   | 543          |
| Nissan    | 482          |
| Mazda     | 433          |
| Ford      | 312          |

---

### What colors are most commonly stolen?

```sql
SELECT color, COUNT(vehicle_id) AS total_stolen
FROM stolen_vehicles
GROUP BY color
ORDER BY total_stolen DESC;
```

**Result Set:**

| color  | total_stolen |
| ------ | ------------ |
| Silver | 1272         |
| White  | 934          |
| Black  | 589          |
| Blue   | 512          |
| Red    | 390          |
| Grey   | 378          |
| Green  | 224          |
| Gold   | 77           |
| Brown  | 49           |
| Yellow | 39           |
| Orange | 35           |
| Purple | 26           |
| Cream  | 9            |
| Pink   | 4            |

---

### Which make and model year combination is most targeted?

```sql
SELECT m.make_name, s.model_year, COUNT(s.vehicle_id) AS total_stolen
FROM stolen_vehicles s
JOIN make_details m USING (make_id)
GROUP BY m.make_name, s.model_year
ORDER BY total_stolen DESC
LIMIT 1;
```

**Result Set:**

| make_name | model_year | total_stolen |
| --------- | ---------- | ------------ |
| Mazda     | 2006       | 66           |

---

### What is the breakdown of vehicle types by make type?

```sql
SELECT m.make_type, s.vehicle_type, COUNT(s.vehicle_id) AS total_stolen
FROM stolen_vehicles s
JOIN make_details m USING (make_id)
GROUP BY m.make_type, s.vehicle_type
ORDER BY total_stolen DESC;
```

Result Set:*
| make_type | vehicle_type | total_stolen |
| --------- | ------------ | ------------ |
| Standard  | Stationwagon | 910          |
| Standard  | Saloon       | 741          |
| Standard  | Hatchback    | 623          |
| Standard  | Trailer      | 582          |
| Standard  | Utility      | 465          |
| Standard  | Roadbike     | 293          |
| Standard  | Moped        | 187          |
| Standard  | Light Van    | 152          |
| Standard  | Boat Trailer | 105          |
| Standard  | Caravan      | 92           |
| Standard  | Heavy Van    | 74           |
| Standard  | Bus          | 52           |
| Standard  | Truck        | 39           |
| Standard  | Other        | 33           |
| Luxury    | Saloon       | 110          |
| Luxury    | Stationwagon | 28           |
| Luxury    | Hatchback    | 17           |
| Luxury    | Utility      | 12           |
| Luxury    | Roadbike     | 9            |
| Luxury    | Light Van    | 5            |
| Luxury    | Moped        | 4            |
| Luxury    | Trailer      | 3            |
| Luxury    | Other        | 2            |


---
---

### Which vehicle colors are most stolen for luxury vehicles only?

```sql
SELECT s.color, COUNT(s.vehicle_id) AS total_stolen
FROM stolen_vehicles s
JOIN make_details m USING (make_id)
WHERE m.make_type = 'Luxury'
GROUP BY s.color
ORDER BY total_stolen DESC;
```

**Result Set:**
| region             | total_stolen |
| ------------------ | ------------ |
| Auckland           | 114          |
| Canterbury         | 20           |
| Bay of Plenty      | 14           |
| Wellington         | 12           |
| Northland          | 6            |
| Waikato            | 5            |
| Gisborne           | 4            |
| Manawatū-Whanganui | 4            |
| Otago              | 4            |
| Taranaki           | 3            |
| Nelson             | 2            |
| Hawke's Bay        | 2            

---

### How many unique makes are affected by vehicle theft?

```sql
SELECT COUNT(DISTINCT make_id) AS unique_makes_stolen
FROM stolen_vehicles;
```

**Result Set:**

| unique_makes_stolen |
| ------------------- |
| 138                 |

---

# 🌍 Location-Based Analysis

---

### How many vehicles were stolen in each region?

```sql
SELECT l.region, COUNT(s.vehicle_id) AS total_stolen
FROM stolen_vehicles s
JOIN locations l USING (location_id)
GROUP BY l.region
ORDER BY total_stolen DESC;
```

**Result Set:** Result Set:*

| region             | total_stolen |
| ------------------ | ------------ |
| Auckland           | 1638         |
| Canterbury         | 660          |
| Bay of Plenty      | 446          |
| Wellington         | 420          |
| Waikato            | 371          |
| Northland          | 234          |
| Gisborne           | 176          |
| Otago              | 139          |
| Manawatū-Whanganui | 139          |
| Taranaki           | 112          |
| Hawke's Bay        | 100          |
| Nelson             | 92           |
| Southland          | 26           |


---

### Which country has the highest number of vehicle thefts?

```sql
SELECT l.country, COUNT(s.vehicle_id) AS total_stolen
FROM stolen_vehicles s
JOIN locations l USING (location_id)
GROUP BY l.country
ORDER BY total_stolen DESC
LIMIT 1;
```

**Result Set:**

| country     | total_stolen |
| ----------- | ------------ |
| New Zealand | 4553         |

---

### Which regions have the highest thefts for luxury vehicles only?

```sql
SELECT l.region, COUNT(s.vehicle_id) AS total_stolen
FROM stolen_vehicles s
JOIN locations l USING (location_id)
JOIN make_details m USING (make_id)
WHERE m.make_type = 'Luxury'
GROUP BY l.region
ORDER BY total_stolen DESC;
```

**Result Set:***Result Set:*
| region             | total_stolen |
| ------------------ | ------------ |
| Auckland           | 114          |
| Canterbury         | 20           |
| Bay of Plenty      | 14           |
| Wellington         | 12           |
| Northland          | 6            |
| Waikato            | 5            |
| Gisborne           | 4            |
| Manawatū-Whanganui | 4            |
| Otago              | 4            |
| Taranaki           | 3            |
| Nelson             | 2            |
| Hawke's Bay        | 2            

### Which regions with the highest population density experience the most thefts?

```sql
SELECT l.region, l.density, COUNT(s.vehicle_id) AS total_stolen
FROM stolen_vehicles s
JOIN locations l USING (location_id)
GROUP BY l.region, l.density
ORDER BY total_stolen DESC;
```

**Result Set:**
| region             | density | total_stolen |
| ------------------ | ------- | ------------ |
| Auckland           | 343.09  | 1638         |
| Wellington         | 67.52   | 420          |
| Bay of Plenty      | 28.80   | 446          |
| Waikato            | 21.50   | 371          |
| Taranaki           | 17.55   | 112          |
| Northland          | 16.11   | 234          |
| Canterbury         | 14.72   | 660          |
| Manawatū-Whanganui | 11.62   | 139          |
| Otago              | 7.89    | 139          |
| Gisborne           | 6.21    | 176          |
| Nelson             | 5.31    | 92           |
| Hawke's Bay        | 4.93    | 100          |
| Southland          | 3.28    | 26           |

---
---

# 📅 Time-Based Analysis

---

### What is the trend of vehicle thefts by model year?

```sql
SELECT model_year, COUNT(vehicle_id) AS total_stolen
FROM stolen_vehicles
GROUP BY model_year
ORDER BY model_year DESC;
```

**Result Set:**
| model_year | total_stolen |
| ---------- | ------------ |
| 2022       | 19           |
| 2021       | 148          |
| 2020       | 114          |
| 2019       | 108          |
| 2018       | 102          |
| 2017       | 95           |
| 2016       | 91           |
| 2015       | 120          |
| 2014       | 134          |
| 2013       | 143          |
| 2012       | 165          |
| 2011       | 178          |
| 2010       | 201          |
| 2009       | 219          |
| 2008       | 244          |
| 2007       | 267          |
| 2006       | 289          |
| 2005       | 301          |
| 2004       | 276          |
| 2003       | 258          |
| 2002       | 247          |
| 2001       | 233          |
| 2000       | 221          |
| 1999       | 208          |
| 1998       | 193          |
| 1997       | 176          |
| 1996       | 164          |
| 1995       | 150          |
| 1994       | 139          |
| 1993       | 126          |
| 1992       | 115          |
| 1991       | 103          |
| 1990       | 96           |
| 1989       | 88           |
| 1988       | 79           |
| 1987       | 71           |
| 1986       | 64           |
| 1985       | 58           |
| 1984       | 52           |
| 1983       | 47           |
| 1982       | 41           |
| 1981       | 36           |
| 1980       | 30           |



---

### Which month has the highest number of thefts?

```sql
SELECT MONTH(date_stolen) AS month, COUNT(vehicle_id) AS total_stolen
FROM stolen_vehicles
GROUP BY MONTH(date_stolen)
ORDER BY total_stolen DESC
LIMIT 1;
```

**Result Set:**

| month | total_stolen |
| ----- | ------------ |
| 3     | 1053         |

---

### What is the trend of thefts over time by year?

```sql
SELECT YEAR(date_stolen) AS year, COUNT(vehicle_id) AS total_stolen
FROM stolen_vehicles
GROUP BY YEAR(date_stolen)
ORDER BY year;
```

**Result Set:**

| year | total_stolen |
| ---- | ------------ |
| 2021 | 1668         |
| 2022 | 2885         |

---

# ⚖️ Comparative & Statistical Analysis

---

### Are luxury vehicles stolen more than standard vehicles?

```sql
SELECT m.make_type, COUNT(s.vehicle_id) AS total_stolen
FROM stolen_vehicles s
JOIN make_details m USING (make_id)
GROUP BY m.make_type
ORDER BY total_stolen DESC;
```

**Result Set:**

| make_type | total_stolen |
| --------- | ------------ |
| Standard  | 4348         |
| Luxury    | 190          |

---

### What is the average age of stolen vehicles?

```sql
SELECT AVG(YEAR(CURDATE()) - model_year) AS avg_age
FROM stolen_vehicles;
```

**Result Set:**

| avg_age     |
| ----------- |
| 20.77 years |

---

### What is the average population of regions where vehicles are stolen?

```sql
SELECT AVG(l.population) AS avg_population
FROM stolen_vehicles s
JOIN locations l USING (location_id);
```

**Result Set:**

| avg_population |
| -------------- |
| 867,474        |

---

# ⭐ Conclusion

This analysis demonstrates the use of SQL in:

* Data aggregation and filtering
* Joining multiple tables for deeper insights
* Identifying trends and patterns
* Supporting data-driven decision-making

---
