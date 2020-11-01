---
layout: default
title: 사각형끼리의 충돌 판정
parent: Collision
nav_order: 1
---

## 1. 사각형끼리의 충돌 판정

### 사각형 구조체 사용
```
var rect_A = {left: 0, top: 0, right: 0, bottom: 0};
var rect_B = {left: 0, top: 0, right: 0, bottom: 0};
```

### 함수 collisionRect

```
function collisionRect(pRect1, pRect2) {
	var nResult = false;

	if ((pRect1.right > pRect2.left) && (pRect1.left  < pRect2.right)) {
		if ((pRect1.bottom > pRect2.top) && (pRect1.top < pRect2.bottom)) {
			nResult = true;
		}
	}

	return nResult;
}
```

### 함수 call
```
collisionRect(rect_A, rect_B);
```

### 설명

**사각형끼리 충돌하지 않는 상황**
1. [상황1] 사각형 1의 오른쪽 끝이 사각형 2의 왼쪽보다 **왼쪽**에 있는 경우
2. [상황2] 사각형 1의 왼쪽 끝이 사각형 2의 오른쪽보다 **오른쪽**에 있는 경우
3. [상황1]이거나 혹은  [상황2]인 경우 충돌하지 않는다.
4. 즉 `[상황1] || [상황2]`

**사각형끼리 충돌하는 상황**

1. `not ([상황1] || [상황2])`
2. not[상황1] && not[상황2]  드모르간의 법칙 적용
3. [상황A] = not[상황1] : 사각형 1의 오른쪽 끝이 사각형 2의 왼쪽보다 **오른쪽**에 있는 경우
4. [상황B] = not[상황2] : 사각형 1의 왼쪽 끝이 사각형 2의 오른쪽보다 **왼쪽**에 있는 경우
5. 즉 not[상황1] && not[상황2] == [상황A] && [상황B]
6. [상황A] : pRect1.right > pRect2.left
7. [상황B] : pRect1.left  < pRect2.right
