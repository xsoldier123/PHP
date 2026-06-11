# Break and Continue Statements in PHP

The **break** and **continue** statements are control flow statements used to alter the normal execution of loops and switch statements.

---

## Break Statement

The `break` statement is used to **exit** from a loop or switch statement immediately, regardless of the loop condition.

### Syntax
```php
break;        // Exit current loop/switch
break n;      // Exit n levels of nested loops
```

### Examples with Loops

**Basic break in a loop:**
```php
for ($i = 1; $i <= 10; $i++) {
    if ($i == 5) {
        break;  // Exit the loop when $i equals 5
    }
    echo $i . " ";
}
// Output: 1 2 3 4
```

**Break in a while loop:**
```php
$count = 0;
while (true) {
    echo $count . " ";
    $count++;
    if ($count >= 5) {
        break;  // Exit infinite loop
    }
}
// Output: 0 1 2 3 4
```

**Break with nested loops:**
```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        if ($j == 2) {
            break;  // Exits only the inner loop
        }
        echo "($i, $j) ";
    }
}
// Output: (1, 1) (2, 1) (3, 1)
```

**Break with level (nested loops):**
```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        if ($j == 2) {
            break 2;  // Exits both loops
        }
        echo "($i, $j) ";
    }
}
// Output: (1, 1)
```

---

## Continue Statement

The `continue` statement **skips the rest of the current iteration** and moves to the next iteration of the loop.

### Syntax
```php
continue;     // Skip to next iteration of current loop
continue n;   // Skip to next iteration of nth enclosing loop
```

### Examples with Loops

**Basic continue in a loop:**
```php
for ($i = 1; $i <= 5; $i++) {
    if ($i == 3) {
        continue;  // Skip when $i equals 3
    }
    echo $i . " ";
}
// Output: 1 2 4 5
```

**Continue to skip even numbers:**
```php
for ($i = 1; $i <= 10; $i++) {
    if ($i % 2 == 0) {
        continue;  // Skip even numbers
    }
    echo $i . " ";
}
// Output: 1 3 5 7 9
```

**Continue in a while loop:**
```php
$i = 0;
while ($i < 5) {
    $i++;
    if ($i == 3) {
        continue;  // Skip when $i is 3
    }
    echo $i . " ";
}
// Output: 1 2 4 5
```

**Continue with nested loops:**
```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        if ($j == 2) {
            continue;  // Skip j=2 in inner loop
        }
        echo "($i, $j) ";
    }
}
// Output: (1, 1) (1, 3) (2, 1) (2, 3) (3, 1) (3, 3)
```

**Continue with level:**
```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        if ($j == 2) {
            continue 2;  // Skip to next iteration of outer loop
        }
        echo "($i, $j) ";
    }
    echo "| ";
}
// Output: (1, 1) (2, 1) (3, 1)
```

---

## Practical Examples

**Finding the first match:**
```php
$numbers = [1, 3, 5, 8, 10, 12];
$target = 8;

foreach ($numbers as $num) {
    if ($num == $target) {
        echo "Found: $num";
        break;  // Stop searching once found
    }
}
// Output: Found: 8
```

**Processing valid data only:**
```php
$values = [10, -5, 20, 0, 30, -8];

foreach ($values as $value) {
    if ($value <= 0) {
        continue;  // Skip non-positive values
    }
    echo $value . " ";
}
// Output: 10 20 30
```

---

## Key Differences

| Feature | Break | Continue |
|---------|-------|----------|
| Purpose | Exits the loop/switch completely | Skips current iteration, continues loop |
| Effect | Stops all remaining iterations | Skips only current iteration |
| Use case | When you've found what you need | When you want to skip certain values |

## Important Notes

- Both statements work with `for`, `foreach`, `while`, and `do-while` loops
- Using numeric arguments (`break 2`, `continue 2`) should be done carefully as it can make code harder to read
- `break` is required in `switch` statements to prevent fall-through
- Be careful with `continue` in `while` loops to avoid infinite loops