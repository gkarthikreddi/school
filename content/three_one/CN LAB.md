1. [[#Subnet]]
2. [[#Character Stuffing]]
3. [[#Bit Stuffing]]
4. [[#CRC]]
5. [[#Data Encryption]]
6. [[#Dijsktra]]
7. [[#Distance Vector]]
8. [[#Frame Sorting]]
## Subnet
```c
#include<stdio.h>

int p,q,u,v,n;
int min=99,mincost=0;
int t[50][2],i,j;
int parent[50],edge[50][50];

void main()
{
    printf("\n Enter the number of nodes");
    scanf("%d",&n);
    for(i=0;i<n;i++)
    {
        printf("%c\t",65+i);
        parent[i]=-1;
    }
    printf("\n");
    for(i=0;i<n;i++)
    {
        printf("%c",65+i);
        for(j=0;j<n;j++)
            scanf("%d",&edge[i][j]);
    }
    for(i=0;i<n;i++)
    {
        for(j=0;j<n;j++)
            if(edge[i][j]!=99)
                if(min>edge[i][j])
                {
                    min=edge[i][j];
                    u=i;
                    v=j;
                }
        p=find(u);
        q=find(v);
        if(p!=q)
        {
            t[i][0]=u;
            t[i][1]=v;
            mincost=mincost+edge[u][v];
            sunion(p,q);
        }
        else
        {
            t[i][0]=-1;
            t[i][1]=-1;
        }
        min=99;
    }
    printf("Minimum cost is %d\n Minimum spanning tree is\n" ,mincost);
    for(i=0;i<n;i++)
        if(t[i][0]!=-1 && t[i][1]!=-1)
        {
            printf("%c %c %d", 65+t[i][0], 65+t[i][1],
                    edge[t[i][0]][t[i][1]]);
            printf("\n");
        }
}

void sunion(int l,int m)
{
    parent[l]=m;
}
int find(int l)
{
    if(parent[l]>0)
        l=parent[l];
    return l;
}
```

## Character Stuffing
```c
#include<stdio.h>

int p,q,u,v,n;
int min=99,mincost=0;
int t[50][2],i,j;
int parent[50],edge[50][50];

void main()
{
    printf("\n Enter the number of nodes");
    scanf("%d",&n);
    for(i=0;i<n;i++)
    {
        printf("%c\t",65+i);
        parent[i]=-1;
    }
    printf("\n");
    for(i=0;i<n;i++)
    {
        printf("%c",65+i);
        for(j=0;j<n;j++)
            scanf("%d",&edge[i][j]);
    }
    for(i=0;i<n;i++)
    {
        for(j=0;j<n;j++)
            if(edge[i][j]!=99)
                if(min>edge[i][j])
                {
                    min=edge[i][j];
                    u=i;
                    v=j;
                }
        p=find(u);
        q=find(v);
        if(p!=q)
        {
            t[i][0]=u;
            t[i][1]=v;
            mincost=mincost+edge[u][v];
            sunion(p,q);
        }
        else
        {
            t[i][0]=-1;
            t[i][1]=-1;
        }
        min=99;
    }
    printf("Minimum cost is %d\n Minimum spanning tree is\n" ,mincost);
    for(i=0;i<n;i++)
        if(t[i][0]!=-1 && t[i][1]!=-1)
        {
            printf("%c %c %d", 65+t[i][0], 65+t[i][1],
                    edge[t[i][0]][t[i][1]]);
            printf("\n");
        }
}

void sunion(int l,int m)
{
    parent[l]=m;
}
int find(int l)
{
    if(parent[l]>0)
        l=parent[l];
    return l;
}
```

## Bit Stuffing
```c
#include<stdio.h>
#include<string.h>

void main()
{
    int a[20],b[30],i,j,k,count,n;
    printf("Enter frame size (Example: 8):");
    scanf("%d",&n);
    printf("Enter the frame in the form of 0 and 1 :");
    for(i=0; i<n; i++)
        scanf("%d",&a[i]);
    i=0;
    count=1;
    j=0;
    while(i<n)
    {
        if(a[i]==1)
        {
            b[j]=a[i];
            for(k=i+1; a[k]==1 && k<n && count<5; k++)
            {
                j++;
                b[j]=a[k];
                count++;
                if(count==5)
                {
                    j++;
                    b[j]=0;
                }
                i=k;
            }
        }
        else
        {
            b[j]=a[i];
        }
        i++;
        j++;
    }
    printf("After Bit Stuffing :");
    for(i=0; i<j; i++)
        printf("%d",b[i]);
}
```

## CRC
```c
#include<stdio.h>

void remainder(int fr[]);

int gen[4],genl,frl,rem[4];

void main()
{
    int i,j,fr[8],dupfr[11],recfr[11],tlen,flag;
    frl=8; genl=4;
    printf("enter frame:");
    for(i=0;i<frl;i++)
    {
        scanf("%d",&fr[i]);
        dupfr[i]=fr[i];
    }
    printf("enter generator:");
    for(i=0;i<genl;i++)
        scanf("%d",&gen[i]);
    tlen=frl+genl-1;
    for(i=frl;i<tlen;i++)
    {
        dupfr[i]=0;
    }
    remainder(dupfr);
    for(i=0;i<frl;i++)
    {
        recfr[i]=fr[i];
    }
    for(i=frl,j=1;j<genl;i++,j++)
    {
        recfr[i]=rem[j];
    }
    remainder(recfr);
    flag=0;
    for(i=0;i<4;i++)
    {
        if(rem[i]!=0)
            flag++;
    }
    if(flag==0)
    {
        printf("frame received correctly");
    }
    else
    {
        printf("the received frame is wrong");
    }
}

void remainder(int fr[])
{
    int k,k1,i,j;
    for(k=0;k<frl;k++)
    {
        if(fr[k]==1)
        {
            k1=k;
            for(i=0,j=k;i<genl;i++,j++)
            {
                rem[i]=fr[j]^gen[i];
            }
            for(i=0;i<genl;i++)
            {
                fr[k1]=rem[i];
                k1++;
            }
        }
    }
}
```

## Data Encryption
```c
#include <stdio.h>

int main()
{
    int i, x;
    char str[100];
    printf("\nPlease enter a string:\t");
    gets(str);
    printf("\nPlease choose following options:\n");
    printf("1 = Encrypt the string.\n");
    printf("2 = Decrypt the string.\n");
    scanf("%d", &x);
    //using switch case statements
    switch(x)
    {
        case 1:
            for(i = 0; (i < 100 && str[i] != '\0'); i++)
                str[i] = str[i] + 3; //the key for encryption is 3 that is added to ASCII value
            printf("\nEncrypted string: %s\n", str);
            break;
        case 2:
            for(i = 0; (i < 100 && str[i] != '\0'); i++)
                str[i] = str[i] - 3; //the key for encryption is 3 that is subtracted to ASCII value
            printf("\nDecrypted string: %s\n", str);
            break;
        default:
            printf("\nError\n");
    }
    return 0;
}
```

## Dijsktra
```c
#include<stdio.h>

void main()
{
    int path[5][5],i,j,min,a[5][5],p,st=1,ed=5,stp,edp,t[5],index;
    printf("enter the cost matrix\n");
    for(i=1;i<=5;i++)
        for(j=1;j<=5;j++)
            scanf("%d",&a[i][j]);
    printf("enter the paths\n");
    scanf("%d",&p);
    printf("enter possible paths\n");
    for(i=1;i<=p;i++)
        for(j=1;j<=5;j++)
            scanf("%d",&path[i][j]);
    for(i=1;i<=p;i++)
    {
        t[i]=0;
        stp=st;
        for(j=1;j<=5;j++)
        {
            edp=path[i][j+1];
            t[i]=t[i]+a[stp][edp];
            if(edp==ed)
                break;
            else
                stp=edp;
        }
    }
    min=t[st];index=st;
    for(i=1;i<=p;i++)
    {
        if(min>t[i])
        {
            min=t[i];
            index=i;
        }
    }
    printf("minimum cost %d",min);
    printf("\n minimum cost path ");
    for(i=1;i<=5;i++)
    {
        printf("--> %d",path[index][i]);
        if(path[index][i]==ed)
            break;
    }
}
```

## Distance Vector
```c
#include<stdio.h>

struct node
{
    unsigned dist[20];
    unsigned from[20];
}
rt[10];

int main()
{
    int dmat[20][20];
    int n,i,j,k,count=0;
    printf("\nEnter the number of nodes : ");
    scanf("%d",&n);
    printf("\nEnter the cost matrix :\n");
    for(i=0;i<n;i++)
        for(j=0;j<n;j++)
        {
            scanf("%d",&dmat[i][j]);
            dmat[i][i]=0;
            rt[i].dist[j]=dmat[i][j];
            rt[i].from[j]=j;
        }
    do
    {
        count=0;
        for(i=0;i<n;i++)
            for(j=0;j<n;j++)
                for(k=0;k<n;k++)
                    if(rt[i].dist[j]>dmat[i][k]+rt[k].dist[j])
                    {
                        rt[i].dist[j]=rt[i].dist[k]+rt[k].dist[j];
                        rt[i].from[j]=k;
                        count++;
                    }
    }while(count!=0);
    for(i=0;i<n;i++)
    {
        printf("\n\nState value for router %d is \n",i+1);
        for(j=0;j<n;j++)
        {
            printf("\t\nnode %d via %d Distance%d",j+1,rt[i].from[j]+1,rt[i].dist[j]);
        }
    }
    printf("\n\n");
}
```

## Frame Sorting
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct frame
{
	int sno;
	char msg[15];
	int flag;
};

int main()
{
	int i,j,n,r,k;
	printf("enter no of frames\n");
	scanf("%d",&n);
	struct frame fr[n];
	int s[n];
	for(i=0;i<n;i++)
	{
		s[i]=-1;
		fr[i].sno=-1;
	}
	printf("enter the message \n");
	for(i=0;i<n;i++)
	{
		scanf("%s",fr[i].msg);
		fr[i].sno=i;
	}
	for(j=0;j<n;j++)
	{
		r=rand()%n;
		if(s[r]==-1)
		{
			fr[j].flag=r;
			s[r]=1;
		}
		else if(s[r]==1)
		{
			for(k=0;k<n;k++){
				r=k;
				if(s[r]==-1)
				{
					fr[j].flag=r;
					s[r]=1;
					break;
				}
			}
		}
	}
	printf("arrived frame are:\n");
	printf("\n sno \t msg \n");
	for(i=0;i<n;i++)
	{
		for(j=0;j<n;j++)
			if(fr[j].flag==i)
			{
				printf("%d\t%s",fr[j].sno,fr[j].msg);
				printf("\n");
			}
	}
	for(i=0;i<n;i++)
	{
		for(j=0;j<n-1;j++)
		{
			if(fr[j].sno>fr[j+1].sno)
			{
				struct frame temp;
				temp=fr[j];
				fr[j]=fr[j+1];
				fr[j+1]=temp;
			}
		}
	}
	printf("after sorting arrived frames are\n");
	printf("\n sno \t msg \n");
	for(i=0;i<n;i++)
	{
		printf("%d\t%s",fr[i].sno,fr[i].msg);
		printf("\n");
	}
	return 0;
}
```

## Leaky Bucket
```c
#include<stdio.h>

int main()
{
    int incoming, outgoing, buck_size, n, store = 0;
    printf("Enter bucket size, outgoing rate and no of inputs: ");
    scanf("%d %d %d", &buck_size, &outgoing, &n);
    while (n != 0) {
        printf("Enter the incoming packet size : ");
        scanf("%d", &incoming);
        printf("Incoming packet size %d\n", incoming);
        if (incoming <= (buck_size - store)){
            store += incoming;
            printf("Bucket buffer size %d out of %d\n", store, buck_size);
        } else {
            printf("Dropped %d no of packets\n", incoming - (buck_size - store));
            printf("Bucket buffer size %d out of %d\n", store, buck_size);
            store = buck_size;
        }
        store = store - outgoing;
        printf("After outgoing %d packets left out of %d in buffer\n", store, buck_size);
        n--;
    }
}
```

## Sliding Window
```c
#include<stdio.h>

int main()
{
    int w,i,f,frames[50];
    printf("Enter window size: ");
    scanf("%d",&w);
    printf("\nEnter number of frames to transmit: ");
    scanf("%d",&f);
    printf("\nEnter %d frames: ",f);
    for(i=1;i<=f;i++)
        scanf("%d",&frames[i]);
    printf("\nWith sliding window protocol the frames will be sent in the following manner (assuming no corruption of frames)\n\n");
    printf("After sending %d frames at each stage sender waits for acknowledgement sent by the receiver\n\n",w);
    for(i=1;i<=f;i++)
    {
        if(i%w==0)
        {
            printf("%d\n",frames[i]);
            printf("Acknowledgement of above frames sent is received by sender\n\n");
        }
        else
            printf("%d ",frames[i]);
    }
    if(f%w!=0)
        printf("\nAcknowledgement of above frames sent is received by sender\n");
    return 0;
}
```