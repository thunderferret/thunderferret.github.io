---
layout: post
title: "알고리즘 1부 : 재귀함수에 대한 이해"
date: 2019-01-07
categories: 알고리즘 TIL 재귀호출
---

## 1. 재귀함수 3


<p>재귀함수의 핵심은 **Clean Code 라고 할 수 있다.** 재귀함수는 직관적이고 이해하기 쉽다. 재귀함수는 **Iter Type** 이라고 불리는 반복문을 사용한 형식과 완전히 호환 가능한 형태이다. 재귀호출을 사용하면, OS의 입장에서 레코드로 스택이 계속 쌓이는 과정이 추가되기 때문에, 반복문과 시간 복잡도는 동일할수는 있어도 훨씬 느리며 **Stack Overflow** 등의 에러가 날 확률이 높다. 그럼에도 알고리즘에서 재귀함수를 가장 먼저 사용하는 것은 재귀함수가 가진 직관적인 문제 해결력이라고 할 수 있을 것이다. </p>

<p>재귀함수는 크게 두 부분으로 나누어진다. 재귀호출을 반복하는 부분과, 그것을 수렴하도록 만드는 **"Base Case"** 부분이다. 예를 한번 들어보자. </p>

### 파이썬
```python

for i in range(10):
  print(i)


```

### C
```c
#include <stdio.h>

int main(){
printf("Hello World!")
);
  return 0;
}


```

### JAVA
```java

public class maze{
  maze(){};
  public int mazeReturn(){return 10;}

}

```
