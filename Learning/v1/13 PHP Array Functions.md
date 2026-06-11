# Array Functions in PHP - Complete Guide

PHP provides over 70+ built-in array functions for manipulating and working with arrays. Here's a comprehensive guide organized by category.

## Table of Contents
1. [Adding/Removing Elements](#adding-removing-elements)
2. [Sorting Functions](#sorting-functions)
3. [Searching Functions](#searching-functions)
4. [Filtering and Mapping](#filtering-and-mapping)
5. [Merging and Combining](#merging-and-combining)
6. [Splitting and Slicing](#splitting-and-slicing)
7. [Key and Value Functions](#key-and-value-functions)
8. [Array Information](#array-information)
9. [Comparison Functions](#comparison-functions)
10. [Other Useful Functions](#other-useful-functions)

---

## Adding/Removing Elements

### array_push()
Adds one or more elements to the end of an array.

```php
$fruits = ["Apple", "Banana"];
array_push($fruits, "Orange", "Mango");
print_r($fruits); // ["Apple", "Banana", "Orange", "Mango"]

// Alternative (faster for single element)
$fruits[] = "Grape";
```

### array_pop()
Removes and returns the last element of an array.

```php
$fruits = ["Apple", "Banana", "Orange"];
$last = array_pop($fruits);
echo $last; // "Orange"
print_r($fruits); // ["Apple", "Banana"]
```

### array_unshift()
Adds one or more elements to the beginning of an array.

```php
$fruits = ["Banana", "Orange"];
array_unshift($fruits, "Apple", "Mango");
print_r($fruits); // ["Apple", "Mango", "Banana", "Orange"]
```

### array_shift()
Removes and returns the first element of an array.

```php
$fruits = ["Apple", "Banana", "Orange"];
$first = array_shift($fruits);
echo $first; // "Apple"
print_r($fruits); // ["Banana", "Orange"]
```

### array_splice()
Removes and/or replaces elements in an array.

```php
$fruits = ["Apple", "Banana", "Orange", "Mango", "Grape"];

// Remove 2 elements starting at index 1
$removed = array_splice($fruits, 1, 2);
print_r($removed); // ["Banana", "Orange"]
print_r($fruits);  // ["Apple", "Mango", "Grape"]

// Replace elements
$fruits = ["Apple", "Banana", "Orange"];
array_splice($fruits, 1, 1, ["Mango", "Grape"]);
print_r($fruits); // ["Apple", "Mango", "Grape", "Orange"]

// Insert without removing
$fruits = ["Apple", "Orange"];
array_splice($fruits, 1, 0, ["Banana"]);
print_r($fruits); // ["Apple", "Banana", "Orange"]
```

### array_pad()
Pads array to specified length with a value.

```php
$arr = [1, 2, 3];
$padded = array_pad($arr, 5, 0);
print_r($padded); // [1, 2, 3, 0, 0]

// Negative length pads to the left
$padded = array_pad($arr, -5, 0);
print_r($padded); // [0, 0, 1, 2, 3]
```

---

## Sorting Functions

### sort()
Sorts an array in ascending order (reindexes).

```php
$numbers = [3, 1, 4, 1, 5, 9];
sort($numbers);
print_r($numbers); // [1, 1, 3, 4, 5, 9]

// With flags
$fruits = ["orange", "Apple", "banana"];
sort($fruits, SORT_STRING | SORT_FLAG_CASE);
print_r($fruits); // ["Apple", "banana", "orange"]
```

### rsort()
Sorts an array in descending order (reindexes).

```php
$numbers = [3, 1, 4, 1, 5, 9];
rsort($numbers);
print_r($numbers); // [9, 5, 4, 3, 1, 1]
```

### asort()
Sorts an array in ascending order, maintaining key association.

```php
$ages = ["Peter" => 35, "Ben" => 37, "Joe" => 43];
asort($ages);
print_r($ages); 
// ["Peter" => 35, "Ben" => 37, "Joe" => 43]
```

### arsort()
Sorts an array in descending order, maintaining key association.

```php
$ages = ["Peter" => 35, "Ben" => 37, "Joe" => 43];
arsort($ages);
print_r($ages); 
// ["Joe" => 43, "Ben" => 37, "Peter" => 35]
```

### ksort()
Sorts an array by key in ascending order.

```php
$ages = ["Peter" => 35, "Ben" => 37, "Joe" => 43];
ksort($ages);
print_r($ages); 
// ["Ben" => 37, "Joe" => 43, "Peter" => 35]
```

### krsort()
Sorts an array by key in descending order.

```php
$ages = ["Peter" => 35, "Ben" => 37, "Joe" => 43];
krsort($ages);
print_r($ages); 
// ["Peter" => 35, "Joe" => 43, "Ben" => 37]
```

### usort()
Sorts an array using a user-defined comparison function.

```php
$numbers = [3, 1, 4, 1, 5, 9];
usort($numbers, function($a, $b) {
    return $a <=> $b; // Spaceship operator
});
print_r($numbers); // [1, 1, 3, 4, 5, 9]

// Sort objects
$people = [
    ["name" => "John", "age" => 30],
    ["name" => "Jane", "age" => 25],
    ["name" => "Bob", "age" => 35]
];

usort($people, function($a, $b) {
    return $a["age"] <=> $b["age"];
});
```

### uasort()
Sorts with user function, maintaining key association.

```php
$ages = ["Peter" => 35, "Ben" => 37, "Joe" => 43];
uasort($ages, function($a, $b) {
    return $a <=> $b;
});
```

### uksort()
Sorts by key using user-defined function.

```php
$ages = ["Peter" => 35, "Ben" => 37, "Joe" => 43];
uksort($ages, function($a, $b) {
    return strcmp($a, $b);
});
```

### natsort() / natcasesort()
Natural order sorting (case-sensitive / case-insensitive).

```php
$files = ["img12.png", "img10.png", "img2.png", "img1.png"];
natsort($files);
print_r($files); // ["img1.png", "img2.png", "img10.png", "img12.png"]
```

### array_multisort()
Sorts multiple arrays or multi-dimensional arrays.

```php
$names = ["Peter", "Ben", "Joe"];
$ages = [35, 37, 43];

array_multisort($ages, SORT_ASC, $names, SORT_ASC);
print_r($names); // ["Peter", "Ben", "Joe"]
print_r($ages);  // [35, 37, 43]
```

### shuffle()
Randomly shuffles an array.

```php
$cards = ["Ace", "King", "Queen", "Jack"];
shuffle($cards);
print_r($cards); // Random order
```

---

## Searching Functions

### array_search()
Searches for a value and returns its key.

```php
$fruits = ["Apple", "Banana", "Orange"];
$key = array_search("Banana", $fruits);
echo $key; // 1

// Strict comparison
$key = array_search("2", [1, 2, 3], true);
echo $key; // false (strict mode)
```

### in_array()
Checks if a value exists in an array.

```php
$fruits = ["Apple", "Banana", "Orange"];
if (in_array("Banana", $fruits)) {
    echo "Found!";
}

// Strict comparison
if (in_array(2, [1, "2", 3], true)) {
    echo "Found!"; // Not executed (strict mode)
}
```

### array_key_exists()
Checks if a key exists in an array.

```php
$person = ["name" => "John", "age" => 30];
if (array_key_exists("name", $person)) {
    echo "Key exists!";
}

// Difference from isset()
$arr = ["key" => null];
array_key_exists("key", $arr); // true
isset($arr["key"]);            // false
```

### array_keys()
Returns all keys or keys with specific value.

```php
$person = ["name" => "John", "age" => 30, "city" => "NY"];
$keys = array_keys($person);
print_r($keys); // ["name", "age", "city"]

// Search for specific value
$numbers = ["a" => 1, "b" => 2, "c" => 1];
$keys = array_keys($numbers, 1);
print_r($keys); // ["a", "c"]
```

### array_values()
Returns all values (reindexed numerically).

```php
$person = ["name" => "John", "age" => 30];
$values = array_values($person);
print_r($values); // ["John", 30]
```

### array_key_first() / array_key_last()
Gets first/last key of an array (PHP 7.3+).

```php
$fruits = ["a" => "Apple", "b" => "Banana", "c" => "Orange"];
echo array_key_first($fruits);  // "a"
echo array_key_last($fruits);   // "c"
```

---

## Filtering and Mapping

### array_filter()
Filters elements using a callback function.

```php
$numbers = [1, 2, 3, 4, 5, 6];

// Filter even numbers
$evens = array_filter($numbers, function($n) {
    return $n % 2 == 0;
});
print_r($evens); // [2, 4, 6]

// With keys
$person = ["name" => "John", "age" => 30, "email" => ""];
$filtered = array_filter($person, function($value, $key) {
    return !empty($value);
}, ARRAY_FILTER_USE_BOTH);

// Remove empty values
$arr = ["", "hello", 0, null, "world"];
$filtered = array_filter($arr); // ["hello", "world"]
```

### array_map()
Applies a callback to all elements.

```php
$numbers = [1, 2, 3, 4, 5];

// Square each number
$squared = array_map(function($n) {
    return $n * $n;
}, $numbers);
print_r($squared); // [1, 4, 9, 16, 25]

// Multiple arrays
$arr1 = [1, 2, 3];
$arr2 = [4, 5, 6];
$result = array_map(function($a, $b) {
    return $a + $b;
}, $arr1, $arr2);
print_r($result); // [5, 7, 9]

// With keys (PHP 7.4+)
$arr = ["a" => 1, "b" => 2];
$result = array_map(function($value, $key) {
    return "$key: $value";
}, $arr, array_keys($arr));
```

### array_reduce()
Reduces array to single value using callback.

```php
$numbers = [1, 2, 3, 4, 5];

// Sum
$sum = array_reduce($numbers, function($carry, $item) {
    return $carry + $item;
}, 0);
echo $sum; // 15

// Product
$product = array_reduce($numbers, function($carry, $item) {
    return $carry * $item;
}, 1);
echo $product; // 120

// Build string
$words = ["Hello", "World", "PHP"];
$sentence = array_reduce($words, function($carry, $word) {
    return $carry . " " . $word;
}, "");
echo trim($sentence); // "Hello World PHP"
```

### array_walk()
Applies a user function to every element.

```php
$fruits = ["apple", "banana", "orange"];

array_walk($fruits, function(&$value, $key) {
    $value = strtoupper($value);
});
print_r($fruits); // ["APPLE", "BANANA", "ORANGE"]

// With additional parameter
array_walk($fruits, function(&$value, $key, $prefix) {
    $value = $prefix . $value;
}, "FRUIT:");
```

### array_walk_recursive()
Applies function recursively to all elements.

```php
$data = [
    "fruits" => ["apple", "banana"],
    "vegetables" => ["carrot", "broccoli"]
];

array_walk_recursive($data, function(&$value) {
    $value = strtoupper($value);
});
print_r($data);
```

---

## Merging and Combining

### array_merge()
Merges one or more arrays.

```php
$arr1 = ["a" => "Apple", "b" => "Banana"];
$arr2 = ["c" => "Orange", "d" => "Mango"];
$result = array_merge($arr1, $arr2);
print_r($result);
// ["a" => "Apple", "b" => "Banana", "c" => "Orange", "d" => "Mango"]

// Numeric keys are reindexed
$arr1 = [1, 2, 3];
$arr2 = [4, 5, 6];
$result = array_merge($arr1, $arr2);
print_r($result); // [1, 2, 3, 4, 5, 6]

// Later values overwrite earlier ones for string keys
$arr1 = ["a" => "Apple"];
$arr2 = ["a" => "Apricot"];
$result = array_merge($arr1, $arr2);
print_r($result); // ["a" => "Apricot"]
```

### array_merge_recursive()
Merges arrays recursively.

```php
$arr1 = [
    "colors" => ["red", "green"],
    "numbers" => [1, 2]
];
$arr2 = [
    "colors" => ["blue"],
    "numbers" => [3, 4]
];

$result = array_merge_recursive($arr1, $arr2);
print_r($result);
// ["colors" => ["red", "green", "blue"], "numbers" => [1, 2, 3, 4]]
```

### array_combine()
Creates array using one array for keys, another for values.

```php
$keys = ["name", "age", "city"];
$values = ["John", 30, "New York"];
$person = array_combine($keys, $values);
print_r($person);
// ["name" => "John", "age" => 30, "city" => "New York"]
```

### array_replace()
Replaces values from subsequent arrays.

```php
$base = ["a" => "Apple", "b" => "Banana", "c" => "Cherry"];
$replace = ["a" => "Apricot", "d" => "Date"];
$result = array_replace($base, $replace);
print_r($result);
// ["a" => "Apricot", "b" => "Banana", "c" => "Cherry", "d" => "Date"]
```

### array_replace_recursive()
Replaces values recursively.

```php
$arr1 = ["fruits" => ["a" => "apple"], "colors" => ["red"]];
$arr2 = ["fruits" => ["b" => "banana"], "colors" => ["blue"]];
$result = array_replace_recursive($arr1, $arr2);
print_r($result);
```

### Union Operator (+)
Combines arrays, keeping keys from first array.

```php
$arr1 = ["a" => "Apple", "b" => "Banana"];
$arr2 = ["b" => "Blueberry", "c" => "Cherry"];
$result = $arr1 + $arr2;
print_r($result);
// ["a" => "Apple", "b" => "Banana", "c" => "Cherry"]
// Note: "b" from $arr2 is NOT used
```

---

## Splitting and Slicing

### array_slice()
Extracts a portion of an array.

```php
$fruits = ["Apple", "Banana", "Orange", "Mango", "Grape"];

// Get 3 elements starting at index 1
$slice = array_slice($fruits, 1, 3);
print_r($slice); // ["Banana", "Orange", "Mango"]

// Negative offset (from end)
$slice = array_slice($fruits, -3);
print_r($slice); // ["Orange", "Mango", "Grape"]

// Preserve keys
$slice = array_slice($fruits, 1, 3, true);

// Without length (to end)
$slice = array_slice($fruits, 2);
print_r($slice); // ["Orange", "Mango", "Grape"]
```

### array_chunk()
Splits an array into chunks.

```php
$numbers = [1, 2, 3, 4, 5, 6, 7, 8];
$chunks = array_chunk($numbers, 3);
print_r($chunks);
// [[1, 2, 3], [4, 5, 6], [7, 8]]

// Preserve keys
$chunks = array_chunk($numbers, 3, true);
```

### array_column()
Returns values from a single column (multi-dimensional arrays).

```php
$users = [
    ["id" => 1, "name" => "John", "age" => 30],
    ["id" => 2, "name" => "Jane", "age" => 25],
    ["id" => 3, "name" => "Bob", "age" => 35]
];

// Get all names
$names = array_column($users, "name");
print_r($names); // ["John", "Jane", "Bob"]

// Use another column as key
$indexed = array_column($users, "name", "id");
print_r($indexed); // [1 => "John", 2 => "Jane", 3 => "Bob"]
```

---

## Key and Value Functions

### array_flip()
Exchanges keys and values.

```php
$arr = ["a" => 1, "b" => 2, "c" => 3];
$flipped = array_flip($arr);
print_r($flipped); // [1 => "a", 2 => "b", 3 => "c"]

// Useful for checking value existence efficiently
$allowed = ["admin", "user", "guest"];
$allowedFlipped = array_flip($allowed);
if (isset($allowedFlipped["admin"])) {
    echo "Allowed!";
}
```

### array_change_key_case()
Changes case of all keys.

```php
$arr = ["Name" => "John", "AGE" => 30];
$lower = array_change_key_case($arr, CASE_LOWER);
print_r($lower); // ["name" => "John", "age" => 30]

$upper = array_change_key_case($arr, CASE_UPPER);
print_r($upper); // ["NAME" => "John", "AGE" => 30]
```

### array_fill()
Fills array with values.

```php
$arr = array_fill(0, 5, "Hello");
print_r($arr); // ["Hello", "Hello", "Hello", "Hello", "Hello"]

// Start index can be any number
$arr = array_fill(10, 3, 0);
print_r($arr); // [10 => 0, 11 => 0, 12 => 0]
```

### array_fill_keys()
Fills array using keys.

```php
$keys = ["name", "age", "city"];
$arr = array_fill_keys($keys, "unknown");
print_r($arr);
// ["name" => "unknown", "age" => "unknown", "city" => "unknown"]
```

---

## Array Information

### count() / sizeof()
Counts elements in an array.

```php
$fruits = ["Apple", "Banana", "Orange"];
echo count($fruits); // 3

// Multidimensional (recursive)
$arr = [1, 2, [3, 4, [5, 6]]];
echo count($arr, COUNT_RECURSIVE); // 8
```

### array_count_values()
Counts frequency of values.

```php
$votes = ["PHP", "Java", "PHP", "Python", "PHP", "Java"];
$counts = array_count_values($votes);
print_r($counts);
// ["PHP" => 3, "Java" => 2, "Python" => 1]
```

### array_product()
Calculates product of values.

```php
$numbers = [2, 3, 4];
echo array_product($numbers); // 24
```

### array_sum()
Calculates sum of values.

```php
$numbers = [1, 2, 3, 4, 5];
echo array_sum($numbers); // 15
```

### is_array()
Checks if variable is an array.

```php
$arr = [1, 2, 3];
if (is_array($arr)) {
    echo "It's an array!";
}
```

---

## Comparison Functions

### array_diff()
Compares arrays and returns differences.

```php
$arr1 = [1, 2, 3, 4, 5];
$arr2 = [3, 4, 5, 6, 7];
$diff = array_diff($arr1, $arr2);
print_r($diff); // [1, 2] (values in $arr1 not in $arr2)
```

### array_diff_key()
Compares arrays by keys.

```php
$arr1 = ["a" => 1, "b" => 2, "c" => 3];
$arr2 = ["b" => 4, "c" => 5, "d" => 6];
$diff = array_diff_key($arr1, $arr2);
print_r($diff); // ["a" => 1]
```

### array_diff_assoc()
Compares arrays with keys and values.

```php
$arr1 = ["a" => 1, "b" => 2, "c" => 3];
$arr2 = ["a" => 1, "b" => 4, "c" => 3];
$diff = array_diff_assoc($arr1, $arr2);
print_r($diff); // ["b" => 2]
```

### array_intersect()
Returns common values.

```php
$arr1 = [1, 2, 3, 4];
$arr2 = [3, 4, 5, 6];
$common = array_intersect($arr1, $arr2);
print_r($common); // [3, 4]
```

### array_intersect_key()
Returns common keys.

```php
$arr1 = ["a" => 1, "b" => 2, "c" => 3];
$arr2 = ["b" => 4, "c" => 5, "d" => 6];
$common = array_intersect_key($arr1, $arr2);
print_r($common); // ["b" => 2, "c" => 3]
```

### array_intersect_assoc()
Returns common key-value pairs.

```php
$arr1 = ["a" => 1, "b" => 2, "c" => 3];
$arr2 = ["a" => 1, "b" => 4, "c" => 3];
$common = array_intersect_assoc($arr1, $arr2);
print_r($common); // ["a" => 1, "c" => 3]
```

---

## Other Useful Functions

### array_unique()
Removes duplicate values.

```php
$arr = [1, 2, 2, 3, 4, 4, 5];
$unique = array_unique($arr);
print_r($unique); // [1, 2, 3, 4, 5]

// With sorting
$unique = array_unique($arr, SORT_NUMERIC);
```

### array_reverse()
Reverses array order.

```php
$arr = [1, 2, 3, 4, 5];
$reversed = array_reverse($arr);
print_r($reversed); // [5, 4, 3, 2, 1]

// Preserve keys
$reversed = array_reverse($arr, true);
```

### array_rand()
Picks random key(s).

```php
$fruits = ["Apple", "Banana", "Orange", "Mango"];
$randomKey = array_rand($fruits);
echo $fruits[$randomKey]; // Random fruit

// Multiple random keys
$randomKeys = array_rand($fruits, 2);
print_r($randomKeys); // [0, 3] (example)
```

### range()
Creates array with range of values.

```php
$numbers = range(1, 10);
print_r($numbers); // [1, 2, 3, ..., 10]

$letters = range('a', 'z');
print_r($letters); // ['a', 'b', 'c', ..., 'z']

// With step
$evens = range(0, 20, 2);
print_r($evens); // [0, 2, 4, 6, ..., 20]
```

### compact()
Creates array from variables.

```php
$name = "John";
$age = 30;
$city = "New York";

$person = compact("name", "age", "city");
print_r($person);
// ["name" => "John", "age" => 30, "city" => "New York"]
```

### extract()
Imports variables from array.

```php
$person = ["name" => "John", "age" => 30];
extract($person);
echo $name; // John
echo $age;  // 30

// With prefix
extract($person, EXTR_PREFIX_ALL, "user");
echo $user_name; // John
```

### list() / []
Assigns variables from array.

```php
$person = ["John", 30, "New York"];
list($name, $age, $city) = $person;
// or
[$name, $age, $city] = $person;

echo $name; // John

// Skip elements
[$name, , $city] = $person;

// With keys (PHP 7.1+)
$person = ["name" => "John", "age" => 30];
["name" => $name, "age" => $age] = $person;
```

### implode() / join()
Joins array elements into string.

```php
$fruits = ["Apple", "Banana", "Orange"];
$str = implode(", ", $fruits);
echo $str; // "Apple, Banana, Orange"

// join() is an alias
$str = join(" | ", $fruits);
```

### explode()
Splits string into array.

```php
$str = "Apple,Banana,Orange";
$fruits = explode(",", $str);
print_r($fruits); // ["Apple", "Banana", "Orange"]

// Limit
$parts = explode(",", $str, 2);
print_r($parts); // ["Apple", "Banana,Orange"]
```

### str_split()
Converts string to array of characters.

```php
$str = "Hello";
$chars = str_split($str);
print_r($chars); // ["H", "e", "l", "l", "o"]

// Custom length
$chunks = str_split($str, 2);
print_r($chunks); // ["He", "ll", "o"]
```

### array_is_list()
Checks if array is a list (PHP 8.1+).

```php
$arr1 = [1, 2, 3];
var_dump(array_is_list($arr1)); // true

$arr2 = [0 => 1, 2 => 3];
var_dump(array_is_list($arr2)); // false

$arr3 = ["a" => 1, "b" => 2];
var_dump(array_is_list($arr3)); // false
```

---

## Practical Examples

### Remove Empty Values
```php
$arr = ["", "hello", 0, null, false, "world"];
$cleaned = array_filter($arr, function($value) {
    return $value !== "" && $value !== null && $value !== false;
});
// Or simply
$cleaned = array_filter($arr);
```

### Group Array by Key
```php
$users = [
    ["name" => "John", "role" => "admin"],
    ["name" => "Jane", "role" => "user"],
    ["name" => "Bob", "role" => "admin"]
];

$grouped = array_reduce($users, function($carry, $user) {
    $carry[$user["role"]][] = $user;
    return $carry;
}, []);

print_r($grouped);
```

### Array Pagination
```php
function paginate($array, $page, $perPage) {
    $offset = ($page - 1) * $perPage;
    return array_slice($array, $offset, $perPage);
}

$items = range(1, 100);
$page2 = paginate($items, 2, 10); // Items 11-20
```

### Pluck Values from Objects
```php
$users = [
    (object)["id" => 1, "name" => "John"],
    (object)["id" => 2, "name" => "Jane"]
];

$names = array_map(fn($user) => $user->name, $users);
print_r($names); // ["John", "Jane"]
```

---

PHP's array functions are incredibly powerful and understanding them will make you a much more efficient PHP developer. Practice using these functions to manipulate data effectively!