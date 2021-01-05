# 2020年下半年-选修课5

1.代码如下：
```c
#include <stdio.h>

char get(int);

int main() {
    // ' ' -> 0, '_' -> 1, '|' -> 2
    int table[10][3][3] = {
        {
            {0, 1, 0}, {2, 0, 2}, {2, 1, 2}
        },
        {
            {0, 0, 0}, {0, 0, 2}, {0, 0, 2}
        },
        {
            {0, 1, 0}, {0, 1, 2}, {2, 1, 0}
        },
        {
            {0, 1, 0}, {0, 1, 2}, {0, 1, 2}
        },
        {
            {0, 0, 0}, {2, 1, 2}, {0, 0, 2}
        },
        {
            {0, 1, 0}, {2, 1, 0}, {0, 1, 2}
        },
        {
            {0, 1, 0}, {2, 1, 0}, {2, 1, 2}
        },
        {
            {0, 1, 0}, {0, 0, 2}, {0, 0, 2}
        },
        {
            {0, 1, 0}, {2, 1, 2}, {2, 1, 2}
        },
        {
            {0, 1, 0}, {2, 1, 2}, {0, 1, 2}
        }
    };
    int input[4];
    while (scanf("%d %d %d %d", &input[0], &input[1], &input[2], &input[3]) != EOF) {
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 4; j++) {
                for (int k = 0; k < 3; k++) {
                    putchar(get(table[input[j]][i][k]));
                }
            }
            putchar('\n');
        }
    }
    return 0;
}

char get(int n) {
    char ret;
    switch (n) {
        case 0:
            ret = ' ';
            break;
        case 1:
            ret = '_';
            break;
        case 2:
            ret = '|';
            break;
        default:
            break;
    }
    return ret;
}
```

2.代码如下：
```c
#include <stdio.h>

#define OUTPUT "Dang"

int main() {
    int hour, min;
    while (scanf("%2d:%2d", &hour, &min) != EOF) {
        if (hour >= 12) {
            if (min > 0) {
                hour++;
            }
            for (int i = 0; i < hour - 12; i++) {
                printf("%s", OUTPUT);
            }
            putchar('\n');
        } else {
            printf("Only %02d:%02d.  Too early to Dang.\n", hour, min);
        }
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>

void func(int n, int k, int a[n][n], int b[n][n]);

int main() {
    int n, k;
    while (scanf("%d %d", &n, &k) != EOF) {
        int a[n][n], b[n][n];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                scanf("%d", &a[i][j]);
            }
        }
        func(n, k, a, b);
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                printf("%d ", a[i][j]);
            }
            putchar('\n');
        }
    }
}

void func(int n, int k, int a[n][n], int b[n][n]) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            b[i][j] = a[n - j - 1][i];
        }
    }
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            a[i][j] = b[i][j];
        }
    }
    if (k > 1) {
        func(n, k - 1, a, b);
    }
}
```

4.代码如下：
```c
#include <stdio.h>

int main() {
    int n;
    while (scanf("%d", &n) != EOF) {
        for (int i = 1; i <= n; i++) {
            if (i & 1) for (int j = (i - 1) * n + 1; j < i * n + 1; j++) printf("%d ", j);
            else for (int j = i * n; j > (i - 1) * n; j--) printf("%d ", j);
            putchar('\n');
        }
    }
    return 0;
}
```

5.代码如下：
```c
#include<stdio.h>
#include<stdlib.h>

int main()
{
    int n;
    int **Array;
    int i,j;
    int t,s,r,k;
    while(~scanf("%d",&n)) {
        Array = (int **)malloc(n * sizeof(int *));
        for(i = 0; i < n; i++)
            Array[i] = (int *)malloc(n * sizeof(int));
        i = 0,j = -1,t = 1;
        s = 1;
        k = n;
        while(s <= n * n) {
            for(r = 0; r < k; r++) {
                j += t;
                Array[i][j] = s++;
            }
            for(r = k; r < 2 * k - 1; r++) {
                i += t;
                Array[i][j] = s++;
            }
            k--;
            t = -t;
        }
        for(i = 0; i < n; i++) {
            for(j = 0; j < n; j++) {
                printf("%d", Array[i][j]);
                if(j != n - 1) printf(" ");
            }
            printf("\n");
        }
    }
    return 0;
}
```

6.代码如下：
```cpp

```

7.代码如下：
```c
#include <stdio.h>

int main() {
    int n;
    while (scanf("%d", &n) != EOF) {
        int arr[n][n];
        for (int i = 0; i < n; i++) {
            if (i & 1) {
                for (int j = 0; j < n; j++) {
                    arr[j][i] = (i + 1) * n - j;
                }
            } else {
                for (int j = 0; j < n; j++) {
                    arr[j][i] = i * n + j + 1;
                }
            }
        }
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                printf("%d ", arr[i][j]);
            }
            putchar('\n');
        }
    }
    return 0;
}
```
