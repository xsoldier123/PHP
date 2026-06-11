# Conditional Statements in PHP

**Conditional statements** allow you to execute different code based on different conditions. They are the building blocks of decision-making in programming.

---

## Types of Conditional Statements

1. **`if` statement**
2. **`if-else` statement**
3. **`if-elseif-else` statement**
4. **`nested if` statement**
5. **`switch` statement**
6. **`match` expression** (PHP 8+)
7. **Ternary operator** (`? :`)

---

## 1. if Statement

Executes code **only if** the condition is true.

### Syntax:
```php
if (condition) {
    // code to execute if condition is true
}
```

### Examples:

```php
<?php
$age = 20;

if ($age >= 18) {
    echo "You are an adult.";
}
// Output: You are an adult.
?>
```

```php
<?php
$temperature = 35;

if ($temperature > 30) {
    echo "It's a hot day!";
}
// Output: It's a hot day!
?>
```

```php
<?php
$score = 85;

if ($score >= 80) {
    echo "Excellent performance!";
}
// Output: Excellent performance!
?>
```

### Practical Example: Stock Check
```php
<?php
$stock = 5;

if ($stock > 0) {
    echo "Product is available!<br>";
    echo "Items in stock: $stock";
}
// Output: Product is available!
//         Items in stock: 5
?>
```

---

## 2. if-else Statement

Executes one block if condition is true, another if it's false.

### Syntax:
```php
if (condition) {
    // code if condition is true
} else {
    // code if condition is false
}
```

### Examples:

```php
<?php
$age = 15;

if ($age >= 18) {
    echo "You can vote.";
} else {
    echo "You cannot vote yet.";
}
// Output: You cannot vote yet.
?>
```

```php
<?php
$number = 7;

if ($number % 2 == 0) {
    echo "$number is even";
} else {
    echo "$number is odd";
}
// Output: 7 is odd
?>
```

```php
<?php
$password = "12345";

if ($password == "secret") {
    echo "Access granted!";
} else {
    echo "Access denied!";
}
// Output: Access denied!
?>
```

### Practical Example: Login System
```php
<?php
$username = "ebrat";
$password = "pass123";

if ($username == "ebrat" && $password == "pass123") {
    echo "✅ Login successful!<br>";
    echo "Welcome back, $username!";
} else {
    echo "❌ Invalid username or password!";
}
// Output: ✅ Login successful!
//         Welcome back, ebrat!
?>
```

---

## 3. if-elseif-else Statement

Tests multiple conditions in sequence.

### Syntax:
```php
if (condition1) {
    // code if condition1 is true
} elseif (condition2) {
    // code if condition2 is true
} elseif (condition3) {
    // code if condition3 is true
} else {
    // code if all conditions are false
}
```

### Examples:

```php
<?php
$score = 85;

if ($score >= 90) {
    echo "Grade: A+";
} elseif ($score >= 80) {
    echo "Grade: A";
} elseif ($score >= 70) {
    echo "Grade: B";
} elseif ($score >= 60) {
    echo "Grade: C";
} else {
    echo "Grade: F";
}
// Output: Grade: A
?>
```

```php
<?php
$time = 14;  // 24-hour format

if ($time < 12) {
    echo "Good morning!";
} elseif ($time < 18) {
    echo "Good afternoon!";
} else {
    echo "Good evening!";
}
// Output: Good afternoon!
?>
```

```php
<?php
$temperature = 25;

if ($temperature < 0) {
    echo "Freezing cold!";
} elseif ($temperature < 15) {
    echo "Cold";
} elseif ($temperature < 25) {
    echo "Pleasant";
} elseif ($temperature < 35) {
    echo "Warm";
} else {
    echo "Hot!";
}
// Output: Warm
?>
```

### Practical Example: Shipping Cost Calculator
```php
<?php
$orderAmount = 2500;

if ($orderAmount >= 5000) {
    $shippingCost = 0;
    echo "Free shipping!";
} elseif ($orderAmount >= 2000) {
    $shippingCost = 50;
    echo "Shipping cost: 50 BDT";
} elseif ($orderAmount >= 1000) {
    $shippingCost = 100;
    echo "Shipping cost: 100 BDT";
} else {
    $shippingCost = 150;
    echo "Shipping cost: 150 BDT";
}

echo "<br>Order amount: $orderAmount BDT";
echo "<br>Total: " . ($orderAmount + $shippingCost) . " BDT";

// Output: Shipping cost: 50 BDT
//         Order amount: 2500 BDT
//         Total: 2550 BDT
?>
```

---

## 4. Nested if Statements

An `if` statement inside another `if` statement.

### Syntax:
```php
if (condition1) {
    if (condition2) {
        // code if both conditions are true
    }
}
```

### Examples:

```php
<?php
$age = 25;
$hasLicense = true;

if ($age >= 18) {
    if ($hasLicense) {
        echo "You can drive!";
    } else {
        echo "You need a license to drive.";
    }
} else {
    echo "You are too young to drive.";
}
// Output: You can drive!
?>
```

```php
<?php
$username = "ebrat";
$password = "pass123";
$isActive = true;

if ($username == "ebrat" && $password == "pass123") {
    if ($isActive) {
        echo "Login successful!";
    } else {
        echo "Account is inactive!";
    }
} else {
    echo "Invalid credentials!";
}
// Output: Login successful!
?>
```

### Practical Example: Discount System
```php
<?php
$isMember = true;
$purchaseAmount = 3000;

if ($isMember) {
    echo "Member discount applied!<br>";
    
    if ($purchaseAmount >= 5000) {
        $discount = 20;
        echo "Discount: 20%";
    } elseif ($purchaseAmount >= 3000) {
        $discount = 15;
        echo "Discount: 15%";
    } else {
        $discount = 10;
        echo "Discount: 10%";
    }
} else {
    $discount = 0;
    echo "No discount (become a member for discounts!)";
}

$finalAmount = $purchaseAmount - ($purchaseAmount * $discount / 100);
echo "<br>Final amount: $finalAmount BDT";

// Output: Member discount applied!
//         Discount: 15%
//         Final amount: 2550 BDT
?>
```

---

## 5. switch Statement

Tests a variable against multiple values. More readable than many `elseif` statements.

### Syntax:
```php
switch (variable) {
    case value1:
        // code if variable == value1
        break;
    case value2:
        // code if variable == value2
        break;
    default:
        // code if no case matches
}
```

### Examples:

```php
<?php
$day = 3;

switch ($day) {
    case 1:
        echo "Monday";
        break;
    case 2:
        echo "Tuesday";
        break;
    case 3:
        echo "Wednesday";
        break;
    case 4:
        echo "Thursday";
        break;
    case 5:
        echo "Friday";
        break;
    case 6:
        echo "Saturday";
        break;
    case 7:
        echo "Sunday";
        break;
    default:
        echo "Invalid day";
}
// Output: Wednesday
?>
```

```php
<?php
$grade = 'B';

switch ($grade) {
    case 'A':
        echo "Excellent!";
        break;
    case 'B':
        echo "Good job!";
        break;
    case 'C':
        echo "Fair";
        break;
    case 'D':
        echo "Needs improvement";
        break;
    case 'F':
        echo "Failed";
        break;
    default:
        echo "Invalid grade";
}
// Output: Good job!
?>
```

### Multiple Cases (Fall-through):
```php
<?php
$month = 'February';

switch ($month) {
    case 'December':
    case 'January':
    case 'February':
        echo "Winter";
        break;
    case 'March':
    case 'April':
    case 'May':
        echo "Spring";
        break;
    case 'June':
    case 'July':
    case 'August':
        echo "Summer";
        break;
    case 'September':
    case 'October':
    case 'November':
        echo "Autumn";
        break;
    default:
        echo "Invalid month";
}
// Output: Winter
?>
```

### Practical Example: Payment Method
```php
<?php
$paymentMethod = "bkash";
$amount = 1000;

switch ($paymentMethod) {
    case "cash":
        echo "Payment method: Cash<br>";
        echo "Please pay $amount BDT at delivery";
        break;
    
    case "card":
    case "credit_card":
    case "debit_card":
        echo "Payment method: Card<br>";
        echo "Redirecting to payment gateway...";
        break;
    
    case "bkash":
    case "nagad":
    case "rocket":
        echo "Payment method: Mobile Banking<br>";
        echo "Send $amount BDT to: 01XXXXXXXXX";
        break;
    
    case "bank_transfer":
        echo "Payment method: Bank Transfer<br>";
        echo "Account: 1234567890<br>";
        echo "Amount: $amount BDT";
        break;
    
    default:
        echo "Invalid payment method!";
}

// Output: Payment method: Mobile Banking
//         Send 1000 BDT to: 01XXXXXXXXX
?>
```

### Important: Break Statement
```php
<?php
$number = 2;

// Without break (fall-through)
switch ($number) {
    case 1:
        echo "One<br>";
    case 2:
        echo "Two<br>";
    case 3:
        echo "Three<br>";
    default:
        echo "Default<br>";
}
// Output: Two
//         Three
//         Default

echo "<br>";

// With break
switch ($number) {
    case 1:
        echo "One<br>";
        break;
    case 2:
        echo "Two<br>";
        break;
    case 3:
        echo "Three<br>";
        break;
    default:
        echo "Default<br>";
}
// Output: Two
?>
```

---

## 6. match Expression (PHP 8+)

Similar to `switch` but more strict and returns a value. **No need for `break`**.

### Syntax:
```php
$result = match (variable) {
    value1 => return_value1,
    value2 => return_value2,
    default => default_value
};
```

### Examples:

```php
<?php
$day = 3;

$dayName = match ($day) {
    1 => "Monday",
    2 => "Tuesday",
    3 => "Wednesday",
    4 => "Thursday",
    5 => "Friday",
    6 => "Saturday",
    7 => "Sunday",
    default => "Invalid day"
};

echo $dayName;
// Output: Wednesday
?>
```

```php
<?php
$statusCode = 404;

$message = match ($statusCode) {
    200 => "Success",
    201 => "Created",
    400 => "Bad Request",
    401 => "Unauthorized",
    404 => "Not Found",
    500 => "Server Error",
    default => "Unknown Status"
};

echo $message;
// Output: Not Found
?>
```

### Multiple Values:
```php
<?php
$month = 'February';

$season = match ($month) {
    'December', 'January', 'February' => "Winter",
    'March', 'April', 'May' => "Spring",
    'June', 'July', 'August' => "Summer",
    'September', 'October', 'November' => "Autumn",
    default => "Invalid month"
};

echo $season;
// Output: Winter
?>
```

### Difference between switch and match:

```php
<?php
$value = "1";

// switch (loose comparison)
switch ($value) {
    case 1:
        echo "Matched 1 (integer)";
        break;
}
// Output: Matched 1 (integer)

// match (strict comparison)
$result = match ($value) {
    1 => "Matched 1 (integer)",
    "1" => "Matched '1' (string)",
};
echo "<br>$result";
// Output: Matched '1' (string)
?>
```

### Practical Example: User Role Permissions
```php
<?php
$role = "editor";

$permissions = match ($role) {
    "admin" => ["read", "write", "delete", "manage_users"],
    "editor" => ["read", "write"],
    "author" => ["read", "write_own"],
    "viewer" => ["read"],
    default => []
};

echo "Role: $role<br>";
echo "Permissions: " . implode(", ", $permissions);

// Output: Role: editor
//         Permissions: read, write
?>
```

---

## 7. Alternative Syntax for Control Structures

PHP offers an alternative syntax using `:` and `endif`, `endwhile`, etc. Useful in templates.

### Syntax:
```php
<?php if (condition): ?>
    <!-- HTML content -->
<?php else: ?>
    <!-- Other HTML content -->
<?php endif; ?>
```

### Examples:

```php
<?php $isLoggedIn = true; ?>

<?php if ($isLoggedIn): ?>
    <h1>Welcome back!</h1>
    <p>You are logged in.</p>
<?php else: ?>
    <h1>Please log in</h1>
    <p>You need to log in to continue.</p>
<?php endif; ?>
```

```php
<?php $score = 85; ?>

<?php if ($score >= 90): ?>
    <div class="grade-a">Grade: A+</div>
<?php elseif ($score >= 80): ?>
    <div class="grade-b">Grade: A</div>
<?php elseif ($score >= 70): ?>
    <div class="grade-c">Grade: B</div>
<?php else: ?>
    <div class="grade-f">Grade: F</div>
<?php endif; ?>
```

---

## Complete Practical Examples

### Example 1: ATM Withdrawal System
```php
<?php
$balance = 5000;
$withdrawAmount = 2000;
$pin = "1234";
$enteredPin = "1234";

echo "===== ATM Withdrawal =====<br>";
echo "Current Balance: $balance BDT<br>";
echo "Withdrawal Amount: $withdrawAmount BDT<br><br>";

if ($enteredPin != $pin) {
    echo "❌ Incorrect PIN!";
} elseif ($withdrawAmount <= 0) {
    echo "❌ Invalid amount!";
} elseif ($withdrawAmount > $balance) {
    echo "❌ Insufficient balance!";
} elseif ($withdrawAmount % 100 != 0) {
    echo "❌ Amount must be in multiples of 100!";
} else {
    $balance -= $withdrawAmount;
    echo "✅ Withdrawal successful!<br>";
    echo "Amount withdrawn: $withdrawAmount BDT<br>";
    echo "Remaining balance: $balance BDT";
}

// Output: ✅ Withdrawal successful!
//         Amount withdrawn: 2000 BDT
//         Remaining balance: 3000 BDT
?>
```

### Example 2: Student Grade System
```php
<?php
$studentName = "Ebrat Hoseen";
$attendance = 85;
$midtermScore = 40;
$finalScore = 45;
$assignmentScore = 15;

echo "===== Student Report Card =====<br>";
echo "Name: $studentName<br><br>";

// Check attendance requirement
if ($attendance < 75) {
    echo "❌ Failed due to low attendance ($attendance%)<br>";
    $status = "Failed";
} else {
    // Calculate total score
    $totalScore = $midtermScore + $finalScore + $assignmentScore;
    
    echo "Attendance: $attendance%<br>";
    echo "Midterm: $midtermScore/40<br>";
    echo "Final: $finalScore/50<br>";
    echo "Assignment: $assignmentScore/10<br>";
    echo "Total Score: $totalScore/100<br><br>";
    
    // Determine grade
    if ($totalScore >= 90) {
        $grade = "A+";
        $gpa = 4.0;
    } elseif ($totalScore >= 80) {
        $grade = "A";
        $gpa = 3.75;
    } elseif ($totalScore >= 70) {
        $grade = "B";
        $gpa = 3.5;
    } elseif ($totalScore >= 60) {
        $grade = "C";
        $gpa = 3.0;
    } elseif ($totalScore >= 50) {
        $grade = "D";
        $gpa = 2.5;
    } else {
        $grade = "F";
        $gpa = 0.0;
    }
    
    // Determine status
    if ($grade == "F") {
        $status = "Failed";
    } else {
        $status = "Passed";
    }
    
    echo "Grade: $grade<br>";
    echo "GPA: $gpa<br>";
    echo "Status: $status<br>";
}

// Output: ===== Student Report Card =====
//         Name: Ebrat Hoseen
//         
//         Attendance: 85%
//         Midterm: 40/40
//         Final: 45/50
//         Assignment: 15/10
//         Total Score: 100/100
//         
//         Grade: A+
//         GPA: 4.0
//         Status: Passed
?>
```

### Example 3: E-commerce Order Status Tracker
```php
<?php
$orderId = "ORD12345";
$orderStatus = "shipped";

echo "===== Order Tracking =====<br>";
echo "Order ID: $orderId<br>";
echo "Status: " . ucfirst($orderStatus) . "<br><br>";

switch ($orderStatus) {
    case "pending":
        echo "📋 Your order is pending confirmation<br>";
        echo "Expected action: Payment verification";
        break;
    
    case "confirmed":
        echo "✅ Your order has been confirmed<br>";
        echo "Expected action: Processing";
        break;
    
    case "processing":
        echo "📦 Your order is being processed<br>";
        echo "Expected action: Packaging";
        break;
    
    case "shipped":
        echo "🚚 Your order has been shipped<br>";
        echo "Expected delivery: 2-3 business days";
        break;
    
    case "delivered":
        echo "✅ Your order has been delivered<br>";
        echo "Thank you for shopping with us!";
        break;
    
    case "cancelled":
        echo "❌ Your order has been cancelled<br>";
        echo "Refund will be processed in 3-5 days";
        break;
    
    case "returned":
        echo "🔙 Your order has been returned<br>";
        echo "Refund initiated";
        break;
    
    default:
        echo "❓ Unknown order status";
}

// Output: ===== Order Tracking =====
//         Order ID: ORD12345
//         Status: Shipped
//         
//         🚚 Your order has been shipped
//         Expected delivery: 2-3 business days
?>
```

### Example 4: Ticket Pricing System
```php
<?php
$age = 15;
$isStudent = true;
$isWeekend = false;
$ticketType = "standard";

$basePrice = 500;

echo "===== Ticket Pricing =====<br>";
echo "Base Price: $basePrice BDT<br>";
echo "Age: $age<br>";
echo "Student: " . ($isStudent ? "Yes" : "No") . "<br>";
echo "Weekend: " . ($isWeekend ? "Yes" : "No") . "<br>";
echo "Ticket Type: $ticketType<br><br>";

// Calculate discount
$discount = 0;

if ($age < 5) {
    $discount = 100;
    echo "Free ticket (Age under 5)<br>";
} else {
    if ($age < 18) {
        $discount += 20;
        echo "Child discount: 20%<br>";
    } elseif ($age >= 60) {
        $discount += 30;
        echo "Senior discount: 30%<br>";
    }
    
    if ($isStudent) {
        $discount += 15;
        echo "Student discount: 15%<br>";
    }
    
    if (!$isWeekend) {
        $discount += 10;
        echo "Weekday discount: 10%<br>";
    }
}

// Apply ticket type multiplier
switch ($ticketType) {
    case "premium":
        $multiplier = 2;
        echo "Premium ticket: 2x price<br>";
        break;
    case "vip":
        $multiplier = 3;
        echo "VIP ticket: 3x price<br>";
        break;
    default:
        $multiplier = 1;
}

$finalPrice = $basePrice * $multiplier;

if ($discount < 100) {
    $finalPrice -= ($finalPrice * $discount / 100);
}

echo "<br>Total Discount: $discount%<br>";
echo "Final Price: $finalPrice BDT";

// Output: ===== Ticket Pricing =====
//         Base Price: 500 BDT
//         Age: 15
//         Student: Yes
//         Weekend: No
//         Ticket Type: standard
//         
//         Child discount: 20%
//         Student discount: 15%
//         Weekday discount: 10%
//         
//         Total Discount: 45%
//         Final Price: 275 BDT
?>
```

### Example 5: Weather-based Activity Recommender
```php
<?php
$temperature = 28;
$isRaining = false;
$windSpeed = 15;  // km/h

echo "===== Weather Activity Recommender =====<br>";
echo "Temperature: {$temperature}°C<br>";
echo "Raining: " . ($isRaining ? "Yes" : "No") . "<br>";
echo "Wind Speed: {$windSpeed} km/h<br><br>";

if ($isRaining) {
    echo "☔ It's raining!<br>";
    echo "Recommended activities:<br>";
    echo "- Stay indoors<br>";
    echo "- Watch movies<br>";
    echo "- Read books<br>";
} else {
    if ($temperature < 10) {
        echo "🥶 It's very cold!<br>";
        echo "Recommended activities:<br>";
        echo "- Wear warm clothes<br>";
        echo "- Drink hot beverages<br>";
        echo "- Indoor activities recommended<br>";
    } elseif ($temperature >= 10 && $temperature < 20) {
        echo "😊 Pleasant weather!<br>";
        echo "Recommended activities:<br>";
        echo "- Go for a walk<br>";
        echo "- Outdoor sports<br>";
        echo "- Picnic in the park<br>";
    } elseif ($temperature >= 20 && $temperature < 30) {
        echo "🌤️ Warm and nice!<br>";
        echo "Recommended activities:<br>";
        
        if ($windSpeed > 20) {
            echo "- Flying kites<br>";
            echo "- Windsurfing<br>";
        } else {
            echo "- Swimming<br>";
            echo "- Beach activities<br>";
        }
        
        echo "- Outdoor games<br>";
    } else {
        echo "🥵 It's very hot!<br>";
        echo "Recommended activities:<br>";
        echo "- Stay hydrated<br>";
        echo "- Stay in shade<br>";
        echo "- Swimming (if available)<br>";
        echo "- Air-conditioned places<br>";
    }
}

// Output: ===== Weather Activity Recommender =====
//         Temperature: 28°C
//         Raining: No
//         Wind Speed: 15 km/h
//         
//         🌤️ Warm and nice!
//         Recommended activities:
//         - Swimming
//         - Beach activities
//         - Outdoor games
?>
```

---

## Comparison: if-elseif vs switch vs match

| **Feature** | **if-elseif** | **switch** | **match** |
|------------|--------------|-----------|----------|
| Flexibility | High (any condition) | Medium (equality only) | Medium (equality only) |
| Comparison | Loose (==) | Loose (==) | Strict (===) |
| Return value | No | No | Yes |
| Break needed | No | Yes | No |
| Fall-through | No | Yes (without break) | No |
| Best for | Complex conditions | Multiple exact matches | Multiple exact matches with return |

---

## Best Practices

### ✅ DO:

```php
// Use meaningful variable names
$isEligible = ($age >= 18 && $hasID);
if ($isEligible) {
    // Clear logic
}

// Keep conditions simple
if ($status == "active") {
    // Easy to understand
}

// Use early returns
function processUser($user) {
    if (!$user) {
        return "User not found";
    }
    
    if (!$user['active']) {
        return "User inactive";
    }
    
    return "Processing user...";
}

// Use switch for multiple exact matches
switch ($paymentMethod) {
    case "card":
        processCard();
        break;
    case "cash":
        processCash();
        break;
}
```

### ❌ DON'T:

```php
// Avoid deeply nested conditions
if ($a) {
    if ($b) {
        if ($c) {
            if ($d) {
                // Too deep!
            }
        }
    }
}

// Don't compare booleans unnecessarily
if ($isActive == true) { }  // ❌ Bad
if ($isActive) { }          // ✅ Good

// Don't forget break in switch
switch ($x) {
    case 1:
        echo "One";
        // Missing break!
    case 2:
        echo "Two";
}

// Avoid complex conditions without parentheses
if ($a && $b || $c && $d) { }  // Confusing
if (($a && $b) || ($c && $d)) { }  // Clear
```

---

## Quick Reference

### When to use what:

| **Use** | **When** |
|---------|----------|
| `if` | Single condition check |
| `if-else` | Two possible outcomes |
| `if-elseif-else` | Multiple conditions in range |
| `nested if` | Dependent conditions |
| `switch` | Multiple exact value matches |
| `match` | Switch with return value (PHP 8+) |
| `ternary` | Simple inline condition |

---

## Key Points to Remember

✅ **if** - executes code if condition is true  
✅ **else** - executes when if condition is false  
✅ **elseif** - tests additional conditions  
✅ **switch** - tests variable against multiple values  
✅ **match** - strict comparison with return value (PHP 8+)  
✅ Always use **break** in switch statements  
✅ Use **curly braces** `{}` for clarity  
✅ **indent properly** for readability  
✅ Keep conditions **simple and clear**  
✅ Use **early returns** to avoid deep nesting  

Conditional statements are the foundation of program logic - mastering them is essential for writing effective PHP code!