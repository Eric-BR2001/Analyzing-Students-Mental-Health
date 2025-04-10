# Analyzing Students' Mental Health

![Illustration of silhouetted heads](mentalhealth.jpg)

## Project Overview
This project investigates whether attending university in a different country affects mental health. The analysis examines data from a Japanese international university's 2018 survey, focusing on:
- Mental health risks for international vs domestic students
- Impact of social connectedness on depression
- Relationship between acculturative stress and mental health
- How length of stay influences these factors

## Dataset Background
The data comes from a published study (2019) approved by ethical and regulatory boards. Key findings from the original study:
- International students have higher mental health risks than general population
- Social connectedness and acculturative stress predict depression

## Data Structure
The `students` table contains the following columns:

| Field Name      | Description                                      |
|-----------------|--------------------------------------------------|
| `inter_dom`     | Student type (International/Domestic)           |
| `japanese_cate` | Japanese language proficiency                   |
| `english_cate`  | English language proficiency                    |
| `academic`      | Academic level (Undergraduate/Graduate)         |
| `age`           | Current age of student                          |
| `stay`          | Length of stay in years                         |
| `todep`         | Depression score (PHQ-9 test)                   |
| `tosc`          | Social connectedness score (SCS test)           |
| `toas`          | Acculturative stress score (ASISS test)         |

## Key Analyses

### 1. View Raw Data
```sql
SELECT * 
FROM students;
```

### 2. Length of Stay Analysis for International Students
```sql
SELECT stay,
       count(stay) as count_int,
       ROUND(avg(todep),2) as average_phq,
       ROUND(avg(tosc),2) as average_scs,
       ROUND(avg(toas),2) as average_as
FROM students 
WHERE inter_dom='Inter' 
GROUP BY stay 
ORDER BY stay desc;
```

This query examines how length of stay affects:

Depression levels (PHQ-9)

Social connectedness (SCS)

Acculturative stress (ASISS)