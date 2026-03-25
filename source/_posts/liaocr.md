---
title: 2023gdgz01 's Template library
date: 2026-03-20 19:39:39
tags: null
---




![](https://cdn.luogu.com.cn/upload/image_hosting/4i6eqqea.png)




------------


C++ 火车头优化：


```cpp
#pragma GCC optimize(2)
#pragma GCC optimize(3)
#pragma GCC target("avx,sse2,sse3,sse4,mmx")
#pragma GCC optimize("Ofast")
#pragma GCC optimize("inline")
#pragma GCC optimize("-fgcse")
#pragma GCC optimize("-fgcse-lm")
#pragma GCC optimize("-fipa-sra")
#pragma GCC optimize("-ftree-pre")
#pragma GCC optimize("-ftree-vrp")
#pragma GCC optimize("-fpeephole2")
#pragma GCC optimize("-ffast-math")
#pragma GCC optimize("-fsched-spec")
#pragma GCC optimize("unroll-loops")
#pragma GCC optimize("-falign-jumps")
#pragma GCC optimize("-falign-loops")
#pragma GCC optimize("-falign-labels")
#pragma GCC optimize("-fdevirtualize")
#pragma GCC optimize("-fcaller-saves")
#pragma GCC optimize("-fcrossjumping")
#pragma GCC optimize("-fthread-jumps")
#pragma GCC optimize("-funroll-loops")
#pragma GCC optimize("-fwhole-program")
#pragma GCC optimize("-freorder-blocks")
#pragma GCC optimize("-fschedule-insns")
#pragma GCC optimize("inline-functions")
#pragma GCC optimize("-ftree-tail-merge")
#pragma GCC optimize("-fschedule-insns2")
#pragma GCC optimize("-fstrict-aliasing")
#pragma GCC optimize("-fstrict-overflow")
#pragma GCC optimize("-falign-functions")
#pragma GCC optimize("-fcse-skip-blocks")
#pragma GCC optimize("-fcse-follow-jumps")
#pragma GCC optimize("-fsched-interblock")
#pragma GCC optimize("-fpartial-inlining")
#pragma GCC optimize("no-stack-protector")
#pragma GCC optimize("-freorder-functions")
#pragma GCC optimize("-findirect-inlining")
#pragma GCC optimize("-fhoist-adjacent-loads")
#pragma GCC optimize("-frerun-cse-after-loop")
#pragma GCC optimize("inline-small-functions")
#pragma GCC optimize("-finline-small-functions")
#pragma GCC optimize("-ftree-switch-conversion")
#pragma GCC optimize("-foptimize-sibling-calls")
#pragma GCC optimize("-fexpensive-optimizations")
#pragma GCC optimize("-funsafe-loop-optimizations")
#pragma GCC optimize("inline-functions-called-once")
#pragma GCC optimize("-fdelete-null-pointer-checks")


using namespace std;


int main()
{
	ios::sync_with_stdio(false);
	cin.tie(0);
	cout.tie(0);
	return 0;
}
```
------------


# 卡常


### 快读快写


```cpp
#ifndef FAST_IO
//正在写
#endif
```


### 卡常火车头（考试不可用）


```cpp
#pragma GCC optimize(2)
#pragma GCC optimize(3)
#pragma GCC target("avx,sse2,sse3,sse4,mmx")
#pragma GCC optimize("Ofast")
#pragma GCC optimize("inline")
#pragma GCC optimize("-fgcse")
#pragma GCC optimize("-fgcse-lm")
#pragma GCC optimize("-fipa-sra")
#pragma GCC optimize("-ftree-pre")
#pragma GCC optimize("-ftree-vrp")
#pragma GCC optimize("-fpeephole2")
#pragma GCC optimize("-ffast-math")
#pragma GCC optimize("-fsched-spec")
#pragma GCC optimize("unroll-loops")
#pragma GCC optimize("-falign-jumps")
#pragma GCC optimize("-falign-loops")
#pragma GCC optimize("-falign-labels")
#pragma GCC optimize("-fdevirtualize")
#pragma GCC optimize("-fcaller-saves")
#pragma GCC optimize("-fcrossjumping")
#pragma GCC optimize("-fthread-jumps")
#pragma GCC optimize("-funroll-loops")
#pragma GCC optimize("-fwhole-program")
#pragma GCC optimize("-freorder-blocks")
#pragma GCC optimize("-fschedule-insns")
#pragma GCC optimize("inline-functions")
#pragma GCC optimize("-ftree-tail-merge")
#pragma GCC optimize("-fschedule-insns2")
#pragma GCC optimize("-fstrict-aliasing")
#pragma GCC optimize("-fstrict-overflow")
#pragma GCC optimize("-falign-functions")
#pragma GCC optimize("-fcse-skip-blocks")
#pragma GCC optimize("-fcse-follow-jumps")
#pragma GCC optimize("-fsched-interblock")
#pragma GCC optimize("-fpartial-inlining")
#pragma GCC optimize("no-stack-protector")
#pragma GCC optimize("-freorder-functions")
#pragma GCC optimize("-findirect-inlining")
#pragma GCC optimize("-fhoist-adjacent-loads")
#pragma GCC optimize("-frerun-cse-after-loop")
#pragma GCC optimize("inline-small-functions")
#pragma GCC optimize("-finline-small-functions")
#pragma GCC optimize("-ftree-switch-conversion")
#pragma GCC optimize("-foptimize-sibling-calls")
#pragma GCC optimize("-fexpensive-optimizations")
#pragma GCC optimize("-funsafe-loop-optimizations")
#pragma GCC optimize("inline-functions-called-once")
#pragma GCC optimize("-fdelete-null-pointer-checks")
#include <iostream>
#define endl '\n'


using namespace std;


int main() {
	ios::sync_with_stdio(false);
	cin.tie(0);
	cout.tie(0);
	return 0;
}
```


# 基础算法


### 高精度


```cpp
class __t_p_unsigned_long_long {
	public:
		void s2BIG(string s, int a[]) {
			a[0] = s.size();
			for (register int i = 1; i <= a[0]; ++i)
				a[i] = s[a[0] - i] - '0';
		}
		void i2BIG(long long n, int a[]) {
			s2BIG(to_string(n), a);
		}
		void printBIG(int a[]) {
			for (register int i = a[0]; i; --i)
				printf("%d", a[i]);
		}
		int cmpBIG(int a[], int b[]) {
			if (a[0] < b[0])
				return -1;
			if (a[0] > b[0])
				return 1;
			for (register int i = a[0]; i; --i) {
				if (a[i] < b[i])
					return -1;
				if (a[i] > b[i])
					return 1;
			}
			return 0;
		}
		void addBIG(int a[], int b[], int c[]) {
			int lena = a[0], lenb = b[0], lenc = max(lena, lenb), t;
			bool u = false;
			for (register int i = 1; i <= lenc; ++i) {
				t = u;
				if (i <= lena)
					t += a[i];
				if (i <= lenb)
					t += b[i];
				c[i] = t % 10;
				u = t / 10;
			}
			if (u) {
				++lenc;
				c[lenc] = u;
			}
			c[0] = lenc;
		}
		void addBIG(int a[], long long b, int c[]) {
			int t[1005];
			i2BIG(b, t);
			addBIG(a, t, c);
		}
		void subBIG(int a[], int b[], int c[]) {
			int lenb = b[0], lenc = max(a[0], lenb), t, u = 0;
			for (register int i = 1; i <= lenc; ++i) {
				t = a[i] - u;
				u = 0;
				if (i <= lenb)
					t -= b[i];
				c[i] = t;
				if (t < 0) {
					u = 1;
					c[i] += 10;
				}
			}
			for (; lenc > 1 && c[lenc] == 0; --lenc);
			c[0] = lenc;
		}
		void subBIG(int a[], long long b, int c[]) {
			int t[1005];
			i2BIG(b, t);
			subBIG(a, t, c);
		}
		void mulBIG(int a[], long long b, int c[]) {
			int lenc = a[0];
			long long t, u = 0;
			for (register int i = 1; i <= lenc; ++i) {
				t = a[i] * b + u;
				c[i] = t % 10;
				u = t / 10;
			}
			while (u > 0) {
				++lenc;
				c[lenc] = u % 10;
				u /= 10;
			}
			c[0] = lenc;
		}
		void mulBIG(int a[], int b[], int c[]) {
			int lenc = a[0], t[1005], u[1005], cur = 1;
			u[0] = 1;
			u[1] = 0;
			for (register int i = 1; i <= lenc; ++i) {
				mulBIG(b, a[i], t);
				addBIG(t, u, t);
				c[i] = t[1];
				if (t[0] == 1 && t[1] == 0) {
					u[0] = 1;
					u[1] = 0;
					continue;
				}
				u[0] = t[0] - 1;
				for (int j = 2; j <= t[0]; j++)
					u[j - 1] = t[j];
			}
			while (cur <= u[0]) {
				++lenc;
				c[lenc] = u[cur];
				++cur;
			}
			for (; lenc > 1 && c[lenc] == 0; --lenc);
			c[0] = lenc;
		}
		void divBIG(int a[], long long b, int c[]) {
			int lenc = a[0];
			long long t, r = 0;
			for (register int i = lenc; i; --i) {
				t = r * 10 + a[i];
				c[i] = t / b;
				r = t % b;
			}
			for (; lenc > 1 && c[lenc] == 0; --lenc);
			c[0] = lenc;
		}
		void facBIG(int l, int r, int a[]) {
			a[0] = a[1] = 1;
			for (register int i = l; i <= r; ++i)
				mulBIG(a, i, a);
		}
		void facBIG(int n, int a[]) {
			facBIG(2, n, a);
		}
		void ABIG(int n, int m, int a[]) {
			facBIG(n - m + 1, n, a);
		}
		void CBIG(int n, int m, int a[]) {
			ABIG(n, m, a);
			for (register int i = 2; i <= m; ++i)
				divBIG(a, i, a);
		}
};
```
# 字符串


### 最小表示法


```cpp
#include <cstdio>


int n, b, c = 1, a[300000];


int main() {
	scanf("%d", &n);
	for (register int i = 0; i < n; ++i)
		scanf("%d", a + i);
	for (register int i = 0; i < n && b < n && c < n;) {
		if (a[(b + i) % n] == a[(c + i) % n])
			++i;
		else {
			if (a[(b + i) % n] > a[(c + i) % n])
				b += i + 1;
			else
				c += i + 1;
			b += (b == c);
			i = 0;
		}
	}
	if (b > c)
		b = c;
	for (register int i = 0; i < n; ++i)
		printf("%d ", a[(i + b) % n]);
	return 0;
}
```


### 后缀数组 SA


```cpp
#include <bits/stdc++.h>
using namespace std;
#define N 2000005
int sa[N], osa[N];
int rk[N], ork[N];
int cnt[N];

void SA(string s)
{
	int n = s.size(), m = 127;
	s = ' ' + s;

	for(int i = 1; i <= n; i++)
	{
		rk[i] = s[i];
		cnt[rk[i]]++;
	}
	for(int i = 1; i <= m; i++)
	{
		cnt[i] += cnt[i-1];
	}
	for(int i = n; i >= 1; i--)
	{
		sa[cnt[rk[i]]--] = i;
	}

	for(int w = 1; w < n; w *= 2,m=n)
	{
		int p = 0;
		for(int i = n - w + 1; i <= n; i++)
		{
			osa[++p] = i;
		}
		for(int i = 1; i <= n; i++)
		{
			if(sa[i] > w) osa[++p] = sa[i] - w;
		}

		memset(cnt,0,sizeof(cnt));
		for(int i = 1; i <= n; i++)
		{
			cnt[rk[osa[i]]]++;
		}
		for(int i = 1; i <= m; i++)
		{
			cnt[i] += cnt[i-1];
		}
		for(int i = n; i >= 1; i--)
		{
			sa[cnt[rk[osa[i]]]--] = osa[i];
		}

		memcpy(ork + 1, rk + 1, n * 4);
		m = 0;
		for(int i = 1; i <= n; i++)
		{
			if(i == 1)
			{
				rk[sa[i]] = ++m;
				continue;
			}
			int x1 = sa[i], x2 = sa[i-1];
			int y1 = (x1 + w <= n) ? ork[x1 + w] : 0;
			int y2 = (x2 + w <= n) ? ork[x2 + w] : 0;

			if(ork[x1] == ork[x2] && y1 == y2)
			{
				rk[sa[i]] = m;
			}
			else
			{
				rk[sa[i]] = ++m;
			}
		}

		if(m == n) break;
	}

	for(int i = 1; i <= n; i++)
	{
		cout << sa[i] << " ";
	}
}

int main()
{
	string s;
	cin >> s;
	SA(s);
	return 0;
}
```

### 后缀自动机 SAM


```cpp
#include <bits/stdc++.h>
using namespace std;
#define N 2000005

int ch[N][26], len[N], fa[N];
long long size[N]; 
int las = 1, tot = 1;
int n; 
char s[N]; 

void insert(int x)
{
	int u = ++tot, p = las;
	las = tot;
	len[u] = len[p] + 1;
	size[u] = 1; 

	for(; p && !ch[p][x]; p = fa[p])
	{
		ch[p][x] = u; 
	}

	if(!p)
	{
		fa[u] = 1;
		return;
	}

	int q = ch[p][x];
	if(len[p] + 1 == len[q])
	{
		fa[u] = q;
		return;
	}

	int uu = ++tot;
	len[uu] = len[p] + 1;
	memcpy(ch[uu], ch[q], sizeof(ch[q]));
	fa[uu] = fa[q];
	fa[q] = fa[u] = uu;
	size[uu] = 0; 
	for(; p && ch[p][x] == q; p = fa[p])
	{
		ch[p][x] = uu;
	}
}

int tp[N], tmp[N];

void get_tp()
{
	for (int i = 0; i <= n; i++)
		tmp[i] = 0;

	for (int i = 1; i <= tot; i++)
		tmp[len[i]]++;

	for (int i = 1; i <= n; i++)
		tmp[i] += tmp[i - 1];

	for (int i = 1; i <= tot; i++)
		tp[tmp[len[i]]--] = i;
}
long long DP() 
{
	for (int i = tot; i >= 1; i--)
	{
		int now = tp[i];
		size[fa[now]] += size[now];
	}

	long long ans = 0;
	for (int i = 1; i <= tot; i++)
	{
		if (size[i] > 1)
		{
			ans = max(ans, size[i] * len[i]);
		}
	}
	return ans;
}
int main()
{
	string s;
	cin >> s;
	n = s.size();
	for(int i = 0; i < n; i++)
	{
		insert(s[i] - 'a');
	}
	get_tp();
	long long ans = DP();
	cout << ans << endl;
	return 0;
}
```


# 数论


## gcd


### 递归算法


```cpp
#include <cstdio>


int a, b, g;


int gcd(int x, int y) {
	if (x)
		return gcd(y % x, x);
	return y;
}


int main() {
	scanf("%d%d", &a, &b);
	g = gcd(a, b);
	printf("%d %d", g, a * b / g);
	return 0;
}
```


### 非递归算法


```cpp
#include <cstdio>


int a, b, g;


inline int gcd(int x, int y) {
	int temp;
	while (x) {
		temp = y % x;
		y = x;
		x = temp;
	}
	return y;
}


int main() {
	scanf("%d%d", &a, &b);
	g = gcd(a, b);
	printf("%d %d", g, a * b / g);
	return 0;
}
```


### exgcd


## 素数筛法


### 暴力算法


```cpp
#include <cstdio>


int n;


inline bool check(int x) {
	for (register int i = 2; i * i <= x; ++i)
		if (x % i == 0)
			return false;
	return true;
}


int main() {
	scanf("%d", &n);
	for (register int i = 2; i <= n; ++i)
		if (check(i))
			printf("%d ", i);
	return 0;
}
```


### 埃氏筛


```cpp
#include <cstdio>


bool prime[10000005];
int n;


int main() {
	scanf("%d", &n);
	for (register int i = 2; i <= n; ++i)
		if (!prime[i]) {
			printf("%d ", i);
			for (register int j = i << 1; j <= n; j += i)
				prime[j] = true;
		}
	return 0;
}
```


### 欧拉筛


```cpp
#include <cstdio>


bool vis[100000005];
int n, cur, prime[6000005];


int main() {
	scanf("%d", &n);
	for (register int i = 2; i <= n; ++i) {
		if (!vis[i]) {
			++cur;
			prime[cur] = i;
			printf("%d ", i);
		}
		for (register int j = 1; j <= cur && i * prime[j] <= n; ++j) {
			vis[i * prime[j]] = true;
			if (i % prime[j] == 0)
				break;
		}
	}
	return 0;
}
```


# 树论


## 并查集


### 并查集


```cpp
#include <cstdio>


int n, m, opt, x, y, fa[100005];


int find(int u) {
	if (u == fa[u])
		return u;
	fa[u] = find(fa[u]);
	return fa[u];
}


int main() {
	scanf("%d%d", &n, &m);
	for (register int i = 1; i <= n; ++i)
		fa[i] = i;
	while (m--) {
		scanf("%d%d%d", &opt, &x, &y);
		if (opt == 1)
			fa[find(x)] = find(y);
		else {
			if (find(x) == find(y))
				printf("Yes");
			else
				printf("No");
			putchar('\n');
		}
	}
	return 0;
}
```


### 带权并查集


```cpp
#include <iostream>


using namespace std;


char opt;
int p, t, x, y, fa[30005], dis[30005], _size[30005];


int find(int u) {
	if (u == fa[u])
		return u;
	t = find(fa[u]);
	dis[u] += dis[fa[u]];
	fa[u] = t;
	return t;
}


inline void Union(int u, int v) {
	u = find(u);
	v = find(v);
	if (u == v)
		return;
	fa[u] = v;
	dis[u] += _size[v];
	_size[v] += _size[u];
}


int main() {
	ios::sync_with_stdio(false);
	cin.tie(0);
	cout.tie(0);
	cin >> p;
	for (register int i = 1; i <= 30000; ++i) {
		fa[i] = i;
		_size[i] = 1;
	}
	while (p--) {
		cin >> opt >> x;
		if (opt == 'M') {
			cin >> y;
			Union(x, y);
		}
		else {
			y = find(x);
			cout << dis[x] << "\n";
		}
	}
	return 0;
}
```


------------


## LCA


### 暴力


```cpp
#include <cstdio>


struct edge {
	int next, to;
};


int n, m, x, y, s, cur, fa[500005], dep[500005], head[500005];
edge e[1000005];


inline void add(int u, int v) {
	++cur;
	e[cur] = {head[u], v};
	head[u] = cur;
}


void dfs(int u, int father) {
	fa[u] = father;
	dep[u] = dep[father] + 1;
	for (register int i = head[u]; i; i = e[i].next)
		if (e[i].to != father)
			dfs(e[i].to, u);
}


inline int LCA(int u, int v) {
	int x = dep[u], y = dep[v];
	while (u != v) {
		if (x < y) {
			--y;
			v = fa[v];
		}
		else {
			--x;
			u = fa[u];
		}
	}
	return u;
}


int main()
{
	scanf("%d%d%d", &n, &m, &s);
	for (register int i = 1; i < n; ++i) {
		scanf("%d%d", &x, &y);
		add(x, y);
		add(y, x);
	}
	dfs(s, 0);
	while (m--) {
		scanf("%d%d", &x, &y);
		printf("%d\n", LCA(x, y));
	}
	return 0;
}
```


### 倍增


```cpp
#include <cstdio>
#include <algorithm>


using namespace std;


struct edge {
	int next, to;
};


int n, m, x, y, s, cur, dep[500005], head[500005], f[30][500005];
edge e[1000005];


inline void add(int u, int v) {
	++cur;
	e[cur] = {head[u], v};
	head[u] = cur;
}


void dfs(int u, int fa) {
	dep[u] = dep[fa] + 1;
	f[0][u] = fa;
	for (register int i = head[u]; i; i = e[i].next) {
		if (!dep[e[i].to])
			dfs(e[i].to, u);
	}
}


inline int LCA(int u, int v) {
	if (dep[u] < dep[v])
		swap(u, v);
	for (register int i = 28; i >= 0; --i)
		if (dep[v] <= dep[u] - (1 << i))
			u = f[i][u];
	if (u == v)
		return u;
	for (register int i = 28; i >= 0; --i)
		if (f[i][u] != f[i][v]) {
			u = f[i][u];
			v = f[i][v];
		}
	return f[0][u];
}


int main()
{
	scanf("%d%d%d", &n, &m, &s);
	for (register int i = 1; i < n; ++i) {
		scanf("%d%d", &x, &y);
		add(x, y);
		add(y, x);
	}
	dfs(s, 0);
	for (register int i = 1; (1 << i) <= n; ++i)
		for (register int j = 1; j <= n; ++j)
			f[i][j] = f[i - 1][f[i - 1][j]];
	while (m--) {
		scanf("%d%d", &x, &y);
		printf("%d\n", LCA(x, y));
	}
	return 0;
}
```


### RMQ


```cpp


```


### Tarjan


```cpp


```


# 图论


## 基础搜索


### dfs


```cpp
#include <cstdio>


struct edge {
	int next, to;
};


bool vis[100005];
int n, m, x, y, cur, head[100005];
edge e[200005];


inline void add(int u, int v) {
	++cur;
	e[cur] = {head[u], v};
	head[u] = cur;
}


void dfs(int u) {
	if (vis[u])
		return;
	vis[u] = true;
	printf("%d ", u);
	for (register int i = head[u]; i; i = e[i].next)
		dfs(e[i].to);
}


int main() {
	scanf("%d%d", &n, &m);
	while (m--) {
		scanf("%d%d", &x, &y);
		add(x, y);
	}
	for (register int i = 1; i <= n; ++i)
		if (!vis[i]) {
			dfs(i);
			putchar('\n');
		}
	return 0;
}
```


### bfs


```cpp
#include <cstdio>
#include <queue>


using namespace std;


struct edge {
	int next, to;
};


bool vis[100005];
int n, m, x, y, cur, head[100005];
queue<int> q;
edge e[200005];


inline void add(int u, int v) {
	++cur;
	e[cur] = {head[u], v};
	head[u] = cur;
}


inline void bfs(int u) {
	q.push(u);
	while (!q.empty()) {
		x = q.front();
		q.pop();
		if (vis[x])
			continue;
		vis[x] = true;
		printf("%d ", x);
		for (register int i = head[x]; i; i = e[i].next)
			q.push(e[i].to);
	}
}


int main() {
	scanf("%d%d", &n, &m);
	while (m--) {
		scanf("%d%d", &x, &y);
		add(x, y);
	}
	for (register int i = 1; i <= n; ++i)
		if (!vis[i]) {
			bfs(i);
			putchar('\n');
		}
	return 0;
}
```


## 拓扑排序


### bfs


```cpp
#include <cstdio>
#include <cstring>
#include <queue>


using namespace std;


struct edge {
	int next, to;
};


int t, n, m, x, y, cur, ans[100005], indegree[100005], head[100005];
queue<int> q;
edge e[100005];


inline void add(int u, int v) {
	++cur;
	e[cur] = {head[u], v};
	head[u] = cur;
}


inline void toposort() {
	for (register int i = 1; i <= n; ++i)
		if (!indegree[i])
			q.push(i);
	while (!q.empty()) {
		x = q.front();
		q.pop();
		++ans[0];
		ans[ans[0]] = x;
		for (register int i = head[x]; i; i = e[i].next) {
			y = e[i].to;
			--indegree[y];
			if (!indegree[y])
				q.push(y);
		}
	}
}


int main() {
	scanf("%d", &t);
	scanf("%d%d", &n, &m);
	while (m--) {
		scanf("%d%d", &x, &y);
		add(x, y);
		++indegree[y];
	}
	toposort();
	if (ans[0] == n)
		for (register int i = 1; i <= n; ++i)
			printf("%d ", ans[i]);
	else
		printf("-1");
	return 0;
}
```


## 最短路


### Dijkstra


```cpp
#include <cstdio>
#include <cstring>
#include <utility>
#include <vector>
#include <queue>


using namespace std;


struct edge {
	int next, to, w;
};


int n, m, s, x, y, w, minn, cur, head[100005], dis[100005];
bool vis[100005];
edge e[200005];
priority_queue<pair<int, int>, vector<pair<int, int> >, greater<pair<int, int> > > pq;


inline void add(int u, int v, int w) {
	++cur;
	e[cur] = {head[u], v, w};
	head[u] = cur;
}


inline void dijkstra() {
	memset(dis, 0x3f, sizeof(dis));
	dis[s] = 0;
	pq.push(make_pair(0, s));
	while (!pq.empty()) {
	    minn = pq.top().second;
		pq.pop();
        if (vis[minn])
            continue;
		vis[minn] = true;
		for (register int i = head[minn]; i; i = e[i].next) {
			x = e[i].to;
			if (dis[minn] + e[i].w < dis[x]) {
				dis[x] = dis[minn] + e[i].w;
				pq.push(make_pair(dis[x], x));
			}
		}
	}
}


int main() {
	scanf("%d%d%d", &n, &m, &s);
	while (m--) {
		scanf("%d%d%d", &x, &y, &w);
		add(x, y, w);
	}
	dijkstra();
	for (register int i = 1; i <= n; ++i)
		printf("%d ", dis[i]);
	return 0;
}
```


### Bellman-ford


```cpp
#include <cstdio>
#include <cstring>


struct edge {
	int u, v, w;
};


int n, m, s, x, y, w, cur, head[100005], dis[100005];
edge e[200005];


inline void add(int u, int v, int w) {
	++cur;
	e[cur] = {u, v, w};
}


int main() {
	scanf("%d%d%d", &n, &m, &s);
	for (register int i = 1; i <= m; ++i) {
		scanf("%d%d%d", &x, &y, &w);
		add(x, y, w);
	}
	memset(dis, 0x3f, sizeof(dis));
	dis[s] = 0;
	for (register int i = 1; i < n; ++i)
		for (register int j = 1; j <= m; ++j)
			if (dis[e[j].u] + e[j].w < dis[e[j].v])
				dis[e[j].v] = dis[e[j].u] + e[j].w;
	for (register int i = 1; i <= n; ++i)
		printf("%d ", dis[i]);
	return 0;
}
```


### spfa


```cpp
#include <cstdio>
#include <cstring>
#include <queue>


using namespace std;


struct edge {
	int next, to, w;
};


bool vis[100005];
int n, m, s, x, y, w, cur, head[100005], dis[100005], cnt[100005];
queue<int> q;
edge e[200005];


inline void add(int u, int v, int w) {
	++cur;
	e[cur] = {head[u], v, w};
	head[u] = cur;
}


inline bool spfa() {
	memset(dis, 0x3f, sizeof(dis));
	dis[s] = 0;
	q.push(s);
	while (!q.empty()) {
		x = q.front();
		q.pop();
		vis[x] = false;
		for (register int i = head[x]; i; i = e[i].next) {
			y = e[i].to;
			if (dis[x] + e[i].w < dis[y]) {
				dis[y] = dis[x] + e[i].w;
				++cnt[y];
				if (cnt[y] > n)
					return true;
				if (!vis[y]) {
					q.push(y);
					vis[y] = true;
				}
			}
		}
	}
	return false;
}


int main() {
	scanf("%d%d%d", &n, &m, &s);
	while (m--) {
		scanf("%d%d%d", &x, &y, &w);
		add(x, y, w);
	}
	if (spfa())
		printf("-1");
	else
		for (register int i = 1; i <= n; ++i)
			printf("%d ", dis[i]);
	return 0;
}
```


### Floyd-warshall


```cpp
#include <cstdio>
#include <cstring>


int n, m, x, y, w, dis[1005][1005];


inline int min(int x, int y) {
	if (x < y)
		return x;
	return y;
}


int main() {
	scanf("%d%d", &n, &m);
	memset(dis, 0x3f, sizeof(dis));
	while (m--) {
		scanf("%d%d%d", &x, &y, &w);
		dis[x][y] = min(dis[x][y], w);
	}
	for (register int i = 1; i <= n; ++i)
		dis[i][i] = 0;
	for (register int i = 1; i <= n; ++i)
		for (register int j = 1; j <= n; ++j)
			for (register int k = 1; k <= n; ++k)
				dis[j][k] = min(dis[j][k], dis[j][i] + dis[i][k]);
	for (register int i = 1; i <= n; ++i) {
		for (register int j = 1; j <= n; ++j)
			printf("%d ", dis[i][j]);
		putchar('\n');
	}
	return 0;
}
```


## K 短路


### A*


```cpp
#include <cstdio>
#include <cstring>
#include <utility>
#include <vector>
#include <queue>


using namespace std;


struct edge {
	int next, to, w;
};


struct node {
	int sorts, dis, u;
	inline bool operator< (const node &nod) const {
		return sorts > nod.sorts;
	}
};


bool vis[100005];
int n, m, s, T, k, x, y, w, ans, cur, dis1[100005], dis2[100005], head1[100005], head2[100005];
priority_queue<pair<int, int>, vector<pair<int, int> >, greater<pair<int, int> > > q1;
priority_queue<node> q2;
pair<int, int> t;
node temp;
edge e1[200005], e2[200005];


inline void add1(int u, int v, int w) {
	++cur;
	e1[cur] = {head1[u], v, w};
	head1[u] = cur;
}


inline void add2(int u, int v, int w) {
	e2[cur] = {head2[u], v, w};
	head2[u] = cur;
}


inline void dijkstra() {
	memset(dis1, 0x3f, sizeof(dis1));
	dis1[T] = 0;
	q1.push(make_pair(0, T));
	while (!q1.empty()) {
		t = q1.top();
		q1.pop();
		if (vis[t.second])
			continue;
		vis[t.second] = true;
		for (register int i = head2[t.second]; i; i = e2[i].next) {
			x = e2[i].to;
			if (dis1[t.second] + e2[i].w < dis1[x]) {
				dis1[x] = dis1[t.second] + e2[i].w;
				if (!vis[x])
					q1.push(make_pair(dis1[x], x));
			}
		}
	}
}


inline int astar() {
	q2.push({dis1[s], 0, s});
	while (!q2.empty()) {
		temp = q2.top();
		q2.pop();
		++dis2[temp.u];
		if (dis2[T] == k)
			return temp.dis;
		for (register int i = head1[temp.u]; i; i = e1[i].next) {
			x = e1[i].to;
			if (dis2[x] < k)
				q2.push({temp.dis + e1[i].w + dis1[x], temp.dis + e1[i].w, x});
		}
	}
	return -1;
}


int main() {
	scanf("%d%d%d%d%d", &n, &m, &s, &T, &k);
	while (m--) {
		scanf("%d%d%d", &x, &y, &w);
		add1(x, y, w);
		add2(y, x, w);
	}
	dijkstra();
	printf("%d", astar());
	return 0;
}
```


### 可持久化左偏树


```cpp
#include <cstdio>
#include <cstring>
#include <algorithm>
#include <utility>
#include <vector>
#include <queue>


using namespace std;


class edgepack {
	private:
		struct edge {
			int next, to, w;
		};
	public:
		int cur, head[100005];
		edge e[200005];
		inline void add(int u, int v, int w) {
			++cur;
			e[cur] = {head[u], v, w};
			head[u] = cur;
		}
};


class Tree {
	private:
		struct node {
			int l, r, fa, dis, w;
		};
	public:
		int cnt, root[100005];
		node tree[4000005];
		inline int insert(int w, int u) {
			++cnt;
			tree[cnt].w = w;
			tree[cnt].fa = u;
			return cnt;
		}
		int merge(int l, int r) {
			if (!l || !r)
				return l | r;
			if (tree[l].w > tree[r].w)
				swap(l, r);
			++cnt;
			int pos = cnt;
			tree[pos] = tree[l];
			tree[pos].r = merge(tree[pos].r, r);
			if (tree[tree[pos].l].dis < tree[tree[pos].r].dis)
				swap(tree[pos].l, tree[pos].r);
			tree[pos].dis = tree[tree[pos].r].dis + 1;
			return pos;
		}
};


bool vis[100005];
int n, m, s, t, k, x, y, w, a[100005], dis[100005], fa[100005];
priority_queue<pair<int, int>, vector<pair<int, int> >, greater<pair<int, int> > > q;
pair<int, int> temp;
edgepack e1, e2;
Tree tree;


inline bool cmp(int x, int y) {
	return dis[x] < dis[y];
}


inline void dijkstra() {
	memset(dis, 0x3f, sizeof(dis));
	dis[t] = 0;
	q.push(make_pair(0, t));
	while (!q.empty()) {
		temp = q.top();
		q.pop();
		if (vis[temp.second])
			continue;
		vis[temp.second] = true;
		for (register int i = e2.head[temp.second]; i; i = e2.e[i].next) {
			x = e2.e[i].to;
			if (temp.first + e2.e[i].w < dis[x]) {
				dis[x] = temp.first + e2.e[i].w;
				fa[x] = i;
				q.push(make_pair(dis[x], x));
			}
		}
	}
}


int main() {
	scanf("%d%d%d%d%d", &n, &m, &s, &t, &k);
	while (m--) {
		scanf("%d%d%d", &x, &y, &w);
		if (x != t) {
			e1.add(x, y, w);
			e2.add(y, x, w);
		}
	}
	dijkstra();
	for (register int i = 1; i <= n; ++i)
		a[i] = i;
	sort(a + 1, a + n + 1, cmp);
	tree.tree[0].dis = -1;
	for (register int i = 1; i <= n; ++i) {
		x = a[i];
		for (register int j = e1.head[x]; j; j = e1.e[j].next) {
			y = e1.e[j].to;
			if (fa[x] != j)
				tree.root[x] = tree.merge(tree.root[x], tree.insert(e1.e[j].w + dis[y] - dis[x], y));
		}
		tree.root[x] = tree.merge(tree.root[x], tree.root[e1.e[fa[x]].to]);
	}
	if (k == 1) {
		printf("%d", dis[s]);
		return 0;
	}
	if (tree.root[s])
		q.push(make_pair(tree.tree[tree.root[s]].w, tree.root[s]));
	while (!q.empty()) {
		temp = q.top();
		q.pop();
		--k;
		if (k == 1) {
			printf("%d", temp.first + dis[s]);
			return 0;
		}
		if (tree.tree[temp.second].l)
			q.push(make_pair(temp.first + tree.tree[tree.tree[temp.second].l].w - tree.tree[temp.second].w, tree.tree[temp.second].l));
		if (tree.tree[temp.second].r)
			q.push(make_pair(temp.first + tree.tree[tree.tree[temp.second].r].w - tree.tree[temp.second].w, tree.tree[temp.second].r));
		x = tree.root[tree.tree[temp.second].fa];
		if (x)
			q.push(make_pair(temp.first + tree.tree[x].w, x));
	}
	printf("-1");
	return 0;
}
```


## Tarjan


### 强连通分量


```cpp
#include <cstdio>
#include <vector>
#include <stack>


using namespace std;


struct edge {
	int next, to;
};


bool vis[500005];
int n, m, x, y, scc, cur, Time, head[500005], low[500005], dfn[500005];
vector<int> v[500005];
stack<int> st;
edge e[4000005];


inline void add(int u, int v) {
	++cur;
	e[cur] = {head[u], v};
	head[u] = cur;
}


void tarjan(int u) {
	++Time;
	low[u] = dfn[u] = Time;
	vis[u] = true;
	st.push(u);
	for (register int i = head[u]; i; i = e[i].next) {
		if (!dfn[e[i].to]) {
			tarjan(e[i].to);
			low[u] = min(low[u], low[e[i].to]);
		}
		else if (vis[e[i].to])
			low[u] = min(low[u], dfn[e[i].to]);
	}
	if (low[u] == dfn[u]) {
		++scc;
		while (st.top() != u) {
			v[scc].push_back(st.top());
			vis[st.top()] = false;
			st.pop();
		}
		v[scc].push_back(u);
		vis[u] = false;
		st.pop();
	}
}


int main() {
	scanf("%d%d", &n, &m);
	while (m--) {
		scanf("%d%d", &x, &y);
		add(x, y);
	}
	for (register int i = 1; i <= n; ++i)
		if (!dfn[i])
			tarjan(i);
	printf("%d\n", scc);
	for (register int i = 1; i <= scc; ++i) {
		printf("%d", v[i].size());
		for (register auto it: v[i])
			printf(" %d", it);
		putchar('\n');
	}
	return 0;
}
```


### 点双连通分量


```cpp
#include <cstdio>
#include <vector>
#include <stack>


using namespace std;


struct edge {
	int next, to;
};


int n, m, x, y, ans, cur, Time, head[500005], low[500005], dfn[500005];
vector<int> v[500005];
stack<int> st;
edge e[4000005];


inline void add(int u, int v) {
	++cur;
	e[cur] = {head[u], v};
	head[u] = cur;
}


void tarjan(int u, int fa) {
	int temp = 0;
	++Time;
	low[u] = dfn[u] = Time;
	st.push(u);
	for (register int i = head[u]; i; i = e[i].next) {
		if (!dfn[e[i].to]) {
			++temp;
			tarjan(e[i].to, u);
			low[u] = min(low[u], low[e[i].to]);
			if (low[e[i].to] >= dfn[u]) {
				++ans;
				do {
					v[ans].push_back(st.top());
					st.pop();
				} while (v[ans].back() != e[i].to);
				v[ans].push_back(u);
			}
		}
		else if (e[i].to != fa)
			low[u] = min(low[u], dfn[e[i].to]);
	}
	if (fa == -1 && !temp) {
		++ans;
		v[ans].push_back(u);
	}
}


int main() {
	scanf("%d%d", &n, &m);
	while (m--) {
		scanf("%d%d", &x, &y);
		add(x, y);
		add(y, x);
	}
	for (register int i = 1; i <= n; ++i)
		if (!dfn[i]) {
			while (!st.empty())
				st.pop();
			tarjan(i, -1);
		}
	printf("%d\n", ans);
	for (register int i = 1; i <= ans; ++i) {
		printf("%d", v[i].size());
		for (register auto it: v[i])
			printf(" %d", it);
		putchar('\n');
	}
	return 0;
}
```


### 边双连通分量


```cpp
#include <cstdio>
#include <vector>


using namespace std;


struct edge {
	int next, to;
};


bool vis[4000005];
int n, m, x, y, cnt, cur = 1, Time, id[500005], low[500005], dfn[500005], head[500005];
vector<int> ans[500005];
edge e[4000005];


inline void add(int x, int y) {
	++cur;
	e[cur] = {head[x], y};
	head[x] = cur;
}


void tarjan(int u, int eid) {
	++Time;
	dfn[u] = low[u] = Time;
	for (register int i = head[u]; i; i = e[i].next) {
		if (!dfn[e[i].to]) {
			tarjan(e[i].to, i);
			if (dfn[u] < low[e[i].to])
				vis[i] = vis[i ^ 1] = true;
			low[u] = min(low[u], low[e[i].to]);
		}
		else if (i != (eid ^ 1))
			low[u] = min(low[u], dfn[e[i].to]);
	}
}


void dfs(int u, int sid) {
	id[u] = sid;
	ans[sid].push_back(u);
	for (register int i = head[u]; i; i = e[i].next)
		if (!id[e[i].to] && !vis[i])
			dfs(e[i].to, sid);
}


int main() {
	scanf("%d%d", &n, &m);
	while (m--) {
		scanf("%d%d", &x, &y);
		if (x == y)
			continue;
		add(x, y);
		add(y, x);
	}
	for (register int i = 1; i <= n; ++i)
		if (!dfn[i])
			tarjan(i, 0);
	for (register int i = 1; i <= n; ++i)
		if (!id[i]) {
			++cnt;
			dfs(i, cnt);
		}
	printf("%d\n", cnt);
	for (register int i = 1; i <= cnt; ++i)
		if (ans[i].size()) {
			printf("%d", ans[i].size());
			for (register auto it: ans[i])
				printf(" %d", it);
			putchar('\n');
		}
	return 0;
}
```


### 割点


```cpp
#include <cstdio>
#include <cstring>
#include <algorithm>
#include <vector>


using namespace std;


int n, m, x, y, Time, __count, dfn[100005], low[100005], cnt[100005];
vector<int> v[400005];


void tarjan(int u, int fa) {
	int temp = 0;
	++Time;
	dfn[u] = low[u] = Time;
	for (register auto it: v[u]) {
		if (!dfn[it]) {
			++temp;
			tarjan(it, u);
			low[u] = min(low[u], low[it]);
			if (low[it] >= dfn[u] && fa != -1) {
				__count += (cnt[u] == 0);
				++cnt[u];
			}
		}
		else
			low[u] = min(low[u], dfn[it]);
	}
	if (temp >= 2 && fa == -1) {
		__count += (cnt[u] == 0);
		cnt[u] = temp - 1;
	}
}


int main() {
	scanf("%d%d", &n, &m);
	while (m--) {
		scanf("%d%d", &x, &y);
		if (x == y)
			continue;
		v[x].push_back(y);
		v[y].push_back(x);
	}
	for (register int i = 1; i <= n; ++i)
		if (!dfn[i])
			tarjan(i, -1);
	printf("%d\n", __count);
	for (register int i = 1; i <= n; ++i)
		if (cnt[i])
			printf("%d ", i);
	return 0;
}
```


## 最小生成树


### Kruskal


```cpp
#include <cstdio>
#include <algorithm>


using namespace std;


struct edge {
	int u, v, w;
	inline bool operator< (const edge &edg) const {
		return w < edg.w;
	}
};


int n, m, x, y, w, cnt, ans, cur, fa[100005];
edge e[200005];


inline void add(int u, int v, int w) {
	++cur;
	e[cur] = {u, v, w};
}


int find(int u) {
	if (u == fa[u])
		return u;
	fa[u] = find(fa[u]);
	return fa[u];
}


int main() {
	scanf("%d%d", &n, &m);
	for (register int i = 1; i <= n; ++i)
		fa[i] = i;
	for (register int i = 1; i <= m; ++i) {
		scanf("%d%d%d", &x, &y, &w);
		add(x, y, w);
	}
	sort(e + 1, e + m + 1);
	for (register int i = 1; i <= m; ++i) {
		x = find(e[i].u);
		y = find(e[i].v);
		if (x != y) {
			fa[x] = y;
			ans += e[i].w;
			++cnt;
		}
	}
	if (cnt == n - 1)
		printf("%d", ans);
	else
		printf("No");
	return 0;
}
```


### Prim


```cpp
#include <cstdio>
#include <cstring>


bool vis[1005];
int n, m, x, y, w, ans, dis[1005], g[1005][1005];


inline int min(int x, int y) {
	if (x < y)
		return x;
	return y;
}


inline void prim() {
	memset(dis, 0x3f, sizeof(dis));
	dis[1] = 0;
	for (register int i = 1; i <= n; ++i) {
		x = 0;
		for (register int j = 1; j <= n; ++j)
			if (!vis[j] && (!x || dis[j] < dis[x]))
				x = j;
		if (dis[x] == 0x3f3f3f3f) {
			ans = -1;
			return;
		}
		ans += dis[x];
		vis[x] = true;
		for (register int j = 1; j <= n; ++j)
			if (!vis[j] && g[x][j] < dis[j])
				dis[j] = g[x][j];
	}
}


int main() {
	scanf("%d%d", &n, &m);
	memset(g, 0x3f, sizeof(g));
	while (m--) {
		scanf("%d%d%d", &x, &y, &w);
		g[x][y] = min(g[x][y], w);
		g[y][x] = min(g[y][x], w);
	}
	prim();
   if (ans == -1)
		printf("No");
	else
		printf("%d", ans);
	return 0;
}
```


## 次小生成树


### Kruskal（严格）


```cpp
#include <cstdio>
#include <utility>
#include <algorithm>
#include <vector>


using namespace std;


struct edge {
	int u, v, w;
	inline bool operator< (const edge &edg) const {
		return w < edg.w;
	}
};


bool vis[1005];
int n, m, x, y, w, cur, sum, ans = 1e9, fa[1005], dis1[1005][1005], dis2[1005][1005];
vector<pair<int, int> > v[1005];
edge e[10005];


inline void add(int u, int v, int w) {
	++cur;
	e[cur] = {u, v, w};
}


int find(int u) {
	if (u == fa[u])
		return u;
	fa[u] = find(fa[u]);
	return fa[u];
}


void dfs(int u1, int u2, int father) {
	for (auto it: v[u2]) {
		x = it.first;
		y = it.second;
		if (x == father)
			continue;
		dis1[u1][x] = dis1[u1][u2];
		dis2[u1][x] = dis2[u1][u2];
		if (y > dis1[u1][x]) {
			dis2[u1][x] = dis1[u1][x];
			dis1[u1][x] = y;
		}
		else if (y < dis1[u1][x] && y > dis2[u1][x])
			dis2[u1][x] = y;
		dfs(u1, x, u2);
	}
}


int main() {
	scanf("%d%d", &n, &m);
	while (m--) {
		scanf("%d%d%d", &x, &y, &w);
		add(x, y, w);
	}
	sort(e + 1, e + cur + 1);
	for (register int i = 1; i <= n; ++i)
		fa[i] = i;
	for (register int i = 1; i <= cur; ++i) {
		x = find(e[i].u);
		y = find(e[i].v);
		if (x != y) {
			fa[x] = y;
			sum += e[i].w;
			vis[i] = true;
			v[e[i].u].push_back(make_pair(e[i].v, e[i].w));
			v[e[i].v].push_back(make_pair(e[i].u, e[i].w));
		}
	}
	for (register int i = 1; i <= n; ++i)
		dfs(i, i, 0);
	for (register int i = 1; i <= cur; ++i) {
		if (vis[i])
			continue;
		x = e[i].u;
		y = e[i].v;
		w = e[i].w;
		if (dis1[x][y] && w > dis1[x][y])
			ans = min(ans, sum - dis1[x][y] + w);
		else if (dis2[x][y] && w > dis2[x][y])
			ans = min(ans, sum - dis2[x][y] + w);
	}
	printf("%d", ans);
	return 0;
}
```






# 数据结构


## 树状数组


### 一维单点修改，区间查询


```cpp
template <typename T, const int _size> class BIT {
	protected:
		int n;
		T c[_size + 5];
		inline int lowbit(int x) {
			return x & -x;
		}
	public:
		inline void setlength(int N) {
			n = N;
		}
		inline void modify(int pos, T v) {
			for (; pos <= n; pos += lowbit(pos))
				c[pos] += v;
		}
		inline T query(int pos) {
			T sum = 0;
			for (; i; i -= lowbit(pos))
				sum += c[pos];
			return sum;
		}
		inline T query(int l, int r) {
			return query(r) - query(l - 1);
		}
};
```


### 二维区间修改，区间查询


```cpp
template <typename T, const int _sizex, const int _sizey> class BIT {
	protected:
		int n, m;
		T a[_sizex + 5][_sizey + 5], b[_sizex + 5][_sizey + 5], c[_sizex + 5][_sizey + 5], d[_sizex + 5][_sizey + 5];
		inline int lowbit(int x) {
			return x & -x;
		}
		inline void modify(int x, int y, T v) {
			for (register int i = x; i <= n; i += lowbit(i))
				for (register int j = y; j <= m; j += lowbit(j)) {
					a[i][j] += v;
					b[i][j] += v * (x - 1);
					c[i][j] += v * (y - 1);
					d[i][j] += v * (x - 1) * (y - 1);
				}
		}
	public:
		inline void setlength(int N, int M) {
			n = N;
			m = M;
		}
		inline void modify(int X1, int Y1, int X2, int Y2, T v) {
			modify(X1, Y1, v);
			modify(X1, Y2 + 1, -v);
			modify(X2 + 1, Y1, -v);
			modify(X2 + 1, Y2 + 1, v);
		}
		inline T query(int x, int y) {
			T ans = 0;
			for (register int i = x; i; i -= lowbit(i))
				for (register int j = y; j; j -= lowbit(j))
					ans += x * y * a[i][j] - x * c[i][j] - y * b[i][j] + d[i][j];
			return ans;
		}
		inline T query(int X1, int Y1, int X2, int Y2) {
			return query(X1 - 1, Y1 - 1) + query(X2, Y2) - query(X2, Y1 - 1) - query(X1 - 1, Y2);
		}
};
```


## 线段树


### 静态开点区间修改，区间查询


```cpp
#include <cstdio>


template <typename T, const int _size> class segment_tree {
	protected:
		int n;
		T tree[_size << 2], flag[_size << 2];
		inline void pushup(int pos) {
			tree[pos] = tree[pos << 1] + tree[pos << 1 | 1];
		}
		inline void pushdown(int pos, int mid, int l, int r) {
			if (flag[pos]) {
				tree[pos << 1] += flag[pos] * (mid - l + 1);
				tree[pos << 1 | 1] += flag[pos] * (r - mid);
				flag[pos << 1] += flag[pos];
				flag[pos << 1 | 1] += flag[pos];
				flag[pos] = 0;
			}
		}
		void build(T a[], int pos, int l, int r) {
			if (l == r) {
				tree[pos] = a[l];
				return;
			}
			int mid = l + r >> 1;
			build(a, pos << 1, l, mid);
			build(a, pos << 1 | 1, mid + 1, r);
			pushup(pos);
		}
		void update(int pos, int l, int r, int left, int right, T v) {
			if (l <= left && r >= right) {
				tree[pos] += (right - left + 1) * v;
				flag[pos] += v;
				return;
			}
			int mid = left + right >> 1;
			pushdown(pos, mid, left, right);
			if (l <= mid)
				update(pos << 1, l, r, left, mid, v);
			if (r > mid)
				update(pos << 1 | 1, l, r, mid + 1, right, v);
			pushup(pos);
		}
		T query(int pos, int l, int r, int left, int right) {
			if (l <= left && r >= right)
				return tree[pos];
			int mid = left + right >> 1;
			pushdown(pos, mid, left, right);
			T ans = 0;
			if (l <= mid)
				ans += query(pos << 1, l, r, left, mid);
			if (r > mid)
				ans += query(pos << 1 | 1, l, r, mid + 1, right);
			return ans;
		}
	public:
		segment_tree() {}
		~segment_tree() {}
		inline void build(int N, T a[]) {
			n = N;
			build(a, 1, 1, n);
		}
		inline void update(int l, int r, T v) {
			update(1, l, r, 1, n, v);
		}
		inline T query(int l, int r) {
			return query(1, l, r, 1, n);
		}
};


int n, m, opt, x, y;
long long k, a[100005];
segment_tree<long long, 100000> tree;


int main() {
	scanf("%d%d", &n, &m);
	for (register int i = 1; i <= n; ++i)
		scanf("%lld", a + i);
	tree.build(n, a);
	while (m--) {
		scanf("%d%d%d", &opt, &x, &y);
		if (opt == 1) {
			scanf("%lld", &k);
			tree.update(x, y, k);
		}
		else
			printf("%lld\n", tree.query(x, y));
	}
	return 0;
}
```


### 动态开点单点修改，区间查询


```cpp
#include <cstdio>


template <typename T, const int _size> class segment_tree {
	protected:
		int n, root, cur, lchild[_size << 1], rchild[_size << 1];
		T tree[_size << 1];
		inline void pushup(int pos) {
			tree[pos] = tree[lchild[pos]] + tree[rchild[pos]];
		}
		void update(int &pos, int l, int r, int cur, T v) {
			if (!pos) {
				++cur;
				pos = cur;
			}
			if (l == r) {
				tree[pos] += v;
				return;
			}
			int mid = l + r >> 1;
			if (cur <= mid)
				update(lchild[pos], l, mid, cur, v);
			else
				update(rchild[pos], mid + 1, r, cur, v);
			pushup(pos);
		}
		T query(int pos, int l, int r, int left, int right) {
			if (!pos)
				return 0;
			if (l >= left && r >= right)
				return tree[pos];
			int mid = l + r >> 1;
			T ans = 0;
			if (left <= mid)
				ans += query(lchild[pos], l, mid, left, right);
			if (right > mid)
				ans += query(rchild[pos], mid + 1, r, left, right);
			return ans;
		}
	public:
		segment_tree() {}
		~segment_tree() {}
		inline void build(int N, T a[]) {
			n = N;
			for (register int i = 1; i <= n; ++i) {
				update(root, 1, n, i, a[i]);
			}
		}
		inline void update(int pos, T v) {
			update(root, 1, n, pos, v);
		}
		inline T query(int l, int r) {
			return query(root, 1, n, l, r);
		}
};


int n, m, opt, x;
long long y, a[100005];
segment_tree<long long, 100000> tree;


int main()
{
	scanf("%d%d", &n, &m);
	for (register int i = 1; i <= n; ++i)
		scanf("%lld", a + i);
	tree.build(n, a);
	while (m--) {
		scanf("%d%d%lld", &opt, &x, &y);
		if (opt == 1)
			tree.update(x, y);
		else
			printf("%lld\n", tree.query(x, y));
	}
	return 0;
}
```


## 平衡树


### 旋转 treap


```cpp
#include <cstdio>
#include <cstdlib> 
#include <ctime>


template <typename T> class rotational_treap {
	private:
		struct node {
			node *child[2];
			T value, rank;
			int cnt, _size;
			node(T v) : value(v), cnt(1), _size(1) {
				child[0] = child[1] = nullptr;
				rank = rand();
			}
			inline void resize() {
				_size = cnt;
				if (child[0])
					_size += child[0]->_size;
				if (child[1])
					_size += child[1]->_size;
			}
		};
	protected:
		T last_prev, last_next;
		node *root;
		inline void rotate(node *&u, int mod) {
			node *temp = u->child[mod];
			u->child[mod] = temp->child[1 - mod];
			temp->child[1 - mod] = u;
			temp->resize();
			u->resize();
			u = temp;
		}
		void insert(node *&u, T v) {
			if (!u) {
				u = new node(v);
				return;
			}
			if (v == u->value) {
				++u->cnt;
				++u->_size;
			}
			else if (v < u->value) {
				insert(u->child[0], v);
				if (u->child[0]->rank < u->rank)
					rotate(u, 0);
				u->resize();
			}
			else {
				insert(u->child[1], v);
				if (u->child[1]->rank < u->rank)
					rotate(u, 1);
				u->resize();
			}
		}
		void remove(node *&u, int v) {
			if (v == u->value) {
				if (u->cnt > 1) {
					--u->cnt;
					--u->_size;
					return;
				}
				node *temp = u;
				if (u->child[0]) {
					if (u->child[1]) {
						int mod = (u->child[0]->rank >= u->child[1]->rank);
						rotate(u, mod);
						remove(u->child[1 - mod], v);
						u->resize();
					}
					else {
						u = temp->child[0];
						delete temp;
					}
				}
				else if (u->child[1]) {
					u = temp->child[1];
					delete temp;
				}
				else {
					delete u;
					u = nullptr;
				}
			}
			else {
				remove(u->child[v > u->value], v);
				u->resize();
			}
		}
		int rank(node *u, int v) {
			int num = 0;
			if (u->child[0])
				num = u->child[0]->_size;
			if (v == u->value)
				return num + 1;
			if (v < u->value) {
				if (u->child[0])
					return rank(u->child[0], v);
				return 1;
			}
			else if (u->child[1])
				return num + u->cnt + rank(u->child[1], v);
			return u->_size + 1;
		}
		int value(node *u, int rank) {
			int num = 0;
			if (u->child[0])
				num = u->child[0]->_size;
			if (rank <= num)
				return value(u->child[0], rank);
			if (rank <= num + u->cnt)
				return u->value;
			return value(u->child[1], rank - num - u->cnt);
		}
		int prev(node *u, int v) {
			if (v <= u->value)
				if (u->child[0])
					return prev(u->child[0], v);
			else {
				last_prev = u->value;
				if (u->child[1])
					prev(u->child[1], v);
				return last_prev;
			}
			return -1e8;
		}
		int next(node *u, int v) {
			if (v >= u->value)
				if (u->child[1])
					return next(u->child[1], v);
			else {
				last_next = u->value;
				if (u->child[0])
					next(u->child[0], v);
				return last_next;
			}
			return -1e8;
		}
	public:
		rotational_treap() {
			root = nullptr;
			last_prev = last_next = 0;
		}
		~rotational_treap() {
			delete root;
		}
		inline void insert(int v) {
			insert(root, v);
		}
		inline void remove(int v) {
			remove(root, v);
		}
		inline int rank(int v) {
			return rank(root, v);
		}
		inline int value(int rank) {
			return value(root, rank);
		}
		inline int prev(int v) {
			return prev(root, v);
		}
		inline int next(int v) {
			return next(root, v);
		}
};


int n, opt, x;
rotational_treap<int> tree;


int main() {
	scanf("%d", &n);
	while (n--)
	{
		scanf("%d%d", &opt, &x);
		switch (opt) {
			case 1:
				tree.insert(x);
				break;
			case 2:
				tree.remove(x);
				break;
			case 3:
				printf("%d\n", tree.rank(x));
				break;
			case 4:
				printf("%d\n", tree.value(x));
				break;
			case 5:
				printf("%d\n", tree.prev(x));
				break;
			case 6:
				printf("%d\n", tree.next(x));
				break;
		}
	}
	return 0;
}
```


### Fhq-treap


```cpp
#include <cstdio>
#include <cstdlib> 
#include <ctime>
#include <utility>
#include <tuple>


using namespace std;


template <typename T> class non_rotational_treap {
	private:
		struct node {
			node *child[2];
			T value;
			int rank, cnt, _size;
			node() {}
			node(T v) : value(v), cnt(1), _size(1) {
				child[0] = child[1] = nullptr;
				rank = rand();
			}
			inline void resize() {
				_size = cnt;
				if (child[0])
					_size += child[0]->_size;
				if (child[1])
					_size += child[1]->_size;
			}
		};
	protected:
		node *root;
		pair<node *, node *> split_by_value(node *u, T v) {
			if (!u)
				return make_pair(nullptr, nullptr);
			pair<node *, node *> temp;
			if (u->value <= v) {
				temp = split_by_value(u->child[1], v);
				u->child[1] = temp.first;
				u->resize();
				return make_pair(u, temp.second);
			}
			temp = split_by_value(u->child[0], v);
			u->child[0] = temp.second;
			u->resize();
			return make_pair(temp.first, u);
		}
		tuple<node *, node *, node *> split_by_rank(node *u, int rank) {
			if (!u)
				return make_tuple(nullptr, nullptr, nullptr);
			int num = 0;
			tuple<node *, node *, node *> temp;
			if (u->child[0])
				num = u->child[0]->_size;
			if (rank <= num) {
				temp = split_by_rank(u->child[0], rank);
				u->child[0] = get<2>(temp);
				u->resize();
				return make_tuple(get<0>(temp), get<1>(temp), u);
			}
			if (rank <= num + u->cnt) {
				node *temp1 = u->child[0], *temp2 = u->child[1];
				u->child[0] = u->child[1] = nullptr;
				return make_tuple(temp1, u, temp2);
			}
			temp = split_by_rank(u->child[1], rank - num - u->cnt);
			u->child[1] = get<0>(temp);
			u->resize();
			return make_tuple(u, get<1>(temp), get<2>(temp));
		}
		node *merge(node *u, node *v) {
			if (!u && !v)
				return nullptr;
			if (u && !v)
				return u;
			if (!u && v)
				return v;
			if (u->rank < v->rank) {
				u->child[1] = merge(u->child[1], v);
				u->resize();
				return u;
			}
			v->child[0] = merge(u, v->child[0]);
			v->resize();
			return v;
		}
		inline int rank(node *u, T v) {
			pair<node *, node *> temp = split_by_value(u, v - 1);
			int ans = 0;
			if (temp.first)
				ans = temp.first->_size;
			root = merge(temp.first, temp.second);
			return ans + 1;
		}
		inline T value(node *u, int rank) {
			tuple<node *, node *, node *> temp = split_by_rank(u, rank);
			T ans = get<1>(temp)->value;
			root = merge(merge(get<0>(temp), get<1>(temp)), get<2>(temp));
			return ans;
		}
	public:
		non_rotational_treap() {
			root = nullptr;
		}
		~non_rotational_treap() {
			delete root;
		}
		inline void insert(T v) {
			pair<node *, node *> temp = split_by_value(root, v), left = split_by_value(temp.first, v - 1);
			node *nod, *t, *combine;
			if (!left.second) {
				nod = new node(v);
				t = nod;
			}
			else {
				++left.second->cnt;
				left.second->resize();
				t = left.second;
			}
			combine = merge(left.first, t);
			root = merge(combine, temp.second);
		}
		inline void remove(T v) {
			pair<node *, node *> temp = split_by_value(root, v), left = split_by_value(temp.first, v - 1);
			if (left.second->cnt > 1) {
				--left.second->cnt;
				left.second->resize();
				left.first = merge(left.first, left.second);
			}
			else {
				if (temp.first == left.second)
					temp.first = nullptr;
				delete left.second;
				left.second = nullptr;
			}
			root = merge(left.first, temp.second);
		}
		inline int rank(T v) {
			return rank(root, v);
		}
		inline T value(int rank) {
			return value(root, rank);
		}
		inline T prev(T v) {
			pair<node *, node *> temp = split_by_value(root, v - 1);
			T ans = value(temp.first, temp.first->_size);
			root = merge(temp.first, temp.second);
			return ans;
		}
		inline T next(T v) {
			pair<node *, node *> temp = split_by_value(root, v);
			T ans = value(temp.second, 1);
			root = merge(temp.first, temp.second);
			return ans;
		}
};


int n, m, opt;
long long x, last, ans;
non_rotational_treap<long long> tree;


int main() {
	srand(time(0));
	scanf("%d%d", &n, &m);
	while (n--) {
		scanf("%lld", &x);
		tree.insert(x);
	}
	while (m--) {
		scanf("%d%lld", &opt, &x);
		switch (opt)
		{
			case 1:
				tree.insert(x);
				break;
			case 2:
				tree.remove(x);
				break;
			case 3:
				printf("%d\n", tree.rank(x));
				break;
			case 4:
				printf("%lld\n", tree.value(x));
				break;
			case 5:
				printf("%lld\n", tree.prev(x));
				break;
			case 6:
				printf("%lld\n", tree.next(x));
				break;
		}
	}
	return 0;
}
```


### 伸展树


### 可持久化旋转 treap


### 可持久化 Fhq-treap


```cpp
#include <cstdio>
#include <cstdlib>
#include <ctime>


template <typename T, const T inf, const int _size> class presistent_non_rotational_treap {
	public:
		int cur, root[_size + 5];
	protected:
		struct node {
			int Size, rank, child[2];
			T value;
		};
		node a[_size * 50 + 5];
		inline void resize(int pos) {
			a[pos].Size = 1;
			for (register int i = 0; i < 2; ++i)
				if (a[pos].child[i])
					a[pos].Size += a[a[pos].child[i]].Size;
		}
		inline int _insert(T v) {
			++cur;
			a[cur] = {1, rand(), {0, 0}, v};
			return cur;
		}
		int merge(int l, int r) {
			if (!l || !r)
				return l | r;
			int pos = _insert(0);
			if (a[l].rank < a[r].rank) {
				a[pos] = a[l];
				a[pos].child[1] = merge(a[pos].child[1], r);
			}
			else {
				a[pos] = a[r];
				a[pos].child[0] = merge(l, a[pos].child[0]);
			}
			resize(pos);
			return pos;
		}
		void split(int pos, int &l, int &r, T v) {
			if (!pos) {
				l = r = 0;
				return;
			}
			if (a[pos].value <= v) {
				l = _insert(0);
				a[l] = a[pos];
				split(a[l].child[1], a[l].child[1], r, v);
				resize(l);
				return;
			}
			r = _insert(0);
			a[r] = a[pos];
			split(a[r].child[0], l, a[r].child[0], v);
			resize(r);
		}
		int find(int pos, int rank) {
			if (rank <= a[a[pos].child[0]].Size)
				return find(a[pos].child[0], rank);
			if (a[pos].child[0])
				rank -= a[a[pos].child[0]].Size;
			--rank;
			if (!rank)
				return pos;
			return find(a[pos].child[1], rank);
		}
	public:
		presistent_non_rotational_treap() {}
		~presistent_non_rotational_treap() {}
		inline void insert(int id, T v) {
			int l = 0, r = 0;
			split(root[id], l, r, v);
			root[id] = merge(merge(l, _insert(v)), r);
		}
		inline void remove(int id, T v) {
			int l = 0, r = 0, temp = 0;
			split(root[id], l, temp, v);
			split(l, l, r, v - 1);
			r = merge(a[r].child[0], a[r].child[1]);
			root[id] = merge(merge(l, r), temp);
		}
		inline int rank(int id, T v) {
			int l = 0, r = 0, temp;
			split(root[id], l, r, v - 1);
			temp = a[l].Size + 1;
			root[id] = merge(l, r);
			return temp;
		}
		inline T value(int id, int rank) {
			return a[find(root[id], rank)].value;
		}
		inline T prev(int id, T v) {
			int l = 0, r = 0, temp = -inf;
			split(root[id], l, r, v - 1);
			if (l) {
				temp = a[find(l, a[l].Size)].value;
				root[id] = merge(l, r);
			}
			return temp;
		}
		inline T next(int id, T v) {
			int l = 0, r = 0, temp = inf;
			split(root[id], l, r, v);
			if (r) {
				temp = a[find(r, 1)].value;
				root[id] = merge(l, r);
			}
			return temp;
		}
};


int n, v, opt, x;
presistent_non_rotational_treap<int, 2147483647, 500000> tree;


int main() {
	scanf("%d", &n);
	for (register int i = 1; i <= n; ++i) {
		scanf("%d%d%d", &v, &opt, &x);
		tree.root[i] = tree.root[v];
		switch (opt) {
			case 1:
				tree.insert(i, x);
				break;
			case 2:
				tree.remove(i, x);
				break;
			case 3:
				printf("%d\n", tree.rank(i, x));
				break;
			case 4:
				printf("%d\n", tree.value(i, x));
				break;
			case 5:
				printf("%d\n", tree.prev(i, x));
				break;
			case 6:
				printf("%d\n", tree.next(i, x));
				break;
		}
	}
	return 0;
}
```


## 树套树


### 线段树套旋转 treap


```cpp
#include <cstdio>
#include <cstdlib>
#include <ctime>
#include <algorithm>


using namespace std;


template <typename T, const int __size> class rotational_treap {
	public:
		rotational_treap() {}
		~rotational_treap() {}
		int root, cur, temp, left_child[__size + 5], right_child[__size + 5], cnt[__size + 5], rank[__size + 5], _size[__size + 5];
		T value[__size + 5];
		inline void pushup(int pos) {
			_size[pos] = _size[left_child[pos]] + _size[right_child[pos]] + cnt[pos];
		}
		inline void left_rotate(int &pos) {
			int temp = right_child[pos];
			right_child[pos] = left_child[temp];
			left_child[temp] = pos;
			_size[temp] = _size[pos];
			pushup(pos);
			pos = temp;
		}
		inline void right_rotate(int &pos) {
			int temp = left_child[pos];
			left_child[pos] = right_child[temp];
			right_child[temp] = pos;
			_size[temp] = _size[pos];
			pushup(pos);
			pos = temp;
		}
		void _insert(int &pos, T v) {
			if (!pos) {
				++cur;
				pos = cur;
				cnt[pos] = 1;
				rank[pos] = rand();
				_size[pos] = 1;
				value[pos] = v;
				return;
			}
			++_size[pos];
			if (value[pos] < v) {
				_insert(right_child[pos], v);
				if (rank[right_child[pos]] < rank[pos])
					left_rotate(pos);
				return;
			}
			if (value[pos] > v) {
				_insert(left_child[pos], v);
				if (rank[left_child[pos]] < rank[pos])
					right_rotate(pos);
				return;
			}
			++cnt[pos];
		}
		void _remove(int &pos, T v) {
			if (!pos)
				return;
			if (value[pos] == v) {
				if (cnt[pos] > 1) {
					--cnt[pos];
					--_size[pos];
					return;
				}
				if (!left_child[pos] || !right_child[pos]) {
					pos = left_child[pos] + right_child[pos];
					return;
				}
				if (rank[left_child[pos]] < rank[right_child[pos]])
					right_rotate(pos);
				else
					left_rotate(pos);
				_remove(pos, v);
				return;
			}
			if (value[pos] < v)
				_remove(right_child[pos], v);
			else
				_remove(left_child[pos], v);
			--_size[pos];
		}
		int _rank(int pos, T v) {
			if (!pos)
				return 0;
			if (value[pos] == v)
				return _size[left_child[pos]];
			if (value[pos] < v)
				return _size[left_child[pos]] + cnt[pos] + _rank(right_child[pos], v);
			return _rank(left_child[pos], v);
		}
		T _value(int pos, int rank) {
			if (!pos)
				return 0;
			if (rank <= _size[left_child[pos]])
				return _value(left_child[pos], rank);
			if (rank > _size[left_child[pos]] + cnt[pos])
				return _value(right_child[pos], rank - _size[left_child[pos]] - cnt[pos]);
			return value[pos];
		}
		void _prev(int pos, T v) {
			if (!pos)
				return;
			if (value[pos] < v) {
				temp = value[pos];
				_prev(right_child[pos], v);
				return;
			}
			_prev(left_child[pos], v);
		}
		void _next(int pos, T v) {
			if (!pos)
				return;
			if (value[pos] > v) {
				temp = value[pos];
				_next(left_child[pos], v);
				return;
			}
			_next(right_child[pos], v);
		}
		inline T prev(int pos, T v) {
			temp = -2147483647;
			_prev(pos, v);
			return temp;
		}
		inline T next(int pos, T v) {
			temp = 2147483647;
			_next(pos, v);
			return temp;
		}
};


template <typename T, const int _size> class rotational_treap_in_segment_tree {
	private:
		struct node {
			int l, r, root;
		};
	protected:
		int n;
		T data[_size + 5];
		rotational_treap<T, _size * 60> treap;
		node tree[_size << 3];
		void build(int pos, int l, int r) {
			tree[pos] = {l, r, tree[pos].root};
			for (register int i = l; i <= r; ++i)
				treap._insert(tree[pos].root, data[i]);
			if (l == r)
				return;
			int mid = l + r >> 1;
			build(pos << 1, l, mid);
			build(pos << 1 | 1, mid + 1, r);
		}
		void modify(int pos, int cur, T v) {
			treap._remove(tree[pos].root, data[cur]);
			treap._insert(tree[pos].root, v);
			if (tree[pos].l == tree[pos].r)
				return;
			int mid = tree[pos].l + tree[pos].r >> 1;
			if (cur <= mid)
				modify(pos << 1, cur, v);
			else
				modify(pos << 1 | 1, cur, v);
		}
		int rank(int pos, int l, int r, T v) {
			if (tree[pos].l > r || tree[pos].r < l)
				return 0;
			if (tree[pos].l >= l && tree[pos].r <= r)
				return treap._rank(tree[pos].root, v);
			return rank(pos << 1, l, r, v) + rank(pos << 1 | 1, l, r, v);
		}
		T prev(int pos, int l, int r, T v) {
			if (tree[pos].l > r || tree[pos].r < l)
				return -2147483647;
			if (tree[pos].l >= l && tree[pos].r <= r)
				return treap.prev(tree[pos].root, v);
			return max(prev(pos << 1, l, r, v), prev(pos << 1 | 1, l, r, v));
		}
		T next(int pos, int l, int r, T v) {
			if (tree[pos].l > r || tree[pos].r < l)
				return 2147483647;
			if (tree[pos].l >= l && tree[pos].r <= r)
				return treap.next(tree[pos].root, v);
			return min(next(pos << 1, l, r, v), next(pos << 1 | 1, l, r, v));
		}
	public:
		rotational_treap_in_segment_tree() {}
		~rotational_treap_in_segment_tree() {}
		inline void build(int N, T a[]) {
			n = N;
			for (register int i = 1; i <= n; ++i)
				data[i] = a[i];
			build(1, 1, n);
		}
		inline void modify(int pos, T v) {
			modify(1, pos, v);
			data[pos] = v;
		}
		inline int rank(int l, int r, T v) {
			return rank(1, l, r, v) + 1;
		}
		inline T value(int l, int r, int k) {
			T L = 0, R = 1e8, mid;
			while (L < R) {
				mid = L + R + 1 >> 1;
				if (rank(1, l, r, mid) < k)
					L = mid;
				else
					R = mid - 1;
			}
			return L;
		}
		inline T prev(int l, int r, T v) {
			return prev(1, l, r, v);
		}
		inline T next(int l, int r, T v) {
			return next(1, l, r, v);
		}
};


int n, m, opt, l, r, k, a[50005];
rotational_treap_in_segment_tree<int, 50000> tree;


int main() {
	srand(time(0));
	scanf("%d%d", &n, &m);
	for (register int i = 1; i <= n; ++i)
		scanf("%d", a + i);
	tree.build(n, a);
	while (m--) {
		scanf("%d%d%d", &opt, &l, &r);
		switch (opt) {
			case 1:
				scanf("%d", &k);
				printf("%d\n", tree.rank(l, r, k));
				break;
			case 2:
				scanf("%d", &k);
				printf("%d\n", tree.value(l, r, k));
				break;
			case 3:
				tree.modify(l, r);
				break;
			case 4:
				scanf("%d", &k);
				printf("%d\n", tree.prev(l, r, k));
				break;
			default:
				scanf("%d", &k);
				printf("%d\n", tree.next(l, r, k));
		}
	}
	return 0;
}
```


## 左偏树


```cpp
#include <cstdio>
#include <algorithm>


using namespace std;


template <typename T, const T inf, const int _size> class leftist_tree {
	private:
		struct node {
			T w;
			int l, r, dis;
		};
	protected:
		int t1, t2, fa[_size + 5];
		node tree[_size + 5];
	public:
		leftist_tree() {}
		~leftist_tree() {}
		int find(int u) {
			if (u == fa[u])
				return u;
			fa[u] = find(fa[u]);
			return fa[u];
		}
		inline void build(int n, T a[]) {
			for (register int i = 1; i <= _size; ++i) {
				tree[i].w = a[i];
				tree[i].dis = 1;
				fa[i] = i;
			}
		}
		inline T query(int x) {
			return tree[x].w;
		}
		int merge(int l, int r) {
			if (!l || !r)
				return l | r;
			if (tree[l].w > tree[r].w || tree[l].w == tree[r].w && l > r)
				swap(l, r);
			tree[l].r = merge(tree[l].r, r);
			fa[tree[l].r] = l;
			if (tree[tree[l].r].dis > tree[tree[l].l].dis)
				swap(tree[l].l, tree[l].r);
			tree[l].dis = tree[tree[l].r].dis + 1;
			return l;
		}
		inline void remove(int u) {
			t1 = tree[u].l;
			t2 = tree[u].r;
			tree[u] = {inf, 0, 0, 1};
			fa[t1] = t1;
			fa[t2] = t2;
			fa[u] = merge(t1, t2);
		}
};


int n, m, opt, x, y, t1, t2, a[100005];
leftist_tree<int, 1000000000, 100000> tree;


int main() {
	scanf("%d%d", &n, &m);
	for (register int i = 1; i <= n; ++i)
		scanf("%d", a + i);
	tree.build(n, a);
	while (m--) {
		scanf("%d%d", &opt, &x);
		if (opt == 1) {
			scanf("%d", &y);
			t1 = tree.find(x);
			t2 = tree.find(y);
			if (tree.query(x) != 1e9 && tree.query(y) != 1e9 && t1 != t2)
				x = tree.merge(t1, t2);
		}
		else {
			if (tree.query(x) == 1e9)
				printf("-1");
			else {
				y = tree.find(x);
				printf("%d", tree.query(y));
				tree.remove(y);
			}
			putchar('\n');
		}
	}
	return 0;
}
```


## 树链剖分


### 重链剖分


```cpp
#include <cstdio>
#include <algorithm>


using namespace std;


template <typename T, const int _size> class segment_tree {
	protected:
		int n;
		T mod, tree[_size << 2], flag[_size << 2];
		inline void pushup(int pos) {
			tree[pos] = tree[pos << 1] + tree[pos << 1 | 1] % mod;
		}
		inline void pushdown(int pos, int l, int r, int mid) {
			if (flag[pos]) {
				tree[pos << 1] = (tree[pos << 1] + (mid - l + 1) * flag[pos]) % mod;
				tree[pos << 1 | 1] = (tree[pos << 1 | 1] + (r - mid) * flag[pos]) % mod;
				flag[pos << 1] = (flag[pos << 1] + flag[pos]) % mod;
				flag[pos << 1 | 1] = (flag[pos << 1 | 1] + flag[pos]) % mod;
				flag[pos] = 0;
			}
		}
		void build(T a[], int pos, int l, int r) {
			if (l == r) {
				tree[pos] = a[l];
				return;
			}
			int mid = l + r >> 1;
			build(a, pos << 1, l, mid);
			build(a, pos << 1 | 1, mid + 1, r);
			pushup(pos);
		}
		void modify(int pos, int l, int r, int left, int right, T v) {
			if (l <= left && r >= right) {
				tree[pos] = (tree[pos] + v * (right - left + 1)) % mod;
				flag[pos] = (flag[pos] + v) % mod;
				return;
			}
			int mid = left + right >> 1;
			pushdown(pos, left, right, mid);
			if (l <= mid)
				modify(pos << 1, l, r, left, mid, v);
			if (mid < r)
				modify(pos << 1 | 1, l, r, mid + 1, right, v);
			pushup(pos);
		}
		T query(int pos, int l, int r, int left, int right) {
			if (l <= left && r >= right)
				return tree[pos] % mod;
			int mid = left + right >> 1;
			T ans = 0;
			pushdown(pos, left, right, mid);
			if (l <= mid)
				ans = query(pos << 1, l, r, left, mid) % mod;
			if (mid < r)
				ans = (ans + query(pos << 1 | 1, l, r, mid + 1, right)) % mod;
			return ans;
		}
	public:
		segment_tree() {}
		~segment_tree() {}
		inline void build(int N, T Mod, T a[]) {
			n = N;
			mod = Mod;
			build(a, 1, 1, n);
		}
		inline void modify(int l, int r, T v) {
			modify(1, l, r, 1, n, v);
		}
		inline T query(int l, int r) {
			return query(1, l, r, 1, n);
		}
};


template <typename T, const int _node, const int _edge> class heavy_light_decomposition {
	private:
		struct edge {
			int next, to;
		};
	protected:
		int cur, cnt, fa[_node + 5], dfn[_node + 5], son[_node + 5], dep[_node + 5], _top[_node + 5], head[_node + 5], _size[_node + 5];
		T mod, w[_node + 5];
		edge e[_edge + 5];
		segment_tree<T, _node> tree;
		void dfs1(int u, int father) {
			fa[u] = father;
			dep[u] = dep[father] + 1;
			son[u] = -1;
			_size[u] = 1;
			for (register int i = head[u]; i; i = e[i].next) {
				if (e[i].to == father)
					continue;
				dfs1(e[i].to, u);
				_size[u] += _size[e[i].to];
				if (son[u] == -1 || _size[e[i].to] > _size[son[u]])
					son[u] = e[i].to;
			}
		}
		void dfs2(T a[], int u, int Top) {
			++cnt;
			w[cnt] = a[u];
			dfn[u] = cnt;
			_top[u] = Top;
			if (son[u] == -1)
				return;
			dfs2(a, son[u], Top);
			for (register int i = head[u]; i; i = e[i].next)
				if (e[i].to != fa[u] && e[i].to != son[u])
					dfs2(a, e[i].to, e[i].to);
		}
	public:
		heavy_light_decomposition() {}
		~heavy_light_decomposition() {}
		inline void add(int u, int v) {
			++cur;
			e[cur] = {head[u], v};
			head[u] = cur;
		}
		inline void build(int n, int root, T Mod, T W[]) {
			cnt = 0;
			mod = Mod;
			dfs1(root, 0);
			dfs2(W, root, root);
			tree.build(n, mod, w);
		}
		inline void modify1(int x, int y, int z) {
			z %= mod;
			while (_top[x] != _top[y]) {
				if (dep[_top[x]] < dep[_top[y]])
					swap(x, y);
				tree.modify(dfn[_top[x]], dfn[x], z);
				x = fa[_top[x]];
			}
			if (dep[x] > dep[y])
				swap(x, y);
			tree.modify(dfn[x], dfn[y], z);
		}
		inline void modify2(int pos, T v) {
			tree.modify(dfn[pos], dfn[pos] + _size[pos] - 1, v % mod);
		}
		inline T query1(int x, int y) {
			T ans = 0;
			while (_top[x] != _top[y]) {
				if (dep[_top[x]] < dep[_top[y]])
					swap(x, y);
				ans = (ans + tree.query(dfn[_top[x]], dfn[x])) % mod;
				x = fa[_top[x]];
			}
			if (dep[x] > dep[y])
				swap(x, y);
			return (ans + tree.query(dfn[x], dfn[y])) % mod;
		}
		inline T query2(int x) {
			return tree.query(dfn[x], dfn[x] + _size[x] - 1);
		}
};


int n, m, r, x, y, z, opt, mod, w[200005];
heavy_light_decomposition<int, 200000, 200000> tree;


int main() {
	scanf("%d%d%d%d", &n, &m, &r, &mod);
	for (register int i = 1; i <= n; ++i)
		scanf("%d", w + i);
	for (register int i = 1; i < n; ++i) {
		scanf("%d%d", &x, &y);
		tree.add(x, y);
		tree.add(y, x);
	}
	tree.build(n, r, mod, w);
	while (m--) {
		scanf("%d%d", &opt, &x);
		switch (opt) {
			case 1:
				scanf("%d%d", &y, &z);
				tree.modify1(x, y, z);
				break;
			case 2:
				scanf("%d", &y);
				printf("%d\n", tree.query1(x, y));
				break;
			case 3:
				scanf("%d", &y);
				tree.modify2(x, y);
				break;
			case 4:
				printf("%d\n", tree.query2(x));
				break;
		}
	}
	return 0;
}
```
