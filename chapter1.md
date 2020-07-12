# Chapter 1 Exercise Solutions
## 1.3

    (define (square x) (* x x))
    
    (define (sum-of-squares x1 x2) (+ (square x1) (square x2)))
    
    (define (two-biggest-of-three-numbers x1 x2 x3)
    	(cond ((and (>= x1 x3) (>= x2 x3)) (sum-of-squares x1 x2))
    	((and (>= x1 x2) (>= x3 x2)) (sum-of-squares x1 x3))
    	((and (>= x2 x1) (>= x3 x1)) (sum-of-squares x2 x3))))
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
