🕒 PHP Date & Time Functions – Full Details


---

1. date_default_timezone_set()

Sets the default timezone for all date/time functions in a script.

Syntax:

date_default_timezone_set(string $timezone);

Example:

date_default_timezone_set("Asia/Dhaka");
echo date("Y-m-d H:i:s");

✅ Output:

2025-10-29 16:35:12

You can check supported timezones here:
👉 https://www.php.net/manual/en/timezones.php


---

2. date_default_timezone_get()

Returns the default timezone currently set.

Example:

echo date_default_timezone_get();

✅ Output:

Asia/Dhaka


---

3. date()

Formats a local date and time.

Syntax:

date(string $format, int $timestamp = time());

Common Format Characters:

Format	Description	Example Output

Y	Year (4 digits)	2025
y	Year (2 digits)	25
m	Month (01–12)	10
n	Month (1–12)	10
d	Day (01–31)	29
j	Day (1–31)	29
H	Hour (00–23)	16
h	Hour (01–12)	04
i	Minutes (00–59)	35
s	Seconds (00–59)	12
a	am / pm	pm
A	AM / PM	PM
l	Day name	Wednesday
D	Short day name	Wed
F	Month name	October
M	Short month name	Oct
U	Unix timestamp	1730210112


Example:

echo date("Y-m-d H:i:s");

✅ Output:

2025-10-29 16:35:12


---

4. time()

Returns the current Unix timestamp (seconds since January 1, 1970).

Example:

echo time();

✅ Output:

1730210112


---

5. getdate()

Returns an associative array containing date/time information.

Example:

print_r(getdate());

✅ Output:

Array
(
    [seconds] => 12
    [minutes] => 35
    [hours] => 16
    [mday] => 29
    [wday] => 3
    [mon] => 10
    [year] => 2025
    [yday] => 301
    [weekday] => Wednesday
    [month] => October
    [0] => 1730210112
)


---

6. localtime()

Returns an array with local time information.

Example:

print_r(localtime(time(), true));

✅ Output:

Array
(
    [tm_sec] => 12
    [tm_min] => 35
    [tm_hour] => 16
    [tm_mday] => 29
    [tm_mon] => 9
    [tm_year] => 125
    [tm_wday] => 3
    [tm_yday] => 301
    [tm_isdst] => 0
)


---

7. mktime()

Returns the Unix timestamp for a specific date.

Syntax:

mktime(hour, minute, second, month, day, year)

Example:

echo mktime(0, 0, 0, 10, 29, 2025);

✅ Output:

1730150400


---

8. gmmktime()

Same as mktime() but returns GMT time (not local time).


---

9. strtotime()

Parses an English textual date/time description into a Unix timestamp.

Example:

echo strtotime("next Friday");

✅ Output:

1730822400

You can use:

"tomorrow"

"yesterday"

"+1 week"

"+2 days"

"2025-12-25"



---

10. gmdate()

Same as date() but returns GMT/UTC time.

Example:

echo gmdate("Y-m-d H:i:s");


---

11. date_create()

Creates a new DateTime object.

Example:

$date = date_create("2025-10-29");
echo date_format($date, "Y/m/d");


---

12. date_format()

Formats a DateTime object.

Example:

$date = date_create("2025-10-29");
echo date_format($date, "l, F j, Y");

✅ Output:

Wednesday, October 29, 2025


---

13. date_modify()

Modifies a DateTime object by adding or subtracting time.

Example:

$date = date_create("2025-10-29");
date_modify($date, "+1 month");
echo date_format($date, "Y-m-d");

✅ Output:

2025-11-29


---

14. date_diff()

Calculates the difference between two dates.

Example:

$date1 = date_create("2025-10-29");
$date2 = date_create("2025-12-25");
$diff = date_diff($date1, $date2);
echo $diff->format("%R%a days");

✅ Output:

+57 days


---

15. checkdate()

Validates a Gregorian date.

Example:

var_dump(checkdate(2, 29, 2025));  // false (2025 not a leap year)
var_dump(checkdate(2, 29, 2024));  // true


---

16. microtime()

Returns the current Unix timestamp with microseconds.

Example:

echo microtime(true);

✅ Output:

1730210112.4567


---

17. date_timestamp_get() / date_timestamp_set()

Used with DateTime objects to get/set timestamps.

Example:

$date = date_create();
echo date_timestamp_get($date);


---

18. timezone Functions

Function	Description

timezone_identifiers_list()	List all supported timezones
timezone_name_from_abbr()	Get timezone name from abbreviation
timezone_version_get()	Get timezone DB version
