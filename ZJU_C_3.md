Pointer
===

### Definition of pointers

```
#include <stdio.h>

void f(int *p);
void g(int k);

int main(void)
{
    int i = 6;
    printf("&i=%p\n",&i);
    f(&i);
    g(i);
    
    return 0;
}

void f(int *p)
{
    printf("p=%p\n",p);
    printf("*p=%d\n",*p);
    
}
void g(int k)
{
    printf("k=%d\n",k);
}
```

### Swap via pointers

```
#include <stdio.h>
void swap(int *pa,int *pb);

int main()
{
    int a=5,b=6;
    printf("Before:a=%d,b=%d\n",a,b);
    swap(&a,&b);
    printf("After:a=%d,b=%d\n",a,b);
    return 0;
}

void swap(int *pa,int *pb)
{
    int t = *pa;
    *pa = *pb;
    *pb = t;
}
```

### Get an array of integers, print min and max of the array

#### 如何实现不给定数组长度、仅以0结尾？

```
#include <stdio.h>
void maxmin(int a[],int len, int *max, int *min);

int main()
{
    int a[10],i;
    for(i=0;;i++)
    {
        scanf("%d",&a[i]);
        if(a[i]==0) break;
    }
    int max,min;
    maxmin(a,sizeof(a)/sizeof(a[0]),&max,&min);
    printf("max=%d, min=%d\n",max,min);
}

void maxmin(int a[],int len,int *max, int *min)
{
    int i;
    *max = * min =a[0];
    for(i=1;i<len;i++)
    {
        if(a[i]<*min) *min=a[i];
        if(a[i]>*max) *max=a[i];
    }
}
```
