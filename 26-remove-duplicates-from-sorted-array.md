# [26 Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array)

Given an integer array `nums` sorted in non-decreasing order, remove the duplicates [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) such that each unique element appears only once. The relative order of the elements should be kept the same. Then return *the number of unique elements in *`nums`.

Consider the number of unique elements of `nums` to be `k`, to get accepted, you need to do the following things:

-   Change the array `nums` such that the first `k` elements of `nums` contain the unique elements in the order they were present in `nums` initially. The remaining elements of `nums` are not important as well as the size of `nums`.
-   Return `k`.

Custom Judge:

The judge will test your solution with the following code:

```js
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, then your solution will be accepted.



Example 1:

Input: nums = [1,1,2]  
Output: 2, nums = [1,2,_]  
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).


Example 2:

Input: nums = [0,0,1,1,1,2,2,3,3,4]  
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]  
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).


## Solutions

For this one you can imagine two lines of array where the second line have been starting before the first one like:

```[0,1,2,3,4]```  
```[0,1,2,3,4]```

It happens due `nums[i-1]` so on an input as `[1,1,2]` if you try `console.log(nums[i], nums[i-1])``you can see:

```bash
1 undefined
1 1
2 1
```

#### JavaScript:

```js
var removeDuplicates = function (nums) {
  var count = 0;

  for (var i = 0; i < nums.length; i++) {
    if (nums[i] !== nums[i-1]) {
        nums[count] = nums[i]
        count++
    }
  }
  
  return count
};
```

#### C++:

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int count = 1;

        for(int i = 1; i < nums.size(); i++) {
            if (nums[i] != nums[i-1]) {
                nums[count] = nums[i];
                count++;
            }
        }

        return count;
    }
};
```


#### PHP:

```php
function removeDuplicates(&$nums)
{
    $count = 1;

    for ($i = 1; $i < count($nums); $i++) {
        if ($nums[$i] !== $nums[$i - 1]) {
            $nums[$count] = $nums[$i];

            $count++;
        }
    }

    return $count;
}
```
