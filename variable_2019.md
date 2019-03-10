# 表達式與變數
#### 2019資訊之芽 語法班
###### 葛家聿
改編自bookgin 2018

---

## Hello world
把下面的程式碼複製貼上到Dev-C++
```cpp
#include <iostream>

int main() {
    std::cout << "Hello World!\n";
    std::cout << "What is 6/2(1+2)?\n";
    std::cout << "It is " << 6/2*(1+2) << std::endl;
    return 0;
}
```

----

## Hello world
這個程式好沒用喔
```cpp
Hello World
What is 6/2(1+2)?
It is 9 
```

----

## 解一元二次方程式
```cpp
#include <iostream>
#include <cmath>

int main(){
    // ax^2 + bx + c = 0
    double a, b, c;
    std::cin >> a >> b >> c;
    std::cout << (-b+sqrt(b*b-4*a*c))/(2*a) << ", ";
    std::cout << (-b-sqrt(b*b-4*a*c))/(2*a) << std::endl;
    return 0;
}
```

---

## 合法的程式 <!-- 編譯器看得懂的意思 -->
<!-- 兩份code的共通點 -->
* 引入標頭檔，就像是指令的說明書
<!-- 康熙大字典，大英百科全書 -->
* 你需要記得什麼功能在哪本說明書裡
<!-- 兩條斜線代表註解(注意方向) -->
```cpp
#include <iostream> // std::cout, std::cin
#include <cmath>    // sqrt
```
* 一個名為main的函數(function)<!-- 功能 程式 -->
* 顧名思義，主程式<!-- 主畫面 -->，程式由此開始執行
```cpp
int main(){
    // 你想做的事(依序)
    return 0;
}
```
<!-- return -->

---

## 輸入輸出
<!-- 從結果反推 -->
* std::cout (大家都念see-out) 代表輸出
* std::cin (大家都念see-in) 代表輸入
* 注意箭頭方向不同，可以想像成資料流向
* 引號裡面的東西就會被解讀成[字或特殊符號](https://en.cppreference.com/w/cpp/language/escape)
* 記得要最後要加分號，表示敘述句結束<!-- 就跟背注釋要加句號一樣重要 -->
```cpp
std::cout << "It is " << 6/2*(1+2) << std::endl;
std::cin >> a >> b >> c;
```

---

## 表達式
* 廣義的算式，代表一個**值** <!-- 方程式不算 -->
* 由運算子(動詞)和運算元(名詞)組成
* 先乘除後加減，每個運算的[優先度](https://en.cppreference.com/w/cpp/language/operator_precedence)不同

```cpp
(-b-sqrt(b*b-4*a*c)/(2*a) // 值由a, b, c的值決定
7122 % 20 // 取餘數運算，算出的值為2
0 < 3 // 小於運算, 算出的值為True，也就是1

6/2(1+2) // 少了乘號，編譯器看不懂
a*x*x + bx + c = 0 // 這是方程式，本身沒有值，編譯器看不懂
```
<!-- 加不加空隔沒差 -->

---

## 變數 <!-- 會變得數字, 微檔案 -->
* 使用前需要宣告，決定[型態](https://en.cppreference.com/w/cpp/language/types)，取個好名字
<!-- 型態就好像副檔名 -->
* 必須是英文或底線開頭，後面可以有數字
* 不可以使用保留字 <!-- 習大大 -->
* 大小寫不同
<!-- 記得分號 -->

```cpp
double a, b, c; // 三個小數
int my_money_1day = 314159, price = 8740; // 兩個整數
int my_money_2day = my_money_1day - price; // 一個整數
```

----

## 變數
* 可以讀，可以寫，存在<!-- 雙關 -->電腦某處(通常是在記憶體)
* 讀值的時候，直接當數值使用
* 寫值的時候，通常用等號來寫
* 這個等號就是[賦值](https://en.cppreference.com/w/cpp/language/operator_assignment)的意思，跟數學課的等號無關
* 等號左邊稱為lvalue、右邊稱為rvalue
<!-- 剛剛的方程式 -->

```cpp
#include <iostream>
int main(){
    int price = 8740;
    int my_money_Monday = 314159;
    int my_money_Tuesday = my_money_Monday - price;
    my_money_Monday = my_money_Monday - price*6; // 寫入
    my_money_Monday -= price * 7; // 偷懶的寫法
    std::cout << my_money_Monday * 1.0106 << std::endl;
    return 0;
}
```

---

## 不好的示範
大家不要學<!-- but I still want to say -->
```cpp
#include <iostream>
int main(){
    int my_money=59457, price=879457  // 沒有分號
    bool have_money, 1_thing_to buy=0; // 數字開頭、有空隔
    my_money <- (my_money - buy*price); // <- 不能給值，請用= 
    have_Money = my_Money <> 0; // 沒有宣告(大寫)、不等於請用!=
    std::cin << price; // 方向錯
    std::cout << "我" < have_Money << "定不是沒錢\n"; // 小於?
    std::cout << yee~ << my_Money > 0; // 沒引號，>運算要加括號
    return 0;
}
```

----

## 表達式&敘述句
* 敘述句(statements)代表會產生一些「作用」
* 表達式(expressions)則被算為值
* 結尾有分號的expression都是statement
* 現在你可能分不出來,未來會談到幾個新的敘述句
<!-- 記事本開記事本, 編譯器編編譯器 -->
<!-- std::cout "<<" -->

---

## 好的示範
* 解二元一次方程式

$\begin{cases}a_1x + b_1y = c_1 \\\\ a_2x + b_2y = c_2\end{cases}$
* 假設
  * 恰一組解
  * 我們只需要解出數值
  * 我們知道[克拉瑪公式](https://zh.wikipedia.org/zh-tw/%E5%85%8B%E8%90%8A%E5%A7%86%E6%B3%95%E5%89%87)

----

## 解二元一次方程式
古人一連串的推倒......得到克拉瑪公式
$(x, y) = \left(\frac{c_1b_2-c_2b_1}{a_1b_2-a_2b_1}, \frac{c_1a_2-c_2a_1}{a_1b_2-a_2b_1}\right)$

----

## 解二元一次方程式
* 電腦能機械化、自動化的來幫我們解這個問題
<!-- 古人就有的概念，但我們有電腦 -->
* 將問題抽象化:
  - 我們有輸入 (某個未知的方程組)
  - 我們(會)有輸出 (解)
* 我們要做的就是寫一個程式讀入資料並輸出結果

----

## 解二元一次方程式
* 數字都要存成變數
$(x, y) = \left(\frac{c_1b_2-c_2b_1}{a_1b_2-a_2b_1}, \frac{c_1a_2-c_2a_1}{a_1b_2-a_2b_1}\right)$

```cpp
double a1, b1, c1;
double a2, b2, c2;

double x = (c1*b2 - c2*b1)/(a1*b2 - a2*b1);
double y = (a1*c2 - a2*c1)/(a1*b2 - a2*b1);
```

----

## 解二元一次方程式
* 化簡重複的部份

```cpp
double a1, b1, c1;
double a2, b2, c2;
double det = a1*b2 - a2*b1;
double x = (c1*b2 - c2*b1) / det;
double y = (a1*c2 - a2*c1) / det;
```

----

## 解二元一次方程式
* 輸入及輸出

```cpp
std::cin >> a1 >> b1 >> c1;
std::cin >> a2 >> b2 >> c2;
```
```cpp
std::cout << "x = " << x << "\ny = " << y << std::endl;
```

----

## 解二元一次方程式

```cpp
#include<iostream>
int main(){
  int a1, b1, c1, a2, b2, c2;
  std::cout << "solving system of linear equations\n\n";
  std::cout << " a1*x + b1*y = c1\n a2*x + b2*y = c2\n\n";
  std::cout << "> a1 b1 c1 := ";
  std::cin >> a1 >> b1 >> c1;
  std::cout << "> a2 b2 c2 := ";
  std::cin >> a2 >> b2 >> c2;
  int det = a1*b2 - a2*b1;
  int x = (c1*b2 - c2*b1)/det;
  int y = (a1*c2 - a2*c1)/det;
  std::cout << "x = " << x << "\ny = " << y << std::endl;
}
```

----

## 解二元一次方程組
* 我們在做什麼? 為什麼會想導出公式?
* 電腦是機器。它們會按照固定的指令來運作。
* 將抽象的「解方程組」轉換成實際的計算步驟。
* 當然我們也可以實作高斯消去法,但會需要用到判斷、迴圈和陣列等知識。但對於二元一次,只要用特定的公式便能解了

---

###### 老畫一張

![programming](https://pbs.twimg.com/media/CincD2pUUAAU55Q.jpg)

---

## 參考資料

* [特殊符號](https://en.cppreference.com/w/cpp/language/escape)
* [運算優先度](https://en.cppreference.com/w/cpp/language/operator_precedence)
* [型態](https://en.cppreference.com/w/cpp/language/types)
* [賦值](https://en.cppreference.com/w/cpp/language/operator_assignment)
