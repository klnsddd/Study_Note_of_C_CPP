- 权限掠夺者
- 掠夺函数权限：阻止重写
	- 如虚函数
	- 尽量不要对纯虚函数使用final，除非想要所有子类都为抽象类
- 掠夺类的权限：阻止派生
	如阻止子类派生子类

```C++
#include <iostream>
using namespace std;

class Father
{
public:
	Father();
	~Father();
	virtual void test_func();
};
class Son : public Father
{
public:
	Son();
	~Son();
	void test_func() final;  //GSon不能再重写test_func
};
class GSon : public Son final; //GGSon不能继承自GSon
{
public:
	GSon();
	~GSon();
	//void test_func();
};
class GGSon : public GSon
{
public:
	GGSon();
	~GGSon();
};

int main()
{
	
	return 0;
}

```