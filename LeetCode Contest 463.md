# LeetCode Contest 463 - Complete Solutions Guide

## Table of Contents

- [Problem 1: Best Time to Buy and Sell Stock using Strategy](#problem-1-best-time-to-buy-and-sell-stock-using-strategy)
- [Problem 2: XOR After Range Multiplication Queries I](#problem-2-xor-after-range-multiplication-queries-i)
- [Problem 3: Minimum Sum After Divisible Sum Deletions](#problem-3-minimum-sum-after-divisible-sum-deletions)
- [Problem 4: XOR After Range Multiplication Queries II](#problem-4-xor-after-range-multiplication-queries-ii)
- [Key Takeaways](#key-takeaways)
- [Links](#links)

---

## Problem 1: [3652. Best Time to Buy and Sell Stock using Strategy](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-using-strategy/description/)

### Problem Understanding

- You can modify at most one contiguous subarray of length `k`.
- The modification sets the first `k/2` elements to `0` (hold) and last `k/2` elements to `1` (sell).
- Maximize `profit = sum(strategy[i] * prices[i])`.

### Approach

- Compute original profit without modifications.
- For each possible subarray of length `k`, calculate the gain from modification:
    - **Gain = new profit from modification - old profit from that subarray**
    - New profit: sum of prices in last `k/2` positions (`sell`)
    - Old profit: sum of `strategy[i] * prices[i]` in the k-subarray
- Use prefix sums for efficiency.

### Solutions

#### Java

```java
class Solution {
    public long maxProfit(int[] prices, int[] strategy, int k) {
        int n = prices.length;
        long originalProfit = 0;
        for (int i = 0; i < n; i++) {
            originalProfit += (long) strategy[i] * prices[i];
        }
        long[] prefixPrice = new long[n + 1];
        long[] prefixStrategyProfit = new long[n + 1];
        for (int i = 0; i < n; i++) {
            prefixPrice[i + 1] = prefixPrice[i] + prices[i];
            prefixStrategyProfit[i + 1] = prefixStrategyProfit[i] + (long) strategy[i] * prices[i];
        }
        long bestGain = 0;
        for (int start = 0; start + k <= n; start++) {
            int end = start + k;
            int mid = start + k / 2;
            long newProfit = prefixPrice[end] - prefixPrice[mid];
            long oldProfit = prefixStrategyProfit[end] - prefixStrategyProfit[start];
            long gain = newProfit - oldProfit;
            bestGain = Math.max(bestGain, gain);
        }
        return originalProfit + bestGain;
    }
}
```

#### C++

```cpp
class Solution {
public:
    long long maxProfit(vector<int>& prices, vector<int>& strategy, int k) {
        int n = prices.size();
        long long originalProfit = 0;
        for(int i = 0; i < n; i++) originalProfit += (long long)strategy[i] * prices[i];

        vector<long long> prefixPrice(n + 1, 0), prefixStrategyProfit(n + 1, 0);
        for(int i = 0; i < n; i++){
            prefixPrice[i+1] = prefixPrice[i] + prices[i];
            prefixStrategyProfit[i+1] = prefixStrategyProfit[i] + (long long)strategy[i] * prices[i];
        }

        long long bestGain = 0;
        for(int start = 0; start + k <= n; start++){
            int end = start + k, mid = start + k/2;
            long long newProfit = prefixPrice[end] - prefixPrice[mid];
            long long oldProfit = prefixStrategyProfit[end] - prefixStrategyProfit[start];
            bestGain = max(bestGain, newProfit - oldProfit);
        }
        return originalProfit + bestGain;
    }
};
```

#### Python

```python
class Solution:
    def maxProfit(self, prices: List[int], strategy: List[int], k: int) -> int:
        n = len(prices)
        originalProfit = sum(strategy[i] * prices[i] for i in range(n))

        prefixPrice = [0] * (n + 1)
        prefixStrategyProfit = [0] * (n + 1)
        for i in range(n):
            prefixPrice[i+1] = prefixPrice[i] + prices[i]
            prefixStrategyProfit[i+1] = prefixStrategyProfit[i] + strategy[i] * prices[i]

        bestGain = 0
        for start in range(n - k + 1):
            end = start + k
            mid = start + k // 2
            newProfit = prefixPrice[end] - prefixPrice[mid]
            oldProfit = prefixStrategyProfit[end] - prefixStrategyProfit[start]
            bestGain = max(bestGain, newProfit - oldProfit)

        return originalProfit + bestGain
```

#### JavaScript

```javascript
var maxProfit = function(prices, strategy, k) {
    const n = prices.length;
    let originalProfit = 0;
    for(let i = 0; i < n; i++) originalProfit += strategy[i] * prices[i];

    const prefixPrice = Array(n+1).fill(0);
    const prefixStrategyProfit = Array(n+1).fill(0);
    for(let i = 0; i < n; i++){
        prefixPrice[i+1] = prefixPrice[i] + prices[i];
        prefixStrategyProfit[i+1] = prefixStrategyProfit[i] + strategy[i] * prices[i];
    }

    let bestGain = 0;
    for(let start = 0; start + k <= n; start++){
        const end = start + k;
        const mid = start + k/2;
        const newProfit = prefixPrice[end] - prefixPrice[mid];
        const oldProfit = prefixStrategyProfit[end] - prefixStrategyProfit[start];
        bestGain = Math.max(bestGain, newProfit - oldProfit);
    }
    return originalProfit + bestGain;
};
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(n)`

---

## Problem 2: [3653. XOR After Range Multiplication Queries I](https://leetcode.com/problems/xor-after-range-multiplication-queries-i/description/)

### Problem Understanding

- For each query `[li, ri, ki, vi]`:
    - Start at index `li`
    - Multiply elements at indices `li, li+ki, li+2*ki, ...` by `vi` (mod 10^9+7)
    - Continue until index exceeds `ri`
- Return XOR of all elements after all queries.

### Approach

- Simulate each query.
- For each, iterate through specified indices and multiply.
- Apply modulo to prevent overflow.
- Finally XOR all elements together.

### Solutions

#### Java

```java
class Solution {
    public int xorAfterQueries(int[] nums, int[][] queries) {
        int MOD = 1_000_000_007;
        for (int[] query : queries) {
            int li = query[0], ri = query[1], ki = query[2], vi = query[3];
            int idx = li;
            while (idx <= ri) {
                nums[idx] = (int)((1L * nums[idx] * vi) % MOD);
                idx += ki;
            }
        }
        int result = 0;
        for (int num : nums) result ^= num;
        return result;
    }
}
```

#### C++

```cpp
class Solution {
public:
    int xorAfterQueries(vector<int>& nums, vector<vector<int>>& queries) {
        const int MOD = 1e9 + 7;
        for (auto &query : queries) {
            int li = query[0], ri = query[1], ki = query[2], vi = query[3];
            for (int idx = li; idx <= ri; idx += ki) {
                nums[idx] = (1LL * nums[idx] * vi) % MOD;
            }
        }
        int result = 0;
        for (int num : nums) result ^= num;
        return result;
    }
};
```

#### Python

```python
class Solution:
    def xorAfterQueries(self, nums: List[int], queries: List[List[int]]) -> int:
        MOD = 10**9 + 7
        for li, ri, ki, vi in queries:
            idx = li
            while idx <= ri:
                nums[idx] = (nums[idx] * vi) % MOD
                idx += ki
        result = 0
        for num in nums:
            result ^= num
        return result
```

#### JavaScript

```javascript
var xorAfterQueries = function(nums, queries) {
    const MOD = 1e9 + 7;
    for (const [li, ri, ki, vi] of queries) {
        for (let idx = li; idx <= ri; idx += ki) {
            nums[idx] = (nums[idx] * vi) % MOD;
        }
    }
    return nums.reduce((acc, num) => acc ^ num, 0);
};
```

**Time Complexity:** `O(q * n)`  
**Space Complexity:** `O(1)`

---

## Problem 3: [3654. Minimum Sum After Divisible Sum Deletions](https://leetcode.com/problems/minimum-sum-after-divisible-sum-deletions/description/)

### Problem Understanding

- You can delete contiguous subarrays whose sum is divisible by `k`.
- After deletion, remaining elements close the gap.
- Find minimum possible sum after any number of deletions.

### Approach

- Dynamic programming with prefix sums.
- Track maximum sum we can delete using DP.
- `dp[r]` represents the maximum deletable sum ending at current position with remainder `r`.
- For each position, check if you can form a new deletable segment.

### Solutions

#### Java

```java
class Solution {
    public long minArraySum(int[] A, int k) {
        long[] dp = new long[k];
        Arrays.fill(dp, Long.MAX_VALUE);
        dp[0] = 0;
        long res = 0;
        for (int a : A) {
            res += a;
            int index = (int) (res % k);
            res = dp[index] = Math.min(dp[index], res);
        }
        return res;
    }
}
```

#### C++

```cpp
class Solution {
public:
    long long minArraySum(vector<int>& A, int k) {
        vector<long long> dp(k, LLONG_MAX);
        dp[0] = 0;
        long long res = 0;
        for (int a : A) {
            res += a;
            res = dp[res % k] = min(dp[res % k], res);
        }
        return res;
    }
};
```

#### Python

```python
from typing import List
from collections import defaultdict

class Solution:
    def minArraySum(self, nums: List[int], k: int) -> int:
        n = len(nums)
        prefix = 0
        total = sum(nums)
        dp = 0 
        best = defaultdict(lambda: float('-inf'))
        best[0] = 0
        for x in nums:
            prefix += x
            mod = prefix % k
            new_dp = dp
            if best[mod] != float('inf'):
                new_dp = max(new_dp, prefix + best[mod])
            dp = new_dp
            best[mod] = max(best[mod], dp - prefix)
        return total - dp
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(k)`

---

## Problem 4: [3655. XOR After Range Multiplication Queries II](https://leetcode.com/problems/xor-after-range-multiplication-queries-ii/description/)

### Problem Understanding

- Similar to Problem 2 but with larger constraints (`n, q ≤ 10^5`), requiring optimization.

### Approach

- Query Compression: Combine queries with same `(l%k, r, k)` pattern
- Square Root Decomposition: Handle small `k` values differently from large ones
- Lazy Propagation: Use differential arrays for efficient range updates
- Modular Arithmetic: Use inverse operations

#### Strategies:

- Small `k` (`≤ √n`): Lazy propagation with differential arrays
- Large `k` (`> √n`): Direct simulation

### Solutions

#### Java (Optimized)

```java
class Solution {
    static final long MOD = 1_000_000_007L;
    public int xorAfterQueries(int[] nums, int[][] queries) {
        int n = nums.length;
        Map<Long, Integer> queryMap = new HashMap<>();
        for (int[] q : queries) {
            int l = q[0], r = q[1], k = q[2], v = q[3];
            long key = (long)l * 10000000000L + (long)r * 100000L + k;
            queryMap.put(key, (int)((1L * queryMap.getOrDefault(key, 1) * v) % MOD));
        }
        for (long key : queryMap.keySet()) {
            long L = key / 10000000000L;
            long R = (key / 100000L) % 100000;
            long K = key % 100000;
            for (int i = (int)L; i <= (int)R; i += (int)K) {
                nums[i] = (int)((1L * nums[i] * queryMap.get(key)) % MOD);
            }
        }
        int result = 0;
        for (int num : nums) result ^= num;
        return result;
    }
}
```

#### Python (Square Root Decomposition)

```python
class Solution:
    def xorAfterQueries(self, A: List[int], queries: List[List[int]]) -> int:
        from math import isqrt
        from collections import defaultdict
        MOD = 10**9 + 7
        N = len(A)
        MAGIC = isqrt(N) + 1
        events = defaultdict(lambda: [1] * N)
        for l, r, k, v in queries:
            if k <= MAGIC:
                events[k][l] = events[k][l] * v % MOD
                r2 = r + ((l - r) % k or k)
                if r2 < N:
                    events[k][r2] = events[k][r2] * pow(v, MOD - 2, MOD) % MOD
            else:
                for i in range(l, r + 1, k):
                    A[i] = A[i] * v % MOD
        for k, row in events.items():
            for i in range(k):
                cur = 1
                for j in range(i, N, k):
                    cur = cur * row[j] % MOD
                    A[j] = A[j] * cur % MOD
        return functools.reduce(lambda x, y: x ^ y, A, 0)
```

#### C++ (Advanced Implementation)

```cpp
class Solution {
private:
    static constexpr long long MOD = 1000000007LL;
    long long modPow(long long base, long long exp, long long mod = MOD) {
        long long result = 1;
        while (exp > 0) {
            if (exp % 2 == 1) result = (result * base) % mod;
            base = (base * base) % mod;
            exp /= 2;
        }
        return result;
    }
    long long modInverse(long long a) {
        return modPow(a, MOD - 2);
    }
public:
    int xorAfterQueries(vector<int>& nums, vector<vector<int>>& queries) {
        int n = nums.size();
        int threshold = sqrt(n) + 1;
        vector<long long> arr(n);
        for (int i = 0; i < n; i++) arr[i] = nums[i];
        map<pair<int, int>, vector<vector<int>>> groupedQueries;
        for (auto& query : queries) {
            int l = query[0], r = query[1], k = query[2], v = query[3];
            if (k > threshold) {
                for (int i = l; i <= r; i += k) {
                    arr[i] = (arr[i] * v) % MOD;
                }
            } else {
                groupedQueries[{k, l % k}].push_back(query);
            }
        }
        for (auto& [key, queryGroup] : groupedQueries) {
            int k = key.first;
            int offset = key.second;
            vector<long long> lazy(n, 1);
            for (auto& query : queryGroup) {
                int l = query[0], r = query[1], v = query[3];
                lazy[l] = (lazy[l] * v) % MOD;
                int nextPos = l + ((r - l) / k + 1) * k;
                if (nextPos < n) {
                    lazy[nextPos] = (lazy[nextPos] * modInverse(v)) % MOD;
                }
            }
            long long mult = 1;
            for (int i = offset; i < n; i += k) {
                mult = (mult * lazy[i]) % MOD;
                arr[i] = (arr[i] * mult) % MOD;
            }
        }
        long long result = 0;
        for (long long x : arr) result ^= x;
        return (int)result;
    }
};
```

**Time Complexity:** `O(q√n + n)`  
**Space Complexity:** `O(n + q)`

---

## Key Takeaways

- **Problem 1:** Use prefix sums for efficient range calculations.
- **Problem 2:** Direct simulation works for smaller constraints.
- **Problem 3:** DP with remainder tracking for divisibility problems.
- **Problem 4:** Square root decomposition for handling different query sizes efficiently.

Each problem demonstrates different algorithmic techniques essential for competitive programming!

---

## Links

- [Problem 1: Best Time to Buy and Sell Stock using Strategy](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-using-strategy/description/)
- [Problem 2: XOR After Range Multiplication Queries I](https://leetcode.com/problems/xor-after-range-multiplication-queries-i/description/)
- [Problem 3: Minimum Sum After Divisible Sum Deletions](https://leetcode.com/problems/minimum-sum-after-divisible-sum-deletions/description/)
- [Problem 4: XOR After Range Multiplication Queries II](https://leetcode.com/problems/xor-after-range-multiplication-queries-ii/description/)
