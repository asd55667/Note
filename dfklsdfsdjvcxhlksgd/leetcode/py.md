#### 1.Two Sum 
>Brute Force
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        idxs = []
        for i in range(len(nums)):
            for j in range(len(nums)-i-1):
                if nums[i] + nums[i+j+1] == target:
                    idxs.append((i, i+j+1))
        return list(idxs[0])
```
>One-pass Hash Table    
```        
    def twoSum(self, nums, target):
        dic = {}
        for i, n in enumerate(nums): 
            if n in dic:
                return [dic[n], i]
            #给元素的匹配数创立键值, 当出现目标时返回双方索引    
            dic[target-n] = i  
```
# 2.Add Two Numbers
```
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

    def addTwoNumbers(self, l1, l2):
        dummy = cur = ListNode(0)  
        carry = 0
        while l1 or l2 or carry:
            if l1:
                carry += l1.val
                l1 = l1.next
            if l2:
                carry += l2.val
                l2 = l2.next
            cur.next = ListNode(carry%10)
            cur = cur.next 
            # 进位 0或1, 参与下一个位数的运算
            carry //= 10   
        return dummy.next #dummy与cur地址相同
```

# 3.Longest Substring Without Repeating Characters
```
    def lengthOfLongestSubstring(self, s):
        start = maxLength = 0
        usedChar = {}        
        for i in range(len(s)):
            # 字符重复且键值未重置时, 重置键值
            if s[i] in usedChar and start <= usedChar[s[i]]: 
                start = usedChar[s[i]] + 1
            else:
                maxLength = max(maxLength, i - start + 1)
            usedChar[s[i]] = i
        return maxLength
```

