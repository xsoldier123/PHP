# 📘 PHP Functions Full Guide (String, Number, and More)

## 🧩 1. String Functions

### ✅ strlen()
Returns the length of a string.
```php
echo strlen("Hello World"); // 11
```

---

### ✅ strrev()
Reverses a string.
```php
echo strrev("Hello"); // olleH
```

---

### ✅ substr()
Extracts part of a string.
```php
echo substr("Hello World", 0, 5); // Hello
echo substr("Hello World", 6);    // World
```

---

### ✅ strtoupper() / strtolower()
Converts to uppercase / lowercase.
```php
echo strtoupper("hello"); // HELLO
echo strtolower("HELLO"); // hello
```

---

### ✅ ucfirst() / lcfirst() / ucwords()
Changes the first letter case.
```php
echo ucfirst("hello world"); // Hello world
echo lcfirst("Hello World"); // hello World
echo ucwords("hello world"); // Hello World
```

---

### ✅ str_replace()
Replaces text within a string.
```php
echo str_replace("World", "PHP", "Hello World"); // Hello PHP
```

---

### ✅ str_repeat()
Repeats a string.
```php
echo str_repeat("Hi ", 3); // Hi Hi Hi
```

---

### ✅ strpos() / strrpos()
Finds the position of a substring.
```php
echo strpos("Hello World", "World"); // 6
```

---

### ✅ trim() / ltrim() / rtrim()
Removes whitespace or characters.
```php
$str = "   Hello World   ";
echo trim($str); // Hello World
```

---

### ✅ strcmp() / strcasecmp()
Compare two strings (case-sensitive / insensitive).
```php
echo strcmp("Hello", "Hello"); // 0
echo strcasecmp("hello", "HELLO"); // 0
```

---

### ✅ str_word_count()
Counts the number of words in a string.
```php
echo str_word_count("Hello world from PHP!"); // 4
```

---

### ✅ explode() / implode()
Splits or joins strings.
```php
$arr = explode(" ", "Hello World PHP");
print_r($arr); // Array ( [0] => Hello [1] => World [2] => PHP )

$str = implode("-", $arr);
echo $str; // Hello-World-PHP
```

---

### ✅ htmlspecialchars() / htmlentities()
Converts HTML special characters.
```php
echo htmlspecialchars("<b>Bold</b>"); // &lt;b&gt;Bold&lt;/b&gt;
```

---

### ✅ addslashes() / stripslashes()
Adds or removes backslashes in a string.
```php
$str = addslashes("John's book");
echo $str; // John's book
```

---

## 🎲 2. Number & Math Functions

### ✅ rand() / mt_rand()
Generates random numbers.
```php
echo rand(1, 10); // Random between 1–10
```

---

### ✅ round() / ceil() / floor()
Rounds a number.
```php
echo round(3.6); // 4
echo ceil(3.1);  // 4
echo floor(3.9); // 3
```

---

### ✅ abs()
Returns absolute (positive) value.
```php
echo abs(-10); // 10
```

---

### ✅ min() / max()
Returns smallest/largest value.
```php
echo min(10, 5, 8); // 5
echo max(10, 5, 8); // 10
```

---

### ✅ sqrt() / pow()
Square root and power.
```php
echo sqrt(16); // 4
echo pow(2, 3); // 8
```

---

## 📅 3. Date & Time (Basic)
```php
echo date("Y-m-d"); // 2025-10-29
echo time(); // Current timestamp
```

---

## 🔢 4. Array Related (Commonly used)
```php
$arr = ["PHP", "Java", "Python"];
echo count($arr); // 3
sort($arr);  // Sort ascending
rsort($arr); // Sort descending
```

---

## 💡 5. Other Useful Functions

| Function | Description | Example |
|-----------|--------------|----------|
| `is_string()` | Check if variable is string | `is_string("abc")` |
| `is_numeric()` | Check if variable is number | `is_numeric(123)` |
| `number_format()` | Format number | `number_format(12345.678, 2)` → `12,345.68` |
| `str_shuffle()` | Shuffle characters | `str_shuffle("abc")` → `cab` |
| `substr_count()` | Count occurrences of substring | `substr_count("banana", "a")` → `3` |

---

### ✅ Bonus Tips:
- Use `var_dump($var);` to check data type & value.
- Combine string functions to clean or modify input.
- Always validate user input in real-world apps.

---

### 🧠 Summary:
PHP provides **100+ built-in functions** for:
- Text processing
- Numbers & Math
- Arrays
- Dates & Time
- HTML handling

You can explore all with:
```php
print_r(get_defined_functions());
```

---

**📄 Created by:** ChatGPT (PHP Full Function Guide 2025)
