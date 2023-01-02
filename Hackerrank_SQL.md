Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than  and less than . Truncate your answer to  decimal places.
Input Format

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |


where LAT_N is the northern latitude and LONG_W is the western longitude.

My answer:
```
select round(sum(LAT_N),4)
FROM STATION
where LAT_N BETWEEN 38.7880 AND 137.2345;
```