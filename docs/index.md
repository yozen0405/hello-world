# 海牛作業_1
## 觀念
### 第1題
- $N$ 每次遞迴時都會遞減 $1$ ，$N\div1=N$，時間複雜度為$O(N)$
- 又根據 `big-O notation` 可以高估的性質，故答案選**C,D**
### 第2題
- $N=2^k\Rightarrow k=\log_2N$，時間複雜度為 $O(\log N)$
- 又根據 `big-O notation` 可以高估的性質，故答案選**B,C,D**
### 第3題
$$
\begin{align}
T(N)
& =T(N−1)+N\\
& =T(N-2)+N+N-1\\
& =T(1)+N+N-1+\cdots +2\\
& =1+2+3+\cdots+N\\
& =\frac{N\times (N+1)}{2}=\frac{1}{2}(N^2+N)\\
& \Rightarrow 時間複雜度為 O(N^2)\\
\end{align}
$$
- 又根據 `big-O notation` 可以高估的性質，故答案選**A,C**
### 第4題
- $arr[i]=arr[i-1]+arr[i-2]$

| $index$ | 0 | 1 | 2 | 3 | 4 | 5 |
| -------- | -------- | -------- | -------- | -------- | -------- | --------|
| $value$ | 1 | 3 | 4 | 7 | 11 | 19 |
- **$arr[5] = 19$**
### 第5題
- $f[0] = 1$
- $f[n] = f[n-1]+n^2$
 
| $index$ | 0 | 1 | 2 | 3 | 4 |
| -------- | -------- | -------- | -------- | -------- | -------- | 
| $value$ | 1 | 2 | 6 | 15 | 31 |
- $f(4)=31$
### 第6題
- $f(0)=O(1)$
$$
\begin{align}
f(n)
& =2\times f(\frac{n}{2})\\
& =2\times (2\times f(\frac{\frac{n}{2}}{2}))\\
& =2^k\times f(\frac{n}{2^k})\\
\end{align}
$$
- 
$$
\begin{align}
& 使 f(\frac{n}{2^k})=f(0)\\
& \Rightarrow\frac{n}{2^k}=0\\
& \Rightarrow n=2^{k-1}\\
& \Rightarrow\log_2n=k-1\\
& \Rightarrow k=\log_2n+1\\
& \end{align}
$$
$$
\begin{align}
f( n)
& =2^{\log n+1}\times f(\frac{n}{2^{\log{n}+1}})\\
& =2^{\log n+1}\times f(0)\\
& =2\times 2^{\log n}\times f(0)\\
& =2\times n\times f(0)\\
\end{align}
$$
$\Rightarrow$ **時間複雜度** $O(2n)$
- 又根據 `big-O notation` 可以高估的性質，故答案選**A,B**
### 第7題
- $O(n! \times 100 \times \sqrt{n})$
$= O((1 \times 2 \times \cdots \times n) \times 100 \times \sqrt{n})$
$= O(n \sqrt{n}\times100\times \Pi_{i=1}^{n-1}i)$
- 又根據 `big-O notation` 可以高估的性質，故答案選**A,C,D**
### 第8題
- 設十進位之數字為 $num=a \times 10^n$
- 跑 `while loop` 將十進位數字除 $2$ 取餘數
- 過程中用開在`global` 的 `pair` 儲存 `0` 和`1` 的數量
- 最後在 output `pair.second`
- $2^k=num$
$k=\log_2num$
- **時間複雜度為 $O(\log num)$**
### 第9題
- 時間複雜度要取 `worst case` ，所以設 $a,b$ 也都是完全平方數且 $a>b$
- `for loop` 在 $\sqrt{a}$ 和 $\sqrt{b}$ 之間跑進行加總
- **時間複雜度為 $O(\sqrt{a}-\sqrt{b})$**
### 第10題
- $f(n)$
$=O(n)+f(\frac{2\times n}{3})$
$=O(n)+O(\frac{2\times n}{3})+f(\frac{2\times \frac{2\times n}{3}}{3})$
$=O(n)+O(\frac{2}{3}\times n)+f((\frac{2}{3})^2\times n)$
$=\sum_{k=0}^\infty O(\frac{2}{3}^k\times n)+f((\frac{2}{3})^k\times n)$
- 等比級數和公式 $S=\frac{a_1}{1-r}$
- $\frac{n}{1-\frac{2}{3}}=\frac{n}{\frac{1}{3}}=3\times n$
- **時間複雜度為 $O(3n)$**
## 實作
### [ZeroJudge b557: 直角三角形](https://zerojudge.tw/ShowProblem?problemid=b557 "Title")
```cpp
#include <bits/stdc++.h> 
#define int long long
using namespace std;
int n,ans=0;
int arr[101];
signed main(){
    cin>>n;
    while(n--){
        int t;
        ans=0;
        cin>>t;
        for(int i=0;i<t;i++){
            cin>>arr[i];
        }
        sort(arr,arr+t);
        for(int i=0;i<t-2;i++){
            if(i==t-2) break;
            for(int j=i+1;j<t-1;j++){
                for(int k=j+1;k<t;k++){
                    if(arr[k]*arr[k]==(arr[j]*arr[j]+arr[i]*arr[i])){
                        ans++;
                    }
                }
            }
        }
        cout<<ans<<"\n";
    }
}
```
### [ZeroJudge a005: Eva 的回家作業](https://zerojudge.tw/ShowProblem?problemid=a005 "Title")
```cpp
#include <bits/stdc++.h>
#define int long long
using namespace std;
int n,m,ans=0;
int arr[5];
signed main(){
    cin>>n;
    while(n--){
        for(int i=0;i<4;i++){
            cin>>arr[i];
        }
        if(arr[1]-arr[0]==arr[2]-arr[1]){
            arr[4]=arr[3]+arr[1]-arr[0];
        }
        else if(arr[1]/arr[0]==arr[2]/arr[1]){
            arr[4]=arr[3]*(arr[1]/arr[0]);
        }
        for(int i=0;i<5;i++) cout<<arr[i]<<" ";
        cout<<"\n";
    }
}
```
### [ZeroJudge a524 - 手機之謎](https://zerojudge.tw/ShowProblem?problemid=a524 "Title")
```cpp
#include <bits/stdc++.h>
#define int long long
using namespace std;
int n,m,ans=0;
map<int,int> mp;
int arr[10];
void rec(int ind){
    if(ind==n){
        for(int i=0;i<n;i++){
            cout<<arr[i];
        }
        cout<<"\n";
    }
    for(int i=n;i>=1;i--){
        if(mp[i]==1) continue;
        mp[i]=1;
        arr[ind]=i;
        rec(ind+1);
        mp[i]=0;
    }
}
signed main(){
    while(cin>>n){
        rec(0);
    }
}
```
### [ZeroJudge a981: 求和問題](https://zerojudge.tw/ShowProblem?problemid=a981 "Title")
```cpp
#include <bits/stdc++.h>
#define int long long
using namespace std;
int n,m;
int arr[30];
int ans[30];
bool is_ans=0;
void rec(int sum,int ind,int len,bool get){ 
    if(get){
        sum+=arr[ind];
        ans[len]=arr[ind];
        len++;
        ind++;
    }
    else ind++;
    if(sum==m){
        is_ans=true;
        for(int i=0;i<len;i++){
            cout<<ans[i]<<" ";
        }
        cout<<"\n";
        return;
    }
    if(ind==n||sum>m){ 
        return;
    } 
    rec(sum, ind, len, 1);
    rec(sum, ind, len, 0);
}
signed main(){
    cin>>n>>m;
    for(int i=0;i<n;i++) cin>>arr[i];
    sort(arr, arr+n);
    rec(0,0,0,1);
    rec(0,0,0,0);
    if(!is_ans) cout<<"-1";
}
```
### [ZeroJudge a229: 括號匹配問題](https://zerojudge.tw/ShowProblem?problemid=a229 "Title")
```cpp
#include <bits/stdc++.h>
#define int long long
using namespace std;
int n,m,ans=0;
string s;
void rec(int a,int b,int times){
    if(a==n&&b==n){
        cout<<s;
        cout<<"\n";
        return;
    }
    if(a<n){
        s[a+b]='(';
        rec(a+1, b,times+1);
    }
    if(a>b){//可以加)
        s[a+b]=')';
        rec(a, b+1,times+1);
    }
}
signed main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    bool first = true;
    while(cin>>n){
        s = "";
        for (int i = 0; i < 2*n; i++){
            s += " ";
        }
        cout<<"\n";
        rec(0,0,0);
    }
}
```
