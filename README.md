# Data-Center
Data center for CSPP, to provide all meta data for the product

# India Location Master Data for CSPP

## Overview

This repository contains the master location data used by the **CSPP (Computer Science Professional Passport)** platform.

The data is derived from the **Government of India Local Government Directory (LGD)** and transformed into a simplified, developer-friendly JSON structure for use in CSPP applications.

The dataset is optimized for:

- Student Registration
- IT Professional Registration
- Company Registration
- College Registration
- Search & Filtering
- Analytics
- Location-based Recommendations

---

# Directory Structure

```
Data-Center/
│
├── states.json
├── districts.json
├── cities.json
└── README.md
```

---

# Data Hierarchy

```
India
│
├── State
│     │
│     ├── District
│     │      │
│     │      ├── City / Sub District
│     │
│     └── ...
│
└── ...
```

Example

```
India
└── Tamil Nadu
      └── Madurai
             └── Madurai
```

---

# Files

## 1. states.json

Contains all **28 States** and **8 Union Territories**.

### Structure

```json
{
  "state_code": 17,
  "state_name": "Meghalaya",
  "cspp_code": "CSPP-STATE-00017"
}
```

### Fields

| Field | Type | Description |
|--------|------|-------------|
| state_code | Number | Official LGD State Code |
| state_name | String | State Name in English |
| cspp_code | String | CSPP Generated State Identifier |

### Example CSPP Code

```
CSPP-STATE-00017
```

---

## 2. districts.json

Contains all districts mapped to their respective states.

### Structure

```json
{
  "state_code": 32,
  "district_code": 554,
  "district_name": "Alappuzha",
  "cspp_code": "CSPP-DISTRICT-00554"
}
```

### Fields

| Field | Type | Description |
|--------|------|-------------|
| state_code | Number | Parent State Code |
| district_code | Number | Official LGD District Code |
| district_name | String | District Name |
| cspp_code | String | CSPP District Identifier |

### Example CSPP Code

```
CSPP-DISTRICT-00554
```

---

## 3. cities.json

Contains all cities (LGD Sub Districts) mapped to their districts.

### Structure

```json
{
  "state_code": 8,
  "district_code": 783,
  "city_code": 7140,
  "city_name": "Aandhi",
  "cspp_code": "CSPP-CITY-07140"
}
```

### Fields

| Field | Type | Description |
|--------|------|-------------|
| state_code | Number | Parent State Code |
| district_code | Number | Parent District Code |
| city_code | Number | Official LGD Sub District Code |
| city_name | String | City / Town Name |
| cspp_code | String | CSPP City Identifier |

### Example CSPP Code

```
CSPP-CITY-07140
```

---

# CSPP Code Format

## States

```
CSPP-STATE-00017
```

Pattern

```
CSPP-STATE-{StateCode(5 Digits)}
```

---

## Districts

```
CSPP-DISTRICT-00554
```

Pattern

```
CSPP-DISTRICT-{DistrictCode(5 Digits)}
```

---

## Cities

```
CSPP-CITY-07140
```

Pattern

```
CSPP-CITY-{CityCode(5 Digits)}
```

---

# Relationships

```
State
   │
   ├── state_code
   │
   ▼

District
   │
   ├── state_code
   ├── district_code
   │
   ▼

City
   │
   ├── state_code
   ├── district_code
   ├── city_code
```

Example

```
Tamil Nadu (33)

        │

Madurai District (596)

        │

Madurai City (5749)
```

---

# Usage

## Student Registration

```
Select State
      ↓
Select District
      ↓
Select City
```

---

## IT Professional Registration

```
State
District
City
```

---

## College Registration

```
State
District
City
```

---

## Company Registration

```
State
District
City
```

---

# Benefits

- Standardized location hierarchy
- No duplicate location names
- Easy filtering
- Optimized for MongoDB
- Optimized for PostgreSQL
- Optimized for MySQL
- Supports cascading dropdowns
- Easy search by State, District, and City
- Consistent CSPP identifiers
- Based on official Government of India LGD codes

---

# Data Source

This dataset is derived from the **Local Government Directory (LGD)** published by the **Government of India** and transformed into a simplified JSON format for use within the CSPP platform.

Official Source:

https://lgdirectory.gov.in/

---

# License

This transformed dataset is intended for use within the CSPP platform. The original administrative data is sourced from the Government of India's Local Government Directory (LGD). Please refer to the LGD portal for the applicable licensing and usage terms.
