# Notes

## Operators
1. `===` : compare if value is same + if the same data type.
1. `!==` : Yah.

## Superglobal Vairables
1. `$_POST`: Similar to get, but doesn't show result in url
1. `$_GET`: To send variable value to php
1. `$_REQUEST`: Array of data from $_POST, $_GET, $_COOKIE. Not recommended to use unless no choice / want all these datas. If know you want specific superglobal vairable, just use it.
1. `$_GLOBALS`: Get vairable in global scope.
1. `$_SERVER`: Holds info abt headers, paths, script locations, etc.
    > refer to [w3schools](https://www.w3schools.com/php/php_superglobals_server.asp) for all elements that can go into $_SERVER

## Error Handling
1. `empty()` : Check if vairable is empty (doesn't exist / value is false)
1. `is_numeric()`: Check if vairable is a number.
1. `filter_input(type, varname, filter)`: Filter `varname` to check for special characters, is float, etc.
1. `htmlspecialchars()`: Check for special html charas like `<color=red></color>`. Only really need to be done when outputting data to the web.

## Arrays
1. `unset($array[index])`: Removes value at index (doesn't shift next indes down!)
1. `array_splice(array, startIndex, indexIncrement)`: Removes value of index startIndex + indexIncrement and shifts it down.
    > Can also do `array_splice(array, startIndex, 0, newValue)` to add `newValue` at position `startIndex`. Existing value at startIndex will be shifted forward 1 index to make space.
    `newValue` can also be an array!

1. Array can function as `dictionary` (also called `associative array`) as well. Can assign keys to each value:
    ```php
    $task =[
        "laundry" => "Daniel"
        "trash" => "Frida"
    ]
    echo $tasks["laundry"]: "Daniel"
    ```
1. `count($array)`: Is the same as .Length in unity.
1. `sort($array)`: Sort incrementaly. Does it for both alphabetical and numerical.
1. `array_push(array, value)`: Adds value to end of array. Only works for indexed arrays!
1. `array_pop`: Pops last index of array.
1. `$array[]`: Adds value to end of array. Works for both indexed & associative arrays!
    ```php
    // Indexed Array
    $array[] = "newValue";
    // Associative Array
    $array["newKey"] = "newValue";
    ```

1. Can also have `array in array`!
    ```php
    // Indexed Array
    food = [
    array("banana", "cherry"),
    "watermelon",
    "apple"
    ]
    echo food[0][0]: "Banana"

    // Associative Array
    food = [
    fruits => array("watermelon", "apple"),
    meats => array("chicken", "pork")
    ]
    echo food["meats"][0]: "meats"

    // Associative Array in Associative Array
    food = [
    fruits => array("watermelon", "apple", "ambiguous" => "tomato"),
    meats => array("chicken", "pork")
    ]
    echo food["fruits"]["ambiguous"]: "tomato"
    ```

## Debugging
`echo`: Prints onto web page. Limited functionality. E.g. cannot print out arrays.
`print_r`: Prints onto web page, but can print out arrays & other data types. 

## Built In Functions
### String
1. `strlen`: String length. Returns length of string (chars).
1. `str_word_count`: Words in string.
1. `strpos(string, stringToFind)`: Returns index of stringToFind within string. If `stringToFind` has more than 1 char, returns the index of first char.
1. `str_replace(stringToFind, stringToReplace, fullString)`: Replaces `stringToFind` with `stringToReplace` in `fullString`.
1. `trim` remove white spaces.
1. `strtolower`: Make str to lower case.
1. `strtoupper`: Make str to upper case.
1. `substr(string, startIndex, incrementIndex)`: Returns string starting from `startIndex` and increment by `incrementIndex`, Inclusive of currentIndex. `incrementIndex` can be negative to start from end of string.
1. `explode(dividerString, string)`: Returns an array with `dividerString` as the seperator.

## Math
1. `abs`: Mathf.Abs() in Unity.
1. `round`: Mathf.Round() round to nearest whole number.
1. `pow`: Mathf.Pow() in Unity.
1. `sqrt`: Mathf.Sqrt() in Unity.
1. `rand`: Random.Range() in Unity.

## Arrays
1. `is_array`: Check if something is an array. 
1. `array_reverse`: Reverse sequence of array.
1. `array_merge(array1, array2)`: Merges array1 with array2.

## Date Time
1. `date(Y-m-d H:i:s)`: Returns date & time in string format. 
1. `time()`: Seconds since 1st Jan 1970. (Unix Timestamp)
1. `strtotime(2024-1-1 12:00:00)`: Returns unix timestamp of date time.

View other popular functions [here](https://www.exakat.io/en/top-100-php-functions/)!

## Functions
```php
// To create a function
function SayHello()
{

}

// No need to declare return type
function SayHello()
{
    return "Hello World";
}

// No need to declare type for value
function SayName($name)
{
    return $name;
}
// But you can also declare type from php7+
function SayName(string $name)
{
    return $name;
}

// Can assign default value
function SayName($name = "Ligma")
{
    return $name;
}

// This will not work!
string $name = "Ligma"
function GetName()
{
    return $name;
}
// Use this instead (tTy to avoid this unless you have a reason to. Pass in as parameter instead.)
string $name = "Ligma"
function GetName()
{
    global $name;
    return $name;
}
```

## Scopes
`global`: Makes var be global.
`static`: Makes var be defined once. Reused when called again.
`class`: Makes var that can be accessed only in the class.
`local`: Makes var that can be accessed locally only in the function.

## Consts
`define(stringVar, value)`: Define a constant `var` of `value`.

## Loops
```php
// Indexed Array
$fruits = ["Apple", "Orange", "Cherry"];
foreach ($fruits as $fruit)
{
    echo $fruit;
}

// Associative Array
$fruits = [
    "Apple" => "Red", 
    "Orange" => "Orange",
    "Cherry" => "Pink"];

// This will give value (color)
foreach ($fruits as $fruit)
{
    echo $fruit;
}
// This will give key (fruit)
foreach ($fruits as $fruit => $color)
{
    echo $fruit;
    echo $color;
}
```

## Classes
```php
class Car 
{
  public $color;
  public $model;

  // Constructor
  public function __construct($color, $model)
  {
    $this->color = $color;
    $this->model = $model;
  }

  public function message() 
  {
    return "My car is a " . $this->color . " " . $this->model . "!";
  }
}

// Instantiation of car object
$myCar = new Car("red", "Volvo");

```

## Database (SQL)
1. `localhost:8080/phpmyadmin`: Access myadmin in web for database, sql, etc.

### Vairables
1. `INT`: Integer from -2137483648 - 2137483648. (4 byte data)
1. `BIGINT` :  8 byte data
1. `INT(11)`: Can add `()` at the back to define width of integer. 11 is default.
1. `FLOAT`: Floating point number.
1. `DOUBLE`: Bigger FLOAT, more bytes.
1. `VARCHAR(10)`: Store 10 chars as string. Cut off parts that exceed char count. Can be used for username, password, etc. (usually max 255 chars)
1. `TEXT`: Store many chars. Usually for comments, blog posts, etc.
1. `DATE 2023-05-04`: Create date. Need to mind formatting.
1. `DATETIME 2023-05-04 11:30:00`: Create date + time. Need to mind formatting.
1. `SIGNED / UNSIGNED`: Allow / Disallow for negative numbers. E.g. (INT UNSIGNED changes the range from `-2137483648 - 2137483648` to `0 - 4294967295`)

1. `AUTO_INCREMENT`: Increments a column by 1. It's also `UNSIGNED`.
1. `DEFAULT`: Assign default value to a column.
1. `CURRNT_TIME`: Return time of current server time.
1. `PRIMARY KEY`: Ensures a certain column is unique, e.g, every user's ID will be unique if:
    ```sql
    id INT(11) PRIMARY KEY
    //or
    PRIMARY KEY (id)
    ```
1. `FOREIGN KEY ... REFERENCES`: A column that references a column in another table.
    ```sql
    FOREIGN KEY (users_id) REFERENCES users (id)
    ```
1. `ON DELETE`: Triggered when referenced table gets deleted.
1. `ON DELETE CASCADE`: Triggered when referenced table gets deleted. Goes to referenced field in another table and delete everything referencing said field.
1. `ON DELETE SET NULL`: Triggered when referenced table gets deleted. Set foreign key to null.

## PHP & SQL Integration
1. `dsn`: Data Source Name. Associates the configuration parameters for communicating with a specific database. Usuall consists of: Name. Host Name. Database Name.
1. `PDO`: PHP Data Object.
1. `include_once` / `include`: `include_once` will do the same as `include`, but will check if file alr been included earlier, if yes, throw warning / `include` will try to find the file, and throw warning if can't find file.
1. `require_once` / `require`: Do the same as `include_once` / `include`, but will throw error instead.
1. `INNER JOIN` / `LEFT JOIN` / `RIGHT JOIN`: Join data from 1 table with another.
1. `exit`: Terminate the current script. Preferablly used in scripts without any connections.
1. `die`: Terminate the current script. Preferablly used in scripts with connections.
1. Query: To prevent SQL injection, don't just add what the user typed straight into a SQL statement.
1. `?` / `:`: Use these placeholders inside a query string and replace them later. 