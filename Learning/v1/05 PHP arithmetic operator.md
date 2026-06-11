# Arithmetic Operators in PHP

Arithmetic operators are used to perform **mathematical calculations** on numbers.

---

## List of Arithmetic Operators

| Operator | Name | Description | Example | Result |
|----------|------|-------------|---------|--------|
| + | Addition | Adds two values | 10 + 5 | 15 |
| - | Subtraction | Subtracts second from first | 10 - 5 | 5 |
| * | Multiplication | Multiplies two values | 10 * 5 | 50 |
| / | Division | Divides first by second | 10 / 5 | 2 |
| % | Modulus | Returns division remainder | 10 % 3 | 1 |
| ** | Exponentiation | Raises to power | 2 ** 3 | 8 |

---

## 1. Addition (+)

Adds two numbers together:

```php
<?php
$a = 10;
$b = 5;
$sum = $a + $b;
echo $sum;  // Output: 15

// Practical example
$price1 = 500;
$price2 = 300;
$total = $price1 + $price2;
echo "Total: " . $total . " BDT";  // Total: 800 BDT
?>
```

---

## 2. Subtraction (-)

Subtracts one number from another:

```php
<?php
$a = 10;
$b = 5;
$difference = $a - $b;
echo $difference;  // Output: 5

// Practical example
$balance = 1000;
$spent = 350;
$remaining = $balance - $spent;
echo "Remaining: " . $remaining . " BDT";  // Remaining: 650 BDT
?>
```

---

## 3. Multiplication (*)

Multiplies two numbers:

```php
<?php
$a = 10;
$b = 5;
$product = $a * $b;
echo $product;  // Output: 50

// Practical example
$pricePerItem = 250;
$quantity = 4;
$totalCost = $pricePerItem * $quantity;
echo "Total Cost: " . $totalCost . " BDT";  // Total Cost: 1000 BDT
?>
```

---

## 4. Division (/)

Divides one number by another:

```php
<?php
$a = 10;
$b = 5;
$quotient = $a / $b;
echo $quotient;  // Output: 2

// Returns float if not evenly divisible
$x = 10;
$y = 3;
echo $x / $y;  // Output: 3.3333333333333

// Practical example
$totalAmount = 1000;
$numberOfPeople = 4;
$perPerson = $totalAmount / $numberOfPeople;
echo "Per person: " . $perPerson . " BDT";  // Per person: 250 BDT
?>
```

**Important:** Division by zero will cause an error!
```php
<?php
// This will cause an error
// $result = 10 / 0;  // Fatal error!
?>
```

---

## 5. Modulus (%)

Returns the **remainder** after division:

```php
<?php
$a = 10;
$b = 3;
$remainder = $a % $b;
echo $remainder;  // Output: 1 (because 10 ÷ 3 = 3 remainder 1)

// More examples
echo 15 % 4;  // Output: 3 (15 ÷ 4 = 3 remainder 3)
echo 20 % 5;  // Output: 0 (20 ÷ 5 = 4 remainder 0)
echo 7 % 2;   // Output: 1 (odd number)
?>
```

**Practical Uses:**

### Check if number is even or odd:
```php
<?php
$number = 19;
if ($number % 2 == 0) {
    echo "Even number";
} else {
    echo "Odd number";  // Output: Odd number
}
?>
```

### Get last digit of a number:
```php
<?php
$number = 12345;
$lastDigit = $number % 10;
echo $lastDigit;  // Output: 5
?>
```

### Cycle through values:
```php
<?php
// Useful for rotating through items (like slideshow)
for ($i = 0; $i < 10; $i++) {
    $position = $i % 3;  // Will cycle: 0, 1, 2, 0, 1, 2...
    echo $position . " ";
}
// Output: 0 1 2 0 1 2 0 1 2 0
?>
```

---

## 6. Exponentiation (**)

Raises a number to the power of another:

```php
<?php
$base = 2;
$exponent = 3;
$result = $base ** $exponent;
echo $result;  // Output: 8 (2 × 2 × 2)

// More examples
echo 5 ** 2;   // Output: 25 (5 × 5)
echo 10 ** 3;  // Output: 1000 (10 × 10 × 10)
echo 3 ** 4;   // Output: 81 (3 × 3 × 3 × 3)
?>
```

**Practical example - Calculate compound interest:**
```php
<?php
$principal = 10000;
$rate = 0.05;  // 5%
$years = 3;
$amount = $principal * (1 + $rate) ** $years;
echo "Amount after " . $years . " years: " . $amount . " BDT";
// Output: Amount after 3 years: 11576.25 BDT
?>
```

---

## Complete Practical Examples

### Example 1: Shopping Cart Calculator
```php
<?php
$item1Price = 500;
$item1Qty = 2;

$item2Price = 300;
$item2Qty = 3;

$item1Total = $item1Price * $item1Qty;  // 1000
$item2Total = $item2Price * $item2Qty;  // 900

$subtotal = $item1Total + $item2Total;  // 1900
$discount = 100;
$finalTotal = $subtotal - $discount;    // 1800

echo "Subtotal: " . $subtotal . " BDT<br>";
echo "Discount: " . $discount . " BDT<br>";
echo "Final Total: " . $finalTotal . " BDT";
?>
```

### Example 2: Calculate Average
```php
<?php
$mark1 = 85;
$mark2 = 90;
$mark3 = 78;
$mark4 = 92;

$totalMarks = $mark1 + $mark2 + $mark3 + $mark4;
$average = $totalMarks / 4;

echo "Total Marks: " . $totalMarks . "<br>";
echo "Average: " . $average;
// Output: Total Marks: 345
//         Average: 86.25
?>
```

### Example 3: Temperature Converter (Celsius to Fahrenheit)
```php
<?php
$celsius = 25;
$fahrenheit = ($celsius * 9 / 5) + 32;
echo $celsius . "°C = " . $fahrenheit . "°F";
// Output: 25°C = 77°F
?>
```

### Example 4: Split Bill Among Friends
```php
<?php
$totalBill = 2500;
$numberOfPeople = 4;

$perPerson = $totalBill / $numberOfPeople;
echo "Each person pays: " . $perPerson . " BDT";
// Output: Each person pays: 625 BDT
?>
```

### Example 5: Calculate Area and Perimeter
```php
<?php
// Rectangle
$length = 10;
$width = 5;

$area = $length * $width;
$perimeter = 2 * ($length + $width);

echo "Area: " . $area . " sq units<br>";
echo "Perimeter: " . $perimeter . " units";
// Output: Area: 50 sq units
//         Perimeter: 30 units
?>
```

### Example 6: Time Converter (Minutes to Hours and Minutes)
```php
<?php
$totalMinutes = 135;

$hours = (int)($totalMinutes / 60);  // 2 hours
$minutes = $totalMinutes % 60;        // 15 minutes

echo $totalMinutes . " minutes = " . $hours . " hours and " . $minutes . " minutes";
// Output: 135 minutes = 2 hours and 15 minutes
?>
```

---

## Order of Operations (PEMDAS/BODMAS)

PHP follows standard mathematical order:

1. **Parentheses** ()
2. **Exponentiation** **
3. **Multiplication & Division** *, /
4. **Addition & Subtraction** +, -

```php
<?php
// Without parentheses
echo 5 + 3 * 2;      // Output: 11 (3*2=6, then 5+6=11)

// With parentheses
echo (5 + 3) * 2;    // Output: 16 (5+3=8, then 8*2=16)

// Complex example
$result = 10 + 5 * 2 ** 3 / 4 - 1;
// 2**3 = 8
// 5*8 = 40
// 40/4 = 10
// 10+10 = 20
// 20-1 = 19
echo $result;  // Output: 19
?>
```

---

## Combining with Variables

```php
<?php
$a = 10;
$b = 3;

echo "Addition: " . ($a + $b) . "<br>";        // 13
echo "Subtraction: " . ($a - $b) . "<br>";     // 7
echo "Multiplication: " . ($a * $b) . "<br>";  // 30
echo "Division: " . ($a / $b) . "<br>";        // 3.333...
echo "Modulus: " . ($a % $b) . "<br>";         // 1
echo "Exponentiation: " . ($a ** $b) . "<br>"; // 1000
?>
```

---

## Key Points to Remember

✅ All arithmetic operators work with both integers and floating-point numbers  
✅ Division always returns a float (even if result is whole number in some PHP versions)  
✅ Modulus (%) only works with integers  
✅ Be careful with division by zero - it causes errors  
✅ Use parentheses to make your calculations clear  
✅ Exponentiation (**) was added in PHP 5.6  

These arithmetic operators are essential for any calculations in PHP - from simple math to complex financial calculations!