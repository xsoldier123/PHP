# Comparison Operators in PHP

Comparison operators are used to **compare two values**. They always return a **boolean** result: `true` or `false`.

---

## List of Comparison Operators

| Operator | Name | Description | Example | Result |
|----------|------|-------------|---------|--------|
| == | Equal | Checks if values are equal | 5 == "5" | true |
| === | Identical | Checks if values AND types are equal | 5 === "5" | false |
| != | Not equal | Checks if values are not equal | 5 != 3 | true |
| <> | Not equal | Same as != | 5 <> 3 | true |
| !== | Not identical | Checks if values OR types are not equal | 5 !== "5" | true |
| > | Greater than | Checks if left is greater | 10 > 5 | true |
| < | Less than | Checks if left is less | 5 < 10 | true |
| >= | Greater than or equal | Checks if left is greater or equal | 10 >= 10 | true |
| <= | Less than or equal | Checks if left is less or equal | 5 <= 10 | true |
| <=> | Spaceship | Returns -1, 0, or 1 | 5 <=> 10 | -1 |

---

## 1. Equal (==)

Checks if two values are equal (ignores data type):

```php
<?php
$a = 5;
$b = "5";
$c = 10;

var_dump($a == $b);  // true (5 equals "5" in value)
var_dump($a == $c);  // false (5 does not equal 10)

// More examples
var_dump(10 == 10);      // true
var_dump(10 == "10");    // true (string converted to number)
var_dump(0 == false);    // true
var_dump(1 == true);     // true
var_dump("" == false);   // true
?>
```

---

## 2. Identical (===)

Checks if two values are equal **AND** have the same data type:

```php
<?php
$a = 5;
$b = "5";
$c = 5;

var_dump($a === $b);  // false (different types: int vs string)
var_dump($a === $c);  // true (same value and type)

// More examples
var_dump(10 === 10);      // true
var_dump(10 === "10");    // false (int vs string)
var_dump(0 === false);    // false (int vs boolean)
var_dump(1 === true);     // false (int vs boolean)
var_dump(true === true);  // true
?>
```

**This is VERY IMPORTANT!** Always use `===` when you want strict comparison.

---

## 3. Not Equal (!=) and (<>)

Checks if two values are NOT equal:

```php
<?php
$a = 5;
$b = 10;
$c = "5";

var_dump($a != $b);   // true (5 is not equal to 10)
var_dump($a != $c);   // false (5 equals "5" in value)
var_dump($a <> $b);   // true (same as !=)

// Practical example
$password = "12345";
$confirmPassword = "54321";

if ($password != $confirmPassword) {
    echo "Passwords do not match!";
}
?>
```

---

## 4. Not Identical (!==)

Checks if two values are NOT equal OR have different types:

```php
<?php
$a = 5;
$b = "5";
$c = 5;

var_dump($a !== $b);  // true (different types)
var_dump($a !== $c);  // false (same value and type)

// More examples
var_dump(10 !== "10");    // true (different types)
var_dump(0 !== false);    // true (different types)
var_dump(5 !== 5);        // false (same value and type)
?>
```

---

## 5. Greater Than (>)

Checks if left value is greater than right value:

```php
<?php
$a = 10;
$b = 5;

var_dump($a > $b);   // true (10 is greater than 5)
var_dump($b > $a);   // false (5 is not greater than 10)
var_dump(10 > 10);   // false (not greater, they're equal)

// Practical example
$age = 19;
if ($age > 18) {
    echo "You are an adult";  // This will execute
}
?>
```

---

## 6. Less Than (<)

Checks if left value is less than right value:

```php
<?php
$a = 5;
$b = 10;

var_dump($a < $b);   // true (5 is less than 10)
var_dump($b < $a);   // false (10 is not less than 5)
var_dump(5 < 5);     // false (not less, they're equal)

// Practical example
$stock = 3;
if ($stock < 5) {
    echo "Low stock alert!";  // This will execute
}
?>
```

---

## 7. Greater Than or Equal To (>=)

Checks if left value is greater than OR equal to right value:

```php
<?php
$a = 10;
$b = 5;
$c = 10;

var_dump($a >= $b);   // true (10 is greater than 5)
var_dump($a >= $c);   // true (10 is equal to 10)
var_dump($b >= $a);   // false (5 is not >= 10)

// Practical example
$marks = 40;
$passingMarks = 40;

if ($marks >= $passingMarks) {
    echo "Passed!";  // This will execute
}
?>
```

---

## 8. Less Than or Equal To (<=)

Checks if left value is less than OR equal to right value:

```php
<?php
$a = 5;
$b = 10;
$c = 5;

var_dump($a <= $b);   // true (5 is less than 10)
var_dump($a <= $c);   // true (5 is equal to 5)
var_dump($b <= $a);   // false (10 is not <= 5)

// Practical example
$price = 500;
$budget = 1000;

if ($price <= $budget) {
    echo "You can afford this!";  // This will execute
}
?>
```

---

## 9. Spaceship Operator (<=>)

Returns:
- **-1** if left is less than right
- **0** if both are equal
- **1** if left is greater than right

```php
<?php
echo 5 <=> 10;   // -1 (5 is less than 10)
echo 10 <=> 10;  // 0 (equal)
echo 15 <=> 10;  // 1 (15 is greater than 10)

// Practical example - sorting
$items = [5, 2, 8, 1, 9];
usort($items, function($a, $b) {
    return $a <=> $b;  // Sort ascending
});
print_r($items);  // [1, 2, 5, 8, 9]
?>
```

---

## == vs === (Very Important!)

This is one of the most important concepts in PHP:

```php
<?php
// Using == (loose comparison)
var_dump(5 == "5");       // true
var_dump(0 == false);     // true
var_dump("" == 0);        // true
var_dump(null == false);  // true
var_dump("10" == 10);     // true

// Using === (strict comparison)
var_dump(5 === "5");      // false (int vs string)
var_dump(0 === false);    // false (int vs boolean)
var_dump("" === 0);       // false (string vs int)
var_dump(null === false); // false (null vs boolean)
var_dump("10" === 10);    // false (string vs int)
?>
```

**Best Practice:** Always use `===` and `!==` unless you specifically need type coercion.

---

## Practical Examples

### Example 1: Age Verification
```php
<?php
$age = 19;

if ($age >= 18) {
    echo "You can vote";
} elseif ($age >= 16) {
    echo "You can get a driving learner's permit";
} else {
    echo "You are a minor";
}
// Output: You can vote
?>
```

### Example 2: Grade Calculator
```php
<?php
$marks = 85;

if ($marks >= 80) {
    $grade = "A+";
} elseif ($marks >= 70) {
    $grade = "A";
} elseif ($marks >= 60) {
    $grade = "B";
} elseif ($marks >= 50) {
    $grade = "C";
} elseif ($marks >= 40) {
    $grade = "D";
} else {
    $grade = "F";
}

echo "Your grade is: " . $grade;
// Output: Your grade is: A+
?>
```

### Example 3: Login System
```php
<?php
$username = "ebrat";
$password = "12345";

$inputUsername = "ebrat";
$inputPassword = "12345";

if ($username === $inputUsername && $password === $inputPassword) {
    echo "Login successful!";
} else {
    echo "Invalid credentials!";
}
// Output: Login successful!
?>
```

### Example 4: Price Comparison
```php
<?php
$productPrice = 500;
$budget = 1000;
$discount = 100;

$finalPrice = $productPrice - $discount;

if ($finalPrice <= $budget) {
    $savings = $budget - $finalPrice;
    echo "You can buy this! You'll save: " . $savings . " BDT";
} else {
    $needed = $finalPrice - $budget;
    echo "You need " . $needed . " BDT more";
}
// Output: You can buy this! You'll save: 600 BDT
?>
```

### Example 5: Form Validation
```php
<?php
$email = "ebrat@example.com";
$confirmEmail = "ebrat@example.com";

if ($email === $confirmEmail) {
    echo "Email confirmed!";
} else {
    echo "Emails do not match!";
}
// Output: Email confirmed!
?>
```

### Example 6: Stock Check
```php
<?php
$availableStock = 5;
$orderQuantity = 3;

if ($orderQuantity <= $availableStock) {
    echo "Order can be fulfilled";
} else {
    $shortage = $orderQuantity - $availableStock;
    echo "Not enough stock. Short by: " . $shortage . " units";
}
// Output: Order can be fulfilled
?>
```

### Example 7: Number Comparison
```php
<?php
$num1 = 15;
$num2 = 25;

if ($num1 > $num2) {
    echo $num1 . " is greater";
} elseif ($num1 < $num2) {
    echo $num2 . " is greater";
} else {
    echo "Both are equal";
}
// Output: 25 is greater
?>
```

### Example 8: Temperature Warning
```php
<?php
$temperature = 38;

if ($temperature > 37.5) {
    echo "You have a fever!";
} elseif ($temperature >= 36 && $temperature <= 37.5) {
    echo "Normal temperature";
} else {
    echo "Temperature is too low";
}
// Output: You have a fever!
?>
```

---

## Comparing Strings

PHP can also compare strings alphabetically:

```php
<?php
var_dump("apple" < "banana");   // true (a comes before b)
var_dump("zebra" > "apple");    // true (z comes after a)
var_dump("Apple" == "apple");   // false (case-sensitive)

// Practical example
$name1 = "Ahmed";
$name2 = "Zainab";

if ($name1 < $name2) {
    echo $name1 . " comes first alphabetically";
}
// Output: Ahmed comes first alphabetically
?>
```

---

## Common Mistakes to Avoid

### ❌ Wrong: Using = instead of ==
```php
<?php
$age = 18;

// Wrong - this assigns 18 to $age, doesn't compare
if ($age = 18) {  // Always true!
    echo "Adult";
}

// Correct
if ($age == 18) {
    echo "Adult";
}
?>
```

### ❌ Wrong: Using == when you need ===
```php
<?php
$userInput = "0";

// Wrong - might give unexpected results
if ($userInput == false) {  // true (unexpected!)
    echo "No input";
}

// Correct - strict comparison
if ($userInput === "") {
    echo "No input";
}
?>
```

---

## Summary Table

| Comparison | == | === |
|------------|-------|--------|
| 5 == "5" | ✅ true | ❌ false |
| 5 == 5 | ✅ true | ✅ true |
| 0 == false | ✅ true | ❌ false |
| "" == false | ✅ true | ❌ false |
| null == false | ✅ true | ❌ false |

---

## Key Points to Remember

✅ Use `===` and `!==` for strict comparison (recommended)  
✅ Use `==` and `!=` only when you want type coercion  
✅ Comparison operators always return `true` or `false`  
✅ String comparisons are case-sensitive  
✅ Be careful with `=` (assignment) vs `==` (comparison)  
✅ The spaceship operator `<=>` is useful for sorting  

These comparison operators are essential for decision-making in PHP - you'll use them in every `if`, `while`, and conditional statement!