
##### 基本输入输出 #####
    void main()
	{
		int a,b,sum;
		printf("Please input information:\n");
		scanf("%d%d",&a,&b);
		sum=a+b;
		printf("Sum is %d\n",sum);
	}

##### 不同格式输出(o表示8进制,x表示16进制) #####
	void main()
	{
		int a=8;int b=15;
		printf("%o,%x,%s\n",a,b, "china");
	}

##### 基符号常量(简单文本替换) #####
	#define PI 3.1415
	void main()
	{
		double radius,area;
		cin>>radius;
		area=radius*radius*PI;
		printf("Area is %f",area);
	}

##### 数学函数 #####
	#include<math.h>
	void main()
	{
		float x,y;
		printf("输入 x :");
		scanf("%f",&x);
		if (x!=0) y=sin(x)/x;
		else y=1;
		printf("x=%5.2f\ty=%5.2f\n",x,y);
	}

##### 强制类型转换 #####
	void main()
	{
		float f=5.63;
		int i=(int)f;
		printf("(int)f=%d",i);
	}

##### 单个字符的输入和输出 #####
	void main()
	{
		char c;
		c=getchar();
		putchar(c);
		putchar('a'-32);
	}

##### 格式化输出 #####
	void main()
	{
		int a=121;
		printf("%5d",a);
		printf("%-8d",a);
		printf("%08d",a);
	
		int b=15;
		printf("%d,%o,%x",b,b,b);
	
		double c=123.456;
		printf("%f",c);
		printf("%5.3f",c);
		printf("%-7.2f",c);
	
		printf("%-4c",'A');
		printf("%20s","Hello");
	}

##### 实数的输入输出 #####
	void main()
	{
		float fx,fy;
		scanf("%f%e",&fx,&fy);
		printf("%f %f",fx,fy);
		double dx;
		scanf("%lf",&dx);
		printf("%.4lf",dx);
	}

##### 字符串的输入输出 #####
	void main()
	{
		char str1[10],str2[10];
		scanf("%s",str1);
		scanf("%10s",str2);
		printf("%-10s,%10s",str1,str2);
	}

##### if与switch语句 #####
	void main()
	{
		int a=2,b=3;
		if(a>b)
			printf("a>b");
		else
			printf("b>a");
	
		int day;
		scanf("%d",&day);
		switch(day)
		{
		case 1:
			printf("Monday");
			break;
		case 2:
			printf("Tuesday");
			break;
		case 3:
			printf("Wednesday");
			break;
		default:
			printf("Fuck");
		}
	}

##### while语句 #####
	void main()
	{
		int i=0,sum=0;
		while(i<=10)
		{
			sum+=i;
			i++;
		}
		printf("%d",sum);
	}

##### do,while语句 #####
	void main()
	{
		int i=0,sum=0;
		do
		{
			sum+=i;
			i++;
		}while(i<=10);
		printf("%d",sum);
	}

##### for循环 #####
	void main()
	{
		int i=0,sum=0;
		for(;i<=10;i++)
		{	sum+=i;	}
		printf("%d",sum);
	}

##### break与continue语句 #####
	void main()
	{
		int i=0,sum=0;
		for(;i<=100;i++)
		{
			if(0==i%2)
				continue;
			if(81==i)
				break;
			sum+=i;
		}
		printf("%d",sum);
	}

##### 一维数组 #####
	void main()
	{
		int a[5]={1,2,3,4,5};
		int b[]={6,7,8,9,10};
		int c[5]={11,12,13};
		for(int i=0;i<5;i++)
			printf("%d,%d,%d\n",a[i],b[i],c[i]);
		for(i=3;i<5;i++)
			scanf("%d",&c[i]);
		printf("%d,%d",c[3],c[4]);
	}

##### 二维数组 #####
	void main()
	{
		int a[2][3]={{1,2,3},{4,5,6}};
		int b[2][3]={1,2,3,4,5,6};
		int c[2][3]={1,2,3,4};
		for(int i=0;i<2;i++)
			for(int j=0;j<3;j++)
				printf("%d,%d,%d\n",a[i][j],b[i][j],c[i][j]);
	}

##### 字符数组 #####
	void main()
	{
		char a[5]={'h','e','l','l','o'};
		char b[6]="hello";
		char c[]="hello";
		puts(b);
		puts(c);
		gets(a);
		puts(a);
		scanf("%s",a);
		printf("%s",a);
	}

##### 字符串函数 #####
	#include"string.h"
	void main()
	{
		char a[20]="Hello";
		char b[20]="World";
		strcat(a,b);
		puts(a);
		strcpy(a,b);
		puts(a);
		printf("%d\n",strlen(b));
		if(0==strcmp(a,b))
			printf("Same");
		else if(strcmp(a,b)>0)
			printf("a is bigger");
		else
			printf("b is bigger");
	}

##### 基本函数调用 #####
	void main()
	{
		int Max(int a,int b);
		int a,b;
		scanf("%d%d",&a,&b);
		printf("Bigger one is %d\n",Max(a,b));
	}
	int Max(int a,int b)
	{	return a>b?a:b;	}

##### 引用 #####

>声明时必须初始化

	void main()
	{
		int a=1;
		int &b=a;   
		printf("%d\n",b);
		b=2;
		printf("%d\n",a);
	}

##### 引用做参数 #####
	void Swap(int &a,int &b)
	{
		int temp=a;
		a=b;
		b=temp;
	}
	void main()
	{
		int a=1,b=2;
		printf("%a=%d,b=%d\n",a,b);
		Swap(a,b);
		printf("%a=%d,b=%d\n",a,b);
	}

##### 宏定义 #####

>简单的文本替换，没有类型，不做任何类型检查

	#define PI 3.1515926
	#define Max(X,Y)   ((X)>(Y)?(X):(Y))
	void main()
	{
		double radius=3,area;
		area=PI*radius*radius;
		printf("%lf\n",area);
		float a=3.14,b=3.15,c;
		c=Max(a,b);
		printf("%.2f\n",c);
	}

##### 条件编译 #####
	#define DEBUG
	void main()
	{
		#ifdef DEBUG
			printf("DEBUG is defined!\n");
		#else
			printf("DEBUG is not defined!\n");
		#endif
	}
	/////////////////////
	void main()
	{
		#ifndef DEBUG
			printf("DEBUG is not defined!\n");
		#else
			printf("DEBUG is defined!\n");
		#endif
	}

##### 指针 #####
	void main()
	{
		int a=4,b=5;
		int *p1=&a,*p2;
		p2=&b;
		printf("%d,%d\n",*p1,*p2);

		scanf("%d",p1);
		printf("%d\n",*p1);

		p1=p2;
		printf("%d\n",*p1);

		int c[5]={1,2,3,4,5};
		p2=c;  //p2=&c[0];
		for(int i=0;i<5;i++)
			printf("%d\n",*(p2+i));		//printf("%d\n",*(p2++));

		char *ps;
		ps="Hello";   //char *ps="Hello";
		puts(ps);
	}
	/////////////////////
	void Swap(int *p1,int *p2)
	{
		int temp=*p1;
		*p1=*p2;
		*p2=temp;
	}
	void main()
	{
		int a=1,b=2;
		int *p1=&a,*p2=&b;
		printf("a=%d,b=%d\n",a,b);
		//Swap(&a,&b);
		Swap(p1,p2);
		printf("After Swap,a=%d,b=%d\n",a,b);
	}
	/////////////////////
	void main()
	{
		int a[3][3]={1,8,9,6,5,4,7,3,2},max;
		int (*p)[3];  //指向数组的指针
		p=a;
		max=**p;
		for(int i=0;i<3;i++)
			for(int j=0;j<3;j++)
				if(max<*(*p+j))
					max=*(*p+j);
				printf("The biggest one is %d\n",max);
	}
	
##### 函数指针(指向函数的指针) #####
	int Max(int a,int b)
	{	return a>b?a:b;	}
	void main()
	{
		int a=3,b=4,c;
		int (*fun)(int ,int);
		fun=Max;
		c=(*fun)(a,b);
		printf("The bigger one is %d\n",c);
	}

##### 指针型函数(返回值是指针) #####
	char *GetDay(int number)
	{
		char*day[8]={"Illegalday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday","Sunday"};  //指针数组
		return (number<7||number>1)?day[number]:day[0];
	}
	void main()
	{
		int day;
		printf("请输入数字:\n");
		scanf("%d",&day);
		puts(GetDay(day));
	}
	
##### 指向指针的指针 #####
	void main()
	{
		char *name[]={"John","Sophia","Mark","Marry"};
		char **p;
		for(int i=0;i<4;i++)
		{
			p=name+i;
			printf("%s\n",*p);
		}
	}

##### 结构体 #####
	void main()
	{
		struct student{
			long int number;  //不能在结构体内初始化
			char name[20];
			float score;
		};
		struct student stu={20110316,"John",98.9};
		printf("Name:%s , Number:%d , Score:%.1f \n",stu.name,stu.number,stu.score);
		struct student *stup=&stu;
		printf("Name:%s , Number:%d , Score:%.1f \n",stup->name,stup->number,stup->score);
	}

##### 动态内存分配 #####
	#include "stdlib.h"
	#include "string.h"
	struct student
	{
		char name[20];
	};
	void main()
	{
		struct student *p;
		p=(struct student*)malloc(sizeof(struct student));
		if(p==NULL)
		{
			printf("Out of Memory!\n");
			exit(-1);
		}
		strcpy(p->name,"John");
		printf("%s\n",p->name);
		free(p);
	}

##### 联合 #####
	union myInfo
	{
		int age;
		double score;
	};
	void main()
	{
		union myInfo m,n;
		m.age=10;
		n.score=99.9;
		printf("%d,%lf\n",m.age,n.score);
	}