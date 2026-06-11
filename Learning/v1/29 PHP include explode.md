# 🧩 PHP File Inclusion — include, include_once, require, require_once

## 📖 Overview

PHP allows you to **reuse code** by including external files into your scripts.  
This helps you organize your project into smaller, reusable components —  
like headers, footers, configurations, and function libraries.

There are **four main inclusion statements**:

| Statement | Executes Multiple Times | Error Type if File Missing |
|------------|--------------------------|-----------------------------|
| `include` | ✅ Yes | ⚠️ *Warning* |
| `include_once` | 🚫 No | ⚠️ *Warning* |
| `require` | ✅ Yes | ❌ *Fatal Error* |
| `require_once` | 🚫 No | ❌ *Fatal Error* |

---

## 🔹 1. `include`

**Definition:**  
The `include` statement imports and executes another PHP file.  
If the file is not found, PHP throws a **warning**, but the script continues to execute.

```php
<?php
include 'header.php';  // includes header.php file

echo "Welcome to my website!";
?>

🟢 Use Case:

Use include when the file is optional and the program should continue even if it’s missing.

⚠️ Error Example (File Missing)

Warning: include(header.php): failed to open stream: No such file or directory

➡ The script continues running.


---

🔹 2. require

Definition:
The require statement also includes a file,
but if the file is missing, it throws a fatal error and stops script execution.

<?php
require 'config.php'; // includes config.php file

echo "Configuration loaded!";
?>

🔴 Use Case:

Use require when the file is critical for the script (e.g., database or config file).

❌ Error Example (File Missing)

Fatal error: require(): Failed opening required 'config.php' (include_path='.;C:\php\pear')

➡ The script stops immediately.


---

🔹 3. include_once

Definition:
Like include, but ensures the file is included only once,
even if it’s called multiple times in the script.

<?php
include_once 'functions.php';
include_once 'functions.php'; // ignored second time

echo "Functions loaded once.";
?>

🟢 Use Case:

Use include_once to prevent duplicate definitions of functions or classes.

✅ Benefits:

Avoids "function already declared" errors.

Keeps code clean and safe from redundancy.



---

🔹 4. require_once

Definition:
Same as require, but ensures the file is included only once.

<?php
require_once 'db_connect.php';
require_once 'db_connect.php'; // ignored

echo "Database connected!";
?>

🟣 Use Case:

Use require_once for essential files that must exist and be loaded only once
(e.g., configuration, database connections, or class definitions).


---

⚖️ Comparison Table

Feature	include	include_once	require	require_once

Imports external file	✅	✅	✅	✅
Stops execution if missing	❌ (Warning)	❌ (Warning)	✅ (Fatal Error)	✅ (Fatal Error)
Includes file only once	❌	✅	❌	✅
Common use case	Optional files (headers, menus)	Optional but prevent duplication	Mandatory files (config, db)	Mandatory but prevent duplication



---

💡 Best Practices

1. ✅ Use require_once for critical files like configurations and database connections.


2. ✅ Use include_once for reusable, optional files like function libraries.


3. ⚠️ Avoid including the same file multiple times without _once — can cause errors.


4. 📁 Use absolute paths for reliability:

require_once __DIR__ . '/config/database.php';


5. 🧱 Organize files into folders (e.g., /includes, /config, /functions).




---

📂 Example Project Structure

/myapp
│
├── index.php
├── config.php
├── header.php
├── footer.php
└── functions.php

index.php

<?php
require_once 'config.php';
include_once 'header.php';
include_once 'functions.php';

echo "Welcome to my website!";

include_once 'footer.php';
?>


---

🧠 Visual Concept (Logic Flow)

include        → File missing? ⚠️ Warning → Continue script
require        → File missing? ❌ Fatal Error → Stop script
include_once   → Include only once (Warning if missing)
require_once   → Include only once (Fatal Error if missing)


---

🔍 Real-Life Example

File: config.php

<?php
$db_host = "localhost";
$db_user = "root";
$db_pass = "";
$db_name = "mydb";
?>

File: index.php

<?php
require_once 'config.php';

$conn = mysqli_connect($db_host, $db_user, $db_pass, $db_name);

if (!$conn) {
    die("Database connection failed!");
}

include_once 'header.php';

echo "<h1>Welcome to My App</h1>";

include_once 'footer.php';
?>


---

🚀 Summary

Keyword	Critical File?	Includes Once?	Error if Missing	Continue Script?

include	No	No	Warning	Yes
include_once	No	Yes	Warning	Yes
require	Yes	No	Fatal Error	No
require_once	Yes	Yes	Fatal Error	No



---

🏁 Final Recommendation

Situation	Best Choice

Optional files (header, footer, sidebar)	include_once
Must-have files (database, config)	require_once
Temporary or debug includes	include
Legacy code compatibility	require



---

Author: Ebrat Hosein
Language: PHP 🐘
License: Free to use, learn, and share ❤️
