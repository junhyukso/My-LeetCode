# Two Sum  

배열 Nums를 인풋으로 받아, 배열의 원소 두개를 골랐을때 그 합이 Target이 되는 원소의 인덱스를 찾는 문제이다.

## Naive Solution(Brute Force)
간단하게 이를 해결하는 방법은, 길이가 2인 모든 부분집합을 조사하는 것이다.
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)-1):
            for j in range(i+1,len(nums)):
                if nums[i] + nums[j] == target : 
                    return [i,j]
```

이는 배열을 이중루프로 순회하므로, O(N^2)의 시간복잡도를 가진다.
별도의 Memory를 사용하지 않으므로, 공간복잡도는 O(1)이다.

- Time Complexity     : O(N^2)
- Storage Complexity  : O(1) 

## Better Solution
이를 O(N)시간에 해결할 수 있는 방법이 존재한다.  
우선 Map을 하나 만든다. Map은 Key:nums[i] , Val:i 가 되도록 저장할 것이다.  
배열을 순회하며 Map에서 Target-nums[i]의 Key가 있는지 확인한다. 없다면 Map에 해당 양식대로 값을 저장한다.  
이렇게 구현하게되면 배열을 한번만 훑고도 답을 찾아낼 수 있다.  
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        Map = {}
        for i,n in enumerate(nums):
            if target - n in Map:
                return [Map[target-n],i]
            Map[n] = i
```

- Time Complexity     : O(N)
- Storage Complexity  : O(N)
