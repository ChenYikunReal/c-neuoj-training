# 2020年下半年-选修课3

1.代码如下：
```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int n;
    while (scanf("%d", &n) != EOF)
    {
        for (int i = 1; i <= n; i++)
        {
            for (int j = 1; j <= i; j++)
            {
                printf("%d*%d=%-4d", j, i, i * j);
            }
            putchar('\n');
        }
    }

    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>
#include <math.h>

int main(int argc, char const *argv[])
{
    int col, row;
    char syb;
    while (scanf("%d %c", &col, &syb) != EOF)
    {
        row = round(col / 2.0);
        for (int i = 0; i < row; i++)
        {
            for (int j = 0; j < col; j++)
            {
                putchar(syb);
            }
            putchar('\n');
        }
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

int len(long long int);

int indexOf(long long int, int, int);

int main(int argc, char const *argv[])
{
    long long int input_0, input_1;
    int ret, sum, len_0, len_1;
    while (scanf("%lld %lld", &input_0, &input_1) != EOF)
    {
        ret = 0, sum = 0;
        len_0 = len(input_0), len_1 = len(input_1);
        for (int i = 0; i < len_0; i++)
        {
            sum = 0;
            for (int j = 0; j < len_1; j++)
            {
                sum += indexOf(input_0, len_0, i) * indexOf(input_1, len_1, j);
            }
            ret += sum;
        }
        printf("%d\n", ret);
    }
    return 0;
}

int len(long long int n)
{
    int ret = 0, tmp = n;
    while (tmp > 0)
    {
        ret++;
        tmp /= 10;
    }
    return ret;
}

int indexOf(long long int n, int len, int idx)
{
    return (int)(n / pow(10, len - idx - 1)) % 10;
}
```

4.代码如下：
```c
#include <stdio.h>

int main()
{
    int N;

    while (scanf("%d", &N) && N != 0)
    {
        int num[N];
        for (int i = 0; i < N; i++)
        {
            scanf("%d", num + i);
        }
        for (int i = 0; i < N; i++)
        {
            int count = 1;
            for (int j = 2; j * j <= num[i]; j++)
            {
                int n = 0;
                while (num[i] % j == 0)
                {
                    n++;
                    num[i] = num[i] / j;
                }
                if (n > 0)
                {        //可以约
                    n++; //0次方的可能
                    count *= n;
                }
            }
            if (num[i] > 1)
            { //把小于平方根的遍历完，还没有除尽，那么就是应该有大于平方根的
                count *= 2;
            }
            num[i] = count;
        }

        for (int i = 0; i < N; i++)
        {
            printf("%d\n", num[i]);
        }
    }
    return 0;
}

int count(long long int);

int count(long long int n)
{
    int ret = 0;
    for (long long int i = 1; i <= n; i++)
    {
        if (n % i == 0)
        {
            ret++;
        }
    }
    return ret;
}
```

5.代码如下：
```c
#include <stdio.h>
#include <ctype.h>

char next(char);

char before(char);

int main(int argc, char const *argv[])
{
    char ch;
    int n, i;
    while (scanf("%c %d", &ch, &n) != EOF)
    {
        i = 0;
        for (i = 0; i <= n / 2; i++)
        {
           for (int j = 0; j < n / 2 - i; j++)
           {
               putchar(' ');
           }
           putchar(ch);
           for (int j = 0; j < 2 * i - 1; j++)
           {
               putchar(' ');
           }
           if (i > 0)
           {
               putchar(ch);
           }
           putchar('\n');
           ch = next(ch);
        }
        ch = before(ch);
        for (i; i < n; i++)
        {
            ch = before(ch);
            for (int j = 0; j < i - n / 2; j++)
            {
                putchar(' ');
            }
            putchar(ch);
            for (int j = 0; j < 2 * (n - i - 1) - 1; j++)
            {
                putchar(' ');
            }
            if (i < n - 1)
            {
                putchar(ch);
            }
            putchar('\n');
        }
    }
    return 0;
}

char next(char ch)
{
    char res = 0;
    int upper = isupper(ch);
    ch = tolower(ch);
    if (ch == 'z')
    {
        res = 'a';
    }
    else
    {
        res = ch + 1;
    } 
    return upper ? toupper(res) : res;
}


char before(char ch)
{
    char res = 0;
    int upper = isupper(ch);
    ch = tolower(ch);
    if (ch == 'a')
    {
        res = 'z';
    }
    else
    {
        res = ch - 1;
    } 
    return upper ? toupper(res) : res;
}
```

6.代码如下：
```c
#include <stdio.h>

int last = 0;

int cpl(int);

int main(int argc, char const *argv[])
{
    int n;
    while (scanf("%d", &n) != EOF) 
    {
        for (int i = 1; i <= n; i++)
        {
            if (cpl(i)) 
            {
                printf("%d", i);
                if (i != last)
                {
                    putchar(' ');
                }
            }
        }
        putchar('\n');
    }
}

int cpl(int n)
{
    int sum = 0;
    for (int i = 1; i < n; i++)
    {
        if (n % i == 0)
        {
            sum += i;
            last = i;
        }
    }
    return sum == n ? 1 : 0;
}
```
