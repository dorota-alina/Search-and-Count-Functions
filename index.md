# findNeedles API

## API description

`findNeedles` method counts and logs how many times particular `needles` (words) occur within a `haystack` (plaintext file) unless there are more than five `needles` with the `needles` array, in which case the method exits with an error message.
 
## Sequence of operations

1. `findNeedles` checks if the size of the `needles` array is greater than five.

   ***Result***
   * If greater than five, it output an error message and exites.
   * If smaller or equal five, it proceeeds to step 2.

2. `findNeedles` uses the `split` function to divide the input string using the following literals: `"`, `'`, `t`, `n`, `b`, `f`, `r`. The `haystack` string is split into words, which consttute the `words` array.
3. `findNeedles` compares each element of the `needles` array to each element of the `words`array.
4. If a `needle` occurs within the `words` array, the count for this `needle` gets launched.
5. With the search and all the counts completed, `findNeedles` outputs a list of matched `needles` with their occurence count results.
6. Function exists.

## Calling the method

```java
public static void findNeedles(String haystack, String[] needles) {
   if (needles.length > 5) {
       System.err.println("Too many words!");
   } else {
       int[] countArray = new int[needles.length];
       for (int i = 0; i < needles.length; i++) {
           String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0);
           for (int j = 0; j < words.length; j++) {
               if (words[j].compareTo(needles[i]) == 0) {
                    countArray[i]++;
                }
            }
        }
        for (int j = 0; j < needles.length; j++) {
            System.out.println(needles[j] + ": " + countArray[j]);
        }
    }
}
```

## Parameters

## Response

Method can return an output
Current code logs output in the console, alternatively an array containing the list of outputs can be returned.




