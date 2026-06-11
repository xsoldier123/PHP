# Concatenation in PHP

Concatenation means **joining strings together**. In PHP, you use the **dot (.) operator** to concatenate strings.

## Basic Concatenation

```php
<?php
$firstName = "Ebrat";
$lastName = "Hoseen";

// Using dot (.) operator
$fullName = $firstName . " " . $lastName;
echo $fullName; // Output: Ebrat Hoseen
?>
```

## Concatenation Methods

### 1. Using the Dot (.) Operator
```php
<?php
$text1 = "Hello";
$text2 = "World";
$result = $text1 . " " . $text2;
echo $result; // Output: Hello World
?>
```

### 2. Using the Dot Equals (.=) Operator
This **appends** to an existing variable:
```php
<?php
$message = "Hello";
$message .= " World";
$message .= "!";
echo $message; // Output: Hello World!
?>
```

### 3. Double Quotes (Variable Interpolation)
PHP automatically parses variables inside double quotes:
```php
<?php
$name = "Ebrat";
$age = 19;

echo "My name is $name and I am $age years old.";
// Output: My name is Ebrat and I am 19 years old.
?>
```

### 4. Single Quotes vs Double Quotes
```php
<?php
$name = "Ebrat";

// Double quotes - variables are parsed
echo "Hello $name"; // Output: Hello Ebrat

// Single quotes - variables are NOT parsed
echo 'Hello $name'; // Output: Hello $name
?>
```

## Practical Examples

### Example 1: Building HTML
```php
<?php
$title = "Web Developer";
$description = "I build websites";

$html = "<h1>" . $title . "</h1>";
$html .= "<p>" . $description . "</p>";
echo $html;
?>
```

### Example 2: Creating URLs
```php
<?php
$baseUrl = "https://example.com";
$page = "portfolio";
$userId = 123;

$fullUrl = $baseUrl . "/" . $page . "?id=" . $userId;
echo $fullUrl;
// Output: https://example.com/portfolio?id=123
?>
```

### Example 3: Multiple Variables
```php
<?php
$name = "Ebrat Hoseen";
$skill = "Web Developer";
$experience = "2 years";

// Method 1: Dot operator
$intro = "Hi, I'm " . $name . ", a " . $skill . " with " . $experience . " experience.";

// Method 2: Double quotes (cleaner)
$intro2 = "Hi, I'm $name, a $skill with $experience experience.";

echo $intro2;
?>
```

### Example 4: Concatenating Numbers and Strings
```php
<?php
$price = 500;
$currency = "BDT";

$total = "Total: " . $price . " " . $currency;
echo $total; // Output: Total: 500 BDT
?>
```

## Common Mistakes to Avoid

```php
<?php
// Wrong: Using + instead of .
$result = "Hello" + "World"; // This doesn't work like JavaScript!

// Correct: Use dot
$result = "Hello" . "World";

// Wrong: Forgetting spaces
$name = "Ebrat";
echo "Hello" . $name; // Output: HelloEbrat (no space)

// Correct: Add spaces
echo "Hello " . $name; // Output: Hello Ebrat
?>
```

## Quick Comparison: PHP vs JavaScript

```php
// PHP uses dot (.)
$result = "Hello" . "World";

// JavaScript uses plus (+)
let result = "Hello" + "World";
```

## Which Method to Use?

- **Dot (.)** - When concatenating few variables or mixing different types
- **Dot Equals (.=)** - When building strings in loops or adding to existing strings
- **Double quotes** - When you have variables inside text (cleaner and easier to read)
- **Single quotes** - When you have plain text with no variables (slightly faster)

The dot operator is PHP's way of joining strings - just remember it's different from JavaScript's plus sign!