# 2020年下半年-选修课2

1.代码如下：
```c
#include <stdio.h>

int main() {
    int f;
    while (scanf("%d", &f) != EOF) {
        printf("Celsius = %d\n", 5*(f-32)/9);
    }
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>

int main() {
    int n, max, sum, remain, ret, i;
    char ch;
    while (scanf("%d %c", &n, &ch) != EOF) {
        i = 0, sum = 1, max = 1, remain = 1, ret = 0;
        while (sum < n) {
            max += 2;
            sum += max * 2;
        }
        if (sum != n) {
            sum -= max * 2;
            max -= 2;
            ret = n - sum;
        }
        for (i = 0; i <= max / 2; i++) {
            for (int j = 0; j < i; j++) {
                putchar(' ');
            }
            for (int j = 0; j < max - 2 * i; j++) {
                putchar(ch);
            }
            putchar('\n');
        }
        for (i; i < max; i++) {
            for (int j = 0; j < max - i - 1; j++) {
                putchar(' ');
            }
            for (int j = 0; j < (i - max / 2) * 2 + 1; j++) {
                putchar(ch);
            }
            putchar('\n');
        }
        printf("%d\n", ret);
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>

int main()
{
    int n, len;
    while (scanf("%d", &n) != EOF)
    {
        for (int i = n; i > 0; i--)
        {
            len = i * 2 - 1;
            for (int j = 0; j < n - i; j++)
            {
                putchar(' ');
            }
            for (int j = 0; j < len; j++)
            {
                putchar('*');
            }
            putchar('\n');
        }
    }
    return 0;
}
```

4.代码如下：
```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int a, b, c, avg;
    scanf("%d%d%d", &a, &b, &c);
    avg = (a + b + c) / 3;
    printf("%d\n", avg);
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int a, b, c;
    double avg;
    scanf("%d%d%d", &a, &b, &c);
    avg = (a + b + c) / 3.0;
    printf("%.2f\n", avg);
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>

/*
 * simplify the problem as:
 * the number of 1 that turn n into binary 
 *      need to be less or equal than k
 *  the usage of x & (-x)
 */

/*
 * get the number of 1 when n is binary.
 */
int func(int);

int main(void) {
    int t, n, k, ret;
    while (scanf("%d", &t) != EOF) {
        for (int i = 0; i < t; i++) {
            ret = 0;
            scanf("%d %d", &n, &k);
            while (func(n) > k) {
                ret += n & (-n);
                n += n & (-n);
            }
            printf("%d\n", ret);
        }
    }
    return 0;
}

int func(int n) {
    int cnt = 0;
    for (; n; n -= n & (-n)) cnt++;
    return cnt;
}
```

7.代码如下：
```cpp
#include <iostream>
#include <cstdio>
#include <cstring>

using namespace std;

typedef long long ll;

int num[20], buf[20], n, t;
int dp[20][20][10][2][2][2];

ll l, r;

int dfs(int now, int len, int last, bool up, bool down, bool isP, bool lz, bool flag) {
    if (now == 0) return up && down && isP;
    if (!flag && dp[now][len][last][up][down][isP] != -1) {
        return dp[now][len][last][up][down][isP];
    }
    int res = 0;
    int u = flag ? num[now] : 9;
    for (int i = 0; i <= u; i++) {
        buf[now] = i;
        if (lz) {
            res += dfs(now - 1, len - (i == 0), i, up, down, 
                isP, i == 0, flag && i == u);
        }
        else if (i == last) {
            if (isP && now <= len / 2) {
                res += dfs(now - 1, len, i, up, down, i == buf[len + 1 - now], false, flag && i == u);
            } else {
                res += dfs(now - 1, len, i, up, down, isP, false, flag && i == u);
            }
        } else if (i < last) {
            if (up) continue;
            if (isP && now <= len / 2) {
                res += dfs(now - 1, len, i, false, true, i == buf[len + 1 - now], false, flag && i == u);
            } else {
                res += dfs(now - 1, len, i, false, true, isP, false, flag && i == u);
            }
        } else {
            if (!down) continue;
            if (isP && now <= len / 2) {
                res += dfs(now - 1, len, i, true, true, i == buf[len + 1 - now], false, flag && i == u);
            } else {
                res += dfs(now - 1, len, i, true, true, isP, false, flag && i == u);
            }
        }
    }
    return flag ? res : dp[now][len][last][up][down][isP] = res;
}

int query(ll x) {
    memset(dp, -1, sizeof(dp));
    n = 0;
    while (x) {
        num[++n] = x % 10;
        x /= 10;
    }
    return dfs(n, n, 0, false, false, true, true, true);
}

int main() {
    int t;
    while (scanf("%d", &t) != EOF) {
        while (t--) {
            scanf("%lld %lld", &l, &r);
            printf("%d\n", query(r) - query(l - 1));
        }
    }
    return 0;
}
```

8.代码如下：
```c
#include <stdio.h>

int func(int);

int main(int argc, char const *argv[])
{
    int n, a;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
    {
        scanf("%d", &a);
        printf("%d\n", func(a));
    }
    return 0;
}

int func(int n)
{
    int bot = n / 2, cap = bot, res = bot;
    int new_bot = 0, new_cap = 0;
    while (bot >= 2 || cap >= 4)
    {
        new_bot = bot / 2;
        new_cap = cap / 4;
        bot = bot - 2 * new_bot + new_bot + new_cap;
        cap = cap - 4 * new_cap + new_bot + new_cap;
        res += new_bot + new_cap;
    }
    return res;
}
```

9.代码如下：
```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int n, m;
    while (scanf("%d %d", &n, &m) != EOF)
    {
        int ar[n][m];
        for (int i = 0; i < n; i++)
        {
            for (int j = 0; j < m; j++)
            {
                scanf("%d", &ar[i][j]);
            }
        }
        for (int i = 0; i < m; i++)
        {
            int j;
            for (j = 0; j < n - 1; j++)
            {
                printf("%d ", ar[j][i]);
            }
            printf("%d", ar[j][i]);
            putchar('\n');
        }
    }
    return 0;
}
```
