A kidnapper wrote a ransom note but is worried it will be traced back to him. He found a magazine and wants to know if he can cut out whole words from it and use them to create an untraceable replica of his ransom note. The words in his note are case-sensitive and he must use whole words available in the magazine, meaning he cannot use substrings or concatenation to create the words he needs.

Given the words in the magazine and the words in the ransom note, print Yes if he can replicate his ransom note exactly using whole words from the magazine; otherwise, print No.

**Input Format**

The first line contains two space-separated integers describing the respective values of  (the number of words in the magazine) and  (the number of words in the ransom note). 
The second line contains  space-separated strings denoting the words present in the magazine. 
The third line contains  space-separated strings denoting the words present in the ransom note.

**Constraints**
* Each word consists of English alphabetic letters (i.e.,  to  and  to ).
* The words in the note and magazine are case-sensitive.

**Output Format**

Print `Yes` if he can use the magazine to create an untraceable replica of his ransom note; otherwise, print `No`.

**Sample Input 0**

`6 4` <br>
`give me one grand today night`<br>
`give one grand today`<br>

**Sample Output 0** 

`Yes`<br>

**Sample Input 1**

`6 5`<br>
`two times three is not four` <br>
`two times two is four` <br>

**Sample Output 1**

`No`

### Solution:
```php
<?php

$handle = fopen("php://stdin", "r");
fscanf($handle, "%d %d", $m, $n);
$magazine_temp = fgets($handle);
$ransom_temp   = fgets($handle);
$ransom        = explode(" ", $ransom_temp);

$result = 'Yes';
for ($i = 0; $i < $n; $i++) {

	$pos = strpos($magazine_temp, $ransom[$i]);

	if ($pos !== false) {
		$magazine_temp = substr_replace($magazine_temp, 'REMOVED', $pos, strlen($ransom[$i]));
	} else {
		$result = 'No';
	}
}

fwrite(STDOUT, $result);

?>
