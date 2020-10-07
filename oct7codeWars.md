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

