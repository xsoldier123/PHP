# Logical Operators in PHP

**Logical operators** are used to combine conditional statements and perform logical operations. They return boolean values (`true` or `false`) and are essential for making complex decisions in your code.

---

## List of Logical Operators

| Operator | Name | Example | Description |
|----------|------|---------|-------------|
| `&&` | AND | `$x && $y` | True if BOTH are true |
| `||` | OR | `$x || $y` | True if AT LEAST ONE is true |
| `!` | NOT | `!$x` | True if $x is false (inverts) |
| `and` | AND (lower precedence) | `$x and $y` | Same as `&&` but lower precedence |
| `or` | OR (lower precedence) | `$x or $y` | Same as `||` but lower precedence |
| `xor` | XOR | `$x xor $y` | True if ONLY ONE is true (exclusive OR) |

---

## 1. AND Operator (&&)

Returns `true` if **BOTH** conditions are true.

### Syntax:
```php
$result = (condition1 && condition2);
```

### Truth Table:
| A | B | A && B |
|---|---|--------|
| true | true | **true** |
| true | false | false |
| false | true | false |
| false | false | false |

### Examples:

```php
<?php
$age = 25;
$hasLicense = true;

// Check if person can drive
if ($age >= 18 && $hasLicense) {
    echo "You can drive!";
} else {
    echo "You cannot drive.";
}
// Output: You can drive!
?>
```

```php
<?php
$username = "ebrat";
$password = "12345";

// Login validation
if ($username == "ebrat" && $password == "12345") {
    echo "Login successful!";
} else {
    echo "Invalid credentials!";
}
// Output: Login successful!
?>
```

```php
<?php
$score = 85;
$attendance = 90;

// Check if student passes (both conditions must be met)
if ($score >= 80 && $attendance >= 75) {
    echo "Passed with honors!";
}
// Output: Passed with honors!
?>
```

### Practical Example: Form Validation
```php
<?php
$name = "Ebrat Hoseen";
$email = "ebrat@example.com";
$age = 19;

if ($name != "" && $email != "" && $age >= 18) {
    echo "Registration successful!<br>";
    echo "Welcome, $name!";
} else {
    echo "Please fill all fields and ensure age is 18+";
}
// Output: Registration successful!
//         Welcome, Ebrat Hoseen!
?>
```

---

## 2. OR Operator (||)

Returns `true` if **AT LEAST ONE** condition is true.

### Syntax:
```php
$result = (condition1 || condition2);
```

### Truth Table:
| A | B | A \|\| B |
|---|---|--------|
| true | true | **true** |
| true | false | **true** |
| false | true | **true** |
| false | false | false |

### Examples:

```php
<?php
$isWeekend = true;
$isHoliday = false;

// Check if person can rest
if ($isWeekend || $isHoliday) {
    echo "You can rest today!";
} else {
    echo "Time to work!";
}
// Output: You can rest today!
?>
```

```php
<?php
$role = "admin";

// Check if user has special privileges
if ($role == "admin" || $role == "moderator") {
    echo "You have special access!";
}
// Output: You have special access!
?>
```

```php
<?php
$paymentMethod = "credit_card";

// Accept multiple payment methods
if ($paymentMethod == "cash" || $paymentMethod == "credit_card" || $paymentMethod == "bkash") {
    echo "Payment method accepted!";
}
// Output: Payment method accepted!
?>
```

### Practical Example: Discount Eligibility
```php
<?php
$isMember = false;
$purchaseAmount = 5000;
$hasCoupon = true;

if ($isMember || $purchaseAmount >= 3000 || $hasCoupon) {
    echo "You are eligible for a discount!";
} else {
    echo "No discount available.";
}
// Output: You are eligible for a discount!
?>
```

---

## 3. NOT Operator (!)

**Inverts** the boolean value (true becomes false, false becomes true).

### Syntax:
```php
$result = !condition;
```

### Truth Table:
| A | !A |
|---|-----|
| true | false |
| false | true |

### Examples:

```php
<?php
$isLoggedIn = false;

if (!$isLoggedIn) {
    echo "Please log in to continue.";
}
// Output: Please log in to continue.
?>
```

```php
<?php
$hasErrors = false;

if (!$hasErrors) {
    echo "Form submitted successfully!";
}
// Output: Form submitted successfully!
?>
```

```php
<?php
$isEmpty = true;

if (!$isEmpty) {
    echo "Cart has items";
} else {
    echo "Your cart is empty";
}
// Output: Your cart is empty
?>
```

### Practical Example: Validation
```php
<?php
$username = "ebrat";

if (!empty($username)) {
    echo "Welcome, $username!";
} else {
    echo "Username is required!";
}
// Output: Welcome, ebrat!
?>
```

---

## 4. XOR Operator (xor)

Returns `true` if **ONLY ONE** condition is true (exclusive OR).

### Syntax:
```php
$result = (condition1 xor condition2);
```

### Truth Table:
| A | B | A xor B |
|---|---|---------|
| true | true | false |
| true | false | **true** |
| false | true | **true** |
| false | false | false |

### Examples:

```php
<?php
$hasCard = true;
$hasCash = true;

// Pay with either card OR cash, not both
if ($hasCard xor $hasCash) {
    echo "Payment method selected!";
} else {
    echo "Please choose ONE payment method!";
}
// Output: Please choose ONE payment method!
?>
```

```php
<?php
$isDay = true;
$isNight = false;

// Either day or night, not both
if ($isDay xor $isNight) {
    echo "Valid time period";
}
// Output: Valid time period
?>
```

```php
<?php
$freeShipping = true;
$expressShipping = true;

// Can't have both free and express
if ($freeShipping xor $expressShipping) {
    echo "Shipping option selected";
} else {
    echo "Please select only one shipping option";
}
// Output: Please select only one shipping option
?>
```

---

## 5. and Operator (Lower Precedence)

Works the same as `&&` but has **lower precedence**.

### Examples:

```php
<?php
$a = true;
$b = false;

$result1 = $a && $b;  // false
$result2 = $a and $b; // false

echo "Result 1: " . ($result1 ? "true" : "false") . "<br>";
echo "Result 2: " . ($result2 ? "true" : "false") . "<br>";
?>
```

### **Precedence Difference** (Important!):

```php
<?php
// Using &&
$result1 = true && false;  // $result1 = false
echo $result1 ? "true" : "false";  // false

// Using and
$result2 = true and false;  // $result2 = true (!)
echo "<br>";
echo $result2 ? "true" : "false";  // true

// Why? Because = has higher precedence than 'and'
// It's evaluated as: ($result2 = true) and false
?>
```

**Recommendation:** Use `&&` instead of `and` to avoid confusion.

---

## 6. or Operator (Lower Precedence)

Works the same as `||` but has **lower precedence**.

### Examples:

```php
<?php
$a = false;
$b = true;

$result1 = $a || $b;  // true
$result2 = $a or $b;  // true

echo "Result 1: " . ($result1 ? "true" : "false") . "<br>";
echo "Result 2: " . ($result2 ? "true" : "false") . "<br>";
?>
```

**Recommendation:** Use `||` instead of `or` to avoid precedence issues.

---

## Combining Multiple Logical Operators

You can combine multiple logical operators to create complex conditions.

### Example 1: Access Control
```php
<?php
$age = 25;
$isMember = true;
$hasPaid = true;

if (($age >= 18 && $isMember) && $hasPaid) {
    echo "Access granted!";
} else {
    echo "Access denied!";
}
// Output: Access granted!
?>
```

### Example 2: Discount System
```php
<?php
$purchaseAmount = 5000;
$isMember = false;
$isFirstPurchase = true;

if ($purchaseAmount >= 3000 || ($isMember && !$isFirstPurchase)) {
    $discount = 10;
} else {
    $discount = 0;
}

echo "Discount: $discount%";
// Output: Discount: 10%
?>
```

### Example 3: Grade Evaluation
```php
<?php
$attendance = 85;
$examScore = 75;
$assignment = 80;

if (($attendance >= 80 && $examScore >= 70) || $assignment >= 90) {
    echo "Passed the course!";
} else {
    echo "Failed the course.";
}
// Output: Passed the course!
?>
```

---

## Short-Circuit Evaluation

PHP uses **short-circuit evaluation** - it stops evaluating as soon as the result is determined.

### AND Short-Circuit:
```php
<?php
function checkA() {
    echo "Checking A<br>";
    return false;
}

function checkB() {
    echo "Checking B<br>";
    return true;
}

// checkB() is never called because checkA() returns false
if (checkA() && checkB()) {
    echo "Both true";
}

// Output: Checking A
// (checkB is not called)
?>
```

### OR Short-Circuit:
```php
<?php
function checkA() {
    echo "Checking A<br>";
    return true;
}

function checkB() {
    echo "Checking B<br>";
    return false;
}

// checkB() is never called because checkA() returns true
if (checkA() || checkB()) {
    echo "At least one true";
}

// Output: Checking A
//         At least one true
// (checkB is not called)
?>
```

### Practical Use:
```php
<?php
// Prevent division by zero
$divisor = 0;

if ($divisor != 0 && 10 / $divisor > 5) {
    echo "Result is greater than 5";
} else {
    echo "Cannot divide or result is small";
}
// Output: Cannot divide or result is small
// Division is never attempted because first condition is false
?>
```

---

## Operator Precedence

When combining operators, precedence matters:

| **Precedence** | **Operator** |
|----------------|-------------|
| 1 (Highest) | `!` |
| 2 | `&&` |
| 3 | `||` |
| 4 | `and` |
| 5 (Lowest) | `or` |

### Examples:

```php
<?php
// Without parentheses
$result = true || false && false;
// Evaluated as: true || (false && false)
// Result: true

echo $result ? "true" : "false";  // true
?>
```

```php
<?php
// With parentheses (better clarity)
$result = (true || false) && false;
// Result: false

echo $result ? "true" : "false";  // false
?>
```

**Best Practice:** Always use parentheses for clarity!

---

## Complete Practical Examples

### Example 1: Login System
```php
<?php
$username = "ebrat";
$password = "pass123";
$isActive = true;
$isBanned = false;

if ($username == "ebrat" && 
    $password == "pass123" && 
    $isActive && 
    !$isBanned) {
    echo "✅ Login successful!<br>";
    echo "Welcome back, $username!";
} else {
    echo "❌ Login failed!<br>";
    
    if (!$isActive) {
        echo "Account is inactive.";
    } elseif ($isBanned) {
        echo "Account is banned.";
    } else {
        echo "Invalid credentials.";
    }
}
// Output: ✅ Login successful!
//         Welcome back, ebrat!
?>
```

### Example 2: Ticket Booking System
```php
<?php
$age = 15;
$isStudent = true;
$isWeekday = true;

// Discount eligibility
if ($age < 18 || $age >= 60 || ($isStudent && $isWeekday)) {
    $discount = 20;
    echo "Eligible for discount!<br>";
} else {
    $discount = 0;
    echo "Regular price applies.<br>";
}

$basePrice = 500;
$finalPrice = $basePrice - ($basePrice * $discount / 100);

echo "Discount: $discount%<br>";
echo "Final Price: $finalPrice BDT";

// Output: Eligible for discount!
//         Discount: 20%
//         Final Price: 400 BDT
?>
```

### Example 3: E-commerce Order Processing
```php
<?php
$itemsInStock = 5;
$orderQuantity = 3;
$paymentReceived = true;
$shippingAddressValid = true;

echo "===== Order Processing =====<br>";

if ($orderQuantity <= $itemsInStock && 
    $paymentReceived && 
    $shippingAddressValid) {
    
    echo "✅ Order confirmed!<br>";
    echo "Processing shipment...<br>";
    
    $remainingStock = $itemsInStock - $orderQuantity;
    echo "Remaining stock: $remainingStock units";
    
} else {
    echo "❌ Order cannot be processed:<br>";
    
    if ($orderQuantity > $itemsInStock) {
        echo "- Insufficient stock<br>";
    }
    if (!$paymentReceived) {
        echo "- Payment not received<br>";
    }
    if (!$shippingAddressValid) {
        echo "- Invalid shipping address<br>";
    }
}

// Output: ✅ Order confirmed!
//         Processing shipment...
//         Remaining stock: 2 units
?>
```

### Example 4: User Permissions System
```php
<?php
$userRole = "editor";
$isOwner = false;
$hasPermission = true;

// Check if user can edit content
$canEdit = ($userRole == "admin" || $userRole == "editor") && $hasPermission;

// Check if user can delete content
$canDelete = ($userRole == "admin" || $isOwner) && $hasPermission;

// Check if user can view content
$canView = $userRole == "admin" || $userRole == "editor" || $userRole == "viewer";

echo "===== User Permissions =====<br>";
echo "Role: $userRole<br>";
echo "Can Edit: " . ($canEdit ? "Yes" : "No") . "<br>";
echo "Can Delete: " . ($canDelete ? "Yes" : "No") . "<br>";
echo "Can View: " . ($canView ? "Yes" : "No") . "<br>";

// Output: ===== User Permissions =====
//         Role: editor
//         Can Edit: Yes
//         Can Delete: No
//         Can View: Yes
?>
```

### Example 5: Shipping Calculator
```php
<?php
$weight = 5;  // kg
$distance = 150;  // km
$isPremium = true;
$isFragile = false;

$baseRate = 100;

// Calculate shipping cost
if ($weight <= 5 && $distance <= 100) {
    $shippingCost = $baseRate;
} elseif ($weight > 5 || $distance > 100) {
    $shippingCost = $baseRate * 1.5;
} else {
    $shippingCost = $baseRate * 2;
}

// Apply premium discount
if ($isPremium && !$isFragile) {
    $shippingCost *= 0.9;  // 10% discount
}

// Add fragile handling fee
if ($isFragile) {
    $shippingCost += 50;
}

echo "===== Shipping Details =====<br>";
echo "Weight: {$weight}kg<br>";
echo "Distance: {$distance}km<br>";
echo "Premium: " . ($isPremium ? "Yes" : "No") . "<br>";
echo "Fragile: " . ($isFragile ? "Yes" : "No") . "<br>";
echo "Shipping Cost: {$shippingCost} BDT";

// Output: ===== Shipping Details =====
//         Weight: 5kg
//         Distance: 150km
//         Premium: Yes
//         Fragile: No
//         Shipping Cost: 135 BDT
?>
```

---

## Logical Operators with Ternary

You can combine logical operators with ternary operators:

```php
<?php
$age = 25;
$hasLicense = true;

$status = ($age >= 18 && $hasLicense) ? "Can drive" : "Cannot drive";
echo $status;  // Output: Can drive
?>
```

```php
<?php
$score = 85;
$attendance = 70;

$result = ($score >= 80 || $attendance >= 75) ? "Pass" : "Fail";
echo $result;  // Output: Pass
?>
```

---

## Common Patterns

### Pattern 1: Range Check
```php
<?php
$age = 25;

if ($age >= 18 && $age <= 60) {
    echo "Working age";
}
?>
```

### Pattern 2: Multiple Conditions
```php
<?php
$role = "admin";

if ($role == "admin" || $role == "superadmin" || $role == "moderator") {
    echo "Has special privileges";
}
?>
```

### Pattern 3: Exclusion Check
```php
<?php
$status = "pending";

if ($status != "deleted" && $status != "banned") {
    echo "Account is active";
}
?>
```

### Pattern 4: Guard Clauses
```php
<?php
function processOrder($order) {
    if (!$order || !isset($order['items'])) {
        return "Invalid order";
    }
    
    if (empty($order['items']) || !$order['payment_received']) {
        return "Cannot process order";
    }
    
    return "Order processed successfully";
}
?>
```

---

## Best Practices

### ✅ DO:
```php
// Use parentheses for clarity
if (($age >= 18 && $hasLicense) || $isSpecialCase) {
    // Clear logic
}

// Use descriptive variable names
$isEligible = $age >= 18 && $hasID;
if ($isEligible) {
    // Easy to understand
}

// Break complex conditions
$hasValidCredentials = $username != "" && $password != "";
$isAccountActive = !$isBanned && $isVerified;
if ($hasValidCredentials && $isAccountActive) {
    // Much clearer!
}
```

### ❌ DON'T:
```php
// Avoid overly complex one-liners
if ($a && $b || $c && !$d || $e && ($f || !$g) && $h) {
    // Too confusing!
}

// Don't mix and/or with &&/||
if ($a && $b or $c || $d and $e) {
    // Precedence nightmare!
}

// Don't compare booleans unnecessarily
if ($isActive == true) { }  // ❌ Bad
if ($isActive) { }          // ✅ Good
```

---

## Comparison Table

| **Operator** | **Precedence** | **Use When** |
|-------------|---------------|-------------|
| `&&` | High | Always (default choice) |
| `||` | High | Always (default choice) |
| `!` | Highest | Inverting conditions |
| `and` | Low | Avoid (precedence issues) |
| `or` | Low | Avoid (precedence issues) |
| `xor` | Medium | Exclusive OR needed |

---

## Key Points to Remember

✅ `&&` (AND) - **ALL** conditions must be true  
✅ `||` (OR) - **AT LEAST ONE** condition must be true  
✅ `!` (NOT) - **INVERTS** the boolean value  
✅ `xor` - **EXACTLY ONE** condition must be true  
✅ Use `&&` and `||` instead of `and` and `or`  
✅ PHP uses **short-circuit evaluation**  
✅ Always use **parentheses** for complex conditions  
✅ **Readability matters** - break complex logic into variables  

Logical operators are fundamental for controlling program flow and making intelligent decisions in your PHP applications!