##### 基本输入输出 #####
	void main()
	{
		int a,b,sum;
		cout<<"Please input information:"<<endl;
		cin>>a>>b;
		sum=a+b;
		cout<<"a+b="<<sum<<endl;
	}

##### 自定义数据类型 typedef #####
	void main()
	{	
		typedef int fuck;
		fuck i=10;
		cout<<i<<endl;	
	}

##### const运算符 #####
	const MAX=100;
	void main()
	{
		for(int i=0;i<MAX;i++)
		{
			cout<<"Hello"<<endl;
		}
		const char*name="John";
		cout<<name<<endl;
	}

##### 枚举 #####
	enum MonthType
	{
		JAN,  FEB,  MAR,  APR,  
		MAY, JUN, JUL,  AUG,  
		SEP,  OCT,  NOV,  DEC
	};
	/////////////////////
	void main()
	{	
		MonthType thisMonth; 
		MonthType  thatMonth=FEB;
		thisMonth=JAN;  
		for(MonthType month = JAN; month<= DEC;month = MonthType(month+1))
		{	
			cout<<month<<endl;   //输出的是序号	
		}	
	}

##### 类相关 #####
	class Student
	{
	
			int age;    //没声明就默认是private属性
		private:
			char name[20];  //不能在声明的时候初始化
			char *department;
		
		public: 
			Student()       //默认构造函数
			{
			}
			Student(int age_,char name_[],char *department_)  //构造函数
			{
				age=age_;
				strcpy(name,name_);
				department=department_;
			}
			~Student()   //析构函数
			{
				//delete(department);
			}
			void Show()  //隐式声明的内联函数
			{
				cout<<"Name: "<<name<<", Age: "<<age<<", Department: "<<department<<endl;
			}
			char *GetName()  //显式声明的内联函数
			{
				return name;
			}
			void Set(int age_,char name_[],char *department_);  //在类的外部定义成员函数的声明
	
	};
	/////////////////////
			void Student::Set(int age_,char name_[],char *department_)  //在类的外部定义成员函数
				{
					age=age_;
					strcpy(name,name_);
					department=department_;
				}
	/////////////////////
	void main()
	{
		Student stu1(56,"John","Society");   //实例化一个对象
		stu1.Show();
	
		Student *stu2=new Student(55,"Sophia","Computer");   
		stu2->Show();         //对象的指针访问
		delete stu2;
	
		Student stu3,*p;
		stu3.Set(54,"Jonny","Computer");
		p=&stu3;
		cout<<p->GetName()<<endl; 
		cout<<(*p).GetName()<<endl;
	}

##### 用参数初始化表初始化数据成员 #####
	class Student
	{
		private:
			int age;
			int score;
			int weight;
		
		public: 
			Student(int age_,int score_,int weight_):age(age_),score(score_),weight(weight_){}
			//用参数初始化表初始化数据成员
	};

##### 动态内存分配 #####
	class Student
	{
		public: 
			char name[20];
			int age;
			int score;
			int weight;
	};
	void main()
	{
		Student *p;
		p=new Student;  //p=new Student();
		strcpy(p->name,"John");
		p->age=18;
		p->score=99;
		p->weight=98;
		cout<<p->name<<endl;
		delete p;
	}

##### this指针 #####
	class Book
	{
		private :
			string name;
		public:
			Book(string name)
			{		
				this->name=name;	
			}
			void show()
			{
				cout<<name<<endl;
			}
	};

##### 友元函数 #####
	class Time
	{
		private:
			int hour;
		public:
			Time(int hour):hour(hour){}
		
			friend void Show(Time t)
			{	cout<<t.hour<<endl;	}
		
			friend void SetHour(Time &t,int hour);
	};

	void SetHour(Time &t,int hour_)
	{	
		t.hour=hour_;	
	}
	
	void main()
	{	
		Time t(5);
		Show(t);
		SetHour(t,6);
		Show(t);	
	}


##### 友元成员 #####
	class Student;
	class Teacher
	{
		public:
			void SetScore(Student &s,int score);
	};
	class Student
	{
		private:
			int score;
		public:
			Student(int score):score(score){}
			void PrintScore()
			{
				cout<<score<<endl;
			}
			friend void Teacher::SetScore(Student &s,int score);
	};

	void Teacher::SetScore(Student &s,int score)
	{	
		s.score=score;	
	}
	void main()
	{	
		Student s(99);
		s.PrintScore();
		Teacher t;
		t.SetScore(s,100);
		s.PrintScore();		
	}

##### 友元类 #####
	class MyArray
	{
		private:
			int IntArray[10];
		public:
			MyArray(){}
			friend class LookUp;
	};
	
	class LookUp
	{
		public:
			int Max(MyArray ma);
			int Min(MyArray ma);
	};
	void main()
	{	
		MyArray ma;
		LookUp lu;
		cout<<"Max is :"<<lu.Max(ma)<<endl;
		cout<<"Min is :"<<lu.Min(ma)<<endl;	
	}

##### 运算符重载 #####
	class Complex
	{
		private:
			double real;
			double imag;
		public:
			Complex():real(0),imag(0){}
			Complex(double real,double imag):real(real),imag(imag){}
			void Display()
			{
				cout<<"("<<real<<","<<imag<<")"<<endl;
			}
			Complex operator+(Complex c);
	};

	Complex Complex::operator+(Complex c)
	{	
		Complex temp;
		temp.real=real+c.real;
		temp.imag=imag+c.imag;
		return temp;	
	}
	
	void main()
	{	
		Complex c1(6.8,10.5);
		Complex c2(5.7,6.9);
		Complex c3=c1+c2;
		c3.Display();	
	}

##### 简单公有继承 #####
	class Person
	{
		protected:
			int num;
			string name;
		public:
			Person(int num,string name):num(num),name(name){}
	};
	class Student:public Person
	{
		private:
			int age;
		public:
			Student(int age,int num,string name):Person(num,name)
			{
				this->age=age;
			}
	};


##### 多级继承派生 #####
	class Student
	{
		protected:
			int num;
			string name;
		public:
			Student(int num,string name):num(num),name(name){}
			void StudentShow()
			{
				cout<<num<<" , "<<name<<endl;
			}
	};
	
	class BigStudent:public Student
	{
		private:
			int age;
		public:
			BigStudent(int num,string name,int age):Student(num,name)
			{
				this->age=age;
			}
			void BigStudentShow()
			{
				StudentShow();
				cout<<age<<endl;
			}
	};
	
	class BiggerStudent:public BigStudent
	{
		private:
			int score;
		public:
			BiggerStudent(int num,string name,int age,int score):BigStudent(num,name,age)
			{
				this->score=score;
			}
			void BiggerStudentShow()
			{
				BigStudentShow();
				cout<<score<<endl;
			}
	};
	void main()
	{	
		BiggerStudent me(2011,"John",21,99);
		me.BiggerStudentShow();	
	}

##### 多继承 #####
	class A
	{
		public:
			A(int i)
			{	
				cout<<"A --"<<i<<endl;	
			}
	};
	
	class B
	{
		public:
			B(int i)
			{	
				cout<<"B --"<<i<<endl;	
			}
	};
	
	class C
	{
		public:
			C()
			{	
				cout<<"C --"<<endl;	
			}
	};
	
	class D:public A,public B,public C
	{
		private:
			A menberA;
			B menberB;
			C menberC;
		public:
			D(int i,int j,int k,int l):A(i),B(j),menberA(k),menberB(l){}
	};

##### 虚基类 #####
	class A
	{
		private:
			int a;
		public:
			A(int a):a(a){}
			void Show()
			{	
				cout<<"A--"<<a<<endl;
			}
	};
	
	class B1:virtual public A
	{
		private:
			int b1;
		public:
			B1(int a,int b1):A(a)
			{	
				this->b1=b1;	
			}
	};
	
	class B2:virtual public A
	{
		private:
			int b2;
		public:
			B2(int a,int b2):A(a)
			{	
				this->b2=b2;	
			}
	};
	
	class C:public B1,public B2
	{
		private:
			int c;
		public:
			C(int c,int b2,int b1,int a):A(a),B1(a,b1),B2(a,b2)
			{	
				this->c=c;	
			}
	};
	
	void main()
	{	
		C c(1,2,3,4);
		c.Show();		
	}

##### 虚函数(不能有虚构造函数,可以有虚析构函数) #####
	class Animal
	{
		public:
			virtual void Show()
			{	
				cout<<"Animal"<<endl;	
			}
	};
	
	class Bird:public Animal
	{
		public:
			void Show()
			{	
				cout<<"Bird"<<endl;	
			}
	};
	
	class Sparrow:public Bird
	{
		public:
			void Show()
			{	
				cout<<"Sparrow"<<endl;	
			}
	};
	
	void main()
	{	
		Animal animal,*p;
		Bird bird;
		Sparrow sparrow;
		p=&animal;
		p->Show();
		p=&bird;
		p->Show();
		p=&sparrow;
		p->Show();	
	}

##### 纯虚函数与抽象类 #####
	const double PI=3.1415926;
	class Figure  //抽象类(带有纯虚函数的类称为抽象类)
	{
		public:
			virtual double Area()=0;   //声明纯虚函数
	};
	
	class Circle:public Figure
	{
		private:
			double radius;
		public:
			Circle(double radius):radius(radius){}
			double Area()
			{	
				return radius*radius*PI;
			}
	};

##### 函数模板 #####
	template<class T>
	T Max(T a,T b)
	{
		return a>b?a:b;
	}
	void main()
	{	
		int a=1,b=2;
		int c=Max(a,b);   //参数只能是相同的类型,否则会报错
		cout<<"Max one is "<<c<<endl;
		double d=3.5,e=6.5;
		double f=Max(d,e);
		cout<<"Max one is "<<f<<endl;	
	}

##### 类模板 #####
	template<typename T>
	class Information
	{
		private:
			T info;
		public:
			Information(T info):info(info){}
			void SetValue(T info);
			void Show();
	};

	template<class T>
	void Information<T>::SetValue(T info)
	{
		this->info=info;
	}

	template<class T>
	void Information<T>::Show()
	{
		cout<<info<<endl;
	}
	
	void main()
	{	
		Information<int> a(3);
		a.Show();
		a.SetValue(4);
		a.Show();
	
		Information<char> b('A');
		b.Show();
		b.SetValue('B');
		b.Show();		
	}

##### 类模板的派生 #####
	template<class T>
	class A
	{
		public:
			void ShowA(T a)
			{
			cout<<"A--"<<a<<endl;
			}
	};
	
	template<class X,class Y>
	class B:public A<Y>
	{
		public:
			void ShowB(X b){cout<<"B--"<<b<<endl;}
	};
	
	void main()
	{	
		B<char,int> b;
		b.ShowA(7);
		b.ShowB('A');	
	}



