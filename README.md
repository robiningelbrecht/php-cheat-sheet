# php-cheat-sheet

## PHP 7.x

### 1. Arrow functions support

```php
$a = [1, 2, 3, 4, 5];
$b = array_map(fn($n) => $n * $n * $n, $a);

``` 

### 2. Coalescing assign operator

```php
$value = $array['key'] ?? NULL;
// This is equivalent to:
$value = isset($array['key']) ? $array['key'] : NULL;
// Coalescing can be chained: this will return the first defined value.
$value = $array['key'] ?? $array['another_key'] ?? NULL;

``` 

### 3. Spread operator in array expression

```php
$parts = ['apple', 'pear'];
$fruits = ['banana', 'orange', ...$parts, 'watermelon'];
var_dump($fruits);

/** Will output
array(5) {
  [0]=>
  string(6) "banana"
  [1]=>
  string(6) "orange"
  [2]=>
  string(5) "apple"
  [3]=>
  string(4) "pear"
  [4]=>
  string(10) "watermelon"
}
**/

``` 
