# codewars
___________________________________

``` java
class Solution{
    public static String[] capitalize(String s){
      String [] capsAlt = new String[2];
      char [] temp = new char[s.length()];
      
      temp = buildTemp(s);
      
      for (int i = 0; i < temp.length; i+=2){
        temp[i] = Character.toUpperCase(temp[i]);
      }
      
      capsAlt[0] = String.valueOf(temp);
      
      temp = buildTemp(s);
      
      for(int i = 1; i < temp.length; i+=2){
        temp[i] = Character.toUpperCase(temp[i]);
      }
      
      capsAlt[1] = String.valueOf(temp);
      
        return capsAlt;
    }
  
    public static char[] buildTemp (String s){
      char [] temp = new char[s.length()];
      
      for (int i = 0; i < s.length(); i++){
        temp[i] = s.charAt(i);
      }
      return temp;
    }
}
```

______________________________________
# Leet Code
______________________________________

``` java
class Solution {
    public String reverseWords(String s) {
        //used as a counter in later for loop
        int c = 0;
        String retString = "";
        
        String[] arrString = s.split(" "); 
        String[] reverse = new String[arrString.length];
        
        for (int i = arrString.length - 1; i >= 0; i--){
            reverse[c] = arrString[i];
            c++;
        }
        
        for (int i = 0; i < reverse.length; i++){
            if(!reverse[i].equals(" ") && !reverse[i].equals("")){
                retString = retString + reverse[i];
                if (i != reverse.length - 1){
                    retString = retString + " ";
                }
            }
        }
        
        return retString;
        
    }
}
```

_______________________________
# Two Sum
_______________________________

``` java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap <Integer, Integer> allNums = new HashMap<>();
        int x;
        int [] result = new int[2];
        
        for(int i = 0; i < nums.length; i++){
            allNums.put(i, nums[i]);
        }
        
        for(int i = 0; i < nums.length; i++){
            x = target - allNums.get(i);
            if (allNums.containsValue(x)){
                result[0] = i;
                for(int j = 0; j < nums.length; j++){
                    if (nums[j] == x && j != i){
                        result[1] = j;
                        return result;
                    }
                }
            }
        }
        return result;
    }
}
```

______________
# top k
______________

I was unfortunately unable to get this code working. The intent was to create a hashmap, which had words as keys and the number of occurences as the values. I then tried to sort the array by most commonly used words with a recursive sorting method. However, I was getting a null pointer exception and was unable to figure out to do next.

``` java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        HashMap<String, Integer> kCount = new HashMap<>();
        String temp;
        
        for(int i = 0; i < words.length; i++){
            if(!kCount.containsKey(words[i])){
                kCount.put(words[i], 1);
            }else{
                kCount.replace(words[i], (kCount.get(words[i])+1));
            }
        }
        
        String [] result = kCount.keySet().toArray(new String[0]);
        sort(result, kCount);
        
        ArrayList <String> list = new ArrayList<>();
        
        for(int i = 0; i < k; i++){
            list.add(result[i]);
        }
        
        return list;
        
    }
    
    public static String[] sort(String[] s, HashMap<String, Integer> m ){
        String temp;
        for(int i = 1; i < s.length; i++){
            if(m.get(i-1) > m.get(i)){
                temp = s[i-1];
                s[i-1] = s[i];
                s[i] = temp;
            }
        }
        for(int i = 1; i < s.length; i++){
            if (m.get(i-1) > m.get(i)){
                s = sort(s, m);
            }
        }
        return s;
    }
}
```
______________________
# second attempt at top K
______________________

``` java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        ArrayList <String> result = new ArrayList<>();
		HashMap<String, Integer> kCount = new HashMap<>();

		
		
		for(int i = 0; i < words.length; i++) {
			if(!kCount.containsKey(words[i])){
                kCount.put(words[i], 1);
            }else{
                kCount.replace(words[i], (kCount.get(words[i])+1));
            }
		}
		
		for(Map.Entry<String, Integer> val : kCount.entrySet()) {
			result.add(val.getKey());
		}
		
		result = sort(result, kCount);
		
		for(int i = k-1; i < result.size(); i++) {
			result.remove(i);
		}
			
		return result;
	}
	
	public static ArrayList<String> sort(ArrayList<String> result, HashMap<String, Integer> kCount){
		int low, high;
		String temp;
		
		
		for(int i = 1; i < result.size(); i++) {
			high = kCount.get(result.get(i-1));
			low = kCount.get(result.get(i));
			
			if(low > high) {
				temp = result.get(i-1);
				result.set(i-1, result.get(i));
				result.set(i, temp);
			}
		}
		
		for(int i = 1; i < result.size(); i++) {
			high = kCount.get(result.get(i-1));
			low = kCount.get(result.get(i));
			
			if(low > high) {
				result = sort(result, kCount);
			}
		}
		
		return result;
		
	}
}
```
