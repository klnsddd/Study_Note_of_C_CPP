cin的作用类似scanf
cout的作用类似printf
在具体使用时有些区别，不需要指定格式符（%d等）
这两个是对象，不是函数
- 注意使用头文件 `#include <iostream>`
- 使用 `using` 来简化 `cin` 和 `cout` 的使用

```C++
#include <iostream>
//using namespcae std;
using std::cin;
using std::cout;
using std::endl;

int main()
{
	//int num;
	//std::cin >> num;
	//std::cout << num <<std::endl; //endl是换行 
	
	int num;
	cin >> num;
	cout << "num = " << num << endl;
	
	int a, b, c, d, e, f;
	cin >> a >> b >> c >> d >> e >> f;
	cout << a << b << c << d << e << f;
	
	return 0;
}
```
