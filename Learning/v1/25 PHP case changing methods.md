# 🔠 PHP Case Changing Methods

PHP provides several **built-in string functions** to change the **letter case** of text — making it **lowercase, uppercase, or title case**.

These are extremely useful for formatting user input, names, or text before display or storage.

---

## 🧩 Common Case Changing Functions

| Function | Description |
|-----------|--------------|
| `strtolower()` | Converts all characters to lowercase |
| `strtoupper()` | Converts all characters to uppercase |
| `ucfirst()` | Converts first letter of a string to uppercase |
| `lcfirst()` | Converts first letter of a string to lowercase |
| `ucwords()` | Converts first letter of each word to uppercase |
| `mb_strtolower()` | Multibyte version for Unicode strings |
| `mb_strtoupper()` | Multibyte version for Unicode strings |

---

## 🔹 1. `strtolower()` – Convert to Lowercase

### ✅ Example:
```php
$text = "HELLO WORLD!";
echo strtolower($text);
```

**Output:**
```
hello world!
```

---

## 🔹 2. `strtoupper()` – Convert to Uppercase

### ✅ Example:
```php
$text = "hello world!";
echo strtoupper($text);
```

**Output:**
```
HELLO WORLD!
```

---

## 🔹 3. `ucfirst()` – Uppercase First Letter

### ✅ Example:
```php
$text = "php is awesome!";
echo ucfirst($text);
```

**Output:**
```
Php is awesome!
```

---

## 🔹 4. `lcfirst()` – Lowercase First Letter

### ✅ Example:
```php
$text = "PHP Is Awesome!";
echo lcfirst($text);
```

**Output:**
```
pHP Is Awesome!
```

---

## 🔹 5. `ucwords()` – Capitalize Each Word

### ✅ Example:
```php
$text = "welcome to php world";
echo ucwords($text);
```

**Output:**
```
Welcome To Php World
```

---

## ⚙️ Combine Functions for Custom Formats

### 🔸 Example 1: Proper Case Sentence
```php
$text = "hELLo WoRLD!";
$formatted = ucfirst(strtolower($text));
echo $formatted;
```

**Output:**
```
Hello world!
```

---

### 🔸 Example 2: Title Case (like Names)
```php
$name = "ebrAt hosein";
echo ucwords(strtolower($name));
```

**Output:**
```
Ebrat Hosein
```

---

### 🔸 Example 3: Sentence Case for a Paragraph
```php
$sentence = "thiS IS a sample SENTENCE.";
echo ucfirst(strtolower($sentence));
```

**Output:**
```
This is a sample sentence.
```

---

## 🌐 Unicode / Multibyte Safe Versions

When working with **non-English characters** (e.g., Bangla, Arabic, Chinese),  
use the **`mb_` functions** instead of normal ones.

### ✅ Example:
```php
$text = "বাংলাদেশ সুন্দর দেশ।";
echo mb_strtoupper($text, "UTF-8");
```

**Output:**
```
বাংলাদেশ সুন্দর দেশ।
```

> 🧠 Use `mb_strtolower()` or `mb_strtoupper()` for multi-language support.

---

## 💡 Practical Example: Format User Input

```php
$name = "ebrAt hoSein";
$email = "Ebrat@Example.Com";

$formattedName = ucwords(strtolower($name));
$formattedEmail = strtolower($email);

echo "Name: $formattedName<br>";
echo "Email: $formattedEmail";
```

**Output:**
```
Name: Ebrat Hosein
Email: ebrat@example.com
```

---

## 🔠 Summary Table

| Function | Input | Output |
|-----------|--------|--------|
| `strtolower("HELLO")` | HELLO | hello |
| `strtoupper("hello")` | hello | HELLO |
| `ucfirst("php")` | php | Php |
| `lcfirst("PHP")` | PHP | pHP |
| `ucwords("welcome to php")` | welcome to php | Welcome To Php |
| `mb_strtoupper("hello")` | hello | HELLO |

---

## 🧩 Summary

- 🧠 **`strtolower()`** → all lowercase  
- 🔠 **`strtoupper()`** → all uppercase  
- 🔹 **`ucfirst()`** → first letter uppercase  
- 🔹 **`lcfirst()`** → first letter lowercase  
- 📚 **`ucwords()`** → capitalize each word  
- 🌍 **`mb_` versions** → for Unicode-safe strings  
- ✅ Combine them for proper name, sentence, or title formatting  
