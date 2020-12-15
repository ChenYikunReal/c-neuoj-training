# 2020年下半年-选修课1

1.代码如下：
```c
#include <stdio.h>

int main() {
    printf("%.4lf %.4lf %.4lf", 1.0/2, 1.0/3, 1.0/9);
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>

int main() {
    printf("#include<stdio.h>\nint main()\n{\nprintf(\"Hello World!\\n\");\nreturn 0;\n}");
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>
#include <math.h>

int main() {
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    printf("r1=%.2lf\nr2=%.2lf", (-b+sqrt(b*b-4*a*c))/(2*a), (-b-sqrt(b*b-4*a*c))/(2*a));
    return 0;
}
```

4.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a+b);
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b;
    while (scanf("%d %d", &a, &b) != EOF) {
        printf("%d\n", a+b);
    }
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>

int main() {
    int n, i, a, b;
    scanf("%d", &n);
    for (i = 0; i < n; i++) {
        scanf("%d %d", &a, &b);
        printf("%d\n", a+b);
    }
    return 0;
}
```

7.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b;
    while (scanf("%d %d", &a, &b) && (a||b)) {
        printf("%d\n", a+b);
    }
    return 0;
}
```

8.代码如下：
```c
#include <stdio.h>

int main() {
    int n, sum;
    while (scanf("%d", &n) && n) {
        int x;
        sum = 0;
        while (n--) {
            scanf("%d", &x);
            sum += x;
        }
        printf("%d\n", sum);
    }
    return 0;
}
```

9.代码如下：
```c
#include <stdio.h>

int main() {
    int count, n, sum;
    scanf("%d", &count);
    while (count--) {
        int x;
        sum = 0;
        scanf("%d", &n);
        while (n--) {
            scanf("%d", &x);
            sum += x;
        }
        printf("%d\n", sum);
    }
    return 0;
}
```

10.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b, count = 0;
    while (scanf("%d %d", &a, &b) != EOF && (a||b)) {
        printf("Case %d: %d\n", ++count, a+b);
    }
    return 0;
}
```
