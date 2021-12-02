# findNeedles API

## API description

`findNeedles` method counts and logs how many times particular `needles` (words) occur within a `haystack` (plaintext file) unless there are more than five `needles` with the `needles` array, in which case the method exits with an error message.
 
## Sequence of operations

1. `findNeedles` checks if the size of the `needles` array is greater than five.

   ***Result***
   * If greater than five, it output an error message and exites.
   * If smaller or equal five, it proceeeds to step 2.

2. `findNeedles` uses the `split` function to divide the input string using the following literals: `"`, `'`, `t`, `n`, `b`, `f`, `r`. The `haystack` string is split into words, which constitute the `words` array.
3. `findNeedles` compares each element of the `needles` array to each element of the `words`array.
4. If a `needle` occurs within the `words` array, the count for this `needle` is launched.
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

There are two input parameters for this method.

|Input parameter|Data type|Description|
|---|---|---|
|heystack|String|Plain text possibly including the following literals: `"`, `'`, `t`, `n`, `b`, `f`, `r`|
|needles| String array| Set of words|

#### Sample input

```java
String[] needles = {"hello", "there", "mac", "one", "123"};
String haystack = "hello there hello! There is an apple macbook";
findNeedles(haystack, needles);
```

## Response

The function logs output in the console: either the error message or a list of words with numbers reflecting how many times they occur in the input text.

### Sample output

#### If needles length is less than or equal to five

```bash
needles[0]: number of occurrences
needles[1]: number of occurrences
needles[2]: number of occurrences
needles[3]: number of occurrences
needles[4]: number of occurrences
```

#### If needles length is greater five

```bash
Too many words!
```




