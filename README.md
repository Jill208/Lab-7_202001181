# Lab-7_202001181

Section-A

Based on the input ranges, we can identify the following equivalence classes:
Equivalence Class Partitions
Day:

| Partition ID |  Range  | Status |
|--------------|---------|--------|
| E1 |  Between 1 and 28  | Valid |
| E2 |  Less than 1	  | Invalid |
| E3 |  Greater than 31	  | Invalid |
| E4 |  Equals 30	  | Valid for leap year |
| E5 |  Equals 29	  | Valid |
| E6 |  Equals 31	  | Valid |

Month:

| Partition ID |	Range |	Status |
|--------------|---------|--------|
|E7|	Between 1 and 12	|Valid|
|E8|	Less than 1	|Invalid|
|E9|	Greater than 12|	Invalid|

Year:

| Partition ID |	Range |	Status |
|--------------|---------|--------|
|E10|	Between 1900 and 2015|	Valid|
|E11|	Less than 1|	Invalid|
|E12|	Greater than 2015|	Invalid|


Equivalence Partitioning Test Cases:

| Tester Action and Input Data |	Expected Outcome |
|-----------------------------|--------------------|
|Valid input: day=1, month=1, year=1900 |	Invalid date|
|Valid input: day=31, month=12, year=2015|	Previous date|
|Invalid input: day=0, month=6, year=2000|	An error message|
|Invalid input: day=32, month=6, year=2000|	An error message|
|Invalid input: day=29, month=2, year=2001|	An error message|


Boundary Value Analysis: Using boundary value analysis, we can identify the following boundary test cases:

    (1) The earliest possible date: (1, 1, 1900)
    (2) The latest possible date: (31, 12, 2015)
    (3) The earliest day of each month: (1, 1, 2000), (1, 2, 2000), (1, 3, 2000),..., (1, 12, 2000)
    (4) The latest day of each month: (31, 1, 2000), (28, 2, 2000), (31, 3, 2000),..., (31, 12, 2000)
    (5) Leap year day: (29, 2, 2000)
    (6) Invalid leap year day: (29, 2, 1900)
    (7) One day before earliest date: (31, 12, 1899)
    (8) One day after latest date: (1, 1, 2016)

