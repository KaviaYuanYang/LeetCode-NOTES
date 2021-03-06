# 1. Two Sum

## 描述

给定一个整数数组，返回两个数字的索引，使得它们加起来等于一个特定的目标值。

您可以假设每个输入都有一且只有一个答案，数组中每个元素只能使用一次。

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## 解析

用哈希表按照“数值-下标”的关系存储给定数组中的数值，单次查找的时间复杂度为O(1)。

* 时间复杂度：O(n)  
* 空间复杂度：O(n)
* 语言：C++

```C++
class Solution 
{
public:
    vector<int> twoSum(vector<int> &numbers, int target)
    {
        // 使用哈希表存储数组中的数值，key为数组中的数值，value为数组中数值对应下标 
    	unordered_map<int, int> hash;
    	vector<int> result;
    	for (int i = 0; i < numbers.size(); i++) 
    	{
    		int numberToFind = target - numbers[i];
    
            // 查找，若找到，则返回下标
    		if (hash.find(numberToFind) != hash.end()) 
    		{
    			result.push_back(hash[numberToFind]);
    			result.push_back(i);			
    			return result;
    		}
    
            //若没有找到，则将该值加入哈希表
    		hash[numbers[i]] = i;
    	}
    	return result;
    }
};
```

