# Notes

## Operators
1. `===` : compare if value is same + if the same data type.
1. `!==` : Yah.

## Superglobal Vairables
1. `$_POST`: Similar to get, but doesn't show result in url
1. `$_GET`: To send variable value to php
1. `$_REQUEST`: Array of data from $_POST, $_GET, $_COOKIE. Not recommended to use unless no choice / want all these datas. If know you want specific superglobal vairable, just use it.
1. `$_SERVER`: Holds info abt headers, paths, script locations, etc.
    > refer to [w3schools](https://www.w3schools.com/php/php_superglobals_server.asp) for all elements that can go into $_SERVER

## Error Handling
1. `empty()` : Check if vairable is empty (doesn't exist / value is false)
1. `is_numeric()`: Check if vairable is a number.
1. `filter_input(type, varname, filter)`: Filter `varname` to check for special characters, is float, etc.
1. `htmlspecialchars()`: Check for special html charas like `<color=red></color>`

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