# findNeedles API

Gets the number of matches for a search query.

>CONTENTS
>>[Resource description](#resource-description)<br>
>>[Request](#request)<br>
>> \- [Reguest syntax](#request-syntax)<br>
>> \- [Request paramters](#request-parameters)<br>
>> \- [Request sample](#request-sample)<br>
>>[Response](#response)<br>
>> \- [Response schema](#response-schema)<br>
>> \- [Response samples](#response-samples)<br>

## Resource description

`findNeedles` counts and logs how many times particular `needles` (elements of the `needles` strings array) occur within `haystack` (string). To achieve that, `findNeedles` uses the `split` function dividing the `haystack` string into `words` strings by means of the following literals: `"`, `'`, `t`, `n`, `b`, `f`, `r`. `findNeedles` compares each element of the `needles` array to each element of the `words` array. It counts the matches and outputs them as a list of strings with numbers of their occurences.

## Request

### Request syntax

```bash
GET /findneedles/{haystack}/?{needles}
```

### Request parameters

This API request requires two parameters.

|Parameter|Type|Value|Description|Required|Limitation|Sample|
|---|---|---|---|---|---|---|
|heystack|Path parameter|String|String of characters (split into words, constitutes the `words` array)|Yes|No|"hello world hello! The world is mine."|
|needles|Query parameter|String array|Set of words (needles to be compared to the `words` array|Yes|Up to five strings per array|{"111", "we", "world", "mine", "hello"}|

### Request sample

```bash
http://localhost:8080/findneedles/hello+world+hello!+The+world+is+mine./?needles=111&needles=we&needles=world/?q=mine&needles=hello
```

## Response

`findNeedles` logs the following output in the console:
* For the `needles` string array of up to five elements: an [error message](#more-than-five-needles) 
* For the `needles` string array of more than five elements, a [list of elements of the `needles` array] found in the `words` array with numbers of the occurances

The returned resource maps to the entire response body.

### Response schema

|Property|Value|Description|
|---|---|---|
|needles[j]|String|Element of the `needles` string array found in the `words` string array|
|countArray[j]|Intiger|Number of occurances of a matched string (needle `j`) within the `words` string array|


```shell
needles[0]: countArray[0]
needles[1]: countArray[1]
needles[2]: countArray[2]
needles[3]: countArray[3]
needles[4]: countArray[4]
```

### Response samples

#### needles.length <= 5

```bash
111: 0
we: 0
world: 2
mine: 1
hello: 1
```

#### needles.length > 5

```bash
Too many words!
```


