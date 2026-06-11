# Operators in PHP

An **operator** is a symbol that performs operations on variables and values. PHP has several types of operators.

---

## 1. Arithmetic Operators

Used for mathematical operations:

```php
<?php
$a = 10;
$b = 3;

echo $a + $b;  // Addition: 13
echo $a - $b;  // Subtraction: 7
echo $a * $b;  // Multiplication: 30
echo $a / $b;  // Division: 3.333...
echo $a % $b;  // Modulus (remainder): 1
echo $a ** $b; // Exponentiation (power): 1000
?>
```

| Operator | Name | Example |
|----------|------|---------|
| + | Addition | $a + $b |
| - | Subtraction | $a - $b |
| * | Multiplication | $a * $b |
| / | Division | $a / $b |
| % | Modulus | $a % $b |
| ** | Exponentiation | $a ** $b |

---

## 2. Assignment Operators

Used to assign values to variables:

```php
<?php
$x = 10;        // Simple assignment
$x += 5;        // $x = $x + 5; (now 15)
$x -= 3;        // $x = $x - 3; (now 12)
$x *= 2;        // $x = $x * 2; (now 24)
$x /= 4;        // $x = $x / 4; (now 6)
$x %= 4;        // $x = $x % 4; (now 2)
?>
```

| Operator | Example | Same As |
|----------|---------|---------|
| = | $x = 5 | $x = 5 |
| += | $x += 3 | $x = $x + 3 |
| -= | $x -= 3 | $x = $x - 3 |
| *= | $x *= 3 | $x = $x * 3 |
| /= | $x /= 3 | $x = $x / 3 |
| %= | $x %= 3 | $x = $x % 3 |
| .= | $x .= "y" | $x = $x . "y" |

---

## 3. Comparison Operators

Used to compare two values:

```php
<?php
$a = 5;
$b = "5";

var_dump($a == $b);   // Equal: true (same value)
var_dump($a === $b);  // Identical: false (different types)
var_dump($a != $b);   // Not equal: false
var_dump($a !== $b);  // Not identical: true
var_dump($a > 3);     // Greater than: true
var_dump($a < 10);    // Less than: true
var_dump($a >= 5);    // Greater than or equal: true
var_dump($a <= 5);    // Less than or equal: true
?>
```

| Operator | Name | Example |
|----------|------|---------|
| == | Equal | $a == $b |
| === | Identical | $a === $b |
| != | Not equal | $a != $b |
| !== | Not identical | $a !== $b |
| > | Greater than | $a > $b |
| < | Less than | $a < $b |
| >= | Greater than or equal | $a >= $b |
| <= | Less than or equal | $a <= $b |

**Important:** `==` checks value only, `===` checks value AND type!

---

## 4. Increment/Decrement Operators

Used to increase or decrease values:

```php
<?php
$x = 10;

echo ++$x;  // Pre-increment: 11 (increment first, then return)
echo $x++;  // Post-increment: 11 (return first, then increment)
echo $x;    // Now: 12

echo --$x;  // Pre-decrement: 11 (decrement first, then return)
echo $x--;  // Post-decrement: 11 (return first, then decrement)
echo $x;    // Now: 10
?>
```

| Operator | Name | Description |
|----------|------|-------------|
| ++$x | Pre-increment | Increments, then returns |
| $x++ | Post-increment | Returns, then increments |
| --$x | Pre-decrement | Decrements, then returns |
| $x-- | Post-decrement | Returns, then decrements |

---

## 5. Logical Operators

Used to combine conditional statements:

```php
<?php
$a = true;
$b = false;

var_dump($a && $b);  // AND: false
var_dump($a || $b);  // OR: true
var_dump(!$a);       // NOT: false
var_dump($a and $b); // AND: false
var_dump($a or $b);  // OR: true
var_dump($a xor $b); // XOR: true
?>
```

| Operator | Name | Example |
|----------|------|---------|
| && | And | $a && $b |
| \|\| | Or | $a \|\| $b |
| ! | Not | !$a |
| and | And | $a and $b |
| or | Or | $a or $b |
| xor | Xor | $a xor $b |

---

## 6. String Operators

Used for string operations:

```php
<?php
$txt1 = "Hello";
$txt2 = "World";

// Concatenation
echo $txt1 . " " . $txt2;  // Hello World

// Concatenation assignment
$txt1 .= " " . $txt2;
echo $txt1;  // Hello World
?>
```

| Operator | Name | Example |
|----------|------|---------|
| . | Concatenation | $a . $b |
| .= | Concatenation assignment | $a .= $b |

---

## 7. Array Operators

Used for array operations:

```php
<?php
$a = array("a" => "apple", "b" => "banana");
$b = array("c" => "cherry", "d" => "date");

$c = $a + $b;  // Union
var_dump($a == $b);   // Equality
var_dump($a === $b);  // Identity
var_dump($a != $b);   // Inequality
var_dump($a !== $b);  // Non-identity
?>
```

| Operator | Name | Example |
|----------|------|---------|
| + | Union | $a + $b |
| == | Equality | $a == $b |
| === | Identity | $a === $b |
| != | Inequality | $a != $b |
| !== | Non-identity | $a !== $b |

---

## 8. Conditional (Ternary) Operator

A shortcut for if-else:

```php
<?php
$age = 19;

// Long form
if ($age >= 18) {
    $status = "Adult";
} else {
    $status = "Minor";
}

// Short form (ternary)
$status = ($age >= 18) ? "Adult" : "Minor";
echo $status;  // Adult
?>
```

**Syntax:** `condition ? value_if_true : value_if_false`

---

## 9. Null Coalescing Operator (??)

Returns the first value if it exists, otherwise returns the second:

```php
<?php
$username = $_GET['user'] ?? 'Guest';
// If $_GET['user'] exists, use it; otherwise use 'Guest'

$name = null;
echo $name ?? "Default Name";  // Output: Default Name
?>
```

---

## 10. Spaceship Operator (<=>)

Returns -1, 0, or 1 for comparison:

```php
<?php
echo 1 <=> 2;  // -1 (first is less)
echo 2 <=> 2;  // 0 (equal)
echo 3 <=> 2;  // 1 (first is greater)
?>
```

---

## Practical Examples

### Example 1: Calculate Total Price
```php
<?php
$price = 500;
$quantity = 3;
$discount = 50;

$total = ($price * $quantity) - $discount;
echo "Total: " . $total . " BDT";  // Total: 1450 BDT
?>
```

### Example 2: Check Age
```php
<?php
$age = 19;
$canVote = ($age >= 18) ? "Yes" : "No";
echo "Can vote: " . $canVote;  // Can vote: Yes
?>
```

### Example 3: Build Counter
```php
<?php
$counter = 0;
echo "Start: " . $counter;     // 0
echo "After: " . ++$counter;   // 1
echo "After: " . $counter++;   // 1
echo "Final: " . $counter;     // 2
?>
```

---

## Operator Precedence

Operators are executed in a specific order (like math: multiplication before addition):

1. **()** - Parentheses (highest priority)
2. **++, --** - Increment/Decrement
3. **!, -** - Logical NOT, Negative
4. **\*, /, %** - Multiplication, Division, Modulus
5. **+, -** - Addition, Subtraction
6. **<, >, <=, >=** - Comparison
7. **==, !=, ===, !==** - Equality
8. **&&** - Logical AND
9. **||** - Logical OR
10. **=, +=, -=** - Assignment (lowest priority)

**Tip:** Use parentheses to make your code clear: `$result = ($a + $b) * $c;`

These operators are the building blocks of PHP programming!