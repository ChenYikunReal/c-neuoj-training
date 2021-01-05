# 2020年下半年-选修课7

1.代码如下：
```c
#include <string.h>
#include <stdio.h>

#define LEN 10000

int contains(const char *, char, int);

int main() {
    char input[LEN], minus[LEN];
    int inlen, minlen;
    while (gets(input) && gets(minus) && input[0] != EOF) {
        inlen = strlen(input);
        minlen = strlen(minus);
        for (int i = 0; i < inlen; i++) {
            if (!contains(minus, input[i], minlen)) putchar(input[i]);
        }
        putchar('\n');
    }
    return 0;
}

int contains(const char *str, char x, int n) {
    for (int i = 0; i < n; i++) {
        if (str[i] == x) return 1;
    }
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>

int main() {
    int n, ret;
    while (scanf("%d", &n) != EOF) {
        ret = 1;
        for (int i = 0; i < n; i++) {
            ret *= 2;
        }
        printf("2^%d = %d\n", n, ret);
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>
#include <string.h>

#define LEN 100

char *get(int);

int main() {
    int n, remain;
    char input[LEN];
    int tmp[LEN], idx;
    while (scanf("%d", &n) != EOF) {
        if (n < 0) {
            printf("fu ");
            n = -n;
        } else if (n == 0) {
            printf("%s\n", get(n));
            continue;
        }
        idx = 0;
        remain = 0;
        while (n > 0) {
            remain = n % 10;
            n /= 10;
            tmp[idx++] = remain;
        }
        for (int i = idx - 1; i >= 0; i--) {
            printf("%s", get(tmp[i]));
            if (i != 0) {
                putchar(' ');
            }
        }
        putchar('\n');
    }
    return 0;
}

char *get(int n) {
    char *ret;
    switch (n) {
        case 0:
            ret = "ling";
            break;
        case 1:
            ret = "yi";
            break;
        case 2:
            ret = "er";
            break;
        case 3:
            ret = "san";
            break;
        case 4:
            ret = "si";
            break;
        case 5:
            ret = "wu";
            break;
        case 6:
            ret = "liu";
            break;
        case 7:
            ret = "qi";
            break;
        case 8:
            ret = "ba";
            break;
        case 9:
            ret = "jiu";
            break;
        default:
            ret = "error";
            break;
    }
    return ret;
}
```

4.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b, count, sum;
    while (scanf("%d %d", &a, &b) != EOF) {
        count = 0, sum = 0;
        for (int i = a; i <= b; i++) {
            if (count == 5) {
                count = 0;
                putchar('\n');
            }
            printf("%5d", i);
            sum += i;
            count++;
        }
        printf("\nsum = %d\n", sum);
    }
    return 0;
}
```

5.代码如下：
```cpp
#include<iostream>

using namespace std;

long long gcd(long long a, long long b)//求最大公约数
{
    if (a == 0) return 0;
    else return (b==0)? a: gcd(b, a % b);
}

int main()
{
    long long n,a,b,nume,deno,divisor,lcm;
    while (scanf("%lld", &n) != EOF) {
        if (n == 0) {
            printf("0\n");
            continue;
        }
        scanf("%lld/%lld",&nume,&deno);
        divisor = gcd(nume, deno);
        if(divisor){
            nume /= divisor;deno /= divisor;
        }
        for (int i = 1; i < n; i++)
        {
            scanf("%lld/%lld",&a,&b);
            lcm = deno / gcd(deno, b) * b ;
            nume = lcm/deno*nume + lcm/b*a;
            deno = lcm;
            divisor = gcd(abs(nume), abs(deno));//divisor为最大公因数
            if(divisor){
                nume /= divisor;//分子约分
                deno /= divisor;//分母约分
            }
        }
        if ((deno < 0 && nume > 0) || (deno < 0 && nume < 0)) {
            deno = -deno;
            nume = -nume;
        }
        if (nume&&nume/deno == 0) {
            printf("%lld/%lld\n", nume, deno);
        } else if (nume%deno == 0) {
            printf("%lld\n", nume/deno);
        } else {
            printf("%lld %lld/%lld\n",nume/deno, nume%deno,deno);
        }
    }
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b, c, low, mid, high;
    while (scanf("%d %d %d", &a, &b, &c) != EOF) {
        if (a > b && a > c) {
            high = a;
            if (b > c) {
                mid = b;
                low = c;
            } else {
                mid = c;
                low = b;
            }
        } else if (b > a && b > c) {
            high = b;
            if (a > c) {
                mid = a;
                low = c;
            } else {
                mid = c;
                low = a;
            }
        } else {
            high = c;
            if (a > b) {
                mid = a;
                low = b;
            } else {
                mid = b;
                low = a;
            }
        }
        printf("%d->%d->%d\n", low, mid, high);
    }
    return 0;
}
```

7.代码如下：
```c
#include <stdio.h>

int main() {
    int n, ret, mul;
    while (scanf("%d", &n) != EOF) {
        ret = 0;
        for (int i = 1; i <= n; i++) {
            mul = 1;
            for (int j = 1; j <= i; j++) {
                mul *= j;
            }
            ret += mul;
        }
        printf("%d\n", ret);
    }
    return 0;
}
```

8.代码如下：
```c
#include <stdio.h>

int main() {
    int n, cols;
    char ch;
    while (scanf("%d %c", &n, &ch) != EOF) {
        cols = (n & 1) ? n / 2 + 1 : n / 2;
        for (int i = 0; i < cols; i++) {
            for (int j = 0; j < n; j++) {
                putchar(ch);
            }
            putchar('\n');
        }
    }
    return 0;
}
```

9.代码如下：
```c
#include <stdio.h>

int main() {
    int xvol, yvol, n, xwow, ywow, xshow, yshow;
    int xcount, ycount, xlose, ylose, done;
    while (scanf("%d %d %d", &xvol, &yvol, &n) != EOF) {
        xcount = 0, ycount = 0, done = 0;
        for (int i = 0; i < n; i++) {
            scanf("%d %d %d %d", &xwow, &xshow, &ywow, &yshow);
            if (!done) {
                xlose = (xshow == xwow + ywow);
                ylose = (yshow == xwow + ywow);
                if (xlose && !ylose) xcount++;
                if (!xlose && ylose) ycount++;
                if (xcount > xvol) {
                    printf("A\n%d\n", ycount);
                    done = 1;
                } 
                if (ycount > yvol) {
                    printf("B\n%d\n", xcount);
                    done = 1;
                }
            }
        }
    }
    return 0;
}
```

10.代码如下：
```c
#include <stdio.h>
#include <ctype.h>

#define LEN 20
#define VALID_LEN 17

int main() {
    int n, sum, all_pass, pass;
    char input[LEN];
    int frac[] = {7, 9, 10, 5, 8, 4, 2, 1, 6, 3, 7, 9, 10, 5, 8, 4, 2};
    char check[] = {'1', '0', 'X', '9', '8', '7', '6', '5', '4', '3', '2'};
    while (scanf("%d", &n) != EOF) {
        all_pass = 1;
        for (int i = 0; i < n; i++) {
            pass = 1;
            scanf("%s", input);
            sum = 0;
            for (int j = 0; j < VALID_LEN; j++) {
                if (!isdigit(input[j])) {
                    puts(input);
                    all_pass = 0;
                    pass = 0;
                    break;
                }
                sum += frac[j] * (input[j] - '0');
            }
            if (pass) {
                sum = sum % 11;
                if (check[sum] != input[VALID_LEN]) {
                    puts(input);
                    all_pass = 0;
                }
            }
        }
        if (all_pass) puts("All passed");
    }
    return 0;
}
```

11.代码如下：
```c
#include <stdio.h>
#include <string.h>

#define LEN 60

int main() {
    char input[LEN];
    double ret, frac;
    int count, len, total;
    while (scanf("%s", input) != EOF) {
        total = len = strlen(input);
        frac = 1, ret = 0.0, count = 0;
        if (input[0] == '-') {
            total--;
            frac *= 1.5;
        }
        if (((input[len - 1] - '0') & 1) == 0) frac *= 2.0;
        for (int i = 0; i < len; i++) {
            if (input[i] == '2') count++;
        }
        ret = (double)count / (double)total;
        ret *= frac;
        printf("%.2f%%\n", ret * 100);
    }
    return 0;
}
```
