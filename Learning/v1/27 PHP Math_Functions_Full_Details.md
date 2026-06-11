# 🧮 PHP Math Functions (Full Details)

PHP provides many built-in math functions that help perform calculations easily.

---

## 🔹 1. ceil()
Rounds a number **up** to the nearest integer.

```php
echo ceil(4.3);   // Output: 5
echo ceil(9.999); // Output: 10
```

## 🔹 2. floor()
Rounds a number **down** to the nearest integer.

```php
echo floor(4.7);  // Output: 4
echo floor(9.999); // Output: 9
```

## 🔹 3. round()
Rounds a number to the nearest integer (or specific decimal places).

```php
echo round(4.5);      // Output: 5
echo round(4.4);      // Output: 4
echo round(4.567, 2); // Output: 4.57
```

## 🔹 4. pow()
Raises a number to the power of another.

```php
echo pow(2, 3);  // Output: 8
echo pow(5, 2);  // Output: 25
```

## 🔹 5. sqrt()
Returns the square root of a number.

```php
echo sqrt(16);  // Output: 4
echo sqrt(25);  // Output: 5
```

## 🔹 6. abs()
Returns the **absolute (positive)** value of a number.

```php
echo abs(-10);  // Output: 10
echo abs(10);   // Output: 10
```

## 🔹 7. max()
Finds the **largest** number from a list or array.

```php
echo max(10, 20, 30); // Output: 30
echo max([3, 7, 1, 9]); // Output: 9
```

## 🔹 8. min()
Finds the **smallest** number from a list or array.

```php
echo min(10, 20, 30); // Output: 10
echo min([3, 7, 1, 9]); // Output: 1
```

## 🔹 9. rand()
Generates a random number.

```php
echo rand();         // Random number
echo rand(1, 10);    // Between 1 and 10
```

> 💡 Use `mt_rand()` for faster, better randomness.

## 🔹 10. mt_rand()
Generates a random number using the **Mersenne Twister algorithm**.

```php
echo mt_rand(1, 100); // Output: e.g. 47
```

## 🔹 11. pi()
Returns the value of π (pi).

```php
echo pi();  // Output: 3.1415926535898
```

## 🔹 12. deg2rad()
Converts degrees to radians.

```php
echo deg2rad(180); // Output: 3.1415926535898
```

## 🔹 13. rad2deg()
Converts radians to degrees.

```php
echo rad2deg(pi()); // Output: 180
```

## 🔹 14. sin(), cos(), tan()
Trigonometric functions (argument in radians).

```php
echo sin(pi()/2); // Output: 1
echo cos(0);      // Output: 1
echo tan(pi()/4); // Output: 1
```

## 🔹 15. asin(), acos(), atan()
Inverse trigonometric functions.

```php
echo asin(1);  // Output: 1.570796 (π/2)
echo acos(0);  // Output: 1.570796
echo atan(1);  // Output: 0.785398 (π/4)
```

## 🔹 16. exp()
Returns `e` raised to the power of a number.

```php
echo exp(1);  // Output: 2.718281828 (≈ e)
```

## 🔹 17. log()
Returns the **natural logarithm (base e)** of a number.

```php
echo log(2.718281828); // Output: 1
echo log(100, 10);     // Output: 2
```

## 🔹 18. log10()
Returns the base-10 logarithm.

```php
echo log10(1000); // Output: 3
```

## 🔹 19. bindec(), decbin(), dechex(), decoct()
Convert numbers between binary, decimal, hexadecimal, and octal.

```php
echo bindec('1010'); // Output: 10
echo decbin(10);     // Output: 1010
echo dechex(255);    // Output: ff
echo decoct(8);      // Output: 10
```

## 🔹 20. number_format()
Formats a number with grouped thousands.

```php
echo number_format(1234.5678, 2); // Output: 1,234.57
```

## 🔹 21. fmod()
Returns the **floating-point remainder** of division.

```php
echo fmod(7, 2.5); // Output: 2
```

## 🔹 22. intdiv()
Performs integer division.

```php
echo intdiv(10, 3); // Output: 3
```

## 🔹 23. hypot()
Calculates the length of the hypotenuse.

```php
echo hypot(3, 4); // Output: 5
```

## 🔹 24. getrandmax()
Shows the largest possible random number for `rand()`.

```php
echo getrandmax(); // Output: 2147483647
```

## 🔹 25. is_finite(), is_infinite(), is_nan()
Checks if a number is finite, infinite, or NaN.

```php
echo is_finite(1.9e411);   // false
echo is_infinite(1.9e411); // true
echo is_nan(acos(1.01));   // true
```

---

## ✅ Summary Table

| Function | Description |
|-----------|--------------|
| ceil() | Round up |
| floor() | Round down |
| round() | Round normally |
| pow() | Power |
| sqrt() | Square root |
| abs() | Absolute value |
| max()/min() | Largest/smallest |
| rand()/mt_rand() | Random number |
| pi() | Value of π |
| log(), log10() | Logarithms |
| exp() | e to power |
| sin(), cos(), tan() | Trigonometry |
| bindec(), dechex(), etc. | Number conversions |
| number_format() | Format number |
| fmod() | Floating remainder |
| intdiv() | Integer division |

---
