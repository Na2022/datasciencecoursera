data type
===

#各数据类型的大小
```
#include <stdio.h>

int main()
{   printf("Size of char=%ld\n",sizeof(char));
    printf("Size of short=%ld\n",sizeof(short));
    printf("Size of int=%ld\n",sizeof(int));
    printf("Size of float=%ld\n",sizeof(float));
    printf("Size of double=%ld\n",sizeof(double));
    printf("Size of long double=%ld\n",sizeof(long double));

    return 0;
}
```
#输入输出字符
```
#include <stdio.h>

int main()
{
    char c;
    scanf("%c",&c);
    printf("c=%d\n",c);
    printf("c=%c\n",c);

    return 0;
}

//
scanf只能处理int类型数据，不能处理char
1
c=49
c=1

z
c=122
c=z

'
c=39
c='
```
```
#include <stdio.h>

int main()
{
    char c = 'm';
    printf("%c\n",c+1);

    return 0;
}
//c+1=n
```
**整数的输入输出

只有2种形式：int 或者long long

%d: int

%u: unsigned

%ld: long long

%lu: unsigned long long

```
#include <stdio.h>

int main()
{
    int a = 12, b = 012, c = 0x12;
    printf("%d %o %x\n",a,b,c);
    printf("%d %d %d\n",a,b,c);
    
}
//
12 12 12
12 10 18
```

#Bool data taype
```
#include <stdio.h>
#include <stdbool.h>

int main()
{
    bool b = 6 > 5;
    printf("%d",b);
}
```

#求和函数
```
#include <stdio.h>
void sum(int begin, int end)
{
    int i, sum = 0;
    for(i=begin;i<=end;i++)
    {
        sum += i;
    }
    printf("%d\n",sum);
}

int main()
{
    sum(1,50);
    sum(1,100);
    sum(1,1000);
}
```

#无返回的函数
```
#include <stdio.h>
void cheers()
{
    printf("Cheers!");
}

int main()
{
    cheers();
}
```
#有返回数值的函数

***为什么main没有输出呢。。。***

```
#include <stdio.h>
int isPrime(int x)
{
    int i,isPrime=1;
    for(i=2;i<x;i++)
    {
        if(x%i==0)
        {
            isPrime = 0;
            break;
        }
    }
    return isPrime;
}

int main()
{
   isPrime(1);
   isPrime(2);
   isPrime(3);
}
```

数组
===

#读入一个以-1结尾的数组，输出平均值及所有大于平均值的数字
```
#include <stdio.h>

int main()
{
    int x;
    double sum = 0;
    int count = 0;
    int number[100];
    scanf("%d",&x);
    while(x != -1)
    {
        number[count] = x;
        sum += x;
        count ++;
        scanf("%d",&x);
    }
    if(count > 0)
    {
        printf("%f\n",sum/count);
        int i;
        for(i=0;i<count;i++)
        {
            if(number[i]>sum/count)
            {
                printf("%d\n",number[i]);
            }
        }
    }
}

```

#输入数量不确定的[0,9]范围内的整数，统计每一种数字出现的次数，输入-1表示结束
```
#include <stdio.h>

int main()
{
    int x, i=0;
    const int number = 10;
    int count[number]={0};

    scanf("%d",&x);
    while(x != -1)
    {
        count[x]++;
        scanf("%d",&x);
    }
    for(i=0;i<number;i++)
    {
        printf("%d:%d\n",i,count[i]);
    }
}

```
