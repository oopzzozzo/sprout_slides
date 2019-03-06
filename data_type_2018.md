# 資料型別與轉型
#### 2018資訊之芽 語法班
###### 葛家聿

---

## 資料型別是什麼
* 變數的種類
* 佔有空間，能表示不同東西
* 可以加修飾字
* 我們已經學過的有int和char

---

## 有哪些型別？
* 整數		int
* 浮點數	float, double
* 字元		char
* 布林		bool

----

## 整數 int
* 以二進位儲存
* 得知空間大小(因裝置而異）

```cpp
std::cout << sizeof(int);
```

----

|  int  |  $-2^{31}$ ~~ $2^{31}-1$ <br> -2,147,483,648  ~~  2,147,483,647 |
|-------|-------------------------|--------------------------------|
| <div style="width:6em;">unsigned int</div> | 0  ~~  $2^{32}-1$ <br> 0  ~~  4,294,967,296               |
| short | $-2^{15}$  ~~  $2^{15}-1$  <br> -32,768  ~~  32,767               |
| long  |  $-2^{31}$  ~~  $2^{31}-1$ <br> -2,147,483,648  ~~  2,147,483,647 |
| long long |  $-2^{63}$  ~~  $2^{63}-1$ <br> -9,223,372,036,854,775,807  ~~  9,223,372,036,854,775,807 |

----

## 浮點數 float
* 以科學記號儲存
* 準確度有限

![格式](https://i.stack.imgur.com/AyCTR.png)

----

| float  | $\pm 10^{-37}$ ~~ $10^{38}$ | 7位左右  |
|--------|--------------|----------|
| double | $\pm 10^{-307}$ ~~ $10^{308}$ | 16位左右 |
| long double | $\pm 10^{-4931}$ ~~ $10^{4932}$ | 19位左右 |

* 不能使用unsigned

----

## 字元 char
* ASCII 0 ~~ 127

![ascii table](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/USASCII_code_chart.png/300px-USASCII_code_chart.png)

----

| char          | -128 ~~ 127 |
|---------------|-------------|
| unsigned char | 0 ~~ 255    |

----

## 布林 bool
* true, false
* 1, 0


---

## 型別轉換
* 自己手動轉
* 編譯器幫你轉
* 不會改變變數型別（函數）

----

## 自己轉
* (資料型態)變數
* static_cast <資料型態>(變數)

```cpp
std::cout << (int)3.14159; 				// 3
std::cout << (float)5 / (float)2; // 2.5
std::cout << (float)(5/2);        // 2
std::cout << (char)(97);          // a

std::cout << static_cast <int>(3.14159);
std::cout << static_cast <float>(5) / static_cast <float>(2);
std::cout << static_cast <float>(5/2);
std::cout << static_cast <char>(97);
```

----

## 編譯器轉
* 整數與浮點數相加

```cpp
std::cout << 3.14 + 1; //4.14
std::cout << (int)(3.14) + (double)(1.2); // 4.2
```

