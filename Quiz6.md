# 2020年下半年-选修课6

1.代码如下：
```c
#include <stdio.h>

int main() {
    int n, cube, ret;
    while (scanf("%d", &n) != EOF) {
        ret = 0;
        cube = n * n * n;
        for (int i = 1; i < cube; i += 2) {
            if (n * (n - 1) + n * i == cube) {
                ret = i;
                break;
            }
        }
        for (int i = 0; i < n; i++) {
            printf("%5d ", ret + i * 2);
        }
    }
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>
#include <limits.h>

int main() {
    for (int i = 11; i < INT_MAX; i++) {
        if (i % 5 == 1 && i % 6 == 5 && i % 7 == 4 && i % 11 == 10) {
            printf("%d\n", i);
            break;
        }
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>

int expa(int, int, int, int);

int expb(int, int, int, int);

int expc(int, int, int, int);

int expd(int, int, int, int);

int main() {
    for (int b = 1; b < 5; b++) {
        for (int d = 1; d < 5; d++) {
            for (int a = 1; a < 5; a++) {
                for (int h = 1; h < 5; h++) {
                    if (expa(b, d, a, h) && expb(b, d, a, h) 
                            && expc(b, d, a, h) && expd(b, d, a, h)) {
                        printf("%d%d%d%d\n", b, d, a, h);
                    }
                }
            }
        }
    }
    return 0;
}

int expa(int b, int d, int a, int h) {
    return d == 1 ^ b == 3;
}

int expb(int b, int d, int a, int h) {
    return a == 2 ^ h == 4;
}

int expc(int b, int d, int a, int h) {
    return a == 1 ^ b == 4;
}

int expd(int b, int d, int a, int h) {
    return d == 2 ^ h == 3;
}
```

4.代码如下：
```c

```

5.代码如下：
```c
#include <stdio.h>

int main() {
    int n, oddc, evenc, cur;
    while (scanf("%d", &n) != EOF) {
        oddc = 0, evenc = 0;
        for (int i = 0; i < n; i++) {
            scanf("%d", &cur);
            if (cur & 1) oddc++;
            else evenc++;
        }
        printf("%d %d\n", oddc, evenc);
    }
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>

int main(void) {
    int h;
    double ret;
    while (scanf("%d", &h) != EOF) {
        ret = (h - 100) * 0.9 * 2;
        printf("%.1f\n", ret);
    }
    return 0;
}
```

7.代码如下：
```c
#include <stdio.h>

int main() {
    int cur, ret;
    while (scanf("%d", &cur) != EOF) {
        ret = cur > 5 ? cur - 5 : cur + 2;
        printf("%d\n", ret);
    }
    return 0;
}
```

8.代码如下：
```c
#include <string.h>
#include <ctype.h>
#include <stdio.h>

#define LEN 10010

int main() {
    char input[LEN];
    int len, gc, pc, lc, tc, tot;
    while (scanf("%s", input) != EOF) {
        gc = pc = lc = tc = 0;
        len = strlen(input);
        for (int i = 0; i < len; i++) {
            switch (toupper(input[i])) {
                case 'G':
                    gc++;
                    break;
                case 'P':
                    pc++;
                    break;
                case 'L':
                    lc++;
                    break;
                case 'T':
                    tc++;
                    break;
                default:
                    break;
            }
        }
        tot = gc + pc + lc + tc;
        for (int i = 0; i < tot; i++) {
            if (gc-- > 0) putchar('G');
            if (pc-- > 0) putchar('P');
            if (lc-- > 0) putchar('L');
            if (tc-- > 0) putchar('T');
        }
        putchar('\n');
    }
   return 0;
}
```

9.代码如下：
```cpp

```
