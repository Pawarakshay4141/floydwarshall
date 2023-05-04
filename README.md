# floydwarshall
#include<stdio.h>
 int min(int a,int b)
  {
   if(a<b)
   {
    return(a);
    else
    {
    return(b);
    }
   }
    void floyds(int p[10][10],int n)
    {
     int i,j,k;
     for (k=0;k<n;k++)
     for (i=0;i<n;i++)
     for (j=0;j<n;j++)
     {
     if(i==j)
      {
       p[i][j]=0;
      }
       else
      {
       p[i][j]=min(p[i][j],p[i][k]+p[k][j]);
      }
   }
 }
}
   int main()
   {
    int p[10][10],w,n,e,u,v,i,j;
    printf("\n Enter the number of vertices:");
    scanf("%d",&n);
    printf("\n Enter the number of edges:\n");
    scanf("%d",&e);
    for(i=0;i<n;i++)
    {
     for(j=0;j<n;j++)
     {
      p[i][j]=999;
     }
  for (i=1;i<=e;i++)
   {
     printf("\n Enter the end vertices of edge %d with its weight \n",i);
     scanf("%d %d %d",&u,&v,&w);
     p[u][v]=w;
   }
     printf("\n Matrix of input data:\n");
     for (i=0;i<n;i++)
     {
       for (j=0;j<n;j++)
       {
         printf("%d \t",p[i][j]);
       }
         printf("\n");
     }
      floyds(p,n);
      printf("\n Transitive closure:\n");
      for (i=0;i<n;i++)
      {
        for (j=0;j<n;j++)
        {
          printf("%d \t",p[i][j]);
        }
          printf("\n");
      }     
        printf("\n The shortest paths are:\n");
        for (i=0;i<n;i++)
        {
           for (j=0;j<n;j++)
          {
            if(i!=j)
            printf("\n <%d,%d>=%d",i,j,p[i][j]);
          }
        }
   }
/*
OUTPUT
Enter the number of vertices:3
Enter the number of edges:
4
Enter the end vertices of edge 1 with its weight
0 1 5
Enter the end vertices of edge 2 with its weight
1 2 6}
Enter the end vertices of edge 3 with its weight
2 3 2
Enter the end vertices of edge 4 with its weight
1 3 5
Matrix of input data:
999 6 5
999 999 2
999 999 999
Transitive closure:
0 6 5
999 0 2
999 999 0
The shortest paths are:
<1,2>=6
<1,3>=5
<2,1>=999
<2,3>=2
<3,1>=999
<3,2>=999
k
