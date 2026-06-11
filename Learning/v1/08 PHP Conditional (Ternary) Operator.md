# Conditional (Ternary) Operator in PHP

The **conditional operator** (also called **ternary operator**) is a shorthand way to write simple `if-else` statements in PHP. It's called "ternary" because it takes **three operands**.

---

## Basic Syntax

```php
$result = (condition) ? value_if_true : value_if_false;
```

**How it works:**
- If the `condition` is **true**, return `value_if_true`
- If the `condition` is **false**, return `value_if_false`

---

## Simple Examples

### Example 1: Check Voting Eligibility
```php
<?php
$age = 20;
$status = ($age >= 18) ? "Can vote" : "Cannot vote";
echo $status;  // Output: Can vote
?>
```

**Traditional if-else equivalent:**
```php
<?php
if ($age >= 18) {
    $status = "Can vote";
} else {
    $status = "Cannot vote";
}
?>
```

### Example 2: Even or Odd
```php
<?php
$number = 7;
$type = ($number % 2 == 0) ? "Even" : "Odd";
echo $type;  // Output: Odd
?>
```

### Example 3: Member Discount
```php
<?php
$isMember = true;
$discount = ($isMember) ? 10 : 0;
echo "Discount: " . $discount . "%";  // Output: Discount: 10%
?>
```

### Example 4: Grade Assignment
```php
<?php
$marks = 85;
$grade = ($marks >= 80) ? "A" : "B";
echo "Grade: " . $grade;  // Output: Grade: A
?>
```

---

## Practical Examples

### Example 1: Shopping Cart Display
```php
<?php
$itemsInCart = 3;
$message = ($itemsInCart > 0) ? "You have $itemsInCart items" : "Your cart is empty";
echo $message;  // Output: You have 3 items
?>
```

### Example 2: Price Display
```php
<?php
$price = 0;
$displayPrice = ($price > 0) ? $price . " BDT" : "Free";
echo $displayPrice;  // Output: Free
?>
```

### Example 3: Login Status
```php
<?php
$isLoggedIn = false;
$welcomeMessage = ($isLoggedIn) ? "Welcome back!" : "Please log in";
echo $welcomeMessage;  // Output: Please log in
?>
```

### Example 4: Stock Availability
```php
<?php
$stock = 5;
$availability = ($stock > 0) ? "In Stock ($stock left)" : "Out of Stock";
echo $availability;  // Output: In Stock (5 left)
?>
```

---

## Nested Ternary Operators

You can nest ternary operators for multiple conditions, but **use sparingly** as they become hard to read.

### Example 1: Multiple Grade Levels
```php
<?php
$score = 85;
$grade = ($score >= 90) ? "A" : (($score >= 80) ? "B" : (($score >= 70) ? "C" : "F"));
echo "Grade: " . $grade;  // Output: Grade: B
?>
```

### Example 2: Age Categories
```php
<?php
$age = 15;
$category = ($age < 13) ? "Child" : (($age < 20) ? "Teenager" : "Adult");
echo $category;  // Output: Teenager
?>
```

**⚠️ Better approach for complex conditions:**
```php
<?php
$score = 85;

if ($score >= 90) {
    $grade = "A";
} elseif ($score >= 80) {
    $grade = "B";
} elseif ($score >= 70) {
    $grade = "C";
} else {
    $grade = "F";
}

echo "Grade: " . $grade;  // Easier to read!
?>
```

---

## Combining with Assignment Operators

You can combine ternary operators with compound assignment operators:

```php
<?php
$balance = 1000;
$hasDiscount = true;

$balance -= ($hasDiscount) ? 100 : 0;
echo "Final balance: " . $balance;  // Output: Final balance: 900
?>
```

```php
<?php
$message = "Hello";
$isUrgent = true;

$message .= ($isUrgent) ? " - URGENT!" : "";
echo $message;  // Output: Hello - URGENT!
?>
```

```php
<?php
$points = 100;
$isVIP = true;

$points *= ($isVIP) ? 2 : 1;  // Double points for VIP
echo "Points: " . $points;  // Output: Points: 200
?>
```

---

## Elvis Operator (Shorthand Ternary) - PHP 5.3+

The **Elvis operator** `?:` is a shortened ternary where you omit the middle part.

### Syntax:
```php
$result = (expression) ?: default_value;
```

Returns `expression` if it's **truthy**, otherwise returns `default_value`.

### Examples:

```php
<?php
$username = "Ebrat";
$name = $username ?: "Guest";
echo $name;  // Output: Ebrat
?>
```

```php
<?php
$username = "";  // Empty string is falsy
$name = $username ?: "Guest";
echo $name;  // Output: Guest
?>
```

```php
<?php
$count = 0;  // 0 is falsy
$display = $count ?: "No items";
echo $display;  // Output: No items
?>
```

**Equivalent to:**
```php
$name = $username ? $username : "Guest";
```

---

## Null Coalescing Operator (??) - PHP 7+

The **null coalescing operator** checks if a variable exists and is not `null`.

### Syntax:
```php
$result = $variable ?? default_value;
```

### Examples:

```php
<?php
// Safely get URL parameters
$username = $_GET['user'] ?? 'Guest';
echo $username;
?>
```

```php
<?php
// Working with arrays
$config = [
    'host' => 'localhost',
    'port' => 3306
];

$host = $config['host'] ?? 'default_host';     // localhost
$user = $config['user'] ?? 'root';             // root (key doesn't exist)
$pass = $config['password'] ?? '';             // empty string

echo "Host: $host, User: $user";
?>
```

```php
<?php
// Chain multiple null coalescing
$color = $userColor ?? $defaultColor ?? 'blue';
?>
```

**Key Difference from Elvis Operator:**

```php
<?php
$value = "";  // Empty string

// Elvis operator: empty string is falsy
$result1 = $value ?: "default";  // "default"

// Null coalescing: empty string exists (not null)
$result2 = $value ?? "default";  // "" (empty string)

echo "Elvis: '$result1'<br>";       // Elvis: 'default'
echo "Null coalescing: '$result2'"; // Null coalescing: ''
?>
```

---

## Null Coalescing Assignment Operator (??=) - PHP 7.4+

Assigns a value **only if** the variable is not set or is `null`.

### Syntax:
```php
$variable ??= default_value;
```

### Examples:

```php
<?php
$config = [];

// Set default values only if not already set
$config['host'] ??= 'localhost';
$config['port'] ??= 3306;
$config['user'] ??= 'root';

print_r($config);
// Output: Array ( [host] => localhost [port] => 3306 [user] => root )
?>
```

```php
<?php
$settings = ['theme' => 'dark'];

$settings['theme'] ??= 'light';     // Already set, keeps 'dark'
$settings['language'] ??= 'en';     // Not set, assigns 'en'

print_r($settings);
// Output: Array ( [theme] => dark [language] => en )
?>
```

**Equivalent to:**
```php
$config['host'] = $config['host'] ?? 'localhost';
```

---

## Complete Practical Example: E-commerce Product Display

```php
<?php
// Product data (some fields might be missing)
$product = [
    'name' => 'Laptop',
    'price' => 50000,
    'stock' => 5,
    'discount' => 10
    // 'image' is not set
    // 'rating' is not set
];

// Safely access data with defaults
$name = $product['name'] ?? 'Unknown Product';
$price = $product['price'] ?? 0;
$stock = $product['stock'] ?? 0;
$discount = $product['discount'] ?? 0;
$image = $product['image'] ?? 'default.jpg';
$rating = $product['rating'] ?? 0;

// Calculate final price
$finalPrice = $price - ($price * $discount / 100);

// Determine availability
$availability = ($stock > 0) ? "In Stock" : "Out of Stock";

// Set stock warning
$stockWarning = ($stock > 0 && $stock <= 5) ? "Only $stock left!" : "";

// Rating display
$ratingDisplay = ($rating > 0) ? $rating . " stars" : "No ratings yet";

// Display product
echo "===== Product Details =====<br>";
echo "Name: $name<br>";
echo "Price: $price BDT<br>";
echo "Discount: $discount%<br>";
echo "Final Price: $finalPrice BDT<br>";
echo "Availability: $availability<br>";
echo "$stockWarning<br>";
echo "Rating: $ratingDisplay<br>";
echo "Image: $image<br>";

// Output:
// ===== Product Details =====
// Name: Laptop
// Price: 50000 BDT
// Discount: 10%
// Final Price: 45000 BDT
// Availability: In Stock
// Only 5 left!
// Rating: No ratings yet
// Image: default.jpg
?>
```

---

## Operator Comparison Table

| **Operator** | **Syntax** | **Checks** | **Use Case** |
|-------------|-----------|-----------|-------------|
| Ternary `? :` | `$x = ($a) ? $b : $c` | Condition true/false | Simple if-else assignment |
| Elvis `?:` | `$x = $a ?: $b` | Truthy/falsy | Default for falsy values |
| Null Coalescing `??` | `$x = $a ?? $b` | Isset and not null | Safe variable access |
| Null Coalescing Assignment `??=` | `$a ??= $b` | Isset and not null | Set default if not set |

---

## When to Use Each

### Use Ternary `? :` when:
```php
// Comparing values
$status = ($age >= 18) ? "Adult" : "Minor";

// Making decisions
$shipping = ($total > 1000) ? 0 : 50;

// Display logic
$label = ($count == 1) ? "item" : "items";
```

### Use Elvis `?:` when:
```php
// Providing defaults for falsy values
$name = $username ?: "Anonymous";
$title = $pageTitle ?: "Untitled";
```

### Use Null Coalescing `??` when:
```php
// Accessing array keys that might not exist
$user = $_SESSION['user'] ?? null;

// Form data
$name = $_POST['name'] ?? '';

// Config with defaults
$timeout = $config['timeout'] ?? 30;
```

### Use Null Coalescing Assignment `??=` when:
```php
// Initializing variables
$counter ??= 0;

// Setting defaults in arrays
$options['color'] ??= 'blue';
```

---

## Common Patterns

### Pattern 1: Form Validation Display
```php
<?php
$errors = [];
// ... validation logic sets $errors

$nameError = isset($errors['name']) ? $errors['name'] : '';
$emailError = $errors['email'] ?? '';  // Shorter with ??

echo $nameError ? "<span class='error'>$nameError</span>" : "";
?>
```

### Pattern 2: Permission Checking
```php
<?php
$userRole = 'admin';
$canEdit = ($userRole == 'admin' || $userRole == 'editor') ? true : false;
$editButton = $canEdit ? "<button>Edit</button>" : "";
?>
```

### Pattern 3: Pagination
```php
<?php
$page = $_GET['page'] ?? 1;
$itemsPerPage = 10;
$offset = ($page - 1) * $itemsPerPage;
?>
```

---

## Best Practices

### ✅ DO:
```php
// Use for simple, clear conditions
$tax = ($isTaxable) ? 0.15 : 0;

// Use for single assignments
$class = ($isActive) ? 'active' : 'inactive';

// Chain null coalescing for fallbacks
$lang = $userLang ?? $browserLang ?? 'en';
```

### ❌ DON'T:
```php
// Don't nest too deeply (hard to read)
$x = ($a) ? (($b) ? (($c) ? "d" : "e") : "f") : "g";

// Don't use for complex logic
$result = ($a && $b || $c) ? (doThis() ? "yes" : "no") : "maybe";

// Don't use when multiple statements needed
// ❌ Can't do this:
$x = ($condition) ? (echo "yes"; $a = 1;) : (echo "no"; $a = 0;);
```

---

## Key Takeaways

✅ Ternary operator = shorthand for simple if-else  
✅ Always has **3 parts**: condition, true value, false value  
✅ Elvis `?:` checks **truthiness** (0, "", false, null = falsy)  
✅ Null coalescing `??` checks **existence and null only**  
✅ Great for **inline assignments** and **default values**  
✅ Keep it **simple** - complex logic needs regular if-else  
✅ **Readability > Brevity** - don't sacrifice clarity  

The conditional operator is powerful for writing concise code, but remember: **clear code is better than clever code!**