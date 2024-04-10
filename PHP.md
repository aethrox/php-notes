### What's PHP?
Betik bir programlama dilidir.
Web tabanlı yazılım geliştirme yanı güçlüdür ve genellikle bu amaçla kullanılır.

```plain text
Author: Rasmus Lerdorf
First Version: 1995
```

Kaynak kodu açık ve ücretsizdir. Server side çalışır. HTML ile birlikte çalışabilir. Geniş işletim sistemi, web sunucu ve veritabanı yazılım desteğine sahiptir.

> Step-By-Step Working Process

1. Yazılan kod sunucu tarafında yorumlanır.
2. Çıktı HTML web sunucusuna yönlendirilir.
3. Web sunucusu çıktıyı tarayıcıya yönlendirir.

> What can be done with PHP?

1. Database apps
2. E-commerce sites
3. Surver, Discussion forums, Search engines, CMS
(...)

## PHP Usage

"echo, print, printf" commands print text on the screen.

### Comments blocks:
> ```php
>   <?php
>       // This is the comment line.
>       echo("PHP Hello World!");
>       /*
>       * Test line 1
>       * Test line 2
>       */
>       echo "PHP Hello World!";
>   ?>
> ```

### Escape characters:
> ```php
>   <?php
>    echo (“\”PHP\” dünyası merhaba”); // çıktısı “PHP” dünyası merhaba
>    // \n New line, \t Tab, \r Return
>   ?>
>```

### Variables types
```php
    <?php
        $sayi1; // Truth
        $isim2; // Truth
        $sayi1!; // Wrong
        $1sayi; // Wrong
        $isim // Truth
        isim // Wrong
    ?>
```

### Data Types:

**Integers:**

* `$number = 10;`
* `$age = 25;`

**Floating-point numbers:**

* `$pi = 3.14;`
* `$price = 12.50;`

**Strings:**

* `$name = "Bard";`
* `$message = "Hello World!";`

**Booleans:**

* `$true = true;`
* `$false = false;`

**Arrays:**

* `$colors = ["red", "green", "blue"];`
* `$numbers = [1, 2, 3, 4, 5];`

**Objects:**

* `$user = new User();`
* `$car = new Car();`

**Null:**

* `$value = null;`

**Empty:**

* `$text = "";`

### Merge variables
```php
    <?php
        $var1 = "Test1";
        $var2 = "Test2";
        $var3 = "Test3";

        $oneLineVar = $var1.$var2.$var3;
    ?>
```

### Arithmetic operators

- **Addition (+):** Adds two operands. `$result = 5 + 3; // $result will be 8`
- **Subtraction (-):** Subtracts the second operand from the first. `$result = 10 - 2; // $result will be 8`
- **Multiplication (*):** Multiplies two operands. `$result = 4 * 5; // $result will be 20`
- **Division (/)**: Divides the first operand by the second. `$result = 12 / 3; // $result will be 4 (usually results in a float)`
- **Modulus (%):** Gives the remainder after division. `$result = 10 % 3; // $result will be 1`

### Define
```php
define('PI', 3.14159);
define('MAX_USERS', 100);
define('DEBUG_MODE', true);

echo PI; // Outputs: 3.14159
echo MAX_USERS; // Outputs: 100
echo DEBUG_MODE; // Outputs: 1 (boolean true)
```

### Type Conversion 
```php
<?php

// Type Juggling Examples:

$number_string = "30";  // String containing a number
$age = $number_string + 5;  // Automatic conversion to integer for addition
echo $age; // Outputs: 35 (integer)

$message = "Age: " . 22;  // Number used in string concatenation
echo $message; // Outputs: "Age: 22" (string)

$is_admin = true;
$admin_level = $is_admin * 10;  // Boolean treated as 1 for multiplication
echo $admin_level; // Outputs: 10 (integer)


// Explicit Casting Examples:

$user_age = "28";
$actual_age = (int)$user_age;  // Explicit conversion to integer
echo $actual_age; // Outputs: 28 (integer)

$pi = 3.14;
$pi_as_string = (string)$pi;  // Explicit conversion to string
echo $pi_as_string; // Outputs: "3.14" (string)

?>
```

### gettype() and settype()
```php
$x = 10;
$y = "Hello";
$z = true;

echo gettype($x); // Outputs: integer
echo gettype($y); // Outputs: string
echo gettype($z); // Outputs: boolean
```

```php
$age = "25";  // String value

// Convert to integer for calculations
settype($age, "integer");

$total = $age + 10;
echo $total; // Outputs: 35 (integer)
```

### isset, unset and empty
```php
<?php

$name = "Alice";  // Declared with a value
$age = null;      // Declared with null value
$message = "";    // Empty string
$numbers = [];    // Empty array

// **isset** checks existence and value (including null)
if (isset($name)) {
  echo "Hello, $name!";
}

// **empty** checks for various "empty" conditions
if (empty($message)) {
  echo "There is no message.";
}

if (empty($numbers)) {
  echo "The array is empty.";
}

// **isset** won't print as $age is null
if (isset($age)) {
  echo "Age: $age";
}

// Remove $age using **unset**
unset($age);

// Error trying to access unset variable
if (isset($age)) {
  echo "Age: $age";  // This results in an error
}

?>
```

### Environment Variables
- `echo $HTTP_COOKIE_DATA;` will show information about a cookie that is being used.
- `echo $HTTP_USER_AGENT;` 

### Receiving data through the form
```php
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>Tek Kodda $_POST ve $_GET</title>
</head>
<body>
    <h1>Bilgilerinizi Girin</h1>
    <form method="post">
        <label for="isim">Adınız:</label>
        <input type="text" name="isim" id="isim">
        <br>
        <label for="soyisim">Soyadınız:</label>
        <input type="text" name="soyisim" id="soyisim">
        <br>
        <br>
        <button type="submit">Gönder</button>
    </form>

    <?php

    // $_POST ve $_GET ile gelen verileri alalım
    $isim = $_POST["isim"] ?? $_GET["isim"];
    $soyisim = $_POST["soyisim"] ?? $_GET["soyisim"];

    // Verileri ekrana yazdıralım
    if ($isim && $soyisim) {
        echo "Merhaba, " . $isim . " " . $soyisim . "!";
    } else {
        echo "Lütfen formdaki alanları doldurun veya URL'ye parametre ekleyin.";
    }

    ?>
</body>
</html>
```

### $_REQUEST
```php
<?php

// Form data (assuming a form with name and email fields submitted using POST)
$name = $_POST["name"];
$email = $_POST["email"];

// URL parameter (example: ?message=Hello)
$message = $_GET["message"];

// Cookie data (assuming a cookie named "user_id" is set)
$user_id = $_COOKIE["user_id"];

// $_REQUEST combines all sources (might not be ideal for SECURITY reasons)
$all_data = $_REQUEST;

// Access specific data from $_REQUEST (if source is unknown)
$combined_name = $_REQUEST["name"];  // Could be from form or URL
?>
```
**Important Note:** Be cautious with $_REQUEST due to security concerns. 
Consider using specific variables like $_POST or $_GET when possible.

### LOGICAL CONTROL AND LOOPS

```php
<?php

// Logical Operators
$age = 20;
$has_id = true;

// && (and): Both conditions true
if ($age >= 18 && $has_id) {
  echo "You can vote.";
} else {
  echo "Sorry, you cannot vote yet.";
}

// || (or): At least one condition true
$is_admin = false;
$is_moderator = true;

if ($is_admin || $is_moderator) {
  echo "You have access to the control panel.";
} else {
  echo "You don't have access.";
}

// ! (not): Flip the truth value
$logged_in = false;

if (! $logged_in) {
  echo "Please log in.";
}


// Control Flow Statements
$grade = 85;

// if/else
if ($grade >= 90) {
  echo "Excellent!";
} else if ($grade >= 80) {
  echo "Great job!";
} else {
  echo "Keep studying!";
}

// switch-case
$day = "Tuesday";

switch ($day) {
  case "Monday":
    echo "Start of the week!";
    break;
  case "Friday":
    echo "TGIF!";
    break;
  default:
    echo "It's a weekday.";
}

// while loop
$count = 1;
while ($count <= 3) {
  echo "Count: $count ";
  $count++;
}
echo "\n";  // New line after loop

// for loop
for ($i = 0; $i < 5; $i++) {
  echo "Number: $i ";
}
echo "\n";  // New line after loop

// foreach loop
$fruits = ["apple", "banana", "orange"];

foreach ($fruits as $fruit) {
  echo "I like $fruit! ";
}
echo "\n";  // New line after loop

// do-while loop
$x = 10;
do {
  echo "Value: $x ";
  $x--;
} while ($x > 0);
echo "\n";  // New line after loop
?>
```