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

```

3.代码如下：
```c
#include <stdio.h>

int main(int argc, char const *argv[])
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

```

7.代码如下：
```c

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
