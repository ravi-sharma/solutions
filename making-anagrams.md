Alice is taking a cryptography class and finding anagrams to be very useful. We consider two strings to be anagrams of each other if the first string's letters can be rearranged to form the second string. In other words, both strings must contain the same exact letters in the same exact frequency For example, bacdc and dcbac are anagrams, but bacdc and dcbad are not.

Alice decides on an encryption scheme involving two large strings where encryption is dependent on the minimum number of character deletions required to make the two strings anagrams. Can you help her find this number?

Given two strings,  and , that may or may not be of the same length, determine the minimum number of character deletions required to make  and  anagrams. Any characters can be deleted from either of the strings.

This challenge is also available in the following translations:

Chinese <br />
Russian

**Input Format**

The first line contains a single string, a.

The second line contains a single string, b.

**Constraints**
* It is guaranteed that  and  consist of lowercase English letters.

**Output Format**

Print a single integer denoting the number of characters which must be deleted to make the two strings anagrams of each other.

**Sample Input**

`cde` <br />
`abc`

**Sample Output**

`4`

**Explanation**

We delete the following characters from our two strings to turn them into anagrams of each other:

1. Remove d and e from cde to get c.<br />
2. Remove a and b from abc to get c.

We had to delete  characters to make both strings anagrams, so we print  on a new line.

### Solution:

```php
<?php

$handle = fopen("php://stdin", "r");
fscanf($handle, "%s", $a);
fscanf($handle, "%s", $b);

$arr_b   = str_split($b);
$arr_a   = str_split($a);
$counter = 0;

function GetDelta($a, $b)
{
	if (count($a) != count($b)) {
		return -1;
	}

	$delta = 0;

	for ($i = 0; $i < count($a); $i++) {
		$diff = abs($a[$i] - $b[$i]);

		$delta += $diff;
	}

	return $delta;
}

$counter = GetDelta(count_chars($a), count_chars($b));

fwrite(STDOUT, $counter);

?>
