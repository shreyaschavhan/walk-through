`Link`:`https://overthewire.org/wargames/natas/natas22.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟐𝟏 - 𝐋𝐞𝐯𝐞𝐥 𝟐𝟐
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas22
- URL:      `http://natas22.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧
- Visit:      `http://natas22.natas.labs.overthewire.org`
- `viewsource`

```
<?
session_start();

if(array_key_exists("revelio", $_GET)) {
    // only admins can reveal the password
    if(!($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1)) {
    header("Location: /");
    }
}
?>


<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="styl
.
.
.
.
.
<?
    if(array_key_exists("revelio", $_GET)) {
    print "You are an admin. The credentials for the next level are:<br>";
    print "<pre>Username: natas23\n";
    print "Password: <censored></pre>";
    }
?> 
```
- Notice: `if(array_key_exists("revelio", $_GET)) {`, if url contains `revelio`, the password will be displayed.
- let's do that: `natas22.natas.labs.overthewire.org/index.php?revelio`
- but also notice:

```
if(!($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1)) {
    header("Location: /");
    }
```
- it means if session doesn't have admin as a key, the site will be redirected to `/` location
- We have to catch request before redirection, we can do that in repeater!
![image](https://user-images.githubusercontent.com/68887544/150103732-3588b7a9-41f2-41b2-bce2-475f964efdce.png)
![image](https://user-images.githubusercontent.com/68887544/150103779-2d20fbb1-4e8f-4243-b4ac-09a8378e4fb6.png)
- Scroll down a lil'


![image](https://user-images.githubusercontent.com/68887544/150103894-4fd0060a-0bba-471a-8da2-563628ba2c1b.png)

- Boom! Solved

```
You are an admin. The credentials for the next level are:<br><pre>Username: natas23
Password: D0vlad33nQF0Hz2EP255TP5wSW9ZsRSE</pre>
```


## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- Always look at the response before redirection
