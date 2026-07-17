<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=28&pause=1000&color=E74C3C&center=true&vCenter=true&width=700&lines=911+Emergency+Calls+Analysis+%F0%9F%9A%A8;Powered+by+MongoDB+Atlas+%E2%98%81%EF%B8%8F;1.3+Million%2B+Records+Processed+%F0%9F%93%8A" alt="Typing SVG" />

![GitHub last commit](https://img.shields.io/github/last-commit/AbdulAzeemHashmi/911-Emergency-Analysis-Mongo-DB?color=E74C3C&style=for-the-badge)
![GitHub stars](https://img.shields.io/github/stars/AbdulAzeemHashmi/911-Emergency-Analysis-Mongo-DB?color=yellow&style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/AbdulAzeemHashmi/911-Emergency-Analysis-Mongo-DB?color=orange&style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=for-the-badge&logo=mongodb&logoColor=white)

</div>

---

## 🚨 Project Overview

This project focuses on the design, implementation, and analysis of a cloud hosted NoSQL database system built to process large scale 911 emergency call data. Using a dataset of over **1.3 million records** 📊 from Montgomery County, Pennsylvania, the system demonstrates efficient data ingestion and complex aggregation querying using **MongoDB Atlas** ☁️.

<div align="center">
<img src="https://user-images.githubusercontent.com/74038190/216122041-518ac897-8d92-4c6b-9b3f-ca01dcaf38ee.gif" width="450">
</div>

---

## 🧰 Tech Stack

<p>
<img src="https://img.shields.io/badge/Language-Python%203.x-3776AB?style=flat-square&logo=python&logoColor=white">
<img src="https://img.shields.io/badge/Database-MongoDB%20Atlas-47A248?style=flat-square&logo=mongodb&logoColor=white">
<img src="https://img.shields.io/badge/Library-Pandas-150458?style=flat-square&logo=pandas&logoColor=white">
<img src="https://img.shields.io/badge/Driver-PyMongo-4EA94B?style=flat-square&logo=mongodb&logoColor=white">
</p>

* 🐍 **Language:** Python 3.x
* ☁️ **Database:** MongoDB Atlas, Cloud NoSQL
* 📦 **Libraries:** Pandas for data pre processing, PyMongo as the database driver

---

## 🔄 Data Pipeline

### 1️⃣ Pre Processing 🧹

Before ingestion, the raw CSV data, `911.csv`, underwent two critical cleaning steps:

* 🏷️ **Type Extraction:** A custom function was used to split the `title` field, for example `EMS: BACK PAINS/INJURY`, to extract the primary categories: **EMS**, **Fire**, or **Traffic**.
* 🗺️ **Missing Data Handling:** To avoid bias in geographic analysis, missing ZIP code values were filled with the sentinel value `00000`, flagging incomplete location data without losing records.

### 2️⃣ Cloud Ingestion ⬆️

The structured documents were converted from Pandas DataFrames into JSON like dictionaries and inserted into a remote MongoDB Atlas cluster. The `insert_many()` bulk operation was utilized to handle the 1.3M+ records efficiently.

### 3️⃣ Database Schema 🗂️

Each incident is stored as a document with the following structure:

```json
{
  "timestamp": "2015-12-10 17:10:52",
  "type": "EMS",
  "location": {
    "lat": 40.2978759,
    "lng": -75.5812935,
    "addr": "REINDEER CT & DEAD END",
    "zip": "19525"
  },
  "description": "EMS: BACK PAINS/INJURY"
}
```

---

## 📈 Key Insights and Analytics

Six aggregation queries were executed against the live Atlas cluster to extract actionable insights:

| Query | Key Finding |
|---|---|
| 🚑 **Most Frequent Type** | **EMS** is the most common, accounting for roughly 50 percent, 665,384 calls |
| ⏰ **Peak Demand** | Emergency volume peaks at **5:00 PM**, 88,238 calls, likely tied to commute hours |
| 📍 **Priority Locations** | *SHANNONDELL DR and SHANNONDELL BLVD* recorded a staggering 14,570 incidents |
| ✅ **Data Quality** | The pipeline achieved **0 NULL records** in core fields, address and description |

<div align="center">
<img src="https://user-images.githubusercontent.com/74038190/212257454-16e3712e-945a-4ca2-b238-408f5f291aad.gif" width="400">
</div>

---

## 📁 Repository Structure

```
911-Emergency-Analysis-Mongo-DB/
├── 📄 24i2013_AbdulAzeem_A4.pdf   # Full technical report with visuals and conclusions
├── 🐍 task.py                     # Dataset loading, cleaning, and bulk ingestion
├── 🐍 queries.py                  # MongoDB Aggregation Framework logic
└── 📘 README.md                   # You are here
```

* 📝 `task.py` : Script for dataset loading, cleaning, and bulk ingestion
* 🔎 `queries.py` : Contains the MongoDB Aggregation Framework logic for the analytical queries
* 📄 `24i2013_AbdulAzeem_A4.pdf` : Full technical report including visual evidence and conclusions

---

## 🏃 How to Run

**Step 1 : Clone the repo**

```bash
git clone https://github.com/AbdulAzeemHashmi/911-Emergency-Analysis-Mongo-DB.git
```

**Step 2 : Install dependencies**

```bash
pip install pandas pymongo
```

**Step 3 : Setup MongoDB** 🔐

Update the connection string in `task.py` and `queries.py` with your Atlas credentials.
> ⚠️ Remember to remove your password before committing.

**Step 4 : Data** 📂

Place the `911.csv` file in the root directory.
> ⚠️ Ensure `911.csv` is added to your `.gitignore`, since it exceeds GitHub's 100MB file limit.

**Step 5 : Execute** ▶️

```bash
python3 task.py        # run data ingestion
python3 queries.py     # view analytical results
```

---

<div align="center">

## 👤 Submitted By

**Abdul Azeem** ([@AbdulAzeemHashmi](https://github.com/AbdulAzeemHashmi/))
Roll No : 24i 2013

<img src="https://img.shields.io/badge/Course-Database%20Systems-2E86DE?style=for-the-badge">
<img src="https://img.shields.io/badge/Submission%20Date-April%2030%2C%202026-black?style=for-the-badge">

<br><br>

<img src="https://user-images.githubusercontent.com/74038190/212257467-871d32b7-e401-42e8-a166-fcfd7baa4c6b.gif" width="100">

⭐ If you found this project helpful, consider giving it a star

</div>
