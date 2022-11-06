---
hide:
    - toc
description: LeetCode 1929 - Concatenation of Array Javobi
---

<iframe width="100%" height="450em" src="https://www.youtube.com/embed/5Reh8MMQY1M" title="LeetCode 1920 - masala. Build Array from Permutation" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## :memo: **MASALA SHARTI:** [LINK](https://leetcode.com/problems/concatenation-of-array/)

:flag_gb: **Inglizcha**: Given an integer array `nums` of length `n`, you want to create an array `ans` of length `2n` where `ans[i] == nums[i]` and `ans[i + n] == nums[i]` for `0 <= i < n` (**0-indexed**).

Specifically, `ans` is the **concatenation** of two `nums` arrays.

Return the array `ans`.

:flag_uz: **O'zbekcha**: `n` uzunlikga ega butun sonli `array` berilgan, siz `ans 2n` uzunlikga ega `array` yaratishingiz kerak qaysiki `ans[i] == nums[i]` va `ans[i + n] == nums[i]` ni qanoatlantirishi kerak `0 <= i < n`.

`ans` bu ikkita `nums` ni birikmasi.

`ans` arrayni natija sifatida qaytaring.

## :green_circle: **Misol 1**

```text
Input: nums = [1,2,1]
Output: [1,2,1,1,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[0],nums[1],nums[2]]
- ans = [1,2,1,1,2,1]
```

## :green_circle: **Misol 2**

```text
Input: nums = [1,3,2,1]
Output: [1,3,2,1,1,3,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[3],nums[0],nums[1],nums[2],nums[3]]
- ans = [1,3,2,1,1,3,2,1]
```

## :red_circle: **Cheklovlar**

* `n == nums.length`
* `1 <= n <= 1000`
* `1 <= nums[i] <= 1000`

## :one: **- Yechim**: [LINK](https://github.com/webdastur/leetcode/blob/main/array/easy/leetcode1929_1.py)

Bizga `nums` ni uzunligi kerak bunga biz `n` o'zgaruvchisini yaratib `nums` ni uzunligini tenglab olamiz va `0` dan `n` gacha sikl ochib `nums` ga `nums[i]` qo'shib boramiz. Oxirida `nums` ni qaytarib yuboramiz.

:alarm_clock: **Time Complexity**: ==O(n)== <br>
:package: **Space Complexity**: ==O(2n)==

```python
# Author: Abdulaminkhon Khaydarov
# Date: 02/11/22 
# Problem URL: https://leetcode.com/problems/concatenation-of-array/

from typing import List


class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        n = len(nums)
        for i in range(n):
            nums.append(nums[i])
        return nums


if __name__ == '__main__':
    solution = Solution()

    # Example 1
    print(solution.getConcatenation([1, 2, 1]) == [1, 2, 1, 1, 2, 1])

    # Example 2
    print(solution.getConcatenation([1, 3, 2, 1]) == [1, 3, 2, 1, 1, 3, 2, 1])
```

## :two: **- Yechim**: [LINK](https://github.com/webdastur/leetcode/blob/main/array/easy/leetcode1929_2.py)

Pythonda `list` ni butun songa ko'paytirsa bo'ladi. Biz bu holatda `nums` ni `2` ga ko'paytirib natija sifatida qaytarib yuborsak bo'ldi.

:alarm_clock: **Time Complexity**: ==O(n)== <br>
:package: **Space Complexity**: ==O(2n)==

```python
# Author: Abdulaminkhon Khaydarov
# Date: 02/11/22 
# Problem URL: https://leetcode.com/problems/concatenation-of-array/

from typing import List


class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        return nums * 2


if __name__ == '__main__':
    solution = Solution()

    # Example 1
    print(solution.getConcatenation([1, 2, 1]) == [1, 2, 1, 1, 2, 1])

    # Example 2
    print(solution.getConcatenation([1, 3, 2, 1]) == [1, 3, 2, 1, 1, 3, 2, 1])
```

## :three: **- Yechim**: [LINK](https://github.com/webdastur/leetcode/blob/main/array/easy/leetcode1929_3.py)

Pythonda `list` ni `list` ga qo'shsa bo'ladi. `nums + nums` ham bizga bir xil natija beradi.

:alarm_clock: **Time Complexity**: ==O(n)== <br>
:package: **Space Complexity**: ==O(2n)==

```python
# Author: Abdulaminkhon Khaydarov
# Date: 02/11/22 
# Problem URL: https://leetcode.com/problems/concatenation-of-array/

from typing import List


class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        return nums + nums


if __name__ == '__main__':
    solution = Solution()

    # Example 1
    print(solution.getConcatenation([1, 2, 1]) == [1, 2, 1, 1, 2, 1])

    # Example 2
    print(solution.getConcatenation([1, 3, 2, 1]) == [1, 3, 2, 1, 1, 3, 2, 1])
```