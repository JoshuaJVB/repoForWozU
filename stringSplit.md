#code solution for converting a string to an array of strings

______________________________________  

The assignment asked that we take a string and split it up by words. For instance "this string is short" should appear as an array containing "this" "string" "is" and "short"

In this case, we chose to use the String classes split method to split by empty spaces with "\\\\s+"

``` java
public class Solution {

    public static String[] stringToArray(String s) {
      String[] splited = s.split("\\s+");
      return splited;
    }
}


