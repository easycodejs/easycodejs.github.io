---
title: "2bis. 원형과 사각형 충돌 판정"
date: 2020-08-12 10:00:00 -0400
categories: Collision
---

---
## 원형과 사각형 충돌

### 구조체
```
var circle_A = {x: 0, y: 0, r: 0};
var rect_B = {left: 0, top: 0, right: 0, bottom: 0};
```

### 함수 collisionCircleRect
```
function distanceSqr(x1, y1, x2, y2) {	            // 거리의 제곱 계산 
    var dx, dy;							            // 위치의 차이 

	dx = x2 - x1;									// ⊿ｘ
	dy = y2 - y1;									// ⊿ｙ

	return dx * dx + dy * dy;
}

function collisionCircleRect(pRect, pCircle) {
	var nResult = false, ar, fDistSqr;

	// 큰 장방형 체크 
	if ((pCircle.x > pRect.left - pCircle.r) && (pCircle.x < pRect.right  + pCircle.r) && (pCircle.y > pRect.top - pCircle.r) && (pCircle.y < pRect.bottom + pCircle.r)) {
		nResult = true;
        ar = pCircle.r;
		// 네 귀퉁이 체크
		// 왼쪽 끝 체크 
		if (pCircle.x < pRect.left) {
			// [귀퉁이 체크 1] 좌측상단 모서리 체크 
            if (pCircle.y < pRect.top) {
				if (distanceSqr(pRect.left, pRect.top, pCircle.x, pCircle.y) >= ar * ar) {
					nResult = false;
				}
			} else {
				// [귀퉁이 체크 2] 좌측하단 모서리 체크 
				if (pCircle.y > pRect.bottom) {
					if ((distanceSqr(pRect.left, pRect.bottom, pCircle.x, pCircle.y) >= ar * ar)) {
						nResult = false;
					}
				}
			}
		} else {
			// 오른쪽 끝 체크 
			if (pCircle.x > pRect.right) {
				// [귀퉁이 체크 3] 우측 상단 모서리 체크 
				if (pCircle.y < pRect.top) {
					if (distanceSqr(pRect.right, pRect.top, pCircle.x, pCircle.y) >= ar * ar) {
						nResult = false;
					}
				} else {
					// [귀퉁이 체크 4] 좌측 하단 모서리 체크 
					if (pCircle.y > pRect.bottom) {
						if (distanceSqr(pRect.right, pRect.bottom, pCircle.x, pCircle.y) >= ar * ar) {
							nResult = false;
						}
					}
				}
			}
		}
	}
    
	return nResult;
}
```

### 함수 call
```
collisionCircleRect(rect_B, circle_A)
```

#### 설명
1. function distanceSqr(x1, y1, x2, y2)  
네 귀퉁이 체크 시 사각형의 정점이 원 내부에 포함되는지 판단하기 위한 거리 측정용  
사각형의 정점과 원의 중점과의 거리의 제곱 값을 계산하여 리턴  
(x1, y1) : 원에서 제일 가까운 사각형의 정점  
(x2, y2) : 원의 중점
2. 판정할 사각형보다 상하좌우 각각 원의 반지름 r 만큼 확장한 사각형 안에 원의 중심 좌표가 포함되면 충돌 가능성이 있다.
3. 2의 조건을 만족해도 원의 중심 좌표가 원래 사각형의 밖, 확장된 사각형의 각 모퉁이에 있고 또한 원이 사각형의 가장 가까운 정점을 내부에 포함하지 않을 때는 충돌하지 않는다.  
[큰 장방형 체크] : 확장된 사각형 안에 원의 중점이 있고 (2의 조건을 만족 즉 nResult = true;), 
	- [귀퉁이 체크 1] : 사각형의 *좌측상단* 모서리에서 원이 사각형의 *좌측상단* 정점을 내부에 포함하지 않으면 (nResult = false;)
	- [귀퉁이 체크 2] : 사각형의 *좌측하단* 모서리에서 원이 사각형의 *좌측하단* 정점을 내부에 포함하지 않으면 (nResult = false;)
	- [귀퉁이 체크 3] : 사각형의 *우측상단* 모서리에서 원이 사각형의 *우측상단* 정점을 내부에 포함하지 않으면 (nResult = false;)
	- [귀퉁이 체크 4] : 사각형의 *우측하단* 모서리에서 원이 사각형의 *우측하단* 정점을 내부에 포함하지 않으면 (nResult = false;)

---

