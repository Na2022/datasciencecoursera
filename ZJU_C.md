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
