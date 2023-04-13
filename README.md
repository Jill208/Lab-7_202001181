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


Based on these boundary test cases, we can design the following test cases:

| Tester Action and Input Data |	Expected Outcome |
|------------------------------|---------------------|
|Valid input: day=1, month=1, year=1900|	Invalid date|
|Valid input: day=31, month=12, year=2015|	Previous date|
|Invalid input: day=0, month=6, year=2000|	An error message|
|Invalid input: day=32, month=6, year=2000|	An error message|
|Invalid input: day=29, month=2, year=2000|	An error message|
|Valid input: day=1, month=6, year=2000|	Previous date|
|Valid input: day=31, month=5, year=2000|	Previous date|
|Valid input: day=15, month=6, year=2000|	Previous date|
|Invalid input: day=31, month=4, year=2000|	An error message|


Program 1: The function linearSearch searches for a value v in an array of integers a. If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.

```
int linearSearch(int v, int a[])
{
    int i = 0;
    while (i < a.length)
    {
        if (a[i] == v)
        return(i);
        i++;
    }
    return (-1);    
}

@Test
public void test() {
    unittesting obj = new unittesting();
    int[] arr1 = {2, 4, 6, 8, 10};
    int[] arr2 = {-3, 0, 3, 7, 11};
    int[] arr3 = {1, 3, 5, 7, 9};
    int[] arr4 = {};
    
    assertEquals(0, obj.linearSearch(2, arr1));
    assertEquals(4, obj.linearSearch(10, arr1));
    assertEquals(-1, obj.linearSearch(3, arr2));
    assertEquals(4, obj.linearSearch(9, arr3));
    assertEquals(-1, obj.linearSearch(2, arr4));
}
```
Equivalence Partitioning:

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
|v is present in a|	Index of v|
|v is not present in a|	-1|

Boundary Value Analysis:

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
|Empty array a|	-1|
|v is present at the first index of a|	0|
|v is present at the last index of a length of a|	a-1|
|v is not present in a|	-1|

Test suites:

| Tester Action and Input Data | Value to be found | Expected Outcome |
|------------------------------|-------------------|------------------|
|Valid partition:		       |                   |                  |
| [1, 2, 3, 4, 5] |	3 |	2|
|[5, 10, 15, 20, 25]	|5|	0|
|[2, 4, 6, 8]	|5	|-1|
|[1, 3, 5, 7]	|4	|-1|
|Boundary Value Analysis:	|  | |	
|[]	|5|	-1|
|[5]|	5|	0|
|[15]|	5|	-1|
|[5, 10, 15, 20, 25]|	5|	0|
|[5, 10, 15, 20, 25]|	25|	4|
|[2, 4, 6, 8]|	2.2	|Invalid input|
|[2, 4, 6, 8]|	a	|Invalid input|
|[1.1, c, 5, 7]|	2|	Invalid input|


Program 2: The function countItem returns the number of times a value v appears in an array of integers a.

```
int countItem(int v, int a[])
{
    int count = 0;
    for (int i = 0; i < a.length; i++)
        {
            if (a[i] == v)
            count++;
        }
    return (count);
}

public void testCountItem() {
    CountItems counter = new CountItems();
    int[] arr1 = {1, 2, 3, 4, 5};
    int[] arr2 = {1, 2, 3, 4, 5, 6, 7, 8, 9};
    int[] arr3 = {1, 2, 3, 4, 4, 4, 5, 6, 7, 8, 9};
    int[] arr4 = {};
    int v1 = 3;
    int v2 = 10;
    assertEquals(1, counter.countItem(v1, arr1));
    assertEquals(0, counter.countItem(v2, arr1));
    assertEquals(9, counter.countItem(v1, arr2));
    assertEquals(0, counter.countItem(v2, arr2));
    assertEquals(1, counter.countItem(v1, arr3));
    assertEquals(0, counter.countItem(v2, arr3));
    assertEquals(0, counter.countItem(v2, arr4));
}
```

Equivalence Partitioning:

|Tester Action and Input Data|	Expected Outcome|
|----------------------------|------------------|
|v is present in a|	Number of times v appears in a|
|v is not present in a|	0|

Boundary Value Analysis:

|Tester Action and Input Data|	Expected Outcome|
|----------------------------|------------------|
|Empty array a|	0|
|v is present once in a|	1|
|v is present multiple times in a|	Number of times v appears in a|
|v is not present in a|	0|

Test suites:

|Tester Action and Input Data|	Value to be found|	Expected Outcome|
|----------------------------|-------------------|------------------|
|Equivalence partition:		| | |
|[1, 2, 3, 4, 5]	3	1
|[5, 10, 15, 20, 25]	11	0
|Boundary Value Analysis: | | |		
|[]	|5|	0|
|[5]	|5|	1|
|[15]	|5	|0|
|[5, 10, 5, 20, 25]	|5|	2|
|[2, 4, 6, 8]|	2.2|	Invalid input|
|[2, 4, 6, 8]|	|a	|Invalid input|
|[3.3, r, 5, 7]|	2|	Invalid input|
