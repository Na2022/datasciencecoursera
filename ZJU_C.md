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
