# 2020年下半年-选修课4

1.代码如下：
```c
#include <stdio.h>
#include <string.h>

int main() {
    int n, diff_1, diff_2, res;
    scanf("%d", &n);
    getchar();
    char input[6];
    const char *one = "one";
    const char *two = "two";
    for (int i = 0; i < n; i++) {
        gets(input);
        diff_1 = 0;
        diff_2 = 0;
        if (strlen(input) == 5) {
            res = 3;
        } else {
            for (int j = 0; j < 3; j++) {
                if (input[j] != one[j]) diff_1++;
                if (input[j] != two[j]) diff_2++;
            }
            if (diff_1 < diff_2) {
                res = 1;
            } else {
                res = 2;
            }
        }
        printf("%d\n", res);
    }
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define LEN 100

int cmp(const void *, const void *);

int main() {
    char input[LEN];
    gets(input);
    qsort(input, strlen(input), sizeof(char), cmp);
    puts(input);
    return 0;
}

int cmp(const void *a, const void *b) {
    return *((char *)a) - *((char *)b);
}
```

3.代码如下：
```c
#include <stdio.h>
#include <stdlib.h>

#define RIGHT_TRIANGLE 1
#define ACUTE_TRIANGLE 2
#define OBTUES_TRIANGLE 3
#define INVALID_TRIANGLE -1

int triangle(double *);

int cmp(const void *, const void *);

/*
 *勾股定理逆定理
 * */
int triangle(double *arr)
{
    if (arr[0] <= 0 || arr[1] <= 0 || arr[2] <= 0)
    {
        return INVALID_TRIANGLE;
    }
    qsort(arr, 3, sizeof(double), cmp);
    if (arr[0] + arr[1] <= arr[2]) 
    {
        return INVALID_TRIANGLE;
    }
    else if (arr[0] * arr[0] + arr[1] * arr[1] == arr[2] * arr[2]) 
    {
        return RIGHT_TRIANGLE;
    }
    else if (arr[0] * arr[0] + arr[1] * arr[1] > arr[2] * arr[2]) 
    {
        return ACUTE_TRIANGLE;
    }
    else 
    {
        return OBTUES_TRIANGLE;
    }
}

int cmp(const void *a, const void *b)
{
    return *((double *)a) - *((double *)b);
}

int main()
{
    double a[3];
    int i=0,j;
    while(scanf("%lf",&a[0])!=EOF)
    {   
        scanf("%lf",&a[1]);
        scanf("%lf",&a[2]);
        if((a[0]+a[1]>a[2])&&(a[0]+a[2]>a[1])&&(a[1]+a[2]>a[0]))
        {
            if((a[0]*a[0]+a[1]*a[1]==a[2]*a[2])||(a[0]*a[0]+a[2]*a[2]==a[1]*a[1])||(a[1]*a[1]+a[2]*a[2]==a[0]*a[0]))
                printf("Z\n\n");
            else if((a[0]*a[0]+a[1]*a[1]>a[2]*a[2])&&(a[0]*a[0]+a[2]*a[2]>a[1]*a[1])&&(a[1]*a[1]+a[2]*a[2]>a[0]*a[0]))
                printf("R\n\n");
            else printf("D\n\n");
        }
        else printf("N\n\n");
    }
    return 0;
}
```

4.代码如下：
```c
#include<stdio.h>
#include <string.h>

#define LEN 10000

/*
 * the bits of input is less than 10000
 * even long long int cannot store the input.
 * need to use char array to solve the problem.
 * */
int main() {
    char input[LEN];
    int length, is_reverse;
    while (fgets(input, LEN, stdin) && input[0] != EOF) {
        length = strlen(input);
        is_reverse = 1;
        for (int i = 0; i < length / 2; i++) {
            if (input[i] != input[length - i - 2]) {
                puts("NO");
                is_reverse = 0;
                break;
            }
        }
        if (is_reverse) puts("Yes");
    }
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>

int main()
{
    double rate, sum, n;
    while (scanf("%lf%%", &rate) != EOF)
    {
        sum += rate;
        n++;
    }
    printf("%.4f\n", sum / (n * 100));
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>
#include <string.h>

#define LEN 2000

/*
 * the bits of input is less than 1000
 * even long long int cannot store the input
 * need to use char array to solve the problem.
 * */
int main() {
    char input[LEN];
    while (fgets(input, LEN, stdin) != NULL && input[0] != EOF) {
        int length = strlen(input);
        int arr[10] = {0};
        for (int i = 0; i < length; i++) {
            arr[input[i] - 48]++;
        }
        for (int i = 0; i < 10; i++) {
            if (arr[i] > 0) printf("%d:%d\n", i, arr[i]);
        }
    }
    return 0;
}
```

7.代码如下：
```c
#include <stdio.h>
#include <string.h>

#define LEN 100

/*
 * alalyse the duplicate letter, assume it's A
 * the situation can devide into these:
 * 1. XAAX
 * 2. XAXAX
 * 3. AXXA
 * 4. AXAX
 * for situation 1:
 *      cannot satisfy the requirement.
 *      because chees cannot jump in place.
 * for situation 2, 3, 4:
 *      satisfy the requirement.
 * endfor
 * 
 * so what we need to do is to check if input can be shown as situation 2, 3, 4.
  * */
int main() {
    char input[LEN];
    int satisfy;
    while (scanf("%s", input) != EOF && input[0] != EOF) {
        satisfy = 1;
        int length = strlen(input);
        for (int i = 0; i < length - 1; i++) {
            if (input[i] == input[i + 1]) {
                satisfy = 0;
                break;
            }
        }
        if (satisfy) puts("Yes");
        else puts("No");
    }
    return 0;
}
```

8.代码如下：
```c
#include <stdio.h>
#include <string.h>

#define LEN 12

int binary_search(const char **, const char *, int);

int main(int argc, char const *argv[]) {
    const char *tablewares[] = {
        "bowl",  "chopsticks", "fork", "knife"
    };
    int n, pos;
    char input[LEN];
    while (scanf("%d", &n) != EOF) {
        for (int i = 0; i < n; i++) {
            scanf("%s", input);
            pos = binary_search(tablewares, input, 4);
            if (pos > -1) {
                printf("%s ", input);
                continue;
            }
        }
        putchar('\n');
    }
}

int binary_search(const char **arr, const char *src, int n) {
    int lw = 0, hg = n, md;
    while (lw < hg) {
        md = ((hg - lw) >> 1) + lw;
        if (strcmp(src, arr[md]) > 0) lw = md + 1;
        else if (strcmp(src, arr[md]) < 0) hg = md - 1;
        else return md;
    }
    if (lw == hg && strcmp(src, arr[lw]) == 0) return lw;
    return -1;
}
```

9.代码如下：
```c
#include <stdio.h>
#include <stdlib.h>

#define LEN 16

typedef struct info {
    char admin[LEN];
    int cptnum;
    int setnum;
} Info;

int cmp(const void *, const void *);

int binary_search(Info *, int, int);

int main(int argc, char const *argv) {
    int n, m, qrycptnum, pos;
    while (scanf("%d", &n) != EOF) {
        Info arr[n];
        for (int i = 0; i < n; i++) {
            scanf("%s %d %d", arr[i].admin, &arr[i].cptnum, &arr[i].setnum);
        }
        qsort(arr, n, sizeof(Info), cmp);
        scanf("%d", &m);
        for (int i = 0; i < m; i++) {
            scanf("%d", &qrycptnum);
            pos = binary_search(arr, n, qrycptnum);
            if (pos > -1) {
                printf("%s %d\n", arr[pos].admin, arr[pos].setnum);
            }
        }
    }
    return 0;
}

int cmp(const void *a, const void *b) {
    return ((Info *)a)->cptnum - ((Info *)b)->cptnum;
}

int binary_search(Info *a, int n, int target) {
    int lw = 0, hg = n - 1, md;
    while (lw < hg) {
        md = ((hg - lw) >> 1) + lw;
        if (a[md].cptnum <target)
            lw = md + 1;
        else if (a[md].cptnum > target)
            hg = md - 1;
        else
            return md;
    }
    if (lw == hg && a[lw].cptnum == target)
        return lw;
    return -1;
}
```
