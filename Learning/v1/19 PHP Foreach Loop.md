# Foreach Loop in PHP

The **foreach loop** is specifically designed for iterating over arrays and objects. It's the easiest and most readable way to work with array elements in PHP.

## Basic Syntax

### Syntax 1: Values Only
```php
foreach ($array as $value) {
    // code to be executed
}
```

### Syntax 2: Keys and Values
```php
foreach ($array as $key => $value) {
    // code to be executed
}
```

## Simple Examples

### Indexed Array (Values Only)
```php
$colors = ["red", "green", "blue", "yellow"];

foreach ($colors as $color) {
    echo "$color<br>";
}

// Output:
// red
// green
// blue
// yellow
```

### Indexed Array (With Keys)
```php
$fruits = ["apple", "banana", "orange"];

foreach ($fruits as $index => $fruit) {
    echo "Index $index: $fruit<br>";
}

// Output:
// Index 0: apple
// Index 1: banana
// Index 2: orange
```

## Associative Arrays

### Values Only
```php
$person = [
    "name" => "John",
    "age" => 30,
    "city" => "New York"
];

foreach ($person as $value) {
    echo "$value<br>";
}

// Output:
// John
// 30
// New York
```

### Keys and Values
```php
$person = [
    "name" => "John",
    "age" => 30,
    "city" => "New York"
];

foreach ($person as $key => $value) {
    echo "$key: $value<br>";
}

// Output:
// name: John
// age: 30
// city: New York
```

## Practical Examples

### Display Product List
```php
$products = [
    "Laptop" => 999,
    "Mouse" => 25,
    "Keyboard" => 75,
    "Monitor" => 300
];

foreach ($products as $product => $price) {
    echo "$product: $$price<br>";
}

// Output:
// Laptop: $999
// Mouse: $25
// Keyboard: $75
// Monitor: $300
```

### Sum Array Values
```php
$numbers = [10, 20, 30, 40, 50];
$sum = 0;

foreach ($numbers as $number) {
    $sum += $number;
}

echo "Total: $sum"; // Output: Total: 150
```

### Generate HTML List
```php
$items = ["Home", "About", "Services", "Contact"];

echo "<ul>";
foreach ($items as $item) {
    echo "<li>$item</li>";
}
echo "</ul>";

// Output:
// <ul>
//   <li>Home</li>
//   <li>About</li>
//   <li>Services</li>
//   <li>Contact</li>
// </ul>
```

### Student Grades
```php
$grades = [
    "Alice" => 85,
    "Bob" => 92,
    "Charlie" => 78,
    "Diana" => 95
];

foreach ($grades as $student => $grade) {
    if ($grade >= 90) {
        echo "$student: $grade - Excellent!<br>";
    } elseif ($grade >= 80) {
        echo "$student: $grade - Good<br>";
    } else {
        echo "$student: $grade - Needs Improvement<br>";
    }
}
```

## Multidimensional Arrays

### Array of Arrays
```php
$students = [
    ["name" => "Alice", "age" => 20, "grade" => "A"],
    ["name" => "Bob", "age" => 22, "grade" => "B"],
    ["name" => "Charlie", "age" => 21, "grade" => "A"]
];

foreach ($students as $student) {
    echo "Name: {$student['name']}, ";
    echo "Age: {$student['age']}, ";
    echo "Grade: {$student['grade']}<br>";
}

// Output:
// Name: Alice, Age: 20, Grade: A
// Name: Bob, Age: 22, Grade: B
// Name: Charlie, Age: 21, Grade: A
```

### Nested Foreach
```php
$teams = [
    "Team A" => ["John", "Jane", "Jim"],
    "Team B" => ["Sarah", "Sam", "Sue"],
    "Team C" => ["Tom", "Tim", "Tina"]
];

foreach ($teams as $teamName => $members) {
    echo "$teamName:<br>";
    foreach ($members as $member) {
        echo "  - $member<br>";
    }
}

// Output:
// Team A:
//   - John
//   - Jane
//   - Jim
// Team B:
//   - Sarah
//   - Sam
//   - Sue
// Team C:
//   - Tom
//   - Tim
//   - Tina
```

## Modifying Array Values

### By Value (Doesn't Modify Original)
```php
$numbers = [1, 2, 3, 4, 5];

foreach ($numbers as $number) {
    $number = $number * 2; // Original array unchanged
}

print_r($numbers);
// Output: [1, 2, 3, 4, 5] - No change!
```

### By Reference (Modifies Original)
```php
$numbers = [1, 2, 3, 4, 5];

foreach ($numbers as &$number) {
    $number = $number * 2; // Use & to modify original
}
unset($number); // Good practice to unset reference

print_r($numbers);
// Output: [2, 4, 6, 8, 10] - Modified!
```

**Important:** Always `unset()` the reference variable after the loop to avoid unexpected behavior.

## Using break and continue

### break - Exit the loop
```php
$numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

foreach ($numbers as $number) {
    if ($number == 6) {
        break; // Stop when we find 6
    }
    echo "$number ";
}
// Output: 1 2 3 4 5
```

### continue - Skip current iteration
```php
$numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

foreach ($numbers as $number) {
    if ($number % 2 == 0) {
        continue; // Skip even numbers
    }
    echo "$number ";
}
// Output: 1 3 5 7 9
```

## Alternative Syntax (for templates)

```php
<ul>
<?php foreach ($items as $item): ?>
    <li><?php echo $item; ?></li>
<?php endforeach; ?>
</ul>
```

Or with short echo syntax:
```php
<ul>
<?php foreach ($items as $item): ?>
    <li><?= $item ?></li>
<?php endforeach; ?>
</ul>
```

## Advanced Examples

### Shopping Cart
```php
$cart = [
    ["product" => "Laptop", "price" => 999, "quantity" => 1],
    ["product" => "Mouse", "price" => 25, "quantity" => 2],
    ["product" => "Keyboard", "price" => 75, "quantity" => 1]
];

$total = 0;

echo "<h3>Shopping Cart</h3>";
foreach ($cart as $item) {
    $subtotal = $item['price'] * $item['quantity'];
    $total += $subtotal;
    
    echo "{$item['product']} - ";
    echo "\${$item['price']} x {$item['quantity']} = ";
    echo "\$$subtotal<br>";
}

echo "<strong>Total: \$$total</strong>";

// Output:
// Shopping Cart
// Laptop - $999 x 1 = $999
// Mouse - $25 x 2 = $50
// Keyboard - $75 x 1 = $75
// Total: $1124
```

### Filter Array
```php
$ages = [15, 22, 17, 30, 19, 25, 16];
$adults = [];

foreach ($ages as $age) {
    if ($age >= 18) {
        $adults[] = $age;
    }
}

print_r($adults);
// Output: [22, 30, 19, 25]
```

### Build HTML Table
```php
$data = [
    ["Name" => "Alice", "Email" => "alice@email.com", "Age" => 25],
    ["Name" => "Bob", "Email" => "bob@email.com", "Age" => 30],
    ["Name" => "Charlie", "Email" => "charlie@email.com", "Age" => 28]
];

echo "<table border='1'>";
echo "<tr><th>Name</th><th>Email</th><th>Age</th></tr>";

foreach ($data as $row) {
    echo "<tr>";
    foreach ($row as $cell) {
        echo "<td>$cell</td>";
    }
    echo "</tr>";
}

echo "</table>";
```

### Count Occurrences
```php
$fruits = ["apple", "banana", "apple", "orange", "banana", "apple"];
$count = [];

foreach ($fruits as $fruit) {
    if (isset($count[$fruit])) {
        $count[$fruit]++;
    } else {
        $count[$fruit] = 1;
    }
}

foreach ($count as $fruit => $number) {
    echo "$fruit: $number<br>";
}

// Output:
// apple: 3
// banana: 2
// orange: 1
```

## Foreach with Objects

```php
class Person {
    public $name = "John";
    public $age = 30;
    private $secret = "hidden"; // Won't be visible
}

$person = new Person();

foreach ($person as $property => $value) {
    echo "$property: $value<br>";
}

// Output:
// name: John
// age: 30
// (private properties are not accessible)
```

## Common Patterns

### Check if Value Exists
```php
$allowedUsers = ["admin", "user1", "user2"];
$currentUser = "user1";

$found = false;
foreach ($allowedUsers as $user) {
    if ($user == $currentUser) {
        $found = true;
        break;
    }
}

if ($found) {
    echo "Access granted!";
} else {
    echo "Access denied!";
}

// Note: in_array() function is better for this
```

### Convert Array Format
```php
$products = ["apple", "banana", "orange"];
$productList = [];

foreach ($products as $index => $product) {
    $productList[] = [
        'id' => $index + 1,
        'name' => ucfirst($product)
    ];
}

print_r($productList);
// Output: 
// [
//   ['id' => 1, 'name' => 'Apple'],
//   ['id' => 2, 'name' => 'Banana'],
//   ['id' => 3, 'name' => 'Orange']
// ]
```

## When to Use Foreach

✅ **Use foreach when:**
- Working with arrays (indexed or associative)
- You need to process every element
- You want clean, readable code for array iteration
- You don't need the counter control of a for loop

❌ **Don't use foreach when:**
- You need precise index control
- You want to skip elements by index
- Working with non-array iterables that need special handling

## Foreach vs For Loop

```php
$colors = ["red", "green", "blue"];

// Foreach (cleaner for arrays)
foreach ($colors as $color) {
    echo $color . " ";
}

// For loop (more control)
for ($i = 0; $i < count($colors); $i++) {
    echo $colors[$i] . " ";
}

// Both output: red green blue
```

The **foreach loop** is the most elegant and efficient way to iterate over arrays in PHP, making your code more readable and less error-prone!