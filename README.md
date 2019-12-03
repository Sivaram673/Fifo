# Fifo
Fifo page replacement programe in c language
  #include<stdio.h>
int search(int);

int a[100],b[10];
int n,f;
int  main()
{


	int i=0,j=0,count=0,k,v;
	printf("\nenter no of references");
	scanf("%d",&n);
	printf("\n enter references");
	for(i=0;i<n;i++)
	{
		scanf("%d",&a[i]);
	}
	printf("\nenter no of frames");
	scanf("%d",&f);
	for(i=0;i<f;i++)
	{
		b[i]=-1;
	}
	//***********logic strats here********************
	for(i=0;i<n;i++)
	{
		if(j<f)//this condition to check whether frame is empty or not initially
		{
				if(b[j]==-1)//if frame is empty done add page into frame
					{
						k=search(a[i]);
						
						if(k<f)
						{
							continue;
						}
						else{
						
					b[j]=a[i];
					j++;
					count++;
				}
					}
		}
		else{
			
			k=search(a[i]);
			if(k==f)
			{
					
						for(v=0;v<f;v++)
						{
							b[v]=b[v+1];
						}
						b[f-1]=a[i];
						count++;
			}
			
			else if(k<f)
			{
				continue;
			}
			
			
		}
		
						
	}
	
	printf("\n the no of page faults=%d",count);
return 0;
}
int search(int m)
{
	int i;
	for(i=0;i<f;i++)
	{
		if(b[i]==m)
			return i;
	}
return f;//if page not found in frame then return the frame number
}
