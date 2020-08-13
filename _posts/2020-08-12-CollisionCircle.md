---
title: "2. 원형끼리 충돌 판정"
date: 2020-08-12 10:02
categories: Collision
---

## 2. 원형끼리 충돌 판정

### 구조체
```
var circleA = {x: 0, y: 0, r: 0};
var circleB = {x: 0, y: 0, r: 0};
```

### 함수 collisionCircle
```
function collisionCircle(pCircle1, pCircle2) {
	var nResult = false, dx, dy, ar, fDistSqr;

    dx = pCircle1.x - pCircle2.x;				// ⊿ｘ
	dy = pCircle1.y - pCircle2.y;				// ⊿ｙ
	fDistSqr = dx * dx + dy * dy;				// 거리의 제곱 
	ar = pCircle1.r + pCircle2.r;
	if (fDistSqr < ar * ar) {					// 제곱으로 비교 
		nResult = true;
	}
    
	return nResult;
}
```

### 함수 call
```
collisionCircle(circleA, circleB);
```

### 설명
두 원형의 중점간의 거리가 두 원형의 반지름을 더한 값 보다 작으면 충돌