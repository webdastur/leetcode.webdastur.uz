---
hide:
    - toc
description: LeetCode 1480 - Running Sum of 1d Array Javobi
---

<iframe width="100%" height="450em" src="https://www.youtube.com/embed/eMJN_kgKYBw" title="LeetCode 1480 - masala. Running Sum of 1d Array Javobi" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## :memo: **MASALA SHARTI:** [LINK](https://leetcode.com/problems/running-sum-of-1d-array/)

:flag_gb: **Inglizcha**: Given an array `nums`. We define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`.

Return the running sum of `nums`.

:flag_uz: **O'zbekcha**: `nums` array berilgan. Biz `nums` array yig'indisini quyidagicha hisoblab `runningSum[i] = sum(nums[0]…nums[i])`.

`nums` ning yig'indisi qaytarilsin.

## :green_circle: **Misol 1**

<div class="termy">

```console
$ Input: nums = [1,2,3,4]
$ Output: [1,3,6,10]
$ Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].
```

</div>

## :green_circle: **Misol 2**

<div class="termy">

```console
$ Input: nums = [1,1,1,1,1]
$ Output: [1,2,3,4,5]
$ Explanation: Running sum is obtained as follows: [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1].
```

</div>

## :green_circle: **Misol 3**

<div class="termy">

```console
$ Input: nums = [3,1,2,10,1]
$ Output: [3,4,6,16,17]
```

</div>

## :red_circle: **Cheklovlar**

* `1 <= nums.length <= 1000`
* `-10^6 <= nums[i] <= 10^6`

## :one: **- Yechim**: [LINK](https://github.com/webdastur/leetcode/blob/main/array/easy/leetcode1920_1.py)

Masala shartiga ko'ra `nums[i]` elementi o'zidan oldingi elementlar yig'indisiga tenglab chiqishimiz kerak. Shu sababli `1` dan `n` gacha sikl ochamiz. Sababi `0` dan boshlashimiz shart emas `0` - elementdan oldin boshqa qiymat yo'q va har bir yurishida biz `nums[i] = nums[i] + nums[i - 1]` ga tenglab boramiz. 

Natija sifatida `nums` ni o'zini qaytarib yuboramiz.

:alarm_clock: **Time Complexity**: ==O(n - 1)== <br>
:package: **Space Complexity**: ==O(1)==

```python linenums="1"
# Author: Abdulaminkhon Khaydarov
# Date: 06/11/22 
# Problem URL: https://leetcode.com/problems/running-sum-of-1d-array/

from typing import List


class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        for i in range(1, len(nums)):
            nums[i] = nums[i] + nums[i - 1]
        return nums


if __name__ == '__main__':
    solution = Solution()

    # Example 1
    print(solution.runningSum([1, 2, 3, 4]) == [1, 3, 6, 10])

    # Example 2
    print(solution.runningSum([1, 1, 1, 1, 1]) == [1, 2, 3, 4, 5])

    # Example 3
    print(solution.runningSum([3, 1, 2, 10, 1]) == [3, 4, 6, 16, 17])
```