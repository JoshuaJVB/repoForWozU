# Parity Outlier  

Codewars posed a challenge to create a method which can read through an array of integers. This array will contain all even or odd numbers with the exception of one instance.

We need to code to do three things here:  

1. Determine if numbers in the array are even or odd
2. Remember which number in the list is the outlier
3. Return that number.  

_______________________________________________________

# The Code  

I was able to both deterimine if the number was even and keep track of placement in the same block
``` java
for(int i = 0; i < integers.length; i++) {
				temp = integers[i] % 2;
				if(temp == 0) {
					evenCount++;
					eHolder = i;
				}else {
					oddCount++;
					oHolder = i;
				}
			}
```
In this loop, we determine if the input is even via a modulus of 2, We then will either add a count to evenCount or oddCount and save our current i in eHolder or oHolder. We then use the holder associated with whichever count will be less (as it will be 1 vs many) and return that value.  

``` java
if (evenCount < oddCount) {
				return integers[eHolder];
			} else {
				return integers[oHolder];
			}
```

For full code, please refer to my Parity Outlier Repo.
