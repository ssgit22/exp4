# exp4
### PAGING TECHNIQUE OF MEMORY MANAGEMENT:
```
#include<stdio.h>
#include<conio.h>
int main()  {
int ms, ps, nop, np, rempages, i, j, x, y, pa, offset;
int s[10], fno[10][20];
printf("\nEnter the memory size -- ");
scanf("%d",&ms);
printf("\nEnter the page size -- ");
scanf("%d",&ps);
nop = ms/ps;
printf("\nThe no. of pages available in memory are -- %d ",nop);
printf("\nEnter number of processes -- ");
scanf("%d",&np);
rempages = nop;
for(i=1;i<=np;i++) {
printf("\nEnter no. of pages required for p[%d]-- ",i);
scanf("%d",&s[i]);
if(s[i] >rempages)  {
printf("\nMemory is Full");
break; }
rempages = rempages - s[i];
printf("\nEnter pagetable for p[%d] --- ",i);
for(j=0;j<s[i];j++)
scanf("%d",&fno[i][j]); }
printf("\nEnter Logical Address to find Physical Address ");
printf("\nEnter process no. and page number and offset -- ");
scanf("%d %d %d",&x,&y, &offset);
if(x>np || y>=s[i] || offset>=ps)
printf("\nInvalid Process or Page Number or offset");
else
{ pa=fno[x][y]*ps+offset;
printf("\nThe Physical Address is -- %d",pa);
}
getch(); }

```

### PAGE REPLACEMENT ALGORITHM (FIFO):
```
#include<stdio.h>
int main() {
int i,j,n,a[50],frame[10],no,k,avail,count=0;
printf("\n ENTER THE NUMBER OF PAGES:\n");
scanf("%d",&n);
printf("\n ENTER THE PAGE NUMBER :\n");
for(i=1;i<=n;i++)
scanf("%d",&a[i]);
printf("\n ENTER THE NUMBER OF FRAMES :");
scanf("%d",&no);
for(i=0;i<no;i++)
frame[i]= -1; j=0;
printf("\tRef string\t Page Frames\n");
for(i=1;i<=n;i++) {
printf("%d\t\t\t",a[i]);
avail=0;
for(k=0;k<no;k++)
if(frame[k]==a[i])
avail=1;
if (avail==0) {
frame[j]=a[i];
j=(j+1)%no;
count++;
for(k=0;k<no;k++)
printf("%d\t",frame[k]); }
printf("\n"); }
printf("\nPage Fault Is %d",count);
return 0; }

```

### PAGE REPLACEMENT ALGORITHM (LRU) :
```
#include<stdio.h>
int main() {
int q[20],p[50],c=0,c1,d,f,i,j,k=0,n,r,t,b[20],c2[20];
printf("Enter no of pages: \n");
scanf("%d",&n);
printf("Enter the reference string: \n");
for(i=0;i<n;i++)
scanf("%d",&p[i]);
printf("Enter no of frames: \n");
scanf("%d",&f);
q[k]=p[k];
printf("\t\n\t %d\n",q[k]);
c++;
k++;
for(i=1;i<n;i++) {
c1=0;
for(j=0;j<f;j++) {
if(p[i]!=q[j])
c1++; }
if(c1==f) {
c++;
if(k<f) {
q[k]=p[i];
k++;
for(j=0;j<k;j++)
printf("\t%d",q[j]);
printf("\n"); }
else {
for(r=0;r<f;r++) {
c2[r]=0;
for(j=i-1;j<n;j--) {
if(q[r]!=p[j])
c2[r]++;
else
break; } }
for(r=0;r<f;r++)
b[r]=c2[r];
for(r=0;r<f;r++) {
for(j=r;j<f;j++) {
if(b[r]<b[j]) {
t=b[r];
b[r]=b[j];
b[j]=t; } } }
for(r=0;r<f;r++) {
if(c2[r]==b[0])

q[r]=p[i];
printf("\t%d",q[r]); }
printf("\n"); } } }
printf("\nThe no of page faults is %d",c); }

```
### PAGE REPLACEMENT ALGORITHM (OPR):
```
#include<stdio.h>
int main() {
int i,j,n,a[50],frame[10],no,k,avail,count=0;
printf("\n ENTER THE NUMBER OF PAGES:\n");
scanf("%d",&n);
printf("\n ENTER THE PAGE NUMBER :\n");
for(i=1;i<=n;i++)
scanf("%d",&a[i]);
printf("\n ENTER THE NUMBER OF FRAMES :");
scanf("%d",&no);
for(i=0;i<no;i++)
frame[i]= -1;
j=0;
printf("\tref string\t page frames\n");
for(i=1;i<=n;i++) {
printf("%d\t\t",a[i]);
avail=0;
for(k=0;k<no;k++)
if(frame[k]==a[i])
avail=1;
if (avail==0) {
frame[j]=a[i];
j=(j+1)%no;
count++;
for(k=0;k<no;k++)
printf("%d\t",frame[k]); }
printf("\n"); }
printf("Page Fault Is %d",count);
return 0; }

```
![3](https://user-images.githubusercontent.com/119419532/224465954-1993feeb-1c28-4100-9c3f-26eeee991b2c.png)
