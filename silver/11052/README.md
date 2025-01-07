# 문제풀이: 11052 카드 구매하기

dp 문제의 핵심은 점화식이다.

## 아이디어

- i개의 카드를 사는데 마지막으로 선택한 카드는 j개짜리 카드를 가진 카드팩일 수 있다.
- 예를 들어 i개 카드를 사기 위해서 마지막에 j개짜리 카드팩을 하나 샀다고 가정하면
  - i - j개의 카드를 이미 샀을 때의 최댓값에 j개짜리 카드팩의 가격 P[j-1]을 더한 값이 dp[i]가 된다.
- 즉 dp[i]는 dp[i - j] + P[j]와 같은 형태가 된다.
  - i - j개의 카드를 구매한 뒤 j개짜리 카드팩을 하나 더 사면 i개가 되기 때문이다.

## 점화식

dp[i]를 구하기 위해서 아래와 같은 점화식을 사용할 수 있다.

```bash
dp[i] = max(dp[i], dp[i-j] + P[j-1])
```

- dp[i] : i개의 카드를 구매했을 때의 최댓값
- dp[i-j] : 이미 i - j개의 카드를 구매한 후의 최댓값
- P[j-1] : j개의 카드팩의 가격 (0-based index이므로 P[j-1]로 참조)

## 설명

- i개의 카드를 만들기 위해서는 이전에 구매한 카드 수와 관련된 상태에서 가격을 갱신한다.
- 예를 들어 i = 5일 때 j는 1, 2, 3 ..., 5까지 가질 수 있다. 그때마다 dp[i - j] + P[j-1]을 비교하여 최댓값을 구한다.

## 예시

카드의 개수 N = 5일 때 카드팩 가격이 P = [3, 5, 7, 8, 9]라면 dp[1]은 1개 카드를 사는데 최댓값, dp[2]는 2개의 카드를 사는 최댓값, dp[3]은 3개의 카드를 사는데 최댓값을 구해야 한다.

- dp[5]는 5개의 카드를 구매하기 위한 최댓값을 구한다.
  - dp[5]는 dp[5-1] + P[0], dp[5-2] + P[1], dp[5-3] + P[2], dp[5-4] + P[3], dp[5-5] + P[4] 중 최댓값을 선택하는 방식이다.