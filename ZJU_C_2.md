***data type, Logic, conditions, etc.***

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
