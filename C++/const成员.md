在C++类中声明对象成员时加上`const`关键字
常量成员分为常量数据成员和常量函数成员
- 必须使用初始化列表初始化常量数据成员
- 对于const函数，`const`写在圆括号后
- const函数在声明或定义时都不能省略`const`
- const函数中不能修改类中任何数据成员，只能访问，**除了`static`数据成员(从生命周期上理解原因)**
- 我们也可以设置`const`对象，同理只能修改static数据
	`const ClassName obj_1();`
	`ClassName const obj_2();`
	常对象不能调用普通函数成员（普通函数可能会修改普通数据），可以调用常函数，可以修改static数据 

```C++
#include <iostream>
using namespace std;

class ClassName()
{
public:
	ClassName();
	ClassName(int v);
	~ClassName();
	
	int num;        //下面的话对普通数据成员也成立
	const int val;  //若在此处初始化，所有对象的val都相同
	static int n;
	
	void test1()
	{
		cout << "test1()" <<endl;
	}
	void test2() const
	{
		cout << "test2()" <<endl;
	}
	void test3() const;
};

int ClassName::n = 0;
void ClassName::test3() const
{
	cout << "test3()" <<endl;
	n = 10;  //static数据成员可以修改
	this->n = 99;
}

ClassName::ClassName(): val(0)
{
}
ClassName::ClassName(int v): val(v)
{
}
ClassName::~ClassName()
{
}

int main()
{
	ClassName obj_1;
	obj_1.test1();
	obj_1.test2();
	return 0;
}
```