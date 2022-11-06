---
hide:
    - toc
description: LeetCode 1920 - Build Array from Permutation Javobi
---

<iframe width="100%" height="450em" src="https://www.youtube.com/embed/fmTZQd9hwBA" title="LeetCode 1920 - masala. Build Array from Permutation" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## :memo: **MASALA SHARTI:** [LINK](https://leetcode.com/problems/build-array-from-permutation/)

:flag_gb: **Inglizcha**: Given a **zero-based permutation** `nums` (**0-indexed**), build an array `ans` of the **same length** where `!# ans[i] = nums[nums[i]]` for each `0 <= i < nums.length` and return it.

A **zero-based permutation** `nums` is an array of **distinct** integers from `0` to `nums.length - 1` (**inclusive**).

:flag_uz: **O'zbekcha**: Nolga asoslangan ya'ni index `0` dan boshlanuvchi `nums` permutatsiya berilgan. Shu bilan bir xil uzunlikda `ans` array yaratib `0 <= i < nums.length` oraliqda `ans[i] = nums[nums[i]]` tenglab natijani qaytarish kerak ekan.

## :green_circle: **Misol 1**

<div class="termy">

```console
$ Input: nums = [0,2,1,5,3,4]
$ Output: [0,1,2,4,5,3]
$ Explanation: The array ans is built as follows: 
ans = [nums[nums[0]], nums[nums[1]], nums[nums[2]], nums[nums[3]], nums[nums[4]], nums[nums[5]]]
    = [nums[0], nums[2], nums[1], nums[5], nums[3], nums[4]]
    = [0,1,2,4,5,3]
```

</div>

## :green_circle: **Misol 2**

<div class="termy">

```console
$ Input: nums = [5,0,1,2,3,4]
$ Output: [4,5,0,1,2,3]
$ Explanation: The array ans is built as follows:
ans = [nums[nums[0]], nums[nums[1]], nums[nums[2]], nums[nums[3]], nums[nums[4]], nums[nums[5]]]
    = [nums[5], nums[0], nums[1], nums[2], nums[3], nums[4]]
    = [4,5,0,1,2,3]
```

</div>

## :red_circle: **Cheklovlar**

- `1 <= nums.length <= 1000`
- `0 <= nums[i] < nums.length`
- The elements in `nums` are **distinct**.

## :one: **- Yechim**: [LINK](https://github.com/webdastur/leetcode/blob/main/array/easy/leetcode1920_1.py)

Agar yangi array yaratmay to'g'ridan to'g'ri `nums[i] = nums[nums[i]]` ga tenglab qo'ysak bizda `nums[i]` ni o'zida turgan qiymat yo'qolib qoladi shu sababli `ans` list yaratib olamiz. ans uzunligi(length) `nums` uzunligi bilan teng bo'lgani sababli yaratish davrida boshlang'ich `0` qiymat berib chiqamiz keyin sikl yaratib ushbu siklda `ans[i] = nums[nums[i]]` ga tenglab olamiz va `ans` ni natija sifatida qaytarib yuboramiz.

:alarm_clock: **Time Complexity**: ==O(n)== <br>
:package: **Space Complexity**: ==O(n)==

```python linenums="1"
# Author: Abdulaminkhon Khaydarov
# Date: 30/10/22 
# Problem URL: https://leetcode.com/problems/build-array-from-permutation/

from typing import List


class Solution:
    def buildArray(self, nums: List[int]) -> List[int]:
        # "nums" ni uzunligi bilan teng "ans" listini yaratib olamiz
        ans: List[int] = [0 for _ in nums]

        # "0" dan "nums" uzunligigacha sikl yaratib "ans[i]" ni "nums[nums[i]]" ga tenglab chiqamiz.
        for i in range(len(nums)):
            ans[i] = nums[nums[i]]

        return ans


if __name__ == '__main__':
    solution = Solution()

    # Example 1
    print(solution.buildArray([0, 2, 1, 5, 3, 4]) == [0, 1, 2, 4, 5, 3])

    # Example 2
    print(solution.buildArray([5, 0, 1, 2, 3, 4]) == [4, 5, 0, 1, 2, 3])
```

## :two: **- Yechim**: [LINK](https://github.com/webdastur/leetcode/blob/main/array/easy/leetcode1920_2.py)

Birinchi yechimda biz qo'shimcha `array` dan foydalandik. Buni qo'shimcha `array` ishlatmay ishlash usuli mavjud biz bunda xotiradan constant joy ishlatamiz. `nums` ni uzunligini `n` ga tenglab olamiz keyin `0` dan `n` gacha sikl ochamiz bunda har bir sikl bosqichida biz `nums[i]` ni `num` ga tenglab turamiz. Agar biz `nums[num]` ni `n` ga bo'lib qoldiqni olsak bizda hozirgi `nums[i]` teng bo'ladigan qiymat kelib chiqadi va buni biz `b` o'zgaruvchisiga saqlab turamizda `nums[i]` da turgan qiymatga  `n * b + num` shuni tenglab qo'yamiz. Bizga yana bitta sikl kerak bo'ladi, bu ham `0` dan `n` gacha bo'ladi. Biz `nums[i]` ni `n` ga bo'lib butun qismini olsak bizga avvalroq saqlab qo'ygan qiymatimizni qaytaradi va buni `nums[i]` ga tenglab qo'yamiz.

:alarm_clock: **Time Complexity**: ==O(n)== <br>
:package: **Space Complexity**: ==O(1)==

```python linenums="1"
# Author: Abdulaminkhon Khaydarov
# Date: 30/10/22 
# Problem URL: https://leetcode.com/problems/build-array-from-permutation/

from typing import List


class Solution:
    def buildArray(self, nums: List[int]) -> List[int]:
        # nums ni uzunligini n ga tenglab olamiz.
        n = len(nums)

        for i in range(len(nums)):
            # "nums[i]" elementini vaqtincha "num" ga olib turamiz
            num = nums[i]

            # "nums[num]" elementini "n" ga bo'lib qoldiqni "b" ga tenglab turamiz.
            b = nums[num] % n

            # "nums[i]" ga "n * b + num" ni tenglab olamiz.
            nums[i] = n * b + num

        for i in range(len(nums)):
            # "nums[i]" ni "nums[i]" ni "n" ga bo'lib butun qismiga tenglab olamiz.
            nums[i] = nums[i] // n

        return nums


if __name__ == '__main__':
    solution = Solution()

    # Example 1
    print(solution.buildArray([0, 2, 1, 5, 3, 4]) == [0, 1, 2, 4, 5, 3])

    # Example 2
    print(solution.buildArray([5, 0, 1, 2, 3, 4]) == [4, 5, 0, 1, 2, 3])
```