# Break and Continue Statements in PHP Loops

**Break** and **Continue** are control statements that change the normal flow of loops. They give you more control over loop execution.

---

## Break Statement

The **break** statement **immediately exits** the current loop, regardless of the loop condition.

### Syntax
```php
break;        // Exit current loop
break 2;      // Exit 2 nested loops
```

### Break in For Loop
```php
for ($i = 1; $i <= 10; $i++) {
    if ($i == 5) {
        break; // Exit loop when $i is 5
    }
    echo "$i ";
}

// Output: 1 2 3 4
```

### Break in While Loop
```php
$x = 1;

while ($x <= 10) {
    if ($x == 6) {
        break; // Exit when $x is 6
    }
    echo "$x ";
    $x++;
}

// Output: 1 2 3 4 5
```

### Break in Do-While Loop
```php
$i = 1;

do {
    echo "$i ";
    if ($i == 4) {
        break; // Exit loop
    }
    $i++;
} while ($i <= 10);

// Output: 1 2 3 4
```

### Break in Foreach Loop
```php
$fruits = ["apple", "banana", "orange", "grape", "mango"];

foreach ($fruits as $fruit) {
    if ($fruit == "orange") {
        break; // Stop at orange
    }
    echo "$fruit ";
}

// Output: apple banana
```

---

## Continue Statement

The **continue** statement **skips** the rest of the current iteration and moves to the next iteration.

### Syntax
```php
continue;     // Skip to next iteration
continue 2;   // Skip to next iteration of outer loop
```

### Continue in For Loop
```php
for ($i = 1; $i <= 10; $i++) {
    if ($i % 2 == 0) {
        continue; // Skip even numbers
    }
    echo "$i ";
}

// Output: 1 3 5 7 9
```

### Continue in While Loop
```php
$x = 0;

while ($x < 10) {
    $x++;
    
    if ($x % 2 == 0) {
        continue; // Skip even numbers
    }
    echo "$x ";
}

// Output: 1 3 5 7 9
```

### Continue in Do-While Loop
```php
$i = 0;

do {
    $i++;
    
    if ($i == 3) {
        continue; // Skip when $i is 3
    }
    echo "$i ";
} while ($i < 6);

// Output: 1 2 4 5 6
```

### Continue in Foreach Loop
```php
$numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

foreach ($numbers as $number) {
    if ($number % 2 == 0) {
        continue; // Skip even numbers
    }
    echo "$number ";
}

// Output: 1 3 5 7 9
```

---

## Practical Examples

### Example 1: Search and Stop
```php
$users = ["Alice", "Bob", "Charlie", "David", "Eve"];
$searchFor = "Charlie";

foreach ($users as $user) {
    if ($user == $searchFor) {
        echo "Found: $user";
        break; // Stop searching once found
    }
}

// Output: Found: Charlie
```

### Example 2: Skip Invalid Data
```php
$prices = [10, 20, -5, 30, 0, 40, -10, 50];
$total = 0;

foreach ($prices as $price) {
    if ($price <= 0) {
        continue; // Skip invalid prices
    }
    $total += $price;
}

echo "Total: \$$total";

// Output: Total: $150
```

### Example 3: Process Until Error
```php
$files = ["file1.txt", "file2.txt", "corrupted.txt", "file3.txt"];

foreach ($files as $file) {
    echo "Processing $file...<br>";
    
    if ($file == "corrupted.txt") {
        echo "Error found! Stopping.<br>";
        break; // Stop processing
    }
    
    echo "$file processed successfully!<br>";
}

// Output:
// Processing file1.txt...
// file1.txt processed successfully!
// Processing file2.txt...
// file2.txt processed successfully!
// Processing corrupted.txt...
// Error found! Stopping.
```

### Example 4: Skip Multiples of 3
```php
for ($i = 1; $i <= 20; $i++) {
    if ($i % 3 == 0) {
        continue; // Skip multiples of 3
    }
    echo "$i ";
}

// Output: 1 2 4 5 7 8 10 11 13 14 16 17 19 20
```

### Example 5: Validate Form Fields
```php
$formData = [
    "name" => "John",
    "email" => "",
    "phone" => "1234567890",
    "address" => ""
];

$errors = [];

foreach ($formData as $field => $value) {
    if (!empty($value)) {
        continue; // Skip valid fields
    }
    $errors[] = "$field is required";
}

if (!empty($errors)) {
    foreach ($errors as $error) {
        echo "$error<br>";
    }
}

// Output:
// email is required
// address is required
```

### Example 6: Find First Prime Number
```php
$numbers = [4, 6, 8, 9, 11, 12, 13, 15];

foreach ($numbers as $number) {
    $isPrime = true;
    
    for ($i = 2; $i <= sqrt($number); $i++) {
        if ($number % $i == 0) {
            $isPrime = false;
            break; // Not prime, stop checking
        }
    }
    
    if ($isPrime && $number > 1) {
        echo "First prime number: $number";
        break; // Found it, stop searching
    }
}

// Output: First prime number: 11
```

---

## Nested Loops with Break/Continue

### Break in Nested Loops (single level)
```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        if ($j == 2) {
            break; // Only breaks inner loop
        }
        echo "($i, $j) ";
    }
    echo "<br>";
}

// Output:
// (1, 1)
// (2, 1)
// (3, 1)
```

### Break Multiple Levels
```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        if ($j == 2) {
            break 2; // Breaks both loops
        }
        echo "($i, $j) ";
    }
}

// Output: (1, 1)
```

### Continue in Nested Loops
```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        if ($j == 2) {
            continue; // Skip $j = 2
        }
        echo "($i, $j) ";
    }
    echo "<br>";
}

// Output:
// (1, 1) (1, 3)
// (2, 1) (2, 3)
// (3, 1) (3, 3)
```

### Continue Outer Loop
```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        if ($j == 2) {
            continue 2; // Continue outer loop
        }
        echo "($i, $j) ";
    }
    echo "<br>";
}

// Output:
// (1, 1)
// (2, 1)
// (3, 1)
```

---

## Real-World Examples

### Example: Login Attempt Limit
```php
$maxAttempts = 3;
$attempts = 0;
$correctPassword = "secret123";

while ($attempts < $maxAttempts) {
    $attempts++;
    $password = getUserInput(); // hypothetical function
    
    if ($password == $correctPassword) {
        echo "Login successful!";
        break; // Exit loop on success
    }
    
    echo "Incorrect password. Attempt $attempts of $maxAttempts<br>";
}

if ($attempts == $maxAttempts) {
    echo "Account locked!";
}
```

### Example: Shopping Cart Discount
```php
$cart = [
    ["item" => "Laptop", "price" => 1000, "quantity" => 1],
    ["item" => "Mouse", "price" => 25, "quantity" => 2],
    ["item" => "Keyboard", "price" => 75, "quantity" => 1],
    ["item" => "Free Gift", "price" => 0, "quantity" => 1]
];

$total = 0;

foreach ($cart as $item) {
    if ($item['price'] == 0) {
        continue; // Skip free items in calculation
    }
    
    $subtotal = $item['price'] * $item['quantity'];
    $total += $subtotal;
    echo "{$item['item']}: \$$subtotal<br>";
}

echo "Total: \$$total";

// Output:
// Laptop: $1000
// Mouse: $50
// Keyboard: $75
// Total: $1125
```

### Example: Find Duplicate
```php
$numbers = [1, 2, 3, 4, 2, 5, 6];
$seen = [];
$duplicate = null;

foreach ($numbers as $number) {
    if (in_array($number, $seen)) {
        $duplicate = $number;
        break; // Found duplicate, stop
    }
    $seen[] = $number;
}

if ($duplicate !== null) {
    echo "First duplicate: $duplicate";
}

// Output: First duplicate: 2
```

### Example: Process Only Active Users
```php
$users = [
    ["name" => "Alice", "active" => true],
    ["name" => "Bob", "active" => false],
    ["name" => "Charlie", "active" => true],
    ["name" => "David", "active" => false]
];

echo "Active users:<br>";
foreach ($users as $user) {
    if (!$user['active']) {
        continue; // Skip inactive users
    }
    echo "- {$user['name']}<br>";
}

// Output:
// Active users:
// - Alice
// - Charlie
```

---

## Break vs Continue: Quick Comparison

| Feature | Break | Continue |
|---------|-------|----------|
| **Action** | Exits the loop completely | Skips current iteration only |
| **Next Step** | Goes to code after loop | Goes to next iteration |
| **Use Case** | Stop when condition met | Skip specific items |
| **Iterations** | Stops all remaining | Continues with remaining |

### Visual Example
```php
// Break - stops at 5
for ($i = 1; $i <= 10; $i++) {
    if ($i == 5) break;
    echo "$i ";
}
// Output: 1 2 3 4

// Continue - skips 5
for ($i = 1; $i <= 10; $i++) {
    if ($i == 5) continue;
    echo "$i ";
}
// Output: 1 2 3 4 6 7 8 9 10
```

---

## Important Notes

1. **Break exits the loop entirely** - no more iterations
2. **Continue skips to the next iteration** - loop continues
3. **Both can specify levels** - `break 2`, `continue 2` for nested loops
4. **Use wisely** - overuse can make code harder to read
5. **Alternative to goto** - better structured control flow

## Common Mistakes

### Mistake 1: Continue in Switch
```php
// WRONG - Continue doesn't work in switch
switch ($value) {
    case 1:
        continue; // This is an error!
    case 2:
        break;
}

// CORRECT
switch ($value) {
    case 1:
        break; // Use break in switch
    case 2:
        break;
}
```

### Mistake 2: Forgetting to Increment
```php
// WRONG - Infinite loop!
$i = 0;
while ($i < 10) {
    if ($i == 5) {
        continue; // $i never increments!
    }
    echo $i;
    $i++;
}

// CORRECT
$i = 0;
while ($i < 10) {
    $i++; // Increment first
    if ($i == 5) {
        continue;
    }
    echo $i;
}
```

**Break** and **Continue** are powerful tools for controlling loop flow, making your code more efficient and readable when used appropriately!