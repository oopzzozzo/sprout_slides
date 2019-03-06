# C++ stream
#### 2018資訊之芽 語法班
###### 葛家聿
參考2017 bookgin 投影片

---

## cmd 標準輸入輸出

```cpp
while(std::cin >> x)
	std::cout << "you input " << x << std::endl;
```

----

## 這不是讀檔啊

![GBA 模擬器](https://pic.jcku.com/upload/allimg/110319/1_110319193659_1.jpg)

讀檔應該是這樣
- 開啟遊戲
- 遊戲存檔

---

## fstream

----

## 讀檔
輸出檔案內容

```cpp
#include <fstream>
std::ifstream fin; // 宣告 ifstream 物件叫作 fin
fin.open("myfile.txt"); // 讓 fin 打開 myfile.txt 這個檔案來讀
std::string str;
while(fin >> str) // 把 fin 當 cin 用
  std::cout << str << std::endl;
fin.close(); // 關閉 fin 現在打開的檔案
```

- 記得close()釋放記憶體

----

## 寫檔

```cpp
#include <fstream>
std::ofstream fout; // 宣告 ofstream 物件叫作 fout
fout.open("myfile.txt"); // 讓 fout 打開 myfile.txt 這個檔案來寫
std::string str = "Hello, file!";
fout << str << std::endl;
fout.close(); // 關閉 fin 現在打開的檔案
```

- ofstream::open() 時會自動產生並清空檔案。
- 如果不想清空檔案的話, 可以寫在檔案後面

```cpp
file_out.open("myname.txt", std::ofstream::app);
```

----

## 練習

---

## stringstream

----

### stream 是個好東西

- 可以流來流去
- 何不把 string 也變成 stream

----

## stringstream

```cpp
#include <sstream>
std::stringstream ss; // 宣告 stringstream 物件
ss << "1 2 3" << " 4 5";
int n;
while(ss >> n)
  std::cout << n+10;
```

把字串丟進ss後，分別加10輸出

----

## 練習
[向量加法](https://neoj.sprout.tw/problem/442)

- 你可能需要 getline()

---

## 格式化I/O

----

## 格式化I/O
 
小數
```cpp
#include <iomanip> // manipulate

// 控制位數
std::cout << std::setprecision(3); 
std::cout << 3.14159; // 3.14

// 控制小數
std::cout << std::fixed << std::setprecision(4);
std::cout << 3.14159; // 3.1416

// 科學記號
std::cout << std::scientific << std::setprecision(2);
std::cout << 3.14159; // 3.14e+00
```
- 各行的效果會一直保留

----

## 格式化I/O
 
表示
```cpp
// 八進位 120
std::cout << std::oct << 80 << std::endl;

// 十進位 80
std::cout << std::dec << 80 << std::endl;

// 十六進位 50
std::cout << std::hex << 80 << std::endl;

// true/false true
std::cout << std::boolalpha << (bool)(1)<< std::endl;

// 設定寬度(預設可能是十六進位，效果不會保留)
std::cout << std::setw(10) << std::oct << 80 << std::endl;
```
- 各行的效果會一直保留

----

## 更多其他功能
[C++ reference](http://www.cplusplus.com/reference/iomanip/)

