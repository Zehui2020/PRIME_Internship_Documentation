# Setup Database
1. To access `phpmyadmin`, use this url: `http://localhost:8080/phpmyadmin` (might differ based on port number).

1. To create your own database, click on the `databases` tab and enter your first database's name, everything else can be left as default. Click `create` to create the database.

    ![](../images/create-database.png)

1. While you can use `phpmyadmin` to create tables in your database, it is preferred to do it manually using `SQL`, as it can later be applied to `php`.

1. To write `SQL` in your databse, make sure you're selecting the correct database > `SQL` tab at the top. 

1. To create a table:
    ```sql
    CREATE TABLE users
    (
        id INT(11) NOT NULL AUTO_INCREMENT,
        username VARCHAR(30) NOT NULL,
        pwd VARCHAR(255) NOT NULL,
        email VARCHAR(100) NOT NULL,
        created_at DATETIME NOT NULL DEFAULT CURRENT_TIME,
        PRIMARY KEY (id)
    );
    ```
    1. Make sure `TABLE` name is NOT using any built-in names in MYSQL.
    1. Make sure vairable names are also NOT using any built-in names in MYSQL (e.g. password).

1. To save and run the database, click on the go button below.

    ![](../images/go-database.png)

1. To create a foreign key:
    ```sql
    CREATE TABLE comments
    (
        id INT(11) NOT NULL AUTO_INCREMENT,
        username VARCHAR(30) NOT NULL,
        comment_text TEXT NOT NULL,
        create_at DATETIME NOT NULL DEFAULT CURRENT_TIME,
        users_id INT(11),
        PRIMARY KEY (id),
        FOREIGN KEY (users_id) REFERENCES users (id) ON DELETE SET NULL
    );
    ```
    1. When referencing a column from another table in current table, MUST be the same data type as in referenced table!

1. To insert data into database:
    ```sql
    INSERT INTO users (username, pwd, email) VALUES ('Daniel', 'Password', 'Dandadan@gmail.com');
    ```

1. To update data in database:
    ```sql
    UPDATE users SET username = 'LIGMASIGMA', pwd = "P@ssw0rd" WHERE id = 2;
    ```

1. To delete data in database:
    ```sql
    DELETE FROM users WHERE id = 1;
    ```

1. To select data in database:
    ```sql
    SELECT username, email FROM users WHERE id = 2;
    /* To select everything */
    SELECT * FROM users WHERE id = 2;
    ```

1. To select data from multiple tables:
    ```sql
    SELECT * FROM users INNER JOIN comments ON users.id = comments.users_id;
    /* Result: Shows all users who made comments */

    /* Left Join */
    SELECT * FROM users LEFT JOIN comments ON users.id = comments.users_id;
    /* Result: Shows all users (including ones with no comments), but users with no comments will have NULL shown under comments */

    /* Right Join*/
    SELECT * FROM users RIGHT JOIN comments ON users.id = comments.users_id;
    /* Result: Shows all comments (including ones with no user), but comments with no user will have NULL shown under user */
    ```

1. To connect database to PHP website, there are 3 methods:
    1. `mysql` (deprecated & unsafe. Do not use this.)
    1. `mysqli`
    1. `PDO`

1. We'll be using `PDO`:
    ```php
    <?php
    $dsn = "mysql:host=localhost;dbname=tutorialdatabase";
    $dbusername = "root";
    $dbpassword = "";

    try
    {
        $pdo = new PDO($dsn, $dbusername, $dbpassword);
        $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    }
    catch(PDOException $e)
    {
        echo "Connection failed: " . $e->getMessage();
    }
    ```
    1. `dbusername`: Username to connect to database for PDO connection.
    1. `dbpassword`: Password to connect to database for PDO connection.
    1. Use `try catch` to catch any errors (just in case). Very popular in PHP.

1. To change stats for users, go to `phpMyAdmin > User Accounts` and find the localhost `Host Name` and root `User Name`. Select that.

    ![](../images/php-users.png)

1. You can change the login info for this user by clicking on `Login Information` near the top. You can change the `Username` to anything you want, but DO NOT change the password directly here. There is a bug.

    ![](../images/user-account.png)

1. To change password, click on `Change Password` tab near the top and do it there.

1. Back to PHP, we'll need to create a file called `formhandler.inc.php` under the `includes` folder, along with a `index.php` file for the html code.

1. In the `index.php`, we create a simple form submission:
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>
        <form action="includes/formhandler.inc.php" method="post">
            <input type = "text" name = "username" placeholder = "Username">
            <input type = "text" name = "pwd" placeholder = "Password">        
            <input type = "text" name = "email" placeholder = "Email">
        </form>
    </body>
    </html>
    ```
    1. Since we want to post the results to php, we'll need the fill in the `name` attribute.
    1. We'll also need the `action` attribute to send the data to `formhandler.inc.php` using `post`.

1. In `formhandler.inc.php`, we'll need:
    ```php
    <?php
    
    if ($_SERVER["REQUEST_METHOD"] == "POST")
    {
        $username = $_POST["username"];
        $pwd = $_POST["pwd"];
        $email = $_POST["email"];

        try
        {
            require_once "dbh.inc.php";
        }
        catch(PDOException $e)
        {
            die("Query Failed: " . $e->getMessage());
        }
    }
    else
    {
        header("Location: ../index.php");
    }
    ```
1. 