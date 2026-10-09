用来描述”真“或”假“

sizeof(bool)  =  1       -128 — 127 ？

取值范围：true，false

非0即真

```C++
#include <stdio.h>

int main()
{
	bool a = true;
	a = false;
	a = 123;
	a = 0;
	
	printf("%d\n", sizeof*(bool));
	return 0;
}
```