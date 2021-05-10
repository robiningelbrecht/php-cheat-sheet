# php-cheat-sheet

## PHP 8.x

### 1. The nullsafe operator

```php
$startDate = $booking->getStartDate();
$dateAsString = $startDate ? $startDate->asDateTimeString() : null;

// Is equivalent to:
$dateAsString = $booking->getStartDate()?->asDateTimeString();

// Can be chained:
$country = $session?->user?->getAddress()?->country;

``` 

### 2. Names arguments:

```php
// Allows you to pass in values to a function, by specifying the value name, 
// so that you don't have to take their order into consideration
function foo(string $a, string $b, ?string $c = null, ?string $d = null) 
{ /* … */ }

foo(
    b: 'value b', 
    a: 'value a', 
    d: 'value d',
);

``` 

### 3. Match expression 

```php
// You could call it the big brother of the switch expression.
$message = match ($statusCode) {
    200, 300 => null,
    400 => 'not found',
    500 => 'server error',
    default => 'unknown status code',
};

``` 

### 4. Throw expression

```php
$triggerError = fn () => throw new MyError();
$foo = $bar['offset'] ?? throw new OffsetDoesNotExist('offset');

``` 

### 5. New str_contains() function

```php
if (strpos('string with lots of words', 'words') !== false) { /* … */ }
// Is equivalent to:
if (str_contains('string with lots of words', 'words')) { /* … */ }

``` 

### 6. New str_starts_with() and str_ends_with() functions

```php
str_starts_with('haystack', 'hay'); // true
str_ends_with('haystack', 'stack'); // true

``` 

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
Antoher example:

```php
$arr1 = [1, 2, 3];
$arr2 = [4, 5, 6];

// Will output the same.
var_dump(array(...$arr1, ...$arr2));
var_dump(array_merge($arr1, $arr2));


``` 
