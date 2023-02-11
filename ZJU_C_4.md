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
    struct date today;
    today = (struct date){07,31,2014};
    struct date day;
    day = today;
    struct date thismonth = {.month = 7, .year=2014};
    printf("Today's date is %i-%i-%i.\n",today.year,today.month,today.day);
    printf("This month is %i-%i-%i.\n",thismonth.year,thismonth.month,thismonth.day);
}
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

```
struct date{
int month;
int day;
int year;
}myday;

struct date *p = &myday;
(*p).month = 12;
p->month = 12;
```
#### 自定义数据类型

Length就是int的别名
```
typedef int Lenth;
```

Union联合
===


```
#include <stdio.h>

typedef union{
    int i;
    char ch[sizeof(int)];
}CHI;

int main(int argc, char const *argv[])
{
    CHI chi;
    int i;
    chi.i = 1234;
    for(i=0;i<sizeof(int);i++){
        printf("%02hhX",chi.ch[i]);
    }
    printf("\n");
    return 0;
}
```

static静态本地变量
===

#### 实际上是特殊的全局变量，位于相同的内存区域，具有全局的生存期
```
#include <stdio.h>
#include <string.h>

int f(void);

int gAll = 12;

int main(int argc, char const *argv[])
{
    f();
    f();
    f();
    return 0;
}

int f(void)
{
    int k = 0;
    
    //这里加static和不加是有区别的
    static int all  = 1;
    
    printf("&gAll=%p\n",&gAll);
    printf("&all=%p\n",&all);
    printf("&k=%p\n",&k);
    
    printf("in f all  = %d\n",all);
    all += 2;
    printf("agn in f all = %d\n",all);
    
    return all;
}
```

#### 返回指针的函数
返回本地变量的地址是危险的

返回全局变量或静态本地变量的地址是安全的

返回在函数内malloc的内存是安全的，但容易造成问题

最好的做法是返回传入的指针
