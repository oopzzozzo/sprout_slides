# C++ string
#### 2018資訊之芽 語法班
###### 葛家聿
參考2017 bookgin 投影片

---

## 字元陣列

```cpp
// 比較兩組自白是否相同
 // 宣告最長1024
char confessA1[1024], confessA2[1024];
char confessB1[1024], confessB2[1024];
 // 輸入
std::cin >> confessA1 >> confessB1;
std::cin >> confessA2 >> confessB2;
 // 把2接到1後面
strcat(confessA1, confessA2);
strcat(confessB1, confessB2);
 // 輸出比較結果
std::cout << (strcmp(confessA1, confessB2)==0);
```

有點冗

----

### 我們想要好用一點
- 不用先決定長度
- 可以用 + 連接, 用 == 比較......

---

## C++ string

```cpp
#include <string>
std::string confessA;

char old_confess[] = "I was sleeping.";

std::string confessB = "I was coding.";
std::string confessC = confessB;
std::string confessD = old_confess;
std::string confessE("I was live on YouTube.");
std::string confessF(confessE);
std::string confessG(old_confess);
```

----

剛剛的程式

```cpp
// 比較兩組自白是否相同
 // 宣告
std::string confessA1, confessA2;
std::string confessB1, confessB2;
 // 輸入
std::cin >> confessA1 >> confessB1;
std::cin >> confessA2 >> confessB2;
 // 輸出比較結果
std::cout << ((confessA1 + confessA2) == (confessB1 + confessB2));
```

----

## C++ string 的其他功能

```cpp
std::string str1, str2;
 // 複製字串 strcpy(str1, str2)
str1 = str2; // 不用擔心空間問題

 // 取得字串長度 strlen(str1)
str1.size();
str1.length(); // 跟size()完全一樣，除了名字以外

 // 連接字串 strcat(str1, str2)
str1 += str2;

 // 比較字典序 strcmp(str1, str2)
(str1 > str2);
(str1 >= str2);
```

----

## C++ string 的其他功能

```cpp
 // 取得字元
std::string confess("I was live on YouTube.");
std::cout << confess[2]; // w 不會檢查長度
std::cout << confess.at(2); // w 會檢查長度

 // 跟字元陣列的關係
char old_confess[] = "I was sleeping.";
std::string confess = old_confess; // 這裡沒問題
old_confess = confess; // 不可以這樣寫，會CE
```

不要把字元陣列跟string混在一起用

----

## C++ string 的其他功能

```cpp
//                   0123456789012345678012
std::string confess("I was live on YouTube.");
 // 尋找字串 find(字串)
int index = confess.find("was"); // 2
int index = confess.find("was not"); // std::string::npos

 // 分割字串 substr(起始位置，長度)
confess.substr(11); // on YouTube
confess.substr(11, 2); // on
```
`find` 的回傳型態其實是 `std::size_t`

----

## 更多其他功能
[C++ reference](http://www.cplusplus.com/reference/string/string/)

---

## 練習
[441-禮貌校園](https://neoj.sprout.tw/problem/441/)

- 你可能需要 getline() 讀到換行

```cpp
// 函式原型
std::getline(isstream, string);

std::string::str;
std::getline(std::cin, str); // 從 std::cin 讀一行到 str
```
