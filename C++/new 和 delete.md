new类似于malloc
delete类似于free

```C++
#include <iostream>
using namespace std;

int main()
{
	//1.申请单个内存
	int* p1 = new int;
	*p1 = 0;
	
	//2.申请单个内存且初始化
	int* p2 = new int(0);
	cout << "*p2 = " << *p2 << endl;
	
	//3.批量申请(连续内存), 无法初始化，后续再初始化
	int* p3 = new int[10];
	for (size_t i=0; i<10; i++)
	{
		p3[i] = i;
		cout << "p3[" << i << "] = " << p3[i] << endl;
	}
	
	//4.释放单个内存
	delete p1;
	delete p2;
	//5.释放连续内存
	delete[] p3;
	
	return 0;
}
```