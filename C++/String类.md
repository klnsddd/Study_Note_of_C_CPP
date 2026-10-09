- String是C++中的字符串
- 类似于C语言中的字符数组
- 其中包括许多方法，使用时需要额外包含 `<string>`

```C++
#include <iostream>
#include <string>
using namespace std;

int main()
{
	string str;
	str = "abc123";  //独特操作
	str.lenth();
	str.clear();
	str.empty();
	if (str1 == str2)
	{}
	char  ch = str[2];
	ch = str.at(1);
	return 0;
}

```