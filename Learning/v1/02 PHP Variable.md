# Rules for Declaring PHP Variables

PHP variables are pretty straightforward, but there are some important rules you must follow:

## Basic Syntax
All PHP variables start with a **dollar sign ($)** followed by the variable name:
```php
$name = "Ebrat";
$age = 19;
```

## The Rules

**1. Must start with a dollar sign ($)**
```php
$variable = "correct";
variable = "wrong"; // Error!
```

**2. Variable name must start with a letter or underscore (_)**
```php
$name = "correct";
$_name = "correct";
$9name = "wrong"; // Error!
```

**3. Can only contain letters, numbers, and underscores**
```php
$user_name = "correct";
$userName = "correct";
$user123 = "correct";
$user-name = "wrong"; // Error!
$user name = "wrong"; // Error!
```

**4. Variable names are case-sensitive**
```php
$name = "Ebrat";
$Name = "Hoseen";
$NAME = "Different";
// These are three different variables!
```

**5. Cannot use PHP reserved words**
```php
$this = "wrong"; // Error! ($this is reserved)
$class = "wrong"; // Error!
$echo = "correct"; // Actually OK as variable name
```

**6. No need to declare type**
PHP is loosely typed, so you don't need to specify if it's a string, number, etc:
```php
$x = 5;        // integer
$x = "Hello";  // now it's a string - no problem!
$x = 3.14;     // now it's a float
```

## Good Naming Practices

```php
// Use descriptive names
$userName = "good";
$u = "not descriptive";

// Use camelCase or snake_case
$firstName = "camelCase style";
$first_name = "snake_case style";

// Be consistent in your project
$userEmail = "if you use camelCase";
$user_phone = "don't mix with snake_case";
```

## Examples

```php
<?php
// Correct declarations
$name = "Ebrat Hoseen";
$age = 19;
$_temp = "temporary value";
$user123 = "username";
$totalPrice = 100.50;

// Wrong declarations
$9users = 10;      // Error: starts with number
$user-name = "x";  // Error: contains hyphen
$user name = "x";  // Error: contains space
?>
```

That's it! Once you follow these rules, you can create and use variables freely in PHP.