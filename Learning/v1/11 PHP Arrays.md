# Arrays in PHP - Full Details

## What is an Array?

An array in PHP is a data structure that stores multiple values in a single variable. Each value can be accessed using a key (index). PHP arrays are extremely flexible and can hold mixed data types.

## Types of Arrays

### 1. Indexed Arrays
Arrays with numeric keys (starting from 0 by default).

```php
// Creating indexed arrays
$fruits = array("Apple", "Banana", "Orange");
// or using short syntax
$fruits = ["Apple", "Banana", "Orange"];

// Accessing elements
echo $fruits[0]; // Outputs: Apple
echo $fruits[1]; // Outputs: Banana
```

### 2. Associative Arrays
Arrays with named keys (key-value pairs).

```php
// Creating associative arrays
$person = array(
    "name" => "John",
    "age" => 30,
    "city" => "New York"
);
// or using short syntax
$person = [
    "name" => "John",
    "age" => 30,
    "city" => "New York"
];

// Accessing elements
echo $person["name"]; // Outputs: John
echo $person["age"];  // Outputs: 30
```

### 3. Multidimensional Arrays
Arrays containing other arrays.

```php
$students = [
    ["John", 25, "Math"],
    ["Jane", 22, "Science"],
    ["Bob", 23, "History"]
];

echo $students[0][0]; // Outputs: John
echo $students[1][2]; // Outputs: Science

// Associative multidimensional array
$users = [
    "user1" => ["name" => "Alice", "age" => 28],
    "user2" => ["name" => "Bob", "age" => 32]
];

echo $users["user1"]["name"]; // Outputs: Alice
```

## Creating Arrays

```php
// Empty array
$arr = [];
$arr = array();

// With values
$colors = ["Red", "Green", "Blue"];

// Using range()
$numbers = range(1, 10); // [1, 2, 3, ..., 10]
$letters = range('a', 'z'); // ['a', 'b', 'c', ..., 'z']

// Using array_fill()
$zeros = array_fill(0, 5, 0); // [0, 0, 0, 0, 0]
```

## Adding Elements

```php
$fruits = ["Apple", "Banana"];

// Add to end
$fruits[] = "Orange";
array_push($fruits, "Mango", "Grape");

// Add to beginning
array_unshift($fruits, "Strawberry");

// Add with specific key
$fruits[10] = "Pineapple";

// Associative
$person["email"] = "john@example.com";
```

## Removing Elements

```php
$fruits = ["Apple", "Banana", "Orange", "Mango"];

// Remove from end
$last = array_pop($fruits);

// Remove from beginning
$first = array_shift($fruits);

// Remove specific element
unset($fruits[1]);

// Remove by value
$key = array_search("Orange", $fruits);
if ($key !== false) {
    unset($fruits[$key]);
}

// Clear entire array
$fruits = [];
```

## Array Functions

### Counting and Checking

```php
$fruits = ["Apple", "Banana", "Orange"];

count($fruits);              // 3
sizeof($fruits);             // 3 (alias of count)
in_array("Apple", $fruits);  // true
array_key_exists(0, $fruits); // true
isset($fruits[0]);           // true
empty($fruits);              // false
```

### Sorting

```php
$numbers = [3, 1, 4, 1, 5, 9];

sort($numbers);       // Sort ascending (values)
rsort($numbers);      // Sort descending (values)
asort($numbers);      // Sort ascending (maintain keys)
arsort($numbers);     // Sort descending (maintain keys)
ksort($numbers);      // Sort by key ascending
krsort($numbers);     // Sort by key descending
usort($numbers, function($a, $b) {
    return $a <=> $b; // Custom sort
});
```

### Searching

```php
$fruits = ["Apple", "Banana", "Orange"];

array_search("Banana", $fruits);  // Returns key: 1
array_keys($fruits);              // [0, 1, 2]
array_values($fruits);            // ["Apple", "Banana", "Orange"]
```

### Merging and Combining

```php
$arr1 = [1, 2, 3];
$arr2 = [4, 5, 6];

array_merge($arr1, $arr2);       // [1, 2, 3, 4, 5, 6]
$arr1 + $arr2;                   // Union operator
array_combine($arr1, $arr2);     // Creates associative array
```

### Slicing and Splicing

```php
$fruits = ["Apple", "Banana", "Orange", "Mango", "Grape"];

array_slice($fruits, 1, 3);      // ["Banana", "Orange", "Mango"]
array_splice($fruits, 1, 2);     // Removes and returns elements
```

### Filtering and Mapping

```php
$numbers = [1, 2, 3, 4, 5, 6];

// Filter
$evens = array_filter($numbers, function($n) {
    return $n % 2 == 0;
}); // [2, 4, 6]

// Map
$squared = array_map(function($n) {
    return $n * $n;
}, $numbers); // [1, 4, 9, 16, 25, 36]

// Reduce
$sum = array_reduce($numbers, function($carry, $item) {
    return $carry + $item;
}, 0); // 21
```

### Other Useful Functions

```php
$arr = [1, 2, 3, 4, 5];

array_reverse($arr);           // Reverse order
array_unique($arr);            // Remove duplicates
array_sum($arr);               // Sum of values: 15
array_product($arr);           // Product of values: 120
max($arr);                     // Maximum value: 5
min($arr);                     // Minimum value: 1
array_rand($arr);              // Random key
shuffle($arr);                 // Randomize order
array_chunk($arr, 2);          // Split into chunks
array_flip($arr);              // Exchange keys and values
implode(", ", $arr);           // Join to string: "1, 2, 3, 4, 5"
explode(", ", "1, 2, 3");      // Split string to array
```

## Looping Through Arrays

```php
$fruits = ["Apple", "Banana", "Orange"];

// foreach loop (most common)
foreach ($fruits as $fruit) {
    echo $fruit . "<br>";
}

// foreach with keys
foreach ($fruits as $key => $value) {
    echo "$key: $value<br>";
}

// for loop
for ($i = 0; $i < count($fruits); $i++) {
    echo $fruits[$i] . "<br>";
}

// while loop
$i = 0;
while ($i < count($fruits)) {
    echo $fruits[$i] . "<br>";
    $i++;
}

// array_walk
array_walk($fruits, function($value, $key) {
    echo "$key: $value<br>";
});
```

## Advanced Techniques

### Array Destructuring (PHP 7.1+)

```php
$person = ["John", 30, "Developer"];

// List syntax
list($name, $age, $job) = $person;

// Short syntax (PHP 7.1+)
[$name, $age, $job] = $person;

echo $name; // John
```

### Spread Operator (PHP 7.4+)

```php
$arr1 = [1, 2, 3];
$arr2 = [...$arr1, 4, 5, 6]; // [1, 2, 3, 4, 5, 6]

function sum(...$numbers) {
    return array_sum($numbers);
}

echo sum(1, 2, 3, 4); // 10
```

### Arrow Functions (PHP 7.4+)

```php
$numbers = [1, 2, 3, 4, 5];

$squared = array_map(fn($n) => $n * $n, $numbers);
$evens = array_filter($numbers, fn($n) => $n % 2 == 0);
```

## Common Patterns

### Check if array is associative

```php
function isAssoc($arr) {
    return array_keys($arr) !== range(0, count($arr) - 1);
}
```

### Remove empty values

```php
$arr = array_filter($arr, function($value) {
    return !empty($value);
});
```

### Get first/last element

```php
$first = reset($arr);  // or $arr[0] for indexed
$last = end($arr);     // or $arr[count($arr)-1]

// Without changing pointer (PHP 7.3+)
$first = array_key_first($arr);
$last = array_key_last($arr);
```

## Best Practices

1. **Use short array syntax** `[]` instead of `array()` (PHP 5.4+)
2. **Use foreach** for iteration when you don't need the index
3. **Use `in_array()` with strict mode**: `in_array($needle, $haystack, true)`
4. **Unset array elements properly** to avoid memory leaks in long-running scripts
5. **Use type hints** in functions accepting arrays (PHP 7+)
6. **Consider array performance** for large datasets - arrays can consume significant memory

Arrays are fundamental to PHP programming and understanding them thoroughly will make you much more effective as a PHP developer!