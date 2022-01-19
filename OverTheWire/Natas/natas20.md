`Link` : `https://overthewire.org/wargames/natas/natas20.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟗 - 𝐋𝐞𝐯𝐞𝐥 𝟐𝟎
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas20
- URL:      `http://natas20.natas.labs.overthewire.org`
## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:  `http://natas20.natas.labs.overthewire.org`
- `view source`

```
<?

function debug($msg) { /* {{{ */
    if(array_key_exists("debug", $_GET)) {
        print "DEBUG: $msg<br>";
    }
}
/* }}} */
function print_credentials() { /* {{{ */
    if($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1) {
    print "You are an admin. The credentials for the next level are:<br>";
    print "<pre>Username: natas21\n";
    print "Password: <censored></pre>";
    } else {
    print "You are logged in as a regular user. Login as an admin to retrieve credentials for natas21.";
    }
}
/* }}} */

/* we don't need this */
function myopen($path, $name) { 
    //debug("MYOPEN $path $name"); 
    return true; 
}

/* we don't need this */
function myclose() { 
    //debug("MYCLOSE"); 
    return true; 
}

function myread($sid) { 
    debug("MYREAD $sid"); 
    if(strspn($sid, "1234567890qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM-") != strlen($sid)) {
    debug("Invalid SID"); 
        return "";
    }
    $filename = session_save_path() . "/" . "mysess_" . $sid;
    if(!file_exists($filename)) {
        debug("Session file doesn't exist");
        return "";
    }
    debug("Reading from ". $filename);
    $data = file_get_contents($filename);
    $_SESSION = array();
    foreach(explode("\n", $data) as $line) {
        debug("Read [$line]");
    $parts = explode(" ", $line, 2);
    if($parts[0] != "") $_SESSION[$parts[0]] = $parts[1];
    }
    return session_encode();
}

function mywrite($sid, $data) { 
    // $data contains the serialized version of $_SESSION
    // but our encoding is better
    debug("MYWRITE $sid $data"); 
    // make sure the sid is alnum only!!
    if(strspn($sid, "1234567890qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM-") != strlen($sid)) {
    debug("Invalid SID"); 
        return;
    }
    $filename = session_save_path() . "/" . "mysess_" . $sid;
    $data = "";
    debug("Saving in ". $filename);
    ksort($_SESSION);
    foreach($_SESSION as $key => $value) {
        debug("$key => $value");
        $data .= "$key $value\n";
    }
    file_put_contents($filename, $data);
    chmod($filename, 0600);
}

/* we don't need this */
function mydestroy($sid) {
    //debug("MYDESTROY $sid"); 
    return true; 
}
/* we don't need this */
function mygarbage($t) { 
    //debug("MYGARBAGE $t"); 
    return true; 
}

session_set_save_handler(
    "myopen", 
    "myclose", 
    "myread", 
    "mywrite", 
    "mydestroy", 
    "mygarbage");
session_start();

if(array_key_exists("name", $_REQUEST)) {
    $_SESSION["name"] = $_REQUEST["name"];
    debug("Name set to " . $_REQUEST["name"]);
}

print_credentials();

$name = "";
if(array_key_exists("name", $_SESSION)) {
    $name = $_SESSION["name"];
}

?> 
```

- Notice that there is a debug function, we can use that to check what's exactly happening behind the scenees
```
function debug($msg) { /* {{{ */
    if(array_key_exists("debug", $_GET)) {
        print "DEBUG: $msg<br>";
    }
} 
```
- `http://natas20.natas.labs.overthewire.org/index.php?debug` will do the debugging
- also notice: `if($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1) {` means session will be printed if and only if key admin == 1 also exists.
- also notice in myread function: 
```
foreach(explode("\n", $data) as $line) {
        debug("Read [$line]");
```
- each line is being read as seperate key value pair


![image](https://user-images.githubusercontent.com/68887544/150090171-3f058ee8-f3ca-4cf8-a269-3851a874b43c.png)

```
You are an admin. The credentials for the next level are:<br><pre>Username: natas21
Password: IFekPyrQXftziDEsUr3x21sYuahypdgJ</pre>
```

## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- `%0A` - is url encoding for newline character `\n`
