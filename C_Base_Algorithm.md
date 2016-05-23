##### 二分法查找 #####
	void main()
	{	
		int  x,bottom,mid,top,a[10]={1,2,3,4,5,6,7,8,9,10};
		printf("请输入要查找的数:");
		scanf("%d",&x);
		bottom=0,top=9;
		while(bottom<=top)
		{
			mid=(bottom+top)/2;
			if(x<a[mid])
				top=mid-1;
			else if(x>a[mid])
				bottom=mid+1;
			else break;
		}
		if(bottom<=top)
			printf("%d在数组中的下标为%d",x,mid);
		else
			printf("查无次数!");	
	}

##### 计算文章中单词个数 #####
	void main()
	{	
		int i=0,num=0;
		char a[100],c;
		printf("输入字符:\n");
		gets(a);
		do{
			while((c=a[i])==' ') i++;
			if(c!='\0') ++num;
			while((c=a[i])!=' '&&c!='\0') i++;
		}while(c!='\0');
		printf("单词个数是:%d\n",num); 	
	}

##### 实现strcat函数的功能 #####
	char *MyStringCatch(char *strDest,const char*strSrc)
	{
		assert(strSrc!=NULL);
		char*temp=strDest;
		while(*strDest!='\0')
			strDest++;
		while((*strDest++=*strSrc++)!='\0');
		return temp;
	}

##### 实现strcpy函数的功能 #####
	char *MyStringCopy(char *strDest,const char*strSrc)
	{
		assert(strDest!=NULL&&strSrc!=NULL);
		char*temp=strDest;
		while((*strDest++=*strSrc++)!='\0');
			return temp;
	}

##### 递归求阶乘 #####
	#include<stdio.h>
	float fac(int n)
	{	
		float f;
		if(n>1) f=fac(n-1)*n;
		else if(n==0||n==1) f=1;
		else f=-5;
		return f;	
	}

##### 指针翻转数组 #####
	void inverse(int *p,int n)
	{	
		int *q,t;
		q=p+n-1;
		while(p<q)
		{	
			t=*p; *p=*q; *q=t; p++; q--;	
		}
	}

##### 递规反向输出字符串 #####
	void inverse(char *p)
	{    
		if( *p = = '\0' ) 
		return;
		    inverse( p+1 );
		printf( "%c", *p );
	}

##### 判断数组是否为升序 #####
	bool fun( int a[], int n )
	{	
		if( n==1 )
			return true;
		if( n==2 )
			return a[n-1] >= a[n-2];
		return fun( a,n-1) && ( a[n-1] >= a[n-2] );
	}

##### 判断质数与合数 #####
	#include<math.h>
	void main()
	{	
		int i,j,k;
		printf("输入一个数:\n");
		scanf("%d",&i);
		k=sqrt(i);
		for(j=2;j<=k;j++)
		{
			if(i%j==0) break;
			if(j>k) printf("%d是一个素数\n",i);
			else printf("%d是一个合数\n",i);	
		}
	}
##### 计算最大公约数和最小公倍数 #####
	void main()
	{	
		int m,n,m1,n1,a;
		printf("输入两个整数:");
		scanf("%d %d",&m,&n);
		m1=m;
		n1=n;
		a=m1%n1;
		while (a!=0) 
		{	m1=n1;
			n1=a;
			a=m1%n1;	}
		printf("最大公约数是:%d\n",n1);
		printf("最小公倍数是:%d\n",m*n/n1);	
	}

##### 倒着输出字符串 #####
	void main()
	{	
		char *p,*q="Language";
		for(p=q;*p!='\0';) p++;
		for(p--;p>=q;p--)
			putchar(*p);
		putchar('\n');	
	}

# #

	排序法	平均时间	最差情形	稳定度	额外空间	备注
	--------------------------------------------------------------------
	冒泡	O(n2)	   	O(n2)		稳定	O(1)		n小时较好
	交换	O(n2)		O(n2)		不稳定	O(1)		n小时较好
	选择	O(n2)		O(n2)		不稳定	O(1)		n小时较好
	插入	O(n2)		O(n2)		稳定	O(1)		大部分已排序时较好
	基数	O(logRB)	O(logRB)	稳定	O(n)		B是真数(0-9), R是基数(个十百)
	Shell	O(nlogn)	O(ns)1<s<2	不稳定	O(1)		s是所选分组
	快速	O(nlogn)	O(n2)		不稳定	O(nlogn)	n大时较好
	归并	O(nlogn)	O(nlogn)	稳定	O(1)		n大时较好
	堆		O(nlogn)	O(nlogn)	不稳定	O(1)		n大时较好
	--------------------------------------------------------------------
	选择排序, 快速排序, 希尔排序, 堆排序不是稳定的排序算法;
	冒泡排序, 插入排序, 归并排序和基数排序是稳定的排序算法;


##### 直接插入排序(带哨兵,最终排完序的数组缺少了原始数组的第一个元素) #####
	void InsertSort(int arr[],int n)
	{
		for(int i=1;i<n;i++)
		{
			if(arr[i]<arr[i-1])
			{
				arr[0]=arr[i];
				int j=i-1;
				for(;arr[j]>arr[0]&&j>=0;j--)
				{
					arr[j+1]=arr[j];
				}
				arr[j+1]=arr[0];
			}
		}
	}

##### 直接插入排序(无哨兵) #####
	void InsertSort(int arr[],int n)
	{
		for(int i=1;i<n;i++)
		{
			if(arr[i]<arr[i-1])
			{
				int temp=arr[i];
				int j=i-1;
				for(;arr[j]>temp&&j>=0;j--)
				{
					arr[j+1]=arr[j];
				}
				arr[j+1]=temp;
			}
		}
	}


##### 希尔排序 #####
	void ShellSort(int* myAarray, int arrayNum)  
	{  
		int d = arrayNum / 2;    //初始增量设为数组长度的一半  
		while(d >= 1)  
		{  
			for (int i = d; i < arrayNum; i += 1)   
			{  
				int j = i - d;  
				int temp = myAarray[i];   
				while (j >= 0 && myAarray[j] > temp)     //从后向前，找到比其小的数的位置  
				{  
					myAarray[j+d] = myAarray[j];       //向后挪动  
					j -= d;  
				}  
				if (j != i - d)                         //存在比其小的数  
					myAarray[j+d] = temp;  
			}  
			d = d / 2; 
		}  
	}  

##### 冒泡排序 #####
	void BubbleSort(int *myArray)
	{
		int len=sizeof(myArray);
		for (int i = 0; i < len-1; i++)
		{  
			for(int j = 0 ;j < len - i - 1; j++)
			{    
				if(myArray[j] < myArray[j + 1])
				{   
					int temp = myArray[j];
					myArray[j] = myArray[j + 1];
					myArray[j + 1] = temp;
				}
			}
		}          
	}


##### 快速排序 #####
	void QuickSort(int a[],int left,int right)
	{
		int i=left;
		int j=right;
		int temp=a[left];
		if(left>=right)
			return;
		while(i!=j)
		{
			while(i<j&&a[j]>=temp) 
				j--;
			if(j>i)
				a[i]=a[j];
			while(i<j&&a[i]<=temp)
				i++;
			if(i<j)
				a[j]=a[i];
		}
		a[i]=temp;                              //把基准插入,此时i与j已经相等
		QuickSort(a,left,i-1);                     //递归左边
		QuickSort(a,i+1,right);                   //递归右边
	}
	
	void main()
	{
		int a[9]={8,2,6,12,1,9,5,5,10};
		int i;
		QuickSort(a,0,8);
		for(i=0;i<9;i++)
			cout<<a[i]<<endl;
	}

##### 简单选择排序 #####
	void SelectionSort(int *myArray, int n)
	{
		int  index, value;
		for (int i = 0; i < n - 1; i ++) 
		{
			value = i;
			for (int j = i + 1; j < n; j ++)
				if (myArray[i] > myArray[j])
				{
					value=j;
				}
				if(i!=value)
				{
					int temp=myArray[i];
					myArray[i]=myArray[value];
					myArray[i]=temp;
				}
		}
	}


##### 线形表a、b为两个有序升序的线形表,使两表合并成一个有序升序线形表h #####
	Linklist *unio(Linklist *p,Linklist *q)
	{
		linklist *R,*pa,*qa,*ra;
		pa=p;
		qa=q;
		R=ra=p;
		while(pa->next!=NULL&&qa->next!=NULL){
			if(pa->data>qa->data){
				ra->next=qa;
				qa=qa->next;	}
			else{
				ra->next=pa;
				pa=pa->next;	}}
		if(pa->next!=NULL)
			ra->next=pa;
		if(qa->next!=NULL)
			ra->next==qa;
		return R;
	}

##### 计算二叉树的深度 #####
	int GetDepth(Tree t)
	{
		if(!t)
			return 0;
		int d1=GetDepth(t->leftChild);
		int d2=GetDepth(t->rightChild);
		return d1>d2?d1+1:d2+1;
	}

##### 在字符串中找出连续最长的数字串,并把这个串的长度返回,并把这个最长数字串付给其中一个函数参数outputstr所指内存.例如:"abcd12345ed125ss123456789"的首地址传给intputstr后,函数将返回 9,outputstr所指的值为123456789 #####
	int Continumax( char *inputstr,char *outputstr)
	{
		char *in = inputstr, *out = outputstr, *temp=NULL, *final=NULL;
		int count = 0, maxlen = 0;
	
		while( *in != '\0' )
		{
			if( *in > 47 && *in < 58 )
			{
				for(temp = in; *in > 47 && *in < 58 ; in++ )
					count++;
			}
			else
				in++;
	
			if( maxlen < count )
			{
				maxlen = count;
				count = 0;
				final = temp;
			}
		}
		for(int i = 0; i < maxlen; i++)
		{
			*out = *final;
			out++;
			final++;
		}
		*out = '\0';
		return maxlen;
	}

##### 求n个数（1....n）中k个数的组合,如:combination(5,3)要求输出：543，542，541，532，531，521，432，431，421，321 #####
	int stack[3]={0};
	int top=-1; 
	int push(int i)
	{
		stack[++top]=i;
		if(top<2)
			return 0;
		else
			return 1;
	}
	int pop(int *i)
	{
		*i=stack[top--];
		if(top>=0)
			return 0;
		else
			return 1;
	}
	void combination(int m,int n)
	{
		int temp=m;
		push(temp);
		while(1)
		{
			if(1==temp)
			{
				if(pop(&temp)&&stack[0]==n) //栈底元素弹出&&为可能取的最小值,循环退出
					break;
			}
			else if( push(--temp))
			{
				cout<<stack[0]<<stack[1]<<stack[2]<<endl;
				pop(&temp);
			}
		}
	}
	void main()
	{	
		combination(5,3);	
	}
	

