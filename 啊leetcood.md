## golang LeetCode两数之和

### 一、题目

给定一个整数数组 `nums` 和一个整数目标值 `target`，请你在该数组中找出 **和为目标值** *`target`* 的那 **两个** 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。

 

**示例 1：**

```
输入：nums = [2,7,11,15], target = 9
输出：[0,1]
解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。
```

**示例 2：**

```
输入：nums = [3,2,4], target = 6
输出：[1,2]
```

**示例 3：**

```
输入：nums = [3,3], target = 6
输出：[0,1]
```

 

**提示：**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **只会存在一个有效答案**

**进阶：**你可以想出一个时间复杂度小于 `O(n2)` 的算法吗？

### 二、题解

#### 1.遍历求解

```go
package main

import (
	"fmt"
)


func main() {

	// 1.两数之和
	nums := make([]int, 0)
	nums = append(nums, 2)
	nums = append(nums, 7)
	nums = append(nums, 11)
	nums = append(nums, 15)
    
	// nums = append(nums, 3)
	// nums = append(nums, 2)
	// nums = append(nums, 4)
    
	// nums = append(nums, 3)
	// nums = append(nums, 3)
	fmt.Println("nums", nums)
	target := 9
	fmt.Println("twoSum2(nums, target)", twoSum2(nums, target))

}

// 遍历求解
func twoSum(nums []int, target int) []int {
	rst := make([]int, 0)
	for i := 0; i < len(nums)-1; i++ {
		for j := i + 1; j < len(nums); j++ {
			if nums[i]+nums[j] == target {
				fmt.Printf("[%d,%d]", i, i+1)
				rst = append(rst, i)
				rst = append(rst, j)
				break
			}
		}
	}
	return rst
}
```



#### 2哈希表

```go
package main

import (
	"fmt"
)


func main() {

	// 1.两数之和
	nums := make([]int, 0)
	nums = append(nums, 2)
	nums = append(nums, 7)
	nums = append(nums, 11)
	nums = append(nums, 15)
    
	// nums = append(nums, 3)
	// nums = append(nums, 2)
	// nums = append(nums, 4)
    
	// nums = append(nums, 3)
	// nums = append(nums, 3)
	fmt.Println("nums", nums)
	target := 9
	fmt.Println("twoSum2(nums, target)", twoSum2(nums, target))

}
// 哈希表
func twoSum2(nums []int, target int) []int {
	hashTable := map[int]int{}
	for i, x := range nums {
		fmt.Printf("i%d,x%d\n", i, x)
		// 6-3
		fmt.Println("||| hashTable", hashTable)

		if p, ok := hashTable[target-x]; ok {
			fmt.Println("|||22 hashTable", hashTable)

			fmt.Println("~~~~ hashTable[target-x]", hashTable[target-x])
			fmt.Printf("p%d,ok%v\n", p, ok)

			return []int{p, i}
		}
		hashTable[x] = i
		fmt.Printf("**** hashTable[x]%d,x%v\n", hashTable[x], hashTable)
		fmt.Println("|||33 hashTable", hashTable)

	}
	return nil

}

/*
		输出结果：
		nums [2 7 11 15]
	i0,x2
	||| hashTable map[]
	**** hashTable[x]0,xmap[2:0]
	|||33 hashTable map[2:0]
	i1,x7----------------------------hashTable[target-x]，9-7=2
	||| hashTable map[2:0]
	|||22 hashTable map[2:0]
	~~~~ hashTable[target-x] 0
	p0,oktrue
	twoSum2(nums, target) [0 1]
*/
```



























