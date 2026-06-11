# Do-While Loop in PHP

The **do-while loop** executes a block of code at least once, and then repeats the loop as long as a specified condition is true. The key difference from a regular while loop is that the condition is checked **after** executing the code block.

## Basic Syntax

```php
do {
    // code to be executed
} while (condition);
```

**Note:** The semicolon `;` at the end is required!

## Simple Example

```php
$x = 1;

do {
    echo "Number: $x<br>";
    $x++;
} while ($x <= 5);

// Output:
// Number: 1
// Number: 2
// Number: 3
// Number: 4
// Number: 5
```

## Key Difference: Do-While vs While

### Do-While (executes at least once)
```php
$x = 10;

do {
    echo "This will print once!<br>";
    $x++;
} while ($x < 5);

// Output: This will print once!
// Even though condition is false, code runs first
```

### While (may never execute)
```php
$x = 10;

while ($x < 5) {
    echo "This will NOT print";
    $x++;
}

// Output: (nothing)
// Condition is false from the start
```

## How It Works

```php
$i = 1;

do {
    echo $i . " ";
    $i++;
} while ($i <= 3);

// Step-by-step:
// 1. Execute code → print 1, $i becomes 2
// 2. Check condition: $i <= 3? Yes → continue
// 3. Execute code → print 2, $i becomes 3
// 4. Check condition: $i <= 3? Yes → continue
// 5. Execute code → print 3, $i becomes 4
// 6. Check condition: $i <= 3? No → stop

// Output: 1 2 3
```

## Practical Examples

### Menu System
```php
$choice = 0;

do {
    echo "=== Menu ===\n";
    echo "1. Option 1\n";
    echo "2. Option 2\n";
    echo "3. Exit\n";
    
    $choice = getUserInput(); // hypothetical function
    
    // Process choice...
    
} while ($choice != 3);

echo "Goodbye!";
```

### Input Validation
```php
$password = "";

do {
    echo "Enter password: ";
    $password = trim(getUserInput());
    
    if ($password != "secret123") {
        echo "Incorrect! Try again.<br>";
    }
    
} while ($password != "secret123");

echo "Access granted!";
```

### Dice Roll Game
```php
$roll = 0;
$attempts = 0;

echo "Rolling until we get a 6...<br>";

do {
    $roll = rand(1, 6);
    $attempts++;
    echo "Roll $attempts: $roll<br>";
} while ($roll != 6);

echo "Got a 6 in $attempts attempts!";
```

### Countdown Timer
```php
$countdown = 5;

do {
    echo "$countdown...<br>";
    $countdown--;
} while ($countdown > 0);

echo "Blast off!";

// Output:
// 5...
// 4...
// 3...
// 2...
// 1...
// Blast off!
```

### Reading User Input Until Valid
```php
$age = -1;

do {
    echo "Enter your age (1-120): ";
    $age = (int)getUserInput();
    
    if ($age < 1 || $age > 120) {
        echo "Invalid age! Please try again.<br>";
    }
    
} while ($age < 1 || $age > 120);

echo "You are $age years old.";
```

### Sum Until Zero
```php
$sum = 0;
$number = 0;

echo "Enter numbers (0 to stop):<br>";

do {
    $number = (int)getUserInput();
    $sum += $number;
    echo "Current sum: $sum<br>";
} while ($number != 0);

echo "Final sum: $sum";
```

## Using break and continue

### break - Exit the loop
```php
$i = 1;

do {
    if ($i == 5) {
        break; // Exit when $i is 5
    }
    echo "$i ";
    $i++;
} while ($i <= 10);

// Output: 1 2 3 4
```

### continue - Skip current iteration
```php
$i = 0;

do {
    $i++;
    
    if ($i % 2 == 0) {
        continue; // Skip even numbers
    }
    
    echo "$i ";
} while ($i < 10);

// Output: 1 3 5 7 9
```

## Nested Do-While Loops

```php
$i = 1;

do {
    $j = 1;
    
    do {
        echo "($i,$j) ";
        $j++;
    } while ($j <= 3);
    
    echo "<br>";
    $i++;
} while ($i <= 3);

// Output:
// (1,1) (1,2) (1,3)
// (2,1) (2,2) (2,3)
// (3,1) (3,2) (3,3)
```

## Common Use Cases

### 1. At Least One Execution Required
```php
// Display prompt at least once
do {
    echo "Press 'q' to quit: ";
    $key = getKey();
} while ($key != 'q');
```

### 2. Retry Logic
```php
$connected = false;
$attempts = 0;
$maxAttempts = 3;

do {
    $attempts++;
    echo "Attempt $attempts to connect...<br>";
    $connected = tryConnection(); // hypothetical function
    
    if (!$connected && $attempts < $maxAttempts) {
        echo "Failed. Retrying...<br>";
        sleep(1);
    }
} while (!$connected && $attempts < $maxAttempts);

if ($connected) {
    echo "Connected successfully!";
} else {
    echo "Connection failed after $attempts attempts.";
}
```

### 3. Generate Random Until Condition Met
```php
$target = 50;
$guess = 0;
$tries = 0;

do {
    $guess = rand(1, 100);
    $tries++;
    echo "Try $tries: Generated $guess<br>";
} while ($guess != $target);

echo "Found $target in $tries tries!";
```

## Important Notes

1. **Always executes at least once** - This is the defining characteristic
2. **Don't forget the semicolon** at the end of `while (condition);`
3. **Update variables inside the loop** to avoid infinite loops
4. **Best for validation** where you need to prompt at least once

## When to Use Do-While

✅ **Use do-while when:**
- Code must run at least once
- User input validation/prompts
- Menu systems
- Retry mechanisms
- "Do something, then check if we should continue"

❌ **Don't use do-while when:**
- Loop might not need to run at all
- A regular while or for loop is clearer

## Infinite Loop Warning

```php
// AVOID THIS - Infinite loop!
do {
    echo "Forever! ";
    // No way to change condition
} while (true);
```

```php
// CORRECT - Has exit condition
$count = 0;
do {
    echo "Safe! ";
    $count++;
} while ($count < 5);
```

The do-while loop is perfect when you need guaranteed execution at least once, making it ideal for interactive programs, validation, and retry logic!