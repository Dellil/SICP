# Chapter 1 Exercise Solutions
## 1.3
``` scheme
(define (square x) (* x x))

(define (sum-of-squares x1 x2) (+ (square x1) (square x2)))

(define (two-biggest-of-three-numbers x1 x2 x3)
	(cond ((and (>= x1 x3) (>= x2 x3)) (sum-of-squares x1 x2))
	((and (>= x1 x2) (>= x3 x2)) (sum-of-squares x1 x3))
	((and (>= x2 x1) (>= x3 x1)) (sum-of-squares x2 x3))))
```
## 1.4

b의 값에 따라 연산자가 + or -로 정해짐
a = 5, b = 6을 주면

    (+ 5 6)
으로 값 11

a = 5, b = -6을 주면

	(- 5 -6)
으로 값 11

사실 b의 값이 크든 작든 a + |b|의 꼴이 됨

## 1.5

Application order라면 

	(test 0 (p))
코드가 계속 반복된다.

Normal order라면

	(if (= 0 0) 0 (p))))
가 되어 0이 나오게 된다.

## 1.6

if문은 파라미터 하나씩 evaluate함
근데 이건 프로시저라 applicative order evaluation을 따르므로 인자가 다 실행됨

하지만 세번째 인자가 재귀함수임   

그래서 개꿀잼몰카로 return을 못하고, 무한호출츠쿠요미에 빠지게 됨

## 1.7

0.0006 제곱근 구하면 0.031~ 나옴
good-enough?의 상수가 0.001이라 guess의 값이 다 구해지지도 않은 채 0,001보다 작은 경우가 나오기 때문임

문제에서 제시한 방향으로 값을 구하면 전보다는 잘 구해짐

``` scheme
(define (good-enough? guess x)
    (< (abs (- (square guess) x)) 0.001))
(sqrt 0.0006)
0.031886781440192566

(define (good-enough? guess x)
    (< (abs (- guess (new-guess guess x))) 0.001))
(sqrt 0.0006)
0.008045190289292459
```

## 1.8
``` scheme
(define (curt x)
    (define (square x) (* x x))
    (define (numerator guess)
      (+ (/ x (square guess))
         (* 2 guess)))
    (define (improve guess)
      (/ (numerator guess) 3))
    (define (good-enough? guess)
      (< (abs (- guess
                 (improve guess)))
         0.001))
    (define (curt-iter guess)
      (if (good-enough? guess)
          guess
          (curt-iter (improve guess))))
    (curt-iter 1.0))
```