# For Loop in PHP

The **for loop** is used when you know in advance how many times you want to execute a block of code. It's the most commonly used loop for counting operations.

## Basic Syntax

```php
for (initialization; condition; increment) {
    // code to be executed
}
```

**Three parts:**
1. **Initialization**: Executed once at the start (set counter variable)
2. **Condition**: Checked before each iteration (continue if true)
3. **Increment**: Executed after each iteration (update counter)

## Simple Example

```php
for ($i = 0; $i < 5; $i++) {
    echo "Number: $i<br>";
}

// Output:
// Number: 0
// Number: 1
// Number: 2
// Number: 3
// Number: 4
```

## How It Works

```php
for ($i = 1; $i <= 3; $i++) {
    echo $i;
}

// Step-by-step:
// 1. $i = 1 (initialization)
// 2. Check: $i <= 3? Yes → execute code → print 1
// 3. $i++ → $i becomes 2
// 4. Check: $i <= 3? Yes → execute code → print 2
// 5. $i++ → $i becomes 3
// 6. Check: $i <= 3? Yes → execute code → print 3
// 7. $i++ → $i becomes 4
// 8. Check: $i <= 3? No → stop loop
```

## Common Patterns

### Counting Up
```php
for ($i = 1; $i <= 10; $i++) {
    echo "$i ";
}
// Output: 1 2 3 4 5 6 7 8 9 10
```

### Counting Down
```php
for ($i = 10; $i >= 1; $i--) {
    echo "$i ";
}
// Output: 10 9 8 7 6 5 4 3 2 1
```

### Skip Numbers (increment by 2)
```php
for ($i = 0; $i <= 10; $i += 2) {
    echo "$i ";
}
// Output: 0 2 4 6 8 10
```

### Increment by 5
```php
for ($i = 0; $i <= 50; $i += 5) {
    echo "$i ";
}
// Output: 0 5 10 15 20 25 30 35 40 45 50
```

## Practical Examples

### Loop Through Array (by index)
```php
$fruits = ["apple", "banana", "orange", "grape"];

for ($i = 0; $i < count($fruits); $i++) {
    echo "Fruit $i: " . $fruits[$i] . "<br>";
}
```

### Multiplication Table
```php
$number = 5;

for ($i = 1; $i <= 10; $i++) {
    echo "$number x $i = " . ($number * $i) . "<br>";
}

// Output:
// 5 x 1 = 5
// 5 x 2 = 10
// ... and so on
```

### Sum of Numbers
```php
$sum = 0;

for ($i = 1; $i <= 100; $i++) {
    $sum += $i;
}

echo "Sum of 1 to 100: $sum"; // Output: 5050
```

### Generate HTML List
```php
echo "<ul>";
for ($i = 1; $i <= 5; $i++) {
    echo "<li>Item $i</li>";
}
echo "</ul>";
```

## Nested For Loops

### Multiplication Table Grid
```php
for ($i = 1; $i <= 5; $i++) {
    for ($j = 1; $j <= 5; $j++) {
        echo ($i * $j) . " ";
    }
    echo "<br>";
}

// Output:
// 1 2 3 4 5
// 2 4 6 8 10
// 3 6 9 12 15
// 4 8 12 16 20
// 5 10 15 20 25
```

### Pattern Printing
```php
for ($i = 1; $i <= 5; $i++) {
    for ($j = 1; $j <= $i; $j++) {
        echo "* ";
    }
    echo "<br>";
}

// Output:
// *
// * *
// * * *
// * * * *
// * * * * *
```

## Loop Control Statements

### break - Exit the loop
```php
for ($i = 1; $i <= 10; $i++) {
    if ($i == 6) {
        break; // Stop when $i is 6
    }
    echo "$i ";
}
// Output: 1 2 3 4 5
```

### continue - Skip current iteration
```php
for ($i = 1; $i <= 10; $i++) {
    if ($i % 2 == 0) {
        continue; // Skip even numbers
    }
    echo "$i ";
}
// Output: 1 3 5 7 9
```

## Alternative Syntax (for templates)

```php
<?php for ($i = 1; $i <= 5; $i++): ?>
    <p>Paragraph <?php echo $i; ?></p>
<?php endfor; ?>
```

## Multiple Variables

```php
for ($i = 0, $j = 10; $i < 10; $i++, $j--) {
    echo "i=$i, j=$j<br>";
}

// Output:
// i=0, j=10
// i=1, j=9
// i=2, j=8
// ... and so on
```

## Empty Parts (advanced)

```php
// Infinite loop (all parts optional)
for (;;) {
    echo "This runs forever!";
    break; // Use break to exit
}

// Initialization outside
$i = 0;
for (; $i < 5; $i++) {
    echo $i;
}
```

## For vs While

**Use for loop when:**
- You know the exact number of iterations
- You need a counter variable
- Working with indexed arrays

**Use while loop when:**
- Number of iterations is unknown
- Loop depends on a condition that may change unpredictably

The for loop is perfect for situations where you need precise control over iteration counts!