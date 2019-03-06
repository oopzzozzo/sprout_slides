# 亂數
#### 2018資訊之芽 語法班
###### 葛家聿

---

## 亂數的功用
抽籤、擲骰子、換座位、下棋軟體......

![random book](https://images-na.ssl-images-amazon.com/images/I/416-PAZ370L._SX384_BO1,204,203,200_.jpg)

---

## 亂數的用法

```cpp
#include <iostream>
#include <stdlib.h>
int main(){
	for(int i=0; i<10; i++)
		std::cout << rand() << std::endl;
}
```
----

## 亂數種子
* 改變執行結果

```cpp
#include <iostream>
#include <stdlib.h>
int main(){
		srand(7122);
		for(int i=0; i<10; i++)
			std::cout << rand() << std::endl;
}
```

----

## 每次不一樣
* 用時間來當亂數種子

```cpp
#include <iostream>
#include <stdlib.h>
#include <time.h>
int main(){
		srand(time(NULL));
		for(int i=0; i<10; i++)
			std::cout << rand() << std::endl;
}
```
----

以上是簡單的用法

[C++11 random](http://chino.taipei/note-2016-1020C-11-%E7%9A%84-Random-library-%E4%BD%A0%E9%82%84%E5%9C%A8%E7%94%A8rand-%E5%97%8E/)

---

## 原理
透過固定的運算產生下一個數字

```cpp
static unsigned long int next = 1;

int rand(void) // RAND_MAX assumed to be 32767
{
    next = next * 1103515245 + 12345;
    return (unsigned int)(next/65536) % 32768;
}

void srand(unsigned int seed)
{
    next = seed;
}
```
[資料來源](https://stackoverflow.com/questions/4768180/rand-implementation)

----

## 細節
* 亂數大小有限

```cpp
std::cout << RAND_MAX << std::endl;
```


