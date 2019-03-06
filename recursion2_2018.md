# 遞迴+
#### 2018資訊之芽 語法班
###### 葛家聿

---

## 複習 - 遞迴

* 分解為同類的子問題
* 函數自己呼叫自己

----

![費氏數列](https://i.imgur.com/N3hRUG6.png)

[動畫](https://media.giphy.com/media/8OPxC6alN0SEQyvVRq/giphy.gif)&[視覺化教學](https://goo.gl/AQhy6A)

---

## 遞迴也可以
* 印出一些字
* 存取一個陣列

----

範例1：輾轉相除法
```cpp
int gcd(int a, int b){
	std::cout << "| " << a << " | " << b << "|\n";
	// 終止條件
	if(a*b == 0)
		return a+b;
	// 遞迴條件
	std::cout << "----------\n";
	if(a>b)
		return gcd(a%b, b);
	else
		return gcd(a, b%a);
}
```

----

範例2：回報費氏數列計算進度
```cpp
int fibonacci_report(int n){
	std::cout << "f(" << n << ")\n";
	// 終止條件
	if(n<=1)
		return n;
	// 遞迴條件
  return  fibonacci_report(n-2) + fibonacci_report(n-1);
}
```

----

範例3：回報費氏數列計算進度
```cpp
int F[100] = {0};
int fibonacci_report(int n){
	if(F[n]){
		std::cout << "我已經知道F" << n << "了\n";
		return F[n];
	}
	if(n<=1)
		return n;
	std::cout << "我要算F" << n << "\n";
    F[n] = fibonacci_report(n-2) + fibonacci_report(n-1);
	std::cout << "我算出F" << n << "=" << F[n] << "了\n";
    return F[n];
}
```

----

## 練習
將範例2排版

* 縮排由樹的深度決定
* 把縮排也當成一個參數

----

## 比較難的練習
[153-文字轉轉轉](https://neoj.sprout.tw/problem/153/)
* 不用next permutation的話要怎麼做?

---

## [河內塔](https://zh.wikipedia.org/zh-tw/%E6%B1%89%E8%AF%BA%E5%A1%94)
* 經典中的經典
* 除了計算步數，我們要輸出搬動教學

----

## 練習
河內塔


---

## DFS
* 深度優先搜尋
* 一種暴力搜尋，可以解決很多問題

![動畫](https://media.giphy.com/media/8OPxC6alN0SEQyvVRq/giphy.gif)

----

## 暴力搜尋
* 每一步的選擇是有限的
* 不會走無限多步
* 先試試看，不行再說

----

## 老鼠走迷宮
<s>Nymphia找寶藏</s>
* 也是經典題
* 搜尋樹長得盤根錯節

![龍血樹](https://cdn2.ettoday.net/images/10/d10323.jpg)

----

## 老鼠走迷宮
* 給定起點, F代表終點
* \*代表路，#代表牆壁
* 找最短路徑

----

## 老鼠走迷宮
* 每一步只有上下左右
* 不走重複的路
* 遲早會到終點或死路

----

```cpp
void give_a_try(int x, int y, int n, int path_length){
	if(x<0 || x>=n || y<0 || y>=n || maze[x][y]=='#')
		return;
	if(maze[x][y] == 'F')
			best = MIN(best, path_length);
	else if(maze[x][y] == '.'){
		maze[x][y] = 'x';
		give_a_try(x-1, y, path_length+1);
		give_a_try(x+1, y, path_length+1);
		give_a_try(x, y-1, path_length+1);
		give_a_try(x, y+1, path_length+1);
		maze[x][y] = '.';
	}
	return;
}
```
[code](https://gist.github.com/oopzzozzo/805ed29c2b89dc3d5186b58cb816c6ef)

----

## DFS
* 很有趣 很強大
* 太複雜的話要很久

---

## 練習
[8787-倒水問題](https://neoj.sprout.tw/problem/8787/)
