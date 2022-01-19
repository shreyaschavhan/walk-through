`Link`:`https://overthewire.org/wargames/natas/natas21.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟐𝟎 - 𝐋𝐞𝐯𝐞𝐥 𝟐𝟏
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas21
- URL:      `http://natas21.natas.labs.overthewire.org`
## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧
- Visit:      `http://natas21.natas.labs.overthewire.org`
- `viewsource`

```
<?

function print_credentials() { /* {{{ */
    if($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1) {
    print "You are an admin. The credentials for the next level are:<br>";
    print "<pre>Username: natas22\n";
    print "Password: <censored></pre>";
    } else {
    print "You are logged in as a regular user. Login as an admin to retrieve credentials for natas22.";
    }
}
/* }}} */

session_start();
print_credentials();

?>

```
- Plus, the websites says that it shares location with `http://natas21-experimenter.natas.labs.overthewire.org/index.php`
- Visit: `http://natas21-experimenter.natas.labs.overthewire.org/index.php`
- `viewsource`

```
session_start();

// if update was submitted, store it
if(array_key_exists("submit", $_REQUEST)) {
    foreach($_REQUEST as $key => $val) {
    $_SESSION[$key] = $val;
    }
}

if(array_key_exists("debug", $_GET)) {
    print "[DEBUG] Session contents:<br>";
    print_r($_SESSION);
}

// only allow these keys
$validkeys = array("align" => "center", "fontsize" => "100%", "bgcolor" => "yellow");
$form = "";

$form .= '<form action="index.php" method="POST">';
foreach($validkeys as $key => $defval) {
    $val = $defval;
    if(array_key_exists($key, $_SESSION)) {
    $val = $_SESSION[$key];
    } else {
    $_SESSION[$key] = $val;
    }
    $form .= "$key: <input name='$key' value='$val' /><br>";
}
$form .= '<input type="submit" name="submit" value="Update" />';
$form .= '</form>';

$style = "background-color: ".$_SESSION["bgcolor"]."; text-align: ".$_SESSION["align"]."; font-size: ".$_SESSION["fontsize"].";";
$example = "<div style='$style'>Hello world!</div>";

?>

<p>Example:</p>
<?=$example?>

<p>Change example values here:</p>
<?=$form?> 
```
- It's kinda similar to previous code.
- What can be done is, let's add `admin=1` to the post request with debug on and see if the key get's added.

![image](https://user-images.githubusercontent.com/68887544/150100439-d888e5b4-eeb8-447f-b738-3dd207c33876.png)


- Now, all those key have been stored in the session! The session is stored using cookie.
- Let's change the cookie on `Host: natas21.natas.labs.overthewire.org` to the cookie with the session that we just altered of `Host: natas21-experimenter.natas.labs.overthewire.org`

![image](https://user-images.githubusercontent.com/68887544/150100924-d18a3bb2-bf97-46ce-b71e-be9cd7bdc340.png)

- And boom! It worked

```
You are an admin. The credentials for the next level are:<br><pre>Username: natas22
Password: chG9fbe1Tq2eWVMgjYYD1MsfIvN461kJ</pre>
```
## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- An website can share it's location and session handling with (it's) another (sub)domain

