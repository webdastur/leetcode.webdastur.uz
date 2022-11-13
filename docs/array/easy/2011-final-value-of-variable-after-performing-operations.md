---
hide:
    - toc
description: LeetCode 2011 - Final Value of Variable After Performing Operations Javobi
---

<iframe width="100%" height="450em" src="https://www.youtube.com/embed/9VH8lRJz8bs" title="LeetCode 2011 - masala. Final Value of Variable After Performing Operations Javobi" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## :memo: **MASALA SHARTI:** [LINK](https://leetcode.com/problems/running-sum-of-1d-array/)

:flag_gb: **Inglizcha**: There is a programming language with only four operations and one variable `X`:

* `++X` and `X++` increments the value of the variable `X` by `1`.
* `--X` and `X--` decrements the value of the variable `X` by `1`.

Initially, the value of `X` is `0`.

Given an array of strings `operations` containing a list of operations, return the final value of `X` after performing all the operations.

:flag_uz: **O'zbekcha**: Bitta dasturlash tili bor 4 ta operatsiya bilan va `X` o'zgaruvchisi bor:

* `++X` va `X++` operatsiyasilari `X` o'zgaruvchini `1` ga oshiradi.
* `--X` va `X--` operatsiyasilari `X` o'zgaruvchini `1` ga kamaytiradi.

`X` ning boshlang'ich qiymati `0`.

Berilgan `operations` array barcha bajarilishi bo'lgan operatsiya(string)larni o'z ichiga olgan. Barcha operatsiyadan so'ng `X` ning yakuniy qiymati qaytarilsin.

## :green_circle: **Misol 1**

<div class="termy">

```console
$ Input: operations = ["--X","X++","X++"]
$ Output: 1
$ Explanation: The operations are performed as follows:
Initially, X = 0.
--X: X is decremented by 1, X =  0 - 1 = -1.
X++: X is incremented by 1, X = -1 + 1 =  0.
X++: X is incremented by 1, X =  0 + 1 =  1.
```

</div>

## :green_circle: **Misol 2**

<div class="termy">

```console
$ Input: operations = ["++X","++X","X++"]
$ Output: 3
$ Explanation: The operations are performed as follows:
Initially, X = 0.
++X: X is incremented by 1, X = 0 + 1 = 1.
++X: X is incremented by 1, X = 1 + 1 = 2.
X++: X is incremented by 1, X = 2 + 1 = 3.
```

</div>

## :green_circle: **Misol 3**

<div class="termy">

```console
$ Input: operations = ["X++","++X","--X","X--"]
$ Output: 0
$ Explanation: The operations are performed as follows:
Initially, X = 0.
X++: X is incremented by 1, X = 0 + 1 = 1.
++X: X is incremented by 1, X = 1 + 1 = 2.
--X: X is decremented by 1, X = 2 - 1 = 1.
X--: X is decremented by 1, X = 1 - 1 = 0.
```

</div>

## :red_circle: **Cheklovlar**

* `1 <= operations.length <= 100`
* `operations[i]` will be either `"++X"`, `"X++"`, `"--X"`, or `"X--"`.

## :one: **- Yechim**: [LINK](https://github.com/webdastur/leetcode/blob/main/array/easy/leetcode2011_1.py)

Bitta `x` o'zgaruvchisini ochib olamiz va operations ni har bitta elementi `"++"` yoki `"--"` o'z ichiga olishini tekshirib shu bo'yicha kerakli amallarni bajaramiz.

:alarm_clock: **Time Complexity**: ==O(n)== <br>
:package: **Space Complexity**: ==O(1)==

```python linenums="1"
# Author: Abdulaminkhon Khaydarov
# Date: 06/11/22 
# Problem URL: https://leetcode.com/problems/final-value-of-variable-after-performing-operations/

from typing import List


class Solution:
    def finalValueAfterOperations(self, operations: List[str]) -> int:
        x = 0

        for operation in operations:
            if "++" in operation:
                x += 1
            else:
                x -= 1

        return x


if __name__ == '__main__':
    solution = Solution()

    # Example 1
    print(solution.finalValueAfterOperations(["--X", "X++", "X++"]) == 1)

    # Example 2
    print(solution.finalValueAfterOperations(["++X", "++X", "X++"]) == 3)

    # Example 3
    print(solution.finalValueAfterOperations(["X++", "++X", "--X", "X--"]) == 0)
```