`Link`:`https://overthewire.org/wargames/natas/natas24.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟐𝟑 - 𝐋𝐞𝐯𝐞𝐥 𝟐𝟒
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas24
- URL:      `http://natas24.natas.labs.overthewire.org`
## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧
- Visit: `http://natas24.natas.labs.overthewire.org`
- `view source`

```
<h1>natas24</h1>
<div id="content">

Password:
<form name="input" method="get">
    <input type="text" name="passwd" size=20>
    <input type="submit" value="Login">
</form>

<?php
    if(array_key_exists("passwd",$_REQUEST)){
        if(!strcmp($_REQUEST["passwd"],"<censored>")){
            echo "<br>The credentials for the next level are:<br>";
            echo "<pre>Username: natas25 Password: <censored></pre>";
        }
        else{
            echo "<br>Wrong!<br>";
        }
    }
    // morla / 10111
?>  
```
- Notice: `if(!strcmp($_REQUEST["passwd"],"<censored>")){` 
- Note that: `strcmp` Compare two strings 
- I thought password bruteforce is the only way, but it didn't work
- But then found out that, strcmp have problem with comparing non-string with string

![image](https://user-images.githubusercontent.com/68887544/150126330-624b3fda-3688-4474-b8bd-dae43d144e9d.png)

- Visit: `http://natas24.natas.labs.overthewire.org/?passwd[]=0`
- and boom! solved

![image](https://user-images.githubusercontent.com/68887544/150126532-9a5ed321-3ca3-4780-a33c-90e54bd5d4e1.png)

- `Username: natas25 Password: GHF6X7YwACaYYssHVY05cFq83hRktl4c`



## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- Hydra : https://www.youtube.com/watch?v=-gE4leMl5Gg
- HTTP basic authentication URL with “@” in password : https://www.tutorialspoint.com/http-basic-authentication-url-with-in-password
- wfuzz
- john the ripper
- 10k most common passwords: https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/10k-most-common.txt
- PHP strcmp bypass: https://www.doyler.net/security-not-included/bypassing-php-strcmp-abctf2016
- strcmp
- PHP `$_REQUEST` : https://www.w3schools.com/php/php_superglobals_request.asp
