PROGRAM OF SPARSE MATRIX ADDITION



#include<stdio.h>
void main()
{
    int a[10][10],b[10][10],t1[10][10],t2[10][10],s[10][10];
    int i,j,k=1,r1,c1,r2,c2,p=0;
    printf("Enter row limit of a :");
    scanf("%d",&r1);
    printf("Enter row limit of b :");
    scanf("%d",&r2);
    printf("Enter column limit of a :");
    scanf("%d",&c1);
    printf("Enter column limit of b :");
    scanf("%d",&c2);
    printf("\nEnter the elements of A :\n");
    for(i=0;i<r1;i++)
    {
   	 for(j=0;j<c1;j++)
   	 {
   	 scanf("%d",&a[i][j]);
   	 }
    }
    printf("\n");
    printf("Enter the elements of B :\n");
    for(i=0;i<r2;i++)
    {
   	 for(j=0;j<c2;j++)
   	 {
   	 scanf("%d",&b[i][j]);
   	 }
    }
    printf("Matrix A :\n");
    for(i=0;i<r1;i++)
    {
   	 for(j=0;j<c1;j++)
   	 {
   	 printf("%d\t",a[i][j]);
   	 }
   	 printf("\n");
    }
    printf("\n");
    printf("Matrix B :\n");
    for(i=0;i<r2;i++)
    {
   	 for(j=0;j<c2;j++)
   	 {
   	 printf("%d\t",b[i][j]);
   	 }
   	 printf("\n");
    }
    for(i=0;i<r1;i++)
    {
   	 for(j=0;j<c1;j++)
   	 {
   	 if(a[i][j]!=0)
   	 {
   		 t1[k][0]=i;
   		 t1[k][1]=j;
   		 t1[k][2]=a[i][j];
   		 k++;
   	 }
   	 }
    }
    t1[0][0]=r1;
    t1[0][1]=c1;
    t1[0][2]=k-1;
    printf("Tuplet form of A :\n");
    for(i=0;i<=t1[0][2];i++)
    {
   	 for(j=0;j<3;j++)
   	 {
   		 printf("%d\t",t1[i][j]);
   	 }
   	 printf("\n");
    }
    k=1;
    for(i=0;i<r2;i++)
    {
   	 for(j=0;j<c2;j++)
   	 {
   	 if(b[i][j]!=0)
   	 {
   		 t2[k][0]=i;
   		 t2[k][1]=j;
   		 t2[k][2]=b[i][j];
   		 k++;
   	 }
   	 }
    }
    t2[0][0]=r2;
    t2[0][1]=c2;
    t2[0][2]=k-1;
    printf("Tuplet form of B :\n");
    
    for(i=0;i<=t2[0][2];i++)
    {
   	 for(j=0;j<3;j++)
   	 {
   		 printf("%d\t",t2[i][j]);
   	 }
   	 printf("\n");
    }
    if((r1==r2)&&(c1==c2))
    {
        {
        i=1,j=1,k=1;
        while((i<=t1[0][2])&&(j<=t2[0][2]))
	{
        if((t1[i][0]==t2[j][0])&&(t1[i][1]==t2[j][1]))
        {
     		s[k][0]=t1[i][0];
			s[k][1]=t1[i][1];
			s[k][2]=t1[i][2]+t2[j][2];
			i++;
			j++;
			k++;
			p++;
	 }
	 else if(t1[i][0]<t2[j][0])
        {
     		s[k][0]=t1[i][0];
			s[k][1]=t1[i][1];
			s[k][2]=t1[i][2];
			i++;
			k++;
			p++;
	 }
	 else if(t1[i][0]>t2[j][0])
        {
     		s[k][0]=t2[j][0];
			s[k][1]=t2[j][1];
			s[k][2]=t2[j][2];
			j++;
			k++;
			p++;
	 }
	 else if((t1[i][0]==t2[j][0])&&(t1[i][1]<t2[j][1]))
        {
     		s[k][0]=t1[i][0];
			s[k][1]=t1[i][1];
			s[k][2]=t1[i][2];
			i++;
			k++;
			p++;
	 }
	 else if((t1[i][0]==t2[j][0])&&(t1[i][1]>t2[j][1]))
        {
     		s[k][0]=t2[j][0];
			s[k][1]=t2[j][1];
			s[k][2]=t2[j][2];
			j++;
			k++;
			p++;
	 }
	 else
	 {
		 while(i<=r1)
		 {
 			s[k][0]=t1[i][0];
			s[k][1]=t1[i][1];
			s[k][2]=t1[i][2];
			i++;
			k++;
			p++;
		 }
		 while(j<=r2)
		 {
   		s[k][0]=t2[j][0];
			s[k][1]=t2[j][1];
			s[k][2]=t2[j][2];
			j++;
			k++;
			p++;
		 }
	 }
	}
	s[0][0]=r1;
	s[0][1]=c1;
	s[0][2]=p;
        }
        printf("Sum of matrix a and b :\n");
        for(i=0;i<=s[0][2];i++)
        {
        for(j=0;j<3;j++)
        {
     	   printf("%d\t",s[i][j]);
        }
        printf("\n");
        }
	 }
    else
    {
        printf("Addition not possible");
    }
}







OUTPUT :

Enter row limit of a :3
Enter row limit of b :3
Enter column limit of a :3
Enter column limit of b :3
Enter the elements of A :
0
6
6
1
0
0
2
0
0
Enter the elements of B :
1
2
3
0
0
0
2
0
0
Matrix A :
0    6    6    
1    0    0    
2    0    0    

Matrix B :
1    2    3    
0    0    0    
2    0    0    
Tuplet form of A :
3    3    4    
0    1    6    
0    2    6    
1    0    1    
2    0    2    
Tuplet form of B :
3    3    4    
0    0    1    
0    1    2    
0    2    3    
2    0    2    
Sum of matrix a and b :
3    3    5    
0    0    1    
0    1    8    
0    2    9    
1    0    1    
2    0    4    


