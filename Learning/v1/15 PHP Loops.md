# Loops in PHP

PHP provides several types of loops to execute code repeatedly. Here's a comprehensive overview:

## 1. **for Loop**
Used when you know how many times you want to iterate.

```php
for ($i = 0; $i < 5; $i++) {
    echo "Number: $i<br>";
}
// Output: Number: 0, 1, 2, 3, 4
```

## 2. **while Loop**
Executes as long as a condition is true.

```php
$x = 1;
while ($x <= 5) {
    echo "The number is: $x<br>";
    $x++;
}
```

## 3. **do...while Loop**
Similar to while, but executes at least once before checking the condition.

```php
$x = 1;
do {
    echo "The number is: $x<br>";
    $x++;
} while ($x <= 5);
```

## 4. **foreach Loop**
Perfect for iterating over arrays.

```php
// Indexed array
$colors = array("red", "green", "blue");
foreach ($colors as $color) {
    echo "$color<br>";
}

// Associative array
$person = array("name" => "John", "age" => 30);
foreach ($person as $key => $value) {
    echo "$key: $value<br>";
}
```

## Loop Control Statements

- **break**: Exits the loop entirely
```php
for ($i = 0; $i < 10; $i++) {
    if ($i == 5) break;
    echo $i;
}
// Output: 01234
```

- **continue**: Skips the current iteration
```php
for ($i = 0; $i < 5; $i++) {
    if ($i == 2) continue;
    echo $i;
}
// Output: 0134
```

## Nested Loops

```php
for ($i = 1; $i <= 3; $i++) {
    for ($j = 1; $j <= 3; $j++) {
        echo "($i, $j) ";
    }
    echo "<br>";
}
```

Each loop type has its use case depending on whether you know the iteration count in advance, need to check conditions, or are working with arrays.