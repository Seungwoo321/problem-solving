# 문제풀이

- 크기가 N * N인 행렬 A의 B제곱을 구하는 문제

## 로직

- 알고리즘 문제해결전략1(종만북)의 7장 분할정복 예제 코드를 연습해 볼 수 있는 문제

## 리팩토링

- `pow` 함수에서 거듭제곱을 할 때 재귀호출을 사용하는데 메모이제이션을 통해 중간결과를 저장하고 재사용 할 수 있다.
- 행렬 곱을 구하는 `timesMatrix` 함수에서 모듈러 연산(mod)을 적용하면 시간 초과 하지 않고 최적화 할 수 있다