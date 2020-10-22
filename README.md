#include<stdio.h>
void divide(int a[],int t[],int lb,int ub);
void merge(int a[],int t[],int lb,int mid,int ub);

int main()
{
int a[100],t[100],lb,ub,i,n;
printf("enter value of n= ");
scanf("%d",&n);
printf("enter the array n= ");
for(i=0;i<n;i++)
scanf("%d",&a[i]);
divide(a,t,0,n-1);
printf("sorted array = ");
for(i=0;i<n;i++)
printf("%d ",a[i]);
return 0;
} 
void divide(int a[],int t[],int lb,int ub)
{int mid;
if(lb<ub)
{
mid=(lb+ub)/2;
divide(a,t,lb,mid);
divide(a,t,mid+1,ub);
merge(a,t,lb,mid,ub);
}
}

void merge(int a[],int t[],int lb,int mid,int ub)
{
int p=mid,k=lb;
while((lb<=p)&&(mid+1<=ub))
{
if(a[lb]<a[mid+1])
{
t[k]=a[lb];
k++;
lb++;
}
else
{
t[k]=a[mid+1];
mid++;
k++;
}
}

while(lb<=p)
{
t[k]=a[lb];
k++;
lb++;
}
while(mid+1<=ub)
{
t[k]=a[mid+1];
k++;
mid++;
}

for(int i=0;i<k;i++)
a[i]=t[i];
}
    

