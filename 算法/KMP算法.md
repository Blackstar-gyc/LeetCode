## KMP算法

#### c++实现

```c++
// KMP算法 
/*
实质就是当两个字符串失配的时候，减少上下两个指针的回溯移动。重点在于理解与构建next数组
0 1 2 3 4 5 6 7 8 9 下标
a s d a y a s d a s  i=4 匹配串
a s d a s            j=4 模式串
例如对上一个例子，当我们比较到下标4的时候，失配。但是我们不需要让i指针往前走，虽然4处失陪，但是也恰恰表示
4之前的都是相同的，因此我们观察数组asdas,当最后一个s处失配的时候，我们已知原字符串失配处前面一定是asda，也
就是说我们知道了它前面的几个字符，那此时我们可以采取何种措施？观察asda，已知匹配串3处一定是a，恰好我模式串第
一个字符也是啊，此时就不需要回溯到第一个字符，可以形成下面的模式：
0 1 2 3 4 5 6 7 8 9 下标
a s d a y a s d a s  i=4 匹配串
          a s d a s  j=1 模式串
我们的j不需要从0开始遍历，只需要从1处开始，因为我们已经知道了i=4的匹配串字符与j=0处的模式串字符一定是相等的
哪对于一个模式串，我们怎么知道任意位置处失配的时候，我们应该把指针指向哪里呢？这就是next数组，其中存储的值就是
j处失配时，j指针跳到next[j]处再比较i和j处的值是否相同。
 
*/
#include <bits/stdc++.h>

using namespace std;

int main(){
	string n,m;               //求m是否是n的子串 ，多组输入数据,输入空值代表输入结束
	while (getline(cin,n)&&n!=""){
		getline(cin,m);
		int num1=n.size();
		int num2=m.size();
		vector<int> next(num2,0);
		next[0]=-1;
		int i=0;
		int j=-1;
		while (i<num2){           //构建next数组
			if (j==-1||m[i]==m[j]){	
				i++; //此处为何要先加再赋值，因为已经知道二者值相等，那么肯定是下一个字符失配的时候跳到
				j++;  //前面已经相同的字符的下一个字符再去进行比较。
				next[i]=j;
			} else {
				j=next[j];    
			}	
		}
		int p=0;
		int q=0;
		while (p<num1&&q<num2){        //两个字符串开始遍历
			if (q==-1||n[p]==m[q]){
				p++;
				q++;
			} else {         //失配发生
				q=next[q];
			}
		}
		if(q==num2) cout<<"true"<<endl;
		else cout<<"false"<<endl;					
	}
	return 0;
} 
```

