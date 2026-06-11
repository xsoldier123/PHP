# User-Defined Functions in PHP - Full Details

User-defined functions in PHP are custom functions that developers create to perform specific tasks. They help organize code, promote reusability, and make programs more maintainable.

## Basic Syntax

```php
function functionName($parameter1, $parameter2, ...) {
    // Function body
    // Code to execute
    return $value; // Optional
}
```

## Key Concepts

### 1. **Function Declaration**

```php
function greet($name) {
    return "Hello, " . $name . "!";
}

echo greet("Alice"); // Output: Hello, Alice!
```

### 2. **Parameters**

**Required Parameters:**
```php
function add($a, $b) {
    return $a + $b;
}
```

**Default Parameters:**
```php
function greet($name = "Guest") {
    return "Hello, " . $name;
}

echo greet();        // Output: Hello, Guest
echo greet("John");  // Output: Hello, John
```

**Type Declarations (Type Hints):**
```php
function multiply(int $a, int $b): int {
    return $a * $b;
}
```

**Variable Number of Arguments:**
```php
function sum(...$numbers) {
    return array_sum($numbers);
}

echo sum(1, 2, 3, 4); // Output: 10
```

### 3. **Return Values**

```php
// Single return value
function square($n) {
    return $n * $n;
}

// Multiple return values (using array)
function getCoordinates() {
    return [10, 20];
}

list($x, $y) = getCoordinates();

// No return value (void)
function printMessage($msg) {
    echo $msg;
}
```

### 4. **Return Type Declarations**

```php
function divide(float $a, float $b): float {
    return $a / $b;
}

function getName(): string {
    return "John Doe";
}

function process(): void {
    // Does not return anything
    echo "Processing...";
}
```

### 5. **Scope**

**Local Scope:**
```php
function test() {
    $localVar = "I'm local";
    echo $localVar;
}
```

**Global Scope:**
```php
$globalVar = "I'm global";

function useGlobal() {
    global $globalVar;
    echo $globalVar;
}
```

**Static Variables:**
```php
function counter() {
    static $count = 0;
    $count++;
    return $count;
}

echo counter(); // 1
echo counter(); // 2
echo counter(); // 3
```

### 6. **Pass by Reference**

```php
function addFive(&$num) {
    $num += 5;
}

$value = 10;
addFive($value);
echo $value; // Output: 15
```

### 7. **Anonymous Functions (Closures)**

```php
$greet = function($name) {
    return "Hello, " . $name;
};

echo $greet("Alice"); // Output: Hello, Alice

// With use keyword
$message = "Hi";
$greet = function($name) use ($message) {
    return "$message, $name";
};
```

### 8. **Arrow Functions (PHP 7.4+)**

```php
$multiply = fn($a, $b) => $a * $b;
echo $multiply(5, 3); // Output: 15

// Automatically captures variables from parent scope
$factor = 10;
$scale = fn($n) => $n * $factor;
```

### 9. **Recursive Functions**

```php
function factorial($n) {
    if ($n <= 1) {
        return 1;
    }
    return $n * factorial($n - 1);
}

echo factorial(5); // Output: 120
```

### 10. **Variable Functions**

```php
function sayHello() {
    return "Hello!";
}

$funcName = "sayHello";
echo $funcName(); // Output: Hello!
```

## Advanced Features

### Nullable Types (PHP 7.1+)
```php
function findUser(?int $id): ?string {
    if ($id === null) {
        return null;
    }
    return "User $id";
}
```

### Union Types (PHP 8.0+)
```php
function process(int|float $number): int|float {
    return $number * 2;
}
```

### Named Arguments (PHP 8.0+)
```php
function createUser($name, $email, $age) {
    // Function body
}

createUser(
    email: "user@example.com",
    name: "John",
    age: 30
);
```

### Variadic Functions with Type Declarations
```php
function sum(int ...$numbers): int {
    return array_sum($numbers);
}
```

## Best Practices

1. **Use descriptive names** - Functions should clearly indicate what they do
2. **Keep functions focused** - Each function should do one thing well
3. **Use type declarations** - Helps catch errors and improves code clarity
4. **Document your functions** - Use PHPDoc comments
5. **Return early** - Avoid deep nesting by returning early when possible
6. **Avoid side effects** - Functions should be predictable

```php
/**
 * Calculate the area of a rectangle
 * 
 * @param float $width The width of the rectangle
 * @param float $height The height of the rectangle
 * @return float The calculated area
 */
function calculateArea(float $width, float $height): float {
    return $width * $height;
}
```

## Common Patterns

### Callback Functions
```php
$numbers = [1, 2, 3, 4, 5];
$squared = array_map(function($n) {
    return $n * $n;
}, $numbers);
```

### Factory Functions
```php
function createUser($name, $email) {
    return [
        'name' => $name,
        'email' => $email,
        'created_at' => date('Y-m-d H:i:s')
    ];
}
```

User-defined functions are fundamental to PHP programming, allowing you to write clean, modular, and maintainable code. They support modern PHP features like type declarations, nullable types, and arrow functions, making PHP a robust language for web development.