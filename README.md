#include<stdio.h> #include<conio.h> #include<stdlib.h> #define TRUE 1
#define TREENODES 100
#define FALSE 0 struct tree
{
int info; int used;
};
struct tree node[TREENODES]; void Createtree();
void Insert(int); void Display(); void Setleft(int,int);
void Setright(int,int); void main()
{
int x;
char ch='1'; clrscr();
printf("\n Enter root node value:"); scanf("%d", &x);
Createtree(x); while(ch!='3')
{
printf("\n1-INSERT"); printf("\n2-DISPLAY"); printf("\n3-QUIT");
printf("\n Enter your choice:"); fflush(stdin);
ch=getchar(); switch(ch)
{
case '1' :
printf("\n Enter the element to be inserted:"); scanf("%d",&x);
Insert(x); break; case '2': Display(); break;


case '3':
break; default:
printf("\n Wrong choice!Try again:");
}
}
}
void Createtree(int x)
{
int i; node[0].info=x;
node[0].used=TRUE; for(i=1;i<TREENODES;i++)
node[i].used=FALSE;
}
void Insert(int x)
{
int p,q; p=q=0;
while(q<TREENODES && node[q].used && x!=node[p].info)
{
p=q; if(x<node[p].info) q=2*p+1;
else q=2*p+2;
}
if(x==node[p].info)
printf("\n %d is a duplicate number\n",x); else
if(x<node[p].info) Setleft(p,x);
else Setright(p,x);
}
void Setleft(int pos,int x)
{
int q; q=2*pos+1;
if(q>TREENODES)
printf("\n Array overflow."); else if(node[q].used==TRUE) printf("\n Invalid insertion."); else
{
node[q].info=x;


node[q].used=TRUE;
}
}
void Setright(int pos,int x)
{
int q; q=2*pos+2;
if(q>TREENODES)
printf("\n Array overflow."); else if(node[q].used==TRUE)
printf("\n Invalid insertion.\n"); else
{
node[q].info=x; node[q].used=TRUE;
}
}
void Display()
{
int i; for(i=0;i<TREENODES;i++)
if(node[i].used==TRUE) printf("%d ",node[i].info); printf("\n");
}
