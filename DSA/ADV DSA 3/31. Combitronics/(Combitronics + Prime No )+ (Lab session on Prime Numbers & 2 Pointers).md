
# 1.  Combitronics
## Math
```

Permutation => selection + arrangement (in how many ways it can be arranged)

nPr =        n! 
         ---------
	      (n - r)!
	      
	How many arragments of r items from n can exist    


Combination => selection + ( arrangement/order does not matters)
nCr =        n! 
         ---------
	      r! (n - r)!
	      
	   
How many ways can I choose `r` items from `n`, where order doesn't matter?


3P1 => $^3P_1$

3C1 => $^3C_1$


```


==Permutation = r! * Combination==
### When to Use Which: The Decisive Question

Ask yourself one question: =="If I swap/change order two of my **chosen/selected** items, is it a different outcome?"==

- ==**Yes, it's different**)== → Permutation (order matters)
- ==**No, it's the same**== → Combination (order doesn't matter)   

### The Mental Model

Think of every counting problem in two stages:

1. **Selection** — which items am I taking?
2. **Arrangement** — in what order am I placing them?

Combinations stop at step 1. Permutations do both. The factorial `r!` in the combination formula's denominator is literally you saying "I don't care about step 2, divide it out."



---
### Q. You have a coin and 3 attempts how many combination can be made out of it

#### Brute 
What are the possible combination => helps determine the unit 

	0 tails
HHH 
	1 tails
HHT
HTH
THH
	2 tails
TTH
HTT
	3 tails
TTT

#### Optimised


$^3C_1$ *  $^3C_1$  *  $^3C_1$
-------
after selecting
==in THH if swap first 2 => THH will it become a different option => Yes => so Permutation==

3 P 3 => 3! / (3! - 3!) ==> 3! => 6



### Q. Given you have 10  girls and 10 boys, in how many ways we can pair them? 

**Ans:**  
**Step1 Selection**  10 C 1 and 10 C 1
**Step 2 Swap test** => a pair {boy, girl} has no internal order (the pair {Alice, Bob} is the same as {Bob, Alice}), so within the pair, no permutation. 
But choosing _which_ boy and _which_ girl is two independent selections
that is pairing {Alice, Bob}  is different to {Carol, Bob} this is ==not different arrangement this is different selection== so, each a C(10,1).

==So when you run the swap test, you must hold the selection _fixed_ and only ask about reordering. If you change who's in the selection, you've left the swap test and entered the territory of "different selections give different answers" — which is true for both combinations and permutations and tells you nothing.==



### Q. given 3 choices A,B,C how many different combination can exist?

**Ans:** 
	Step 1: Selection
		3C1  *  2C1  * 1C1
		
		Step 2: Swap test => so from ACB if i swap B with C to => ABC will it be a diff ans yes so Permutation


so ans =====> ==3P3==


# 2. Prime no

## What is prime no?
1. No. which are divisible by 1 and itself
2. Total no of factors are 2 
3. e.g 2,3,5,7,11,13,17..............


### GIven a no n check if it is prime or not?
```java
int rootN = Math.sqrt(n);
int noOfFactors = 2; //consdiering no is divisible by itself and by 1

//for (int i = 2; i <= n; i++; i++ ){
	//if(n % i == 0){
		//noOfFactors++;
	//}

//}


//why root(n) becasue till root all the first half exist and if they exist there
//sec half also exist so for e.g 
//n = 10 
//root(10) => 3
// so 2 is divisble by 10 then 5 also exist which is divisible 10
//so if one exist then other also exist
for (int i = 2; i <= rootN; i++; i++ ){
	if(n % i == 0){
		noOfFactors += 2; // we are adding 2 and 5 
	}

}

return noOfFactors == 2;

```


### Q. Given a number n find all the prime number under that

#### Brute Force
```
int k = 0;
for (i = 2; i <= n; i++)
	if checkPrime(i) => true
		ans[k] = i;
		
		
		
T.C
loop => O(n)
checkPrime => sqrt(n)

T.C => n * sqrt(n)

	
```


### Optimised
#### Sieve of Eratosthenes 

Logic is: don't call checkPrime on all the numbers but on the factors of the primeNumbers

```
for i = 2; i <= n; i++

	// it is prime till now
	if(checker[i] == 1){
			//at i = 3 j = 9, 12, 15....etc
		for(int j = i * i ; j < n; j += i)
			
			
	}
```
##### Dry Run

Step 1. for  i = 1; i <= n; i++

Step 2.  i == 1 not prime mark it and move forward

Step 3.  i == 2 it is prime  so start checking it's factors
j = ~~2* 1~~ , 2 * 2, 2 * 3.............   2 * 25 (50)
=> 2* 1 is not needed becasuse you already check 2 before it's factors

| 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| no  | yes |     | no  |     | no  |     | no  |     | no  |
| 11  | 12  | 13  | 14  | 15  | 16  | 17  | 18  | 19  | 20  |
|     | no  |     | no  |     | no  |     | no  |     | no  |
| 21  | 22  | 23  | 24  | 25  | 26  | 27  | 28  | 29  | 30  |
|     | no  |     | no  |     | no  |     | no  |     | no  |
| 31  | 32  | 33  | 34  | 35  | 36  | 37  | 38  | 39  | 40  |
|     | no  |     | no  |     | no  |     | no  |     | no  |
| 41  | 42  | 43  | 44  | 45  | 46  | 47  | 48  | 49  | 50  |
|     | no  |     | no  |     | no  |     | no  |     | no  |


Step 4.  i == 3 it is prime  so start checking it's factors if they are 
j = ~~3* 1 , 3 * 2~~, 3 * 3.............   3 * 16 (48)
=> 3 * 2 is not needed becasue you have already checked above 

| 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| no  | yes | no  | no  |     | no  |     | no  | no  | no  |
| 11  | 12  | 13  | 14  | 15  | 16  | 17  | 18  | 19  | 20  |
|     | no  |     | no  | no  | no  |     | no  |     | no  |
| 21  | 22  | 23  | 24  | 25  | 26  | 27  | 28  | 29  | 30  |
|     | no  |     | no  |     | no  | no  | no  |     | no  |
| 31  | 32  | 33  | 34  | 35  | 36  | 37  | 38  | 39  | 40  |
|     | no  | no  | no  |     | no  |     | no  |     | no  |
| 41  | 42  | 43  | 44  | 45  | 46  | 47  | 48  | 49  | 50  |
|     | no  |     | no  |     | no  |     | no  |     | no  |

Step 5.  i == 4 it is not a prime so skip

Step 6.  i == 5 it is a prime 

5 * 1  to 5 * 4  => is checked so start from 5 * 5
25, 30,35,40,45,50

| 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| no  | yes | no  | no  |     | no  |     | no  | no  | no  |
| 11  | 12  | 13  | 14  | 15  | 16  | 17  | 18  | 19  | 20  |
|     | no  |     | no  | no  | no  |     | no  |     | no  |
| 21  | 22  | 23  | 24  | 25  | 26  | 27  | 28  | 29  | 30  |
|     | no  |     | no  | no  | no  | no  | no  |     | no  |
| 31  | 32  | 33  | 34  | 35  | 36  | 37  | 38  | 39  | 40  |
|     | no  | no  | no  | no  | no  |     | no  |     | no  |
| 41  | 42  | 43  | 44  | 45  | 46  | 47  | 48  | 49  | 50  |
|     | no  |     | no  | no  | no  |     | no  |     | no  |

Step 7.  i == 6 it is a not a prime so skip

step 8. i == 7 

| 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| no  | yes | no  | no  |     | no  |     | no  | no  | no  |
| 11  | 12  | 13  | 14  | 15  | 16  | 17  | 18  | 19  | 20  |
|     | no  |     | no  | no  | no  |     | no  |     | no  |
| 21  | 22  | 23  | 24  | 25  | 26  | 27  | 28  | 29  | 30  |
| no  | no  |     | no  | no  | no  | no  | no  |     | no  |
| 31  | 32  | 33  | 34  | 35  | 36  | 37  | 38  | 39  | 40  |
|     | no  | no  | no  | no  | no  |     | no  |     | no  |
| 41  | 42  | 43  | 44  | 45  | 46  | 47  | 48  | 49  | 50  |
|     | no  |     | no  | no  | no  |     | no  | no  | no  |

step 9.  i == 8 => not a prime so skip

step 10. i == 9 => not a prime so skip

step 11. i == 11
....


![[Pasted image 20260430153604.png]]


1. let's say n = 23 then consider the range from 2 to 24 (n+1)
	1. why 2 because 1 is not prime
	2. and why 24 because we want to check if 23 is also prime or not

```java
int lastNum = n+1;

//Step 0. array which stores all the numbers and ones which are prime are marked as true

//Step 1. consider all the values as true
int[] ans = new int[lastNum];

for(int i = 2; i <= lastNum; i++){
	ans[i] = 1; 
}

//Step 2. start from 2 to 7
// Step 2: sieve  
for (int i = 2; i * i <= lastNum; i++) {  
	if (ans[i] == 1 && checkPrime(ans[i])) { 
		//for i check all its factors from i*i because before that 
		//its previous would have checked it already
		//i = 3; 3*3(i*i) => 9 but before that 6 would have been already checked by 2 
		//for those factors mark them as non prime 
		for (int j = i * i; j <= lastNum; j += i) {  
			ans[j] = 0;  
		}  
	}  
}  
  
return ans;

```

```java
 T.C => 
 
 i. timesCalled
 2   4, 6,8,10.....50 => 25
 3.  3 9 12,.......48 => 16
 5   25



```



# Lab session on Prime Numbers & 2 Pointers



### Q. Given N print first n lines of the pascal trianagle

e.g
```
N = 5

0C0
1C0 1C1
2C0 2C1 2C2
3C0 3C1 3C2 3C3
4C0 4C1 4C2 4C3 4C4
5Co 5C1 5C2 5C3 5C4 5C5



```






















### Q  Given a no n return the smallest factor which is prime
e.g
```
n = 15
fac => 3, 5
ans => 3


n = 6
fact => 2, 3
ans => 2

n = 7
fact => 7
ans => 7

```

#### Brute
```

	i = 2; i <= Math.sqrt(n); i++

		if n % i == 0 && i is prime 
			return i
			
return n

T.C
check prime => root(n)
outer loop => root(n)
Total => O(n)

```

#### Optimised

```

```