---
title: "3. 가늘고 긴 물체와 원과의 충돌 판정"
date: 2020-08-12 10:03
categories: Collision
---

## 3. 가늘고 긴 물체와 원과의 충돌 판정

### 구조체
```
var circleA = {x: 0, y: 0, r: 0};
```
- (x, y) : 원의 중점 좌표
- r : 원의 반지름
```
var rectCircleB = {x: 0, y: 0, vx: 0, vy: 0, r: 0, newVX: 0};
```
- rectCircleB를 선분으로 보고 양 끝에 반원을 형성한다고 보면 
- (x, y) : 선분 rectCircleB 벡터 (vx, vy)의 출발 좌표
- r : 선분의 굵기의 반, 선분 끝 원의 반지름
- newVX : 회전된 선분 rectCircleB의 새 벡터의 vx 값

### 함수 collisionCircle_RectCircle

```
function collisionCircle_RectCircle(pCircle, pRectCircle) {
	var nResult = false, dx, dy, t, mx, my, ar, fDistSqr, fRate;
    
	fRate = pRectCircle.newVX / pRectCircle.vx;

	dx = pCircle.x - pRectCircle.x;				// ⊿ｘ
	dy = pCircle.y - pRectCircle.y;				// ⊿ｙ

	t = (pRectCircle.vx * dx + pRectCircle.vy * dy) / (pRectCircle.vx * pRectCircle.vx + pRectCircle.vy * pRectCircle.vy);
	if (t < 0) { t = 0; }					    // t의 하한
	if (t > fRate) { t = fRate;	}				// t의 상한 (1이 정상이나 도형그리기에 오차를 보정한 값)
	mx = pRectCircle.vx * t + pRectCircle.x;	// 최소 위치가 되는 좌표
	my = pRectCircle.vy * t + pRectCircle.y;
	fDistSqr = (mx - pCircle.x) * (mx - pCircle.x) + (my - pCircle.y) * (my - pCircle.y);	// 거리의 제곱 
	ar = pCircle.r + pRectCircle.r;
	if (fDistSqr < ar * ar) {					// 제곱인 채로 비교 
		nResult = true;
	}
    
	return nResult;
}
```

### 함수 call
```
```

### 설명
- fRate : 원본 vx의 길이를 t = 1 이라고 할때 선분 rectCircleB가 회전된 후 얻어지는 newVX 의 비율로 t의 상한값으로 사용됨
- dx : 원의 중점의 x 값과 선분 rectCircleB 벡터의 출발점의 x 값의 차이
- dy : 원의 중점의 y 값과 선분 rectCircleB 벡터의 출발점의 y 값의 차이