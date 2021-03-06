# 一維陣列
#### 2018資訊之芽 語法班
###### 葛家聿

---

## 陣列的用處
* 迴圈做不到的事情

```cpp
std::cin >> a1 >> a2 ... >> a100;
std::cin >> b1 >> b2 ... >> b100;
std::cout << a1+b1 << a2+b2 ... << a100+b100;
```

----

## 重複的動作 ≠ 更多的變數

---

## 陣列的用法
* 一大條相同型態的變數
* 先宣告才能使用
* 通常會配合迴圈服用

```cpp
int a[6], b[6];
std::cin >> a[0] >> a[1] ... >> a[5]; //從零開始
std::cin >> b[0] >> b[1] ... >> b[5];
std::cout << a[0]+b[0] << a[1]+b[1] ... << a[5]+b[5] << std::endl;
```

----

## 視覺化教學
https://goo.gl/XKDKTF

----

* 宣告

```cpp
//型態 陣列名[陣列大小];
int a[100];
int a[100] = {1, 2, 3}; //沒指定滿大小，後面會自動補零
bool b[] = {1, 0, 1}; //沒指定大小，會自動計算大小
```

----

* 存取

```cpp
//陣列名[索引值];
int a[100]; //可以用 a[0] ~ a[99]
std::cout << a[0];
std::cin >> a[1];
a[2] = a[2] * 2;

int i = 3;
a[i] = i;
a[a[i]] = a[i];
```

---

## 練習
[我愛零分](https://neoj.sprout.tw/problem/294/)
