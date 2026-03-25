
## 1. Subarray with sum as 0

^0c0b86

```
Given an array of integers **A**, find and return whether the given array contains a **non-empty** subarray with a sum equal to 0.

If the given array contains a sub-array with sum zero return 1, else return 0.


**Problem Constraints**  

1 <= |A| <= 100000

-10^9 <= A[i] <= 10^9



**Example Input**  

Input 1:  A = [1, 2, 3, 4, 5] ; Output 1:  0

Input 2: A = [4, -1, 1] ; Output 2: 1

Input 3: A = [4, -1, -2, -1] ; Output 3: 1

Input 4: A = [2, 2, 1, -3, 4, 3, 1, -2, -3, 2] ; Output 3: 1
result: 2, 1, -3


```

### Brute
1. Find out all the subarray combination and see if any of them sum is 0 
	1. T.C: O(N^2), Space: O(1)
		```
		for( i = 0; i < n; i++)
			sum = [i] 
			if(sum == 0) => return 1
			for(j = i+1; j < n; j++)
				sum += j
				if(sum == 0) => return 1
		```

### Optimise
1. If I can avoid computing the j loop somehow I can make it O(n)
2. with the j loop I am doing computation right and if I reduce it I can remove O(n) 
	1. to store the sum best way prefix array 
	```
	A =   [2, 2, 1, -3, 4, 3, 1, -2, -3, 2]
	pre = [2, 4, 5, 2,  6, 9, 10, 8,  5, 7]
	
	now ans came due to 2, 1, -3
	                    |  |  |
	which was due to 2, 4, 5, 2
	```
1. now in prefix whenever you see 0 or if there an element that already came that resulted to 0
2. now to check if already check part requires loop which we can avoid using hashset 
3. edge case is considering about the  problem constraint 
	```java
	
	public int solve(int[] A) {
		int n = A.length;
		Long[] prefixArr = new Long[n];
		Set<Long> set = new HashSet<Long>();

		for(int i = 0; i < n; i++){
			int num = A[i];
			prefixArr[i] = i == 0 ? num : num + prefixArr[i -1];
			
			if(prefixArr[i] == 0 || set.contains(prefixArr[i])){
				return 1;
			}
			set.add(prefixArr[i]);
		}
		return 0;

	}
	```
4. prefixArr had to be a long because A : 10^ 9 and n is 10^4 so max prefix might have to hold is 10^13


## 2. Subarray sum equals to k
```
Given an array of integers **A** and an integer **B**.  
Find the total number of subarrays having sum equals to **B**.



**Problem Constraints**  

 1 <= length of the array <= 50000  
-1000 <= A[i] <= 1000


input: [100, 200, 1,5,3,2,4] ans: 5
1,2,3,4,5
```

