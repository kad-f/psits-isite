# PATTERN


## Number Pattern

### Arithmetic Sequence

```c
  for (int i = 0; i < 10; i++) {
        printf("%d ", 1 + i * 2); // 1 3 5 7 9
    }
```

### Geometric Sequence

```c
for (int i = 0; i < 5; i++) {
        printf("%d ", 1 * (int)pow(2, i)); // 1 2 4 8 16 
    }
```

### Fibonacci Seq
```c
 int first = 0, second = 1, next;

 for (int i = 0; i < 5; i++) {
        printf("%d ", firstTerm);
        next = first + second;
        first = second;
        second = next;
    }

```


### Square

```c
for(i=1; i<=N; i++)
    {
        for(j=1; j<=N; j++)
        {
            printf("*");
        }
        
        printf("\n");
    }
```

### Pascal Pattern

```c

int pascal(int n, int k) {
    int res = 1;
    if (k > n - k)
        k = n - k;
    for (int i = 0; i < k; ++i) {
        res *= (n - i);
        res /= (i + 1);
    }
    return res;
}

int n = 5; 
    
printf("Pascal's Triangle Pattern:\n");
for (int i = 0; i < n; i++) {
    for (int j = 0; j <= i; j++) {
            printf("%d ", pascal(i, j));
        }
        printf("\n");
    }

```