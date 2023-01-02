
#Weather Observation Station 13

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
select truncate(cast(sum(LAT_N) AS decimal(18,4)),4)
FROM STATION
where LAT_N BETWEEN 38.7880 AND 137.2345;
```
为什么这里用truncate和round最后出来都是8位小数呢 T-T

问题解决了，但我不理解为什么4需要出现2次，以及18的作用是啥？


#Weather Observation Station 15

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than . Round your answer to  decimal places.

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

···
select truncate(cast(LONG_W AS decimal(18,4)),4)
FROM STATION
where LAT_N =
(SELECT max(LAT_N) 
from STATION
where LAT_N < 137.2345);
···
为什么结果不对呢……
