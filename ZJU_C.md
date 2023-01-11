#时差计算器
```
#include <stdio.h>

int main()
{
    int hour1, minute1;
    int hour2, minute2;
    
    scanf("%d %d",&hour1,&minute1);
    scanf("%d %d",&hour2,&minute2);
    
    int ih = hour2-hour1;
    int im = minute2 - minute1;
    
    if(im<0)
    {
        im+=60;
        ih--;
    }
    printf("时间差为%d小时%d分钟",ih,im);
}
```

#找零计算器
```
#include <stdio.h>
int main()
{
    int price, pay;
    printf("请输入账单金额：");
    scanf("%d",&price);
    printf("请输入支付金额：");
    scanf("%d",&pay);
    int change = pay - price;
    if(change>=0)
    {
    printf("找您%d",change);
    }
    else printf("您仍需支付%d",-change);
}
```

#运算符的优先级
```
5>3==6>4
//5>3和6>4均为真，==两边值均为1
6>5>4
//先计算6?5为真
a==b==6
//首先判断a与b是否相等
a==b>0
//
```


#一个数字有几位
```
#include <stdio.h>
int main()
{
    int x;
    scanf("%d",&x);
    int n = 0;
    n++;
    x /= 10;
    /*避免输入0时输出0位数*/
    while(x>0)
    {
        n++;
        x /= 10;
    }
    printf("这是一个%d位数",n);
}
```
或者 
```
#include <stdio.h>

int main()
{
    int x;
    scanf("%d",&x);
    int n = 0;
    do
    {
        n++;
        x /= 10;
    }while(x>0);
    printf("这是一个%d位数",n);
}
```

#逆序输出一个数字 
```
#include <stdio.h>

int main()
{
    int x, rev = 0;
    printf("enter an integer:");
    scanf("%d",&x);
    
    do
    { 
        int digit;
        digit = x%10;
        rev = rev*10+digit;
        x /= 10;
        
    }while(x>0);
    
    printf("The reverse is %d",rev);
    
    return 0;
}
```
#输出一个数字的阶乘
```
#include <stdio.h>

int main()
{
    int x,fact = 1;
    printf("enter an integer:");
    scanf("%d",&x);
    int original =x;
    for(;x>1;x--)
    {
        fact *=x;
    }
    
    printf("The factor of %d is %d",original,fact);
    
    return 0;
}
```

#判断一个正整数是否为质数
```
#include <stdio.h>

int main()
{
    printf("Input an integer:");
    int x;
    scanf("%d",&x);
    int i, Prime = 1;
    for(i=2;i<=x/2;i++)
/*这里如果是i<x/2，就会把4误判为质数*/
    {
        if(x%i == 0)
        {
            Prime = 0;
            break;
        }
    }
    if(Prime == 1) {printf("This is a prime number.");}
    else printf("This is not a prime number.");
    

    return 0;
}

```

#输出100以内的质数
```
#include <stdio.h>

int main()
{
    int x;

    
    for(x=1;x<=100;x++)
    {
      int i, Prime = 1;
      /*这里i和Prime的定义要放在x的循环之内*/
      for(i=2;i<=x/2;i++)
      {
        if(x%i == 0)
        {
            Prime = 0;
            break;
        }
      }
      if(Prime == 1) {printf("%d is a prime number.\n",x);}
    }
    

    return 0;
}
```
#用1角2角5角硬币凑整
为什么出来的数字不对呢……
```
#include <stdio.h>

int main()
{
    int one=0, two=0, five=0, x;
    printf("Please enter an integer:\n");
    scanf("%d",&x);
    for(one=1;one<x*10;one++)
    {
        for(two=1;two<10*x/2;two++)
        {
            for(five=1;five<10*x/5;five++)
            {
                if(5*five+2*two+one == 10*x)
                {
                    printf("%d 10-cent coins, %d 20-cent and %d 50-cent would make %d dollars.\n",one,two,five,x);
                    goto out;
                }
            }
        }
    }
    out:
    return 0;
}
```
#正序输出一个正整数的每一位
```
int main()
{
    int x;
    printf("Please input an integer:");
    scanf("%d",&x);
    int t = x, mask = 1, count=0, d;
    while(t>9)
    {
        t /= 10;
        count ++;
        mask *= 10;
        printf("t = %d \ncount = %d \nmask = %d\n",t,count,mask);
    }

    do
    {
        d = x/mask;
        printf("%d",d);
        if(mask>9) printf(" ");
        x %= mask;
        mask /= 10;
    }while(mask>0);
    printf("\n");
}
```

#The greatest common divisor
```
#include <stdio.h>

int main()
{
    int a, b, t1,t2,t;
    printf("Please enter 2 integers:");
    scanf("%d %d",&a,&b);
    t1=a,t2=b;
    while(t2>0)
    {
        t = t1%t2;
        t1 = t2;
        t2 = t;
    };
    printf("The greatest common divisor of %d and %d is %d",a,b,t1);
    return 0;
}
```

#a and n are two integers, a∈[0,9],n∈[1,8], output sum = a + aa + aaa ......+ aaaaaa(n of a).
```
#include <stdio.h>
#include <math.h>
int main()
{
    int n, a,i=0,sum=0,temp=0;
    printf("Please enter 2 integers:");
    scanf("%d %d",&n,&a);
    for(i=0;i<n;i++)
    {
        temp+=a*pow(10,i);
        sum += temp;
    }
    printf("Sum=%d",sum);
    return 0;
}
```
#Input an integer, output the sum of 2/1+3/2+5/3+8/5+...
```
#include <stdio.h>
#include <math.h>
int main()
{
    double sum=0.0, dividend = 2.0, divisor = 1.0,temp = 0.0;
    int i,n;
    scanf("%d",&n);
    for(i=1;i<=n;i++)
    {
        sum+= dividend/divisor;
        temp = dividend,
        dividend += divisor;
        divisor = temp;
        printf("%f/%f\n",dividend,divisor);
    }
    printf("%.2f\n",sum);
}

```
