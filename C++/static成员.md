静态成员
在C++类中声明成员时，加上static关键字
静态成员分为静态数据成员和静态函数成员
# 静态数据成员
- 所有对象共享类中的同一个static数据成员（static变量是可修改值的）
- static数据成员是存储在全局数据区，比Class的生命周期长，所以要在类外初始化，之后就能在类内外正常使用了
- static数据成员还可以通过 `类名::数据名` 来从类外访问，普通数据成员是不能这么访问，得从对象名访问
# 静态函数成员
- 类内类外定义都可以，声明的时候加static即可
- 可以不依赖对象而通过`类名::数据名` 来从类外访问，注意普通函数成员必须从对象名访问
- 注意静态函数内不能用到需要定义对象才能用到的数据（普通数据成员），普通函数成员也不能调用，因为普通函数成员可能会用到普通数据成员
- 构造函数不是普通函数成员，所以可以被静态函数调用

```C++
#include <iostream>
using namespace std;

class ClassName
{
public:
	ClassName();
	~ClassName();
	
	static int num;
	static void testFunc_1();  //声明的时候加static即可
};

int ClassName::num = 0;   //可以在类外对类内的静态成员进行初始化
//静态成员是存储在全局数据区，比ClassName的生命周期长，所以要在类外初始化

void ClassName::testFunc_1()
{
	cout << "ClassName::testFunc_1()" << endl;
}

ClassName::ClassName()
{
	num++;   //可以记录创建了多少个对象
}

ClassName::~ClassName()
{
}

int main()
{
	ClassName obj_1;
	cout << "obj_1.num = " << obj_1.num << endl;
	
	obj_1.num = 10;
	
	ClassName obj_2;
	cout << "obj_2.num = " << obj_2.num << endl;
	
	cout << "sizeof(obj_1) = " << sizeof(obj_1) << endl;
	//输出是1，对应obj_1中没有任何数据成员，而static int num是4字节，位于类中
	cout << "num = " << ClassName::num << endl;
	
	ClassName::testFunc_1();
	
	return 0;
}

```