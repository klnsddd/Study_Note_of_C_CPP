this指针是系统自动生成，且隐藏的
this指针不是对象的一部分，作用域在类内部
类的普通函数访问类的普通成员时，this指针总是指向调用者对象。
this指针用于区分**重名**的数据成员与成员函数中的参数

每个对象都有各自新建的数据成员，但成员函数是在类中由所有对象共用的

![[Pasted image 20251121160113.png]]



```C++

class MyClass
{
	int num;
public:
	void setNum(int num) //隐藏的指针(MyClass* this, int num)
	{
		this->num = num;
	}
	int getNum()
	{
		this->num;    //各种用法
		this->setNum();
		(*this).num;
		return num;
	}
};

int main()
{
	MyClass obj_1;
	obj_1.setNum(10);  //隐藏的传参(&obj_1, 10)
	cout << "num = " << obj_1.getNum() << endl;
	return 0;
}
```