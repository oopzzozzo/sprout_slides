# while 迴圈
#### 2018資訊之芽 語法班
###### 葛家聿

---

## 迴圈的用處
* 讓電腦做重複的事情

```cpp
std::cout << 1 << std::endl;
std::cout << 2 << std::endl;
std::cout << 3 << std::endl;
...
std::cout << 600 << std::endl;
```

----

![夜市遊戲](https://uc.udn.com.tw/photo/2015/08/28/1/1254889.jpg)

---

## while 的用法
* 當 x <= 600 時， 輸出 x。

```cpp
int x = 1;
while (x <= 600) {
    std::cout << x << std::endl;
    x++;
}
```

----

```cpp
while (條件式) {
    要做的動作;
    要做的動作;
    ...
    要做的動作;
}
```

----
![while 流程圖](https://drive.google.com/uc?id=1K1VVryRs77ArJDryD4yqxdRD7_ztsHtF)

----

## 視覺化教學
https://goo.gl/Fub8pG

----

![cout 流程圖](https://drive.google.com/uc?id=1PCz09Tm7tKkMvJy7naHTJKNbdxp1K5Ab)

---

## 練習
[階乘](https://neoj.sprout.tw/problem/107/)

---

## while 可以做的事

----

* 偷懶，不加大括號（限一行）

```cpp
int x = 1;
while (x <= 600)
    std::cout << x++ << std::endl;
```

----

* 無限迴圈

```cpp
int x = 1;
while (x <= 600)
    std::cout << x << std::endl;
```
x 值不變，永遠小於等於 600

----

* 再包一層迴圈或判斷
* 建質數表

```cpp
int range = 100;
int test_prime = 2;
while(test_prime <= range){
    bool is_still_prime = 1;
    int divisor = 2;
    while(divisor < test_prime){
        if(test_prime % divisor == 0)
            is_still_prime = 0;
        divisor++;
    }
    if(is_still_prime == 1)
        std::cout << test_prime << std::endl;
    test_prime++;
}
```

----

* 被跳過

```cpp
int x = 31995;
while (x <= 600)
    std::cout << x << std::endl;
```
x 一開始就大於 600

----

![while 流程圖](https://drive.google.com/uc?id=1K1VVryRs77ArJDryD4yqxdRD7_ztsHtF)

----

* do-while
* 不會一開始就被跳過

```cpp
int x = 31995;
do{
    std::cout << x << std::endl;
}
while (x <= 600);
```
do-while 的 while 後面要加分號

----

![do-while 流程圖](https://drive.google.com/uc?id=1e5l2maT4NAz4_geFOfUCWqH9mt65orZh)
