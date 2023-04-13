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

