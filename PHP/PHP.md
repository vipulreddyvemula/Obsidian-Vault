```
echo
print
var_dump()

strlen()
strrev()
str_word_count()
strpos()
strtoupper()
strtolower()

isset()
unset()
empty()
count()
print_r()
array_keys()
array_values()

fopen()
fread()
fwrite()
fclose()
file_get_contents()
file_put_contents()
file_exists()
filesize()
unlink()
nl2br()

setcookie()
time()

session_start()
$_SESSION
session_unset()
session_destroy()

header()
include()
require()
include_once()
require_once()

mysqli_connect()
mysqli_query()
mysqli_fetch_assoc()
mysqli_close()

date()
date_default_timezone_set()
htmlspecialchars()
```
## Super Short Final Function Table

| Function                                                | Use                   | Tiny Example                                |
| ------------------------------------------------------- | --------------------- | ------------------------------------------- |
| `echo`                                                  | Print output          | `echo "Hi";`                                |
| `print`                                                 | Print output          | `print "Hi";`                               |
| `var_dump()`                                            | Show type/value       | `var_dump($x);`                             |
| `strlen()`                                              | String length         | `strlen("abc")`                             |
| `strrev()`                                              | Reverse string        | `strrev("abc")`                             |
| `str_word_count()`                                      | Count words           | `str_word_count("hi bro")`                  |
| `strpos()`                                              | Find position         | `strpos("abc", "b")`                        |
| `strtoupper()`                                          | Uppercase             | `strtoupper("php")`                         |
| `strtolower()`                                          | Lowercase             | `strtolower("PHP")`                         |
| `isset()`                                               | Check exists          | `isset($x)`                                 |
| `unset()`                                               | Delete variable       | `unset($x)`                                 |
| `empty()`                                               | Check empty           | `empty($x)`                                 |
| `count()`                                               | Count array elements  | `count($arr)`                               |
| `print_r()`                                             | Print array           | `print_r($arr)`                             |
| `array_keys()`                                          | Get keys              | `array_keys($arr)`                          |
| `array_values()`                                        | Get values            | `array_values($arr)`                        |
| `fopen()`                                               | Open file             | `fopen("a.txt","r")`                        |
| `fread()`                                               | Read file             | `fread($f, filesize("a.txt"))`              |
| `fwrite()`                                              | Write file            | `fwrite($f,"Hi")`                           |
| `fclose()`                                              | Close file            | `fclose($f)`                                |
| `file_get_contents()`                                   | Read full file        | `file_get_contents("a.txt")`                |
| `file_put_contents()`                                   | Write full file       | `file_put_contents("a.txt","Hi")`           |
| `file_exists()`                                         | Check file            | `file_exists("a.txt")`                      |
| `filesize()`                                            | File size             | `filesize("a.txt")`                         |
| `unlink()`                                              | Delete file           | `unlink("a.txt")`                           |
| `nl2br()`                                               | Newline to `<br>`     | `nl2br($text)`                              |
| `setcookie()` <br>access cookies by $_COOKIE[u]="Daksh" | Create cookie         | `setcookie("u","Daksh",time()+3600,"/")`    |
| `time()`                                                | Current timestamp     | `time()`                                    |
| `session_start()`                                       | Start session         | `session_start()`                           |
| `$_SESSION`                                             | Store session data    | `$_SESSION["u"]="admin"`                    |
| `session_unset()`                                       | Remove session vars   | `session_unset()`                           |
| `session_destroy()`                                     | Destroy session       | `session_destroy()`                         |
| `header()`                                              | Redirect              | `header("Location: home.php")`              |
| `include()`                                             | Include optional file | `include("menu.php")`                       |
| `require()`                                             | Include required file | `require("config.php")`                     |
| `include_once()`                                        | Include once          | `include_once("a.php")`                     |
| `require_once()`                                        | Require once          | `require_once("db.php")`                    |
| `mysqli_connect()`                                      | DB connect            | `mysqli_connect(...)`                       |
| `mysqli_query()`                                        | Run SQL               | `mysqli_query($conn,$sql)`                  |
| `mysqli_fetch_assoc()`                                  | Fetch DB row          | `mysqli_fetch_assoc($result)`               |
| `mysqli_close()`                                        | Close DB              | `mysqli_close($conn)`                       |
| `date()`                                                | Date/time             | `date("d-m-Y H:i:s")`                       |
| `date_default_timezone_set()`                           | Set timezone          | `date_default_timezone_set("Asia/Kolkata")` |
| `htmlspecialchars()`                                    | Safe output           | `htmlspecialchars($_POST["name"])`          |
