# Assignment Operators in PHP

Assignment operators are used to **assign values to variables**. The basic assignment operator is `=`, but PHP has many shorthand assignment operators that make code shorter and cleaner.

---

## List of Assignment Operators

| Operator | Name | Example | Same As | Description |
|----------|------|---------|---------|-------------|
| = | Assignment | $x = 5 | $x = 5 | Assigns value |
| += | Addition assignment | $x += 5 | $x = $x + 5 | Add and assign |
| -= | Subtraction assignment | $x -= 5 | $x = $x - 5 | Subtract and assign |
| *= | Multiplication assignment | $x *= 5 | $x = $x * 5 | Multiply and assign |
| /= | Division assignment | $x /= 5 | $x = $x / 5 | Divide and assign |
| %= | Modulus assignment | $x %= 5 | $x = $x % 5 | Modulus and assign |
| **= | Exponentiation assignment | $x **= 3 | $x = $x ** 3 | Power and assign |
| .= | Concatenation assignment | $x .= "y" | $x = $x . "y" | Concatenate and assign |

---

## 1. Basic Assignment (=)

The simplest operator - assigns a value to a variable:

```php
<?php
$name = "Ebrat Hoseen";
$age = 19;
$salary = 50000;
$isStudent = true;

echo $name;    // Output: Ebrat Hoseen
echo $age;     // Output: 19
?>
```

### Multiple Assignments
```php
<?php
// Assign same value to multiple variables
$a = $b = $c = 10;
echo $a;  // 10
echo $b;  // 10
echo $c;  // 10
?>
```

### Assign by Reference
```php
<?php
$original = 100;
$copy = &$original;  // Reference assignment

$copy = 200;
echo $original;  // 200 (changed because of reference)
?>
```

---

## 2. Addition Assignment (+=)

Adds a value to the variable and assigns the result:

```php
<?php
$x = 10;
$x += 5;  // Same as: $x = $x + 5
echo $x;  // Output: 15

// More examples
$balance = 1000;
$balance += 500;  // Add 500 to balance
echo $balance;    // 1500
?>
```

**Practical Example - Shopping Cart:**
```php
<?php
$totalPrice = 500;
echo "Initial total: " . $totalPrice . " BDT<br>";

$totalPrice += 300;  // Add item worth 300
echo "After adding item 1: " . $totalPrice . " BDT<br>";

$totalPrice += 150;  // Add item worth 150
echo "After adding item 2: " . $totalPrice . " BDT<br>";

// Output:
// Initial total: 500 BDT
// After adding item 1: 800 BDT
// After adding item 2: 950 BDT
?>
```

---

## 3. Subtraction Assignment (-=)

Subtracts a value from the variable and assigns the result:

```php
<?php
$x = 10;
$x -= 3;  // Same as: $x = $x - 3
echo $x;  // Output: 7

// More examples
$stock = 100;
$stock -= 15;  // Sold 15 items
echo $stock;   // 85
?>
```

**Practical Example - Bank Account:**
```php
<?php
$balance = 5000;
echo "Initial balance: " . $balance . " BDT<br>";

$balance -= 1500;  // Withdraw 1500
echo "After withdrawal: " . $balance . " BDT<br>";

$balance -= 500;   // Withdraw 500
echo "After second withdrawal: " . $balance . " BDT<br>";

// Output:
// Initial balance: 5000 BDT
// After withdrawal: 3500 BDT
// After second withdrawal: 3000 BDT
?>
```

---

## 4. Multiplication Assignment (*=)

Multiplies the variable by a value and assigns the result:

```php
<?php
$x = 10;
$x *= 3;  // Same as: $x = $x * 3
echo $x;  // Output: 30

// More examples
$price = 100;
$price *= 2;  // Double the price
echo $price;  // 200
?>
```

**Practical Example - Interest Calculation:**
```php
<?php
$amount = 10000;
$interestRate = 1.05;  // 5% interest

echo "Initial amount: " . $amount . " BDT<br>";

$amount *= $interestRate;  // Apply interest
echo "After 1 year: " . $amount . " BDT<br>";

$amount *= $interestRate;  // Apply interest again
echo "After 2 years: " . $amount . " BDT<br>";

// Output:
// Initial amount: 10000 BDT
// After 1 year: 10500 BDT
// After 2 years: 11025 BDT
?>
```

---

## 5. Division Assignment (/=)

Divides the variable by a value and assigns the result:

```php
<?php
$x = 20;
$x /= 4;  // Same as: $x = $x / 4
echo $x;  // Output: 5

// More examples
$total = 1000;
$total /= 2;  // Half the amount
echo $total;  // 500
?>
```

**Practical Example - Split Bill:**
```php
<?php
$totalBill = 2400;
$numberOfPeople = 4;

echo "Total bill: " . $totalBill . " BDT<br>";

$totalBill /= $numberOfPeople;  // Divide equally
echo "Each person pays: " . $totalBill . " BDT<br>";

// Output:
// Total bill: 2400 BDT
// Each person pays: 600 BDT
?>
```

---

## 6. Modulus Assignment (%=)

Gets the remainder and assigns it:

```php
<?php
$x = 17;
$x %= 5;  // Same as: $x = $x % 5
echo $x;  // Output: 2 (17 divided by 5 = 3 remainder 2)

// More examples
$number = 28;
$number %= 10;  // Get last digit
echo $number;   // 8
?>
```

**Practical Example - Cycle Through Values:**
```php
<?php
$position = 0;

for ($i = 0; $i < 10; $i++) {
    echo "Position: " . $position . "<br>";
    $position++;
    $position %= 3;  // Keep cycling 0, 1, 2
}

// Output:
// Position: 0
// Position: 1
// Position: 2
// Position: 0
// Position: 1
// Position: 2
// ...
?>
```

---

## 7. Exponentiation Assignment (**=)

Raises to a power and assigns:

```php
<?php
$x = 2;
$x **= 3;  // Same as: $x = $x ** 3
echo $x;   // Output: 8 (2^3 = 2*2*2)

// More examples
$base = 5;
$base **= 2;  // Square the number
echo $base;   // 25
?>
```

**Practical Example - Exponential Growth:**
```php
<?php
$bacteria = 100;
$generations = 3;

echo "Initial bacteria: " . $bacteria . "<br>";

for ($i = 1; $i <= $generations; $i++) {
    $bacteria *= 2;  // Double each generation
    echo "Generation " . $i . ": " . $bacteria . "<br>";
}

// Output:
// Initial bacteria: 100
// Generation 1: 200
// Generation 2: 400
// Generation 3: 800
?>
```

---

## 8. Concatenation Assignment (.=)

Appends a string to the variable:

```php
<?php
$message = "Hello";
$message .= " World";  // Same as: $message = $message . " World"
echo $message;  // Output: Hello World

// More examples
$name = "Ebrat";
$name .= " Hoseen";
echo $name;  // Ebrat Hoseen
?>
```

**Practical Example - Building HTML:**
```php
<?php
$html = "<html>";
$html .= "<head>";
$html .= "<title>My Page</title>";
$html .= "</head>";
$html .= "<body>";
$html .= "<h1>Welcome</h1>";
$html .= "</body>";
$html .= "</html>";

echo $html;
?>
```

**Practical Example - Building a Message:**
```php
<?php
$greeting = "Hello";
echo $greeting . "<br>";  // Hello

$greeting .= ", Ebrat";
echo $greeting . "<br>";  // Hello, Ebrat

$greeting .= "! Welcome to PHP.";
echo $greeting . "<br>";  // Hello, Ebrat! Welcome to PHP.
?>
```

---

## Complete Practical Examples

### Example 1: Score Tracker
```php
<?php
$totalScore = 0;

echo "Initial score: " . $totalScore . "<br>";

$totalScore += 10;  // Level 1 completed
echo "After level 1: " . $totalScore . "<br>";

$totalScore += 20;  // Level 2 completed
echo "After level 2: " . $totalScore . "<br>";

$totalScore += 30;  // Level 3 completed
echo "After level 3: " . $totalScore . "<br>";

$totalScore -= 5;   // Penalty
echo "After penalty: " . $totalScore . "<br>";

// Output:
// Initial score: 0
// After level 1: 10
// After level 2: 30
// After level 3: 60
// After penalty: 55
?>
```

### Example 2: E-commerce Cart
```php
<?php
$cartTotal = 0;

echo "Cart Total: " . $cartTotal . " BDT<br><br>";

// Add items
$cartTotal += 500;
echo "Added item (500 BDT). Total: " . $cartTotal . " BDT<br>";

$cartTotal += 300;
echo "Added item (300 BDT). Total: " . $cartTotal . " BDT<br>";

$cartTotal += 150;
echo "Added item (150 BDT). Total: " . $cartTotal . " BDT<br><br>";

// Apply discount
$discount = 100;
$cartTotal -= $discount;
echo "Applied discount (100 BDT). Total: " . $cartTotal . " BDT<br>";

// Output:
// Cart Total: 0 BDT
//
// Added item (500 BDT). Total: 500 BDT
// Added item (300 BDT). Total: 800 BDT
// Added item (150 BDT). Total: 950 BDT
//
// Applied discount (100 BDT). Total: 850 BDT
?>
```

### Example 3: Inventory Management
```php
<?php
$stock = 100;

echo "Initial stock: " . $stock . " units<br>";

$stock -= 15;  // Sold 15
echo "After sale 1: " . $stock . " units<br>";

$stock -= 20;  // Sold 20
echo "After sale 2: " . $stock . " units<br>";

$stock += 50;  // Restocked 50
echo "After restock: " . $stock . " units<br>";

// Output:
// Initial stock: 100 units
// After sale 1: 85 units
// After sale 2: 65 units
// After restock: 115 units
?>
```

### Example 4: Building a Report
```php
<?php
$report = "";

$report .= "===== Sales Report =====\n";
$report .= "Date: October 29, 2025\n";
$report .= "Salesperson: Ebrat Hoseen\n";
$report .= "------------------------\n";
$report .= "Total Sales: 10,000 BDT\n";
$report .= "Commission: 1,000 BDT\n";
$report .= "========================\n";

echo nl2br($report);  // nl2br converts \n to <br>
?>
```

### Example 5: Points System
```php
<?php
$points = 0;

// User actions
$points += 10;  // Signed up
$points += 50;  // Completed profile
$points += 25;  // First purchase
$points *= 2;   // Double points promotion!
$points -= 30;  // Redeemed reward

echo "Final points: " . $points;
// Output: Final points: 140
// Calculation: (10 + 50 + 25) * 2 - 30 = 170 - 30 = 140
?>
```

### Example 6: Temperature Converter with Updates
```php
<?php
$celsius = 25;
echo "Temperature: " . $celsius . "°C<br>";

// Convert to Fahrenheit formula: (C * 9/5) + 32
$celsius *= 9;
$celsius /= 5;
$celsius += 32;

echo "Temperature: " . $celsius . "°F<br>";
// Output: Temperature: 77°F
?>
```

### Example 7: Counter Application
```php
<?php
$counter = 0;

for ($i = 0; $i < 5; $i++) {
    $counter += 1;
    echo "Count: " . $counter . "<br>";
}

// Output:
// Count: 1
// Count: 2
// Count: 3
// Count: 4
// Count: 5
?>
```

### Example 8: Building a URL
```php
<?php
$url = "https://example.com";
$url .= "/api";
$url .= "/v1";
$url .= "/users";
$url .= "?id=123";
$url .= "&name=ebrat";

echo $url;
// Output: https://example.com/api/v1/users?id=123&name=ebrat
?>
```

---

## Combining Multiple Assignment Operators

```php
<?php
$value = 100;

$value += 50;   // 150
$value -= 20;   // 130
$value *= 2;    // 260
$value /= 4;    // 65
$value %= 10;   // 5

echo "Final value: " . $value;
// Output: Final value: 5
?>
```

---

## Assignment vs Comparison

**⚠️ Common Mistake: Using = instead of ==**

```php
<?php
$age = 18;

// ❌ WRONG - This is assignment, not comparison!
if ($age = 25) {  // Assigns 25 to $age, always true!
    echo "This always runs!";
}
echo $age;  // 25 (changed!)

// ✅ CORRECT - This is comparison
$age = 18;
if ($age == 25) {  // Compares $age with 25
    echo "This won't run";
}
echo $age;  // 18 (unchanged)
?>
```

---

## Benefits of Assignment Operators

✅ **Shorter code:** `$x += 5` instead of `$x = $x + 5`  
✅ **More readable:** Clear what operation is being performed  
✅ **Less error-prone:** Don't have to type variable name twice  
✅ **Efficient:** Slightly faster in some cases  

---

## Comparison Table

| Long Form | Short Form |
|-----------|------------|
| $x = $x + 5 | $x += 5 |
| $x = $x - 3 | $x -= 3 |
| $x = $x * 2 | $x *= 2 |
| $x = $x / 4 | $x /= 4 |
| $x = $x % 3 | $x %= 3 |
| $x = $x ** 2 | $x **= 2 |
| $x = $x . "y" | $x .= "y" |

---

## Key Points to Remember

✅ `=` assigns a value to a variable  
✅ Compound operators (`+=`, `-=`, etc.) modify and assign in one step  
✅ `.=` is for strings (concatenation), not numbers  
✅ Assignment operators can be chained: `$a = $b = $c = 10`  
✅ Don't confuse `=` (assignment) with `==` (comparison)  
✅ These operators make code cleaner and more efficient  

Assignment operators are fundamental in PHP - you'll use them constantly to update variables, build strings, manage counters, and much more!