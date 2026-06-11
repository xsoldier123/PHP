# Functions in PHP - Full Details

## What is a Function?

A function is a reusable block of code that performs a specific task. Functions help organize code, reduce repetition, and make programs easier to maintain and debug.

## Basic Function Syntax

```php
// Define a function
function functionName() {
    // code to be executed
}

// Call a function
functionName();
```

### Simple Example

```php
function greet() {
    echo "Hello, World!";
}

greet(); // Outputs: Hello, World!
```

## Function Parameters

Functions can accept input values called parameters or arguments.

```php
// Single parameter
function greet($name) {
    echo "Hello, $name!";
}

greet("John"); // Outputs: Hello, John!

// Multiple parameters
function add($a, $b) {
    echo $a + $b;
}

add(5, 3); // Outputs: 8
```

### Default Parameters

```php
function greet($name = "Guest") {
    echo "Hello, $name!";
}

greet();        // Outputs: Hello, Guest!
greet("Alice"); // Outputs: Hello, Alice!

// Multiple defaults
function createUser($name, $role = "user", $active = true) {
    echo "Name: $name, Role: $role, Active: " . ($active ? "Yes" : "No");
}

createUser("John");                    // Uses defaults for role and active
createUser("Jane", "admin");           // Uses default for active
createUser("Bob", "moderator", false); // All specified
```

## Return Values

Functions can return values using the `return` statement.

```php
function add($a, $b) {
    return $a + $b;
}

$result = add(5, 3);
echo $result; // Outputs: 8

// Multiple return points
function getGrade($score) {
    if ($score >= 90) return "A";
    if ($score >= 80) return "B";
    if ($score >= 70) return "C";
    if ($score >= 60) return "D";
    return "F";
}

echo getGrade(85); // Outputs: B
```

### Returning Multiple Values

```php
// Using array
function getUser() {
    return ["John", 30, "john@example.com"];
}

list($name, $age, $email) = getUser();
// or
[$name, $age, $email] = getUser();

// Using associative array
function getUserInfo() {
    return [
        "name" => "John",
        "age" => 30,
        "email" => "john@example.com"
    ];
}

$user = getUserInfo();
echo $user["name"]; // John
```

## Type Declarations (PHP 7+)

### Parameter Type Hints

```php
// Scalar types (PHP 7.0+)
function add(int $a, int $b): int {
    return $a + $b;
}

add(5, 3);    // 8
add(5.7, 3.2); // 8 (floats converted to ints)

// Available types
function example(
    int $integer,
    float $float,
    string $string,
    bool $boolean,
    array $array,
    object $object,
    callable $callback,
    iterable $iterable
) {
    // function body
}

// Class type hints
class User {}

function processUser(User $user) {
    // $user must be an instance of User
}
```

### Return Type Declarations

```php
function multiply(int $a, int $b): int {
    return $a * $b;
}

function getName(): string {
    return "John";
}

function getUsers(): array {
    return ["Alice", "Bob", "Charlie"];
}

// Void return type (PHP 7.1+)
function logMessage(string $message): void {
    echo $message;
    // Cannot return a value
}

// Nullable types (PHP 7.1+)
function findUser(int $id): ?User {
    // Can return User object or null
    return null;
}

// Union types (PHP 8.0+)
function process(int|float $number): int|float {
    return $number * 2;
}

// Mixed type (PHP 8.0+)
function getData(): mixed {
    return "anything";
}
```

### Strict Types

```php
declare(strict_types=1); // Must be at the top of the file

function add(int $a, int $b): int {
    return $a + $b;
}

add(5, 3);    // OK
add(5.5, 3.2); // TypeError - no automatic conversion
```

## Variable Scope

### Local Scope

```php
function test() {
    $x = 10; // Local variable
    echo $x;
}

test(); // Outputs: 10
// echo $x; // Error: undefined variable
```

### Global Scope

```php
$x = 10; // Global variable

function test() {
    global $x; // Access global variable
    echo $x;
}

test(); // Outputs: 10

// Alternative using $GLOBALS
function test2() {
    echo $GLOBALS['x'];
}

test2(); // Outputs: 10
```

### Static Variables

```php
function counter() {
    static $count = 0; // Retains value between calls
    $count++;
    echo $count . "<br>";
}

counter(); // 1
counter(); // 2
counter(); // 3
```

## Variable Functions

You can call functions dynamically using variables.

```php
function greet() {
    echo "Hello!";
}

$funcName = "greet";
$funcName(); // Calls greet() - Outputs: Hello!

// Useful for callbacks
function process($data, $callback) {
    return $callback($data);
}

$result = process(10, function($n) {
    return $n * 2;
});

echo $result; // 20
```

## Anonymous Functions (Closures)

Functions without a name, often used as callbacks.

```php
// Assign to variable
$greet = function($name) {
    return "Hello, $name!";
};

echo $greet("John"); // Outputs: Hello, John!

// As callback
$numbers = [1, 2, 3, 4, 5];
$squared = array_map(function($n) {
    return $n * $n;
}, $numbers);

print_r($squared); // [1, 4, 9, 16, 25]
```

### Closures with `use`

```php
$message = "Hello";

$greet = function($name) use ($message) {
    return "$message, $name!";
};

echo $greet("John"); // Outputs: Hello, John!

// Pass by reference
$counter = 0;

$increment = function() use (&$counter) {
    $counter++;
};

$increment();
$increment();
echo $counter; // 2
```

## Arrow Functions (PHP 7.4+)

Short syntax for simple anonymous functions.

```php
// Traditional anonymous function
$multiply = function($n) {
    return $n * 2;
};

// Arrow function
$multiply = fn($n) => $n * 2;

echo $multiply(5); // 10

// With array functions
$numbers = [1, 2, 3, 4, 5];
$squared = array_map(fn($n) => $n * $n, $numbers);

// Automatically captures variables from parent scope
$factor = 10;
$multiply = fn($n) => $n * $factor; // No 'use' needed!

echo $multiply(5); // 50
```

## Variadic Functions

Functions that accept variable number of arguments.

```php
// Using ... operator (PHP 5.6+)
function sum(...$numbers) {
    return array_sum($numbers);
}

echo sum(1, 2, 3);          // 6
echo sum(1, 2, 3, 4, 5);    // 15

// Type hints with variadic
function sumIntegers(int ...$numbers): int {
    return array_sum($numbers);
}

// Mixing regular and variadic parameters
function logMessage(string $level, string ...$messages) {
    echo "[$level] " . implode(" ", $messages);
}

logMessage("ERROR", "Database", "connection", "failed");
// Outputs: [ERROR] Database connection failed
```

### Argument Unpacking

```php
function add($a, $b, $c) {
    return $a + $b + $c;
}

$numbers = [1, 2, 3];
echo add(...$numbers); // 6 (unpacks array to arguments)
```

## Pass by Reference

```php
// Pass by value (default)
function increment($n) {
    $n++;
}

$num = 5;
increment($num);
echo $num; // 5 (unchanged)

// Pass by reference
function incrementRef(&$n) {
    $n++;
}

$num = 5;
incrementRef($num);
echo $num; // 6 (changed)

// Swap example
function swap(&$a, &$b) {
    $temp = $a;
    $a = $b;
    $b = $temp;
}

$x = 10;
$y = 20;
swap($x, $y);
echo "$x, $y"; // 20, 10
```

## Named Arguments (PHP 8.0+)

```php
function createUser($name, $email, $role = "user", $active = true) {
    // function body
}

// Traditional call
createUser("John", "john@example.com", "admin", false);

// Named arguments (order doesn't matter)
createUser(
    email: "john@example.com",
    name: "John",
    active: false,
    role: "admin"
);

// Skip optional parameters
createUser(
    name: "Jane",
    email: "jane@example.com",
    active: false
    // role uses default value
);
```

## Recursive Functions

Functions that call themselves.

```php
// Factorial
function factorial($n) {
    if ($n <= 1) {
        return 1;
    }
    return $n * factorial($n - 1);
}

echo factorial(5); // 120

// Fibonacci
function fibonacci($n) {
    if ($n <= 1) {
        return $n;
    }
    return fibonacci($n - 1) + fibonacci($n - 2);
}

echo fibonacci(10); // 55

// Directory tree (practical example)
function listFiles($dir, $indent = 0) {
    $files = scandir($dir);
    foreach ($files as $file) {
        if ($file != '.' && $file != '..') {
            echo str_repeat("  ", $indent) . $file . "\n";
            $path = $dir . '/' . $file;
            if (is_dir($path)) {
                listFiles($path, $indent + 1);
            }
        }
    }
}
```

## Built-in Functions

PHP has thousands of built-in functions. Here are some categories:

### String Functions
```php
strlen("Hello");              // 5
strtoupper("hello");          // "HELLO"
strtolower("HELLO");          // "hello"
str_replace("o", "0", "Hello"); // "Hell0"
substr("Hello", 1, 3);        // "ell"
explode(",", "a,b,c");        // ["a", "b", "c"]
trim("  hello  ");            // "hello"
```

### Array Functions
```php
count([1, 2, 3]);             // 3
array_push($arr, $value);     // Add to end
array_pop($arr);              // Remove from end
array_merge($arr1, $arr2);    // Merge arrays
sort($arr);                   // Sort array
in_array($value, $arr);       // Check if exists
```

### Math Functions
```php
abs(-5);                      // 5
round(3.7);                   // 4
ceil(3.1);                    // 4
floor(3.9);                   // 3
max(1, 5, 3);                 // 5
min(1, 5, 3);                 // 1
rand(1, 100);                 // Random between 1-100
pow(2, 3);                    // 8 (2^3)
sqrt(16);                     // 4
```

### Date/Time Functions
```php
date("Y-m-d");                // Current date
time();                       // Current timestamp
strtotime("+1 week");         // Timestamp for 1 week from now
date("Y-m-d", strtotime("+1 month")); // Date 1 month from now
```

## Generator Functions (PHP 5.5+)

Functions that yield values instead of returning them all at once.

```php
function generateNumbers($start, $end) {
    for ($i = $start; $i <= $end; $i++) {
        yield $i; // Yields one value at a time
    }
}

foreach (generateNumbers(1, 5) as $number) {
    echo $number . " "; // 1 2 3 4 5
}

// Memory efficient for large datasets
function readLargeFile($file) {
    $handle = fopen($file, 'r');
    while (!feof($handle)) {
        yield fgets($handle);
    }
    fclose($handle);
}
```

## Function Best Practices

1. **Single Responsibility**: Each function should do one thing well
2. **Descriptive Names**: Use clear, verb-based names (`getUserData`, `calculateTotal`)
3. **Keep Functions Short**: Aim for functions under 20-30 lines
4. **Use Type Hints**: Specify parameter and return types (PHP 7+)
5. **Avoid Side Effects**: Functions should be predictable
6. **Document Complex Functions**: Use PHPDoc comments
7. **Return Early**: Use guard clauses to reduce nesting
8. **Default Parameters**: Place them at the end

### PHPDoc Example

```php
/**
 * Calculate the total price including tax
 *
 * @param float $price The base price
 * @param float $taxRate The tax rate as decimal (e.g., 0.08 for 8%)
 * @return float The total price including tax
 */
function calculateTotal(float $price, float $taxRate): float {
    return $price * (1 + $taxRate);
}
```

Functions are the building blocks of organized, reusable PHP code. Mastering them is essential for effective PHP development!