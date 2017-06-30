# A Product Array Puzzle
Given an array arr[] of n integers, construct a Product Array prod[] (of same size) such that prod[i] is equal to the product of all the elements of arr[] except arr[i]. Solve it without division operator and in O(n).

Example:<br>
Input: `arr[] = {10, 3, 5, 6, 2}`

Output: `prod[] = {180, 600, 360, 300, 900}`

Recommended: Please solve it on “PRACTICE” first, before moving on to the solution.

Algorithm:
1) Construct a temporary array left[] such that left[i] contains product of all elements on left of arr[i] excluding arr[i].<br>
2) Construct another temporary array right[] such that right[i] contains product of all elements on on right of arr[i] excluding arr[i].<br>
3) To get prod[], multiply left[] and right[].<br>

### Implementation:

#### Case: 1 big O(N3) complexity

```php
<?php

$a    = [1, 3, 5, 7];
$prod = [];

// big O(N3) complexity
for ($i = 0; $i < count($a); $i++) {
	$pr       = implode("*", array_diff($a, [$a[$i]])); // implode() O(N)  *  array_diff O(π param_i_size, for all i) = O(n2)
	$prod[$i] = eval("return $pr;");
}

print_r($prod);
```

#### Case: 2 big O(N2) complexity
```php
<?php

$a    = [1, 3, 5, 7];
$prod = [];

// big O(N2) complexity
for ($i = 0; $i < count($a); $i++) {
	$prod[$i] = array_product(array_diff($a, [$a[$i]])); // array_product() O(N)  *  array_diff O(π param_i_size, for all i) = O(n2)
}

print_r($prod);
```

#### Case: 3 big O(N) complexity
```php
<?php

$a    = [1, 3, 5, 7];
$prod = [];

$p = 1;

// big O(N) complexity 
// Traverse to left
for ($i = 0; $i < count($a); $i++) {
	$prod[$i] = $p;
	$p *= $a[$i];
}

// Traverse to right
$p = 1;
for ($i = count($a) - 1; $i >= 0; --$i) {
	$prod[$i] *= $p;
	$p *= $a[$i];
}

print_r($prod);
```
