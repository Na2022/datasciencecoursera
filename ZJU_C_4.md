Enumerate枚举
===
用户定义的数据类型，关键字enum
enum 枚举类型名字{名字0，……，名字n}；


Structure
===
结构的成员不必是同类型

可以对整个结构做赋值、取地址、传递给函数参数
```
p1=(struct point){5,10};
相当于p1.x=5;p1.y=10.
```

```
p1=(struct point){5,10};
相当于p1.x=5;p1.y=10.
```

定义结构
```
p1=p2;
相当于p1.x=p2.x;p1.y=p2.y;
```

或者定义两个结构：
```
struct{
int x;
int y;
}p1,p2;
```

```
#include <stdio.h>
#include <string.h>

struct date{
    int month;
    int day;
    int year;
};

int main(int argc, char const *argv[])
{    
    struct date today = {07,31,2014};
    struct date thismonth = {.month = 7, .year=2014};
    printf("Today's date is %i-%i-%i.\n",today.year,today.month,today.day);
    printf("This month is %i-%i-%i.\n",thismonth.year,thismonth.month,thismonth.day);
}
```
