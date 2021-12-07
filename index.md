# findNeedles API

Gets the number of matches for a search query.

>CONTENTS
>> \> [Description](#description)<br>
>> \> [Request](#request)<br>
>>   \>>> [Reguest syntax](#description)<br>
>>   \>>> [Paramters](#description)<br>
>>   \>>> [Sample](#description)<br>
>> \> [Response](#response)<br>
>>   \>>> [Schema](#description)<br>
>>   \>>> [Samples](#description)<br>

## Description

`findNeedles` counts and logs how many times particular `needles` (elements of the `needles` strings array) occur within `haystack` (string). To achieve that, `findNeedles` uses the `split` function dividing the `haystack` string into `words` strings by means of the following literals: `"`, `'`, `t`, `n`, `b`, `f`, `r`. `findNeedles` compares each element of the `needles` array to each element of the `words` array. It counts the matches and outputs them as a list of strings with numbers of their occurences.

## Request

### Request syntax

```bash
GET http://server/findneedles/{haystack}/?{needles}
```

### Request parameters

This API request requires two query-string parameters.

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


