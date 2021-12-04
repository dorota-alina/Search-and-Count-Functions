# findNeedles API

Gets the number of matches for a search query.

CONTENTS

1. [Description](#description)
2. [Request](#request)
3. [Response](#response)
4. [Appendix](#appendix)

## Description

`findNeedles` counts and logs how many times particular `needles` (elements of the `needles` strings array) occur within `haystack` (string). To achieve that, `findNeedles` uses the `split` function dividing the `haystack` string into `words` strings by means of the following literals: `"`, `'`, `t`, `n`, `b`, `f`, `r`. `findNeedles` compares each element of the `needles` array to each element of the `words` array. It counts the matches and outputs them as a list of strings with numbers of their occurences.

## Request

### Request syntax

```Shell
GET /findneedles/{haystrack}{needles} HTTP/1.1
```

### Request parameters

This API request requires two query-string parameters.

|Parameter|Type|Description|Required|Limitation|Sample|
|---|---|---|---|---|---|
|heystack|String|String of characters (split into words, constitutes the `words` array)|Yes|No|"hello world hello! The world is mine."|
|needles|String array|Set of words (needles to be compared to the `words` array|Yes|Up to five strings per array|{"111", "we", "world", "mine", "hello"}|

### Request sample

```bash
http://localhost:8080/findneedles?haystack=hello+world+hello!+The+world+is+mine.&needles=111&needles=we&needles=world&needles=mine&needles=hello
```

## Response

`findNeedles` logs the following output in the console:
* For `needles` of up to five elements: an [error message](#more-than-five-needles) 
* For `needles` of more than five elements, a [list of words with numbers](#up-to-five-needles) reflecting how many times they occur in the `words` array.

### Response schema

```shell
needles[0]: occurrences no.
needles[1]: occurrences no.
needles[2]: occurrences no.
needles[3]: occurrences no.
needles[4]: occurrences no.
```

### Response samples

#### Up to five needles

```bash
111: 0
we: 0
world: 2
mine: 1
hello: 1
```

#### More than five needles

```bash
Too many words!
```

## Appendix

### Logic behind

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

### Operational sequence

1. `findNeedles` checks if the size of the `needles` array is greater than five.
   * If greater than five, it output an error message and exites.
   * If smaller or equal five, it proceeeds to step 2.
2. `findNeedles` uses the `split` function to divide the input string using the following literals: `"`, `'`, `t`, `n`, `b`, `f`, `r`. The `haystack` string is split into words, which constitute the `words` array.
3. `findNeedles` compares each element of the `needles` array to each element of the `words`array.
4. If a `needle` occurs within the `words` array, the count for this `needle` is launched.
5. With the search and all the counts completed, `findNeedles` outputs a list of matched `needles` with their occurence count results.

