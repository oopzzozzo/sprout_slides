# 指標、函數、參考
#### 2018資訊之芽 語法班
###### 葛家聿

---

## 複習 - 指標
* 儲存一個記憶體位址

```cpp
int sleep_hours = 8;
int *my_alarm = &sleep_hours;  // 宣告指標my_alarm == 0x69fef8
my_alarm == &sleep_hours;      // true 0x69fef8
*my_alarm == sleep_hours;      // true 8
my_alarm == &**&my_alarm;      // true 0x69fef8
```

![解釋指標](https://i.imgur.com/4aeU3Py.png)

----

## 複習 - 陣列
* 一連串的記憶體
* 指標，指向最前面的記憶體

```cpp
int a[100];
a[1] = 1;
a == &a[0];        // true 陣列a就是指向a[0]的位址
a[1] == *(a + 1);  // true 陣列a的下一個int
a[1] == 1[a];      // true 混亂程式碼
```

----

## 複習 - 函式
* 可以被重複呼叫的功能

```cpp
int add(int a, int b)
{
    printf("我要做加法囉~");
    int c = a + b;
    return c;
}
```
----

![注意事項](https://i.imgur.com/0SSzwQi.png)

---

## 函數的裏面與外面
* 函數裏面做的事情不會影響外面
* 陣列, call by reference 例外

----

## CALL BY VALUE
* 複製一份值(value)在函數裏面跑
* 函數裏面做的事情不會影響外面
* 注意namespace std裡面也有一個std::swap

```cpp
void swap(int a, int b) {
	int tmp = a;
	a = b;
	b = tmp;
}
int main()
{
	int a = 5, b = 3;
	std::cout << a << " " << b << std::endl; // 5 3
	swap(a, b);
	std::cout << a << " " << b << std::endl; // 還是 5 3
}
```
[視覺化教學](https://goo.gl/bUz4YM)

----

## CALL BY ADDRESS
* 複製一份位址(address)在函數裏面跑
* 可以更改位址上的值

```cpp
void swap(int *a, int *b) {
	int tmp = *a;
	*a = *b;
	*b = tmp;
}

swap(&a, &b);
```
[視覺化教學](https://goo.gl/CDTfY9)

----

## CALL BY REFERENCE
* C++ 才有, 好用
* 幫外面的變數取一個別名
* reference 可以想成指標常數
* std::swap

```cpp
void swap(int &a, int &b) {
	int tmp = a;
	a = b;
	b = tmp;
}

swap(a, b);
```
[視覺化教學](https://goo.gl/heOG1h)

----

## 練習
* 試著用自己喜歡的方式寫swap
* using namespace std 請小心

---

## 範例

----

## [3n+1 Problem](https://neoj.sprout.tw/problem/220/)
* 普通的寫法

```cpp
int main(){
	int n, counter;
	for(counter = 0; n!=1; counter++)
		if(n % 2)
			n = 3*n + 1;
		else
			n /= 2;
	std::cout << counter << std::endl;
}
```

----

## [3n+1 Problem](https://neoj.sprout.tw/problem/220/)
* 用函式、counter 放全域（不推薦）

```cpp
int counter = 0;
int san_n_jai_i(int n){
	counter ++;
	if(n % 2)
		return 3*n + 1;
	else
		return n/2;
}
int main(){
	int n;
	while(n != 1)
		n = san_n_jai_i(n);
	std::cout << counter << std::endl;
}
```

----

## [220 - 3n+1 Problem](https://neoj.sprout.tw/problem/220/)
* 直接修改n
* 回傳是否繼續

```cpp
int san_n_jai_i(int &n){
	if(n == 1)
		return 0;
	if(n % 2)
		n = 3*n + 1;
	else
		n = n/2;
	return 1;
}
int main(){
	int n, counter = 0;
	while(san_n_jai_i(n))
		counter ++;
	std::cout << counter << std::endl;
}
```

----

## [220 - 3n+1 Problem](https://neoj.sprout.tw/problem/220/)
* 試試自己的寫法

----

## [236 - 榜單排序](https://neoj.sprout.tw/problem/236/)
[作業檢討](https://drive.google.com/open?id=14n8Io5zODNwtzoTPGUSjTHStlEbLgtV9)

----

## [236 - 榜單排序](https://neoj.sprout.tw/problem/236/)
* 傳陣列當參數
* 以下全相同

```cpp
admissionListSort(Student students[10], int size)
admissionListSort(Student students[], int size)
admissionListSort(Student *students, int size)
```

----

## 傳多維陣列
```cpp
admissionListSort(Student students[10][10], int size);
admissionListSort(Student students[][10], int size);
// 要有陣列大小，否則會CE

admissionListSort(Student **students, int size);  // 同下
admissionListSort(Student *students[10], int size)
// 一個陣列裡面放了很多指標
```

---

## 補充 - reference
* 取一個別名
* 最大的用途就是傳參考

```cpp
int sleep_hours = 8;
int &my_alarm = sleep_hours;
// 幫sleep_hours取一個別名叫my_alarm

my_alarm = 4;
std::cout << sleep_hours << std::endl; // 4
sleep_hours = 5;
std::cout << my_alarm << std::endl; // 5
&my_alarm == &sleep_hours // true
```
