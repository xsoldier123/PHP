# 🌀 While Loop in PHP

The **while loop** is used when **you don’t know in advance** how many times you want to execute a block of code.  
It runs **as long as a given condition is true**.

---

## 🧠 Basic Syntax

```php
while (condition) {
    // code to be executed
}
```

**How it works:**
1. The condition is checked first.  
2. If it’s **true**, the code inside the loop executes.  
3. Then it checks the condition again — if still true, it repeats.  
4. Stops when the condition becomes **false**.

---

## ✅ Simple Example

```php
$i = 1;

while ($i <= 5) {
    echo "Number: $i<br>";
    $i++;
}
```

**Output:**
```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```

---

## ⚙️ Step-by-Step Explanation

1. `$i = 1` → Initialization  
2. Check `$i <= 5` → true → print → `$i++`  
3. `$i = 2` → Check again → true → print  
4. Repeats until `$i = 6`  
5. `$i <= 5` → false → stop

---

## 🔁 Common Patterns

### Counting Up
```php
$i = 1;
while ($i <= 10) {
    echo "$i ";
    $i++;
}
// Output: 1 2 3 4 5 6 7 8 9 10
```

### Counting Down
```php
$i = 10;
while ($i >= 1) {
    echo "$i ";
    $i--;
}
// Output: 10 9 8 7 6 5 4 3 2 1
```

### Skip Numbers
```php
$i = 0;
while ($i <= 10) {
    echo "$i ";
    $i += 2;
}
// Output: 0 2 4 6 8 10
```

---

## 💡 Practical Examples

### Sum of Numbers
```php
$i = 1;
$sum = 0;

while ($i <= 100) {
    $sum += $i;
    $i++;
}

echo "Sum of 1 to 100: $sum";
```

**Output:**  
`Sum of 1 to 100: 5050`

---

### Multiplication Table
```php
$number = 5;
$i = 1;

while ($i <= 10) {
    echo "$number x $i = " . ($number * $i) . "<br>";
    $i++;
}
```

---

### Loop Through Array
```php
$fruits = ["apple", "banana", "orange"];
$i = 0;

while ($i < count($fruits)) {
    echo "Fruit: " . $fruits[$i] . "<br>";
    $i++;
}
```

---

## 🚫 Infinite Loop Warning
If you **forget to update** the loop variable, it can run forever!

❌ Example (infinite loop):
```php
$i = 1;
while ($i <= 5) {
    echo "$i "; // No increment! $i never changes
}
```

✅ Fix:
```php
$i = 1;
while ($i <= 5) {
    echo "$i ";
    $i++;
}
```

---

## 🧩 Using `break` and `continue`

### break – stop the loop early
```php
$i = 1;
while ($i <= 10) {
    if ($i == 6) break;
    echo "$i ";
    $i++;
}
// Output: 1 2 3 4 5
```

### continue – skip current iteration
```php
$i = 0;
while ($i < 10) {
    $i++;
    if ($i % 2 == 0) continue;
    echo "$i ";
}
// Output: 1 3 5 7 9
```

---

## ⚖️ While vs For Loop

| Feature | `for` Loop | `while` Loop |
|----------|-------------|--------------|
| When to use | When number of iterations is known | When iterations depend on condition |
| Initialization | Inside loop header | Usually before loop |
| Counter | Commonly used | Optional |
| Example | Counting from 1–10 | Waiting for user input |

---

## 🧱 Alternative Syntax (for templates)

```php
<?php $i = 1; ?>
<?php while ($i <= 5): ?>
    <p>Item <?php echo $i; ?></p>
    <?php $i++; ?>
<?php endwhile; ?>
```

---

## 🧩 Summary

- ✅ Use **while** when you **don’t know how many times** the loop should run.  
- ⚠️ Always **update** the variable inside the loop to avoid infinite loops.  
- 🌀 Perfect for loops that depend on **changing conditions**, like reading from a file or waiting for input.
