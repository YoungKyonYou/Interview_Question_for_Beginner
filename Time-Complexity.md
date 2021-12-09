# 시간복잡도
- O(1): 상수 시간
- O(logN): 로그
- O(N): 직선(선형)
- O(NlogN): 선형 로그
- O(N^2): 제곱
- O(2^N): 지수(N의 n제곱)



##### ex1

- 한번 돌 때마다 b만큼 가서 a까지 가는 것이다
- 즉 a 나누기 b만큼 가는 것
- 답: O(a/b)

```java
int div(int a, int b){
    int count=0;
    int sum=b;
    while(sum<=a){
        sum+=b;
        count++;
    }
    return count;
}
```

###### ex2
- g가 n의 제곱근일때까지 함수를 돌린다
- g가 n의 제곱근때까지 커지면 반환하게 된다
- g^2<=n로 두고 g에 대한 식-> g<=sqrt(n) 이런 식으로 계산하기
```java
int sqrt(int n){
    for(int g=1;g*g<=n;g++){
        if(g*g==n){
            return g;
        }
    }
    return -1;
}
```


##### ex3

- 문제: If a binary search tree is not balanced, how long might it take (worst case) to find an element in it?
- 답: O(n)
- 이진 검색트리는 balance가 잘 맞을 때는 O(logn)의 시간이 걸린다
- 하지만 밸런스가 맞지 않아서 한쪽으로만 편향되어 있을때는 O(n)의 시간이 걸린다.


##### ex4

- 문제: You are looking for specific value in a binary tree, but the tree is not a binary search tree. what is the time complexity of this?
- 답: O(n)
- 모든 노드를 방문해야 되기 때문이다.


##### ex5

```java
int[] appendToNew(int[] array, int value){
    int[] bigger=new int[array.length+1];
    for(int i=0;i<array.length;i++){
        bigger[i]=array[i];
    }
    bigger[bigger.length-1]=value;
    return bigger;
}
```

```java
int[] copyArray(int[] array){
    int[] copy new int[0];
    for(int value: array){
        copy=appendToNew(copy,value);
    }
    return copy
}
```

- 답: O(n^2);


##### ex6

```java
int sumDigits(int n){
    int sum=0;
    while(n>0){
        sum+=n%10;
        n/=10;
    }
}
```

- 정답 : O(logN)
- 10씩 계속 뚝뚝 떨어진다 이진 검색 트리에서 2로 계속 나눠지는 것이랑 같다.


##### ex7

```java
int intersection(int[] a,int[] b){
    mergesort(b);
    int intersect=0;
    for(int x: a){
        if(binarySearch(b,x)>=0{
            intersect++;
        }
    }
    return intersect;
}
```

- 답: O(blogb+alogb)


##### ex 8

```java
int a=0
int b=0;
for(i=0;i<N;i++){
    for(int j=0;j<N;j++){
        a=a+j;
    }
}
for(k=0;k<N;k++){
    b=b+k;
}
```

- 답: O(N^2)


##### ex 9

```java 
int a=0;
for(i=0;i<N;i++){
    for(j=N;j>i;j--){
        a=a+i+j;
    }
}
```

- 답: O(n^2)


##### ex10

```java
if(x<7){
    print "x is less than 8";
}else{
    for(i=1;i<=n;i++){
        print i;
    }
}
```

- 답: O(N)


##### ex 11

```java
for(int x=1;x<=n;x*=2){
    print x;
}
```

- 답: O(logN)


##### ex 12

```java
int a=0, i=N;
while(i>0){
    a+=i;
    i/=2;
}
```

- 답: O(logN)(밑이 2)


##### ex 13

```java
for(i=1;i<n;i+=2){
    stmt;
}
```

- 답: n/2 지만 polynomial하게 보면 O(N)이다.


##### ex 14

```java
p=0;
for(int i=1;i<=n;i++){
    p=p+i;
}
```

- 답: sqrt(n)
- i:   1           2         3             4                   5     ------       k
- P:(0+1)      (0+1+2)    (0+1+2+3)     (0+1+2+3+4)  (0+1+2+3+4+5)       (0+1+2+3+4+5+---+k)
- P>N에 대한 식으로 변환 (0+1+2+3+4+---+k)=k(k+1)/2
- k(k+1)/2>N 
- k^2>N
- sqrt(k)>N
- 답: O(sqrt(k))

##### ex 15

```java
for(i=1;i<n;i=i*2){
    stmt;
}
```

- 답: logN

##### ex 16

```java
for(i=n;i>=1;i=i/2){
    stmt;
}
```

- 답: O(logN)

##### ex 17

```java
for(i=0;i*i<n;i++){
    stmt;
}
```

- i^2=>n
- i>=sqrt(n);
- O(sqrt(n))

##### ex 18

```java
for(i=1;i<n;i=i*2){
    p++;
}

for(j=1;j<p;j=j*2){
    stmt;
}
```

- 첫 번째 for에서 2^i>=n -> logn 즉 p=logn
- 두 번째 for 문에서 2^j>=P -> logp 
- p=logn 즉 loglogn
- 답: O(loglogn)


##### ex 19

```java
for(i=0;i<n;i++){
    for(j=1;j<n;j=j*2){
        stmt;
    }
}
```

- 답: O(nlogn)


##### 참고

- for(i=0;i<n;i++) ---- O(n)
- for(i=0;i<n;i=i+2)---- O(n)
- for(i=n;i>1;i--)----O(n)
- for(i=1;i<n;i=i*2)----O(logn)(밑이 2)
- for(i=1;i<n;i=i*3)----O(logn)(밑이 3)
- for(i=n;i>1;i=i/2)----O(logn)(밑이 2)


##### ex 20

```java
a=1;
while(a<b){
    stmt;
    a=a*2;
}
```
- k=logb(밑이 2)
- 답: O(logn)

##### ex 21

```java
i=n;
while(i>1){
    stmt;
    i=i/2;
}
```

- 답: O(logn)

##### ex 22
```java
i=1;
k=1;
while(k<n){
    stmt;
    k=k+i;
    i++;
}
```

- 답: O(sqrt(n))
- i =>&nbsp;;&nbsp;&nbsp;&nbsp;&nbsp; 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;----- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;m
- k => (1+1)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(2+2)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(2+2+3)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(2+2+3+4)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(2+2+3+4+.....+m)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;m(m+1)/2
- k>=n
- m(m+1)/2>=n
- m^2>=n
- m=sqrt(n)

##### ex 23
```java
for(k=1,i=1;k<n;i++)}
stmt;
k=k+i;
```
- 답:O(sqrt(n))
- 위의 문제와 똑같다.


##### ex 24
```java
while(m!=n){
    if(m>n){
        m=m-n;
    }else{
        n=n-m;
    }
}
```
- 답: maximum time: O(n)  minimum time: O(1)














