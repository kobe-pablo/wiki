# スタック

スタックとは，先に入れたデータを先に取り出すことができるデータ構造である.  
入れ物があって，上に物を積んでいったり，一番上の物を取り出したりするようなイメージ．  
C++だとstd::stackが使える．

## 参考
- [スタックとキューを極める！ 〜 考え方と使い所を特集 〜](https://qiita.com/drken/items/6a95b57d2e374a3d3292)

## 操作例
- push
	- スタックに値を追加する．
	- O(1)
- pop
	- スタックの一番上の値を消す．
	- O(1)
- top
	- スタックの一番上の値を参照する.
	- O(1)

## コード(C++)

~~~cpp
stack<int> myStack;	//myStackというスタックを宣言

myStack.push(2);	//myStackに2を追加
myStack.push(5); 	//myStackに5を追加

cout << myStack.top() << endl;	//myStackの一番上の要素を出力(結果は5)

myStack.pop();	//myStackの一番上を削除

myStack.push(9);	//myStackに9を追加

myStack.pop();	//myStackの一番上を削除

cout << myStack.top() << endl;	//myStackの一番上の要素を出力(結果は2)
~~~