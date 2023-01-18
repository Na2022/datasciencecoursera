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
#输入正整数key，找出key在数组a中的位置，如找不到则返回-1
key：要寻找的数字
a：作为寻找范围的数组
length：数组a的长度
```
#include <stdio.h>

int search(int key, int a[],int length)
{
    int ret = -1;
    int i;
    for(i=0;i<length;i++)
    {
        if(a[i] == key)
        {
            ret = i;
            break;
        }
    }
    return ret;
}

int main()
{
    int a[]={2,4,6,8,10,12,14,16,18,20,22,24,26,28,30};
    int x;
    int loc;
    printf("Enter the key:\n");
    scanf("%d",&x);
    loc = search(x,a,sizeof(a)/sizeof(a[0]));
    printf("x=%d loc=%d\n",x,loc);
    if(loc != -1)
    {
        printf("%d在第%d个位置上",x,loc);
    }
    else printf("%d不存在当前数组中",x);
}
```

#构造素数表：
令x为2，
将2x、3x、4x直至ax<n的数标记为非素数，
零x为下一个没有被标记为非素数的数，重复上一步直至所有书都已经尝试完毕。
```
#include <stdio.h>
#include <math.h>

int IsPrime(int x,int knownPrimes[],int numberofKnownPrimes)
{
    int i, Prime = 1;
    for(i=0;i<numberofKnownPrimes;i++)
    {
        if(x%knownPrimes[i]==0)
        {
            Prime=0;
            break;
        }
    }
    return Prime;
}

int main()
{
    const int number =100;
    int prime[number];
    prime[0]=2;
    int count =1;
    int i=3;
    while(count<number)
    {
        if(IsPrime(i,prime,count))
        {
            prime[count++]=i;
        }
        i++;
    }
    for(i=0;i<number;i++)
    {
        printf("%d",prime[i]);
        if((i+1)%5) printf("\t");
        else printf("\n");
    }
    return 0;
}
```
