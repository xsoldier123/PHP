# 🔁 Recursion in PHP

**Recursion** is a programming technique where a **function calls itself** to solve smaller instances of the same problem.  
It continues until a certain condition (called the **base case**) is met.

---

## 🧠 Basic Concept

A recursive function must have:
1. **Base Case** → the condition to stop recursion  
2. **Recursive Case** → the function calling itself

---

## 🧩 Syntax

```php
function functionName() {
    if (condition) {
        // base case (stop calling itself)
    } else {
        // recursive case (call itself)
        functionName();
    }
}
```

---

## ✅ Simple Example

```php
function countdown($number) {
    if ($number <= 0) {
        echo "Done!";
    } else {
        echo "$number<br>";
        countdown($number - 1); // recursive call
    }
}

countdown(5);
```

**Output:**
```
5
4
3
2
1
Done!
```

---

## ⚙️ Step-by-Step Explanation

1. `countdown(5)` → prints 5 → calls `countdown(4)`  
2. `countdown(4)` → prints 4 → calls `countdown(3)`  
3. continues until `$number <= 0`  
4. prints “Done!” and stops recursion  

---

## 💡 Practical Examples

### 1️⃣ Factorial of a Number

The factorial of a number `n! = n × (n−1) × (n−2) × … × 1`

```php
function factorial($n) {
    if ($n == 0) {
        return 1; // base case
    } else {
        return $n * factorial($n - 1); // recursive case
    }
}

echo factorial(5);
```

**Output:**  
`120`

---

### 2️⃣ Sum of Numbers (1 to n)

```php
function sumNumbers($n) {
    if ($n == 0) {
        return 0;
    } else {
        return $n + sumNumbers($n - 1);
    }
}

echo sumNumbers(5); // Output: 15
```

**Explanation:**  
`5 + 4 + 3 + 2 + 1 = 15`

---

### 3️⃣ Print Array Elements Recursively

```php
function printArray($arr, $index = 0) {
    if ($index < count($arr)) {
        echo $arr[$index] . "<br>";
        printArray($arr, $index + 1);
    }
}

$fruits = ["Apple", "Banana", "Mango"];
printArray($fruits);
```

---

### 4️⃣ Fibonacci Series (Recursion)

Fibonacci: `0, 1, 1, 2, 3, 5, 8, 13, ...`

```php
function fibonacci($n) {
    if ($n == 0) return 0;
    if ($n == 1) return 1;
    return fibonacci($n - 1) + fibonacci($n - 2);
}

for ($i = 0; $i < 10; $i++) {
    echo fibonacci($i) . " ";
}
```

**Output:**  
`0 1 1 2 3 5 8 13 21 34`

---

## ⚠️ Common Mistake: Missing Base Case

❌ Example (infinite recursion):
```php
function infinite() {
    echo "Running...<br>";
    infinite(); // no stopping condition
}
infinite();
```

💥 This will crash with an **"Allowed memory size exhausted"** error!

✅ Always include a **base case** to stop recursion.

---

## 🧱 Recursive vs Iterative (Loop)

| Task | Recursive | Iterative (Loop) |
|------|------------|------------------|
| Factorial | Easier to write | Faster, less memory |
| Counting | Possible | Simpler |
| File structure traversal | Natural | Harder to manage |
| Memory use | Higher (stack calls) | Lower |

---

## 🧩 Real-Life Example: Directory Traversal

```php
function listFiles($dir) {
    $files = scandir($dir);
    foreach ($files as $file) {
        if ($file == '.' || $file == '..') continue;

        if (is_dir("$dir/$file")) {
            echo "<strong>Directory:</strong> $file<br>";
            listFiles("$dir/$file"); // recursive call
        } else {
            echo "File: $file<br>";
        }
    }
}

listFiles("myFolder");
```

---

## 🧠 Summary

- 🔁 **Recursion** = a function calling itself  
- 🧩 Must have a **base case** to prevent infinite loops  
- ⚙️ Useful for problems like **factorials, Fibonacci, tree structures, and nested folders**  
- ⚠️ Recursive code is elegant but may use more memory than loops
