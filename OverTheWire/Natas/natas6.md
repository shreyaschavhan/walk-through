`Link` : `https://overthewire.org/wargames/natas/natas6.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟓 - 𝐋𝐞𝐯𝐞𝐥 𝟔

## 𝐆𝐢𝐯𝐞𝐧
- Username: natas6
- URL:      `http://natas6.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:      `http://natas6.natas.labs.overthewire.org`
- Notice `View sourcecode`
- Analyze:

```
<?

include "includes/secret.inc";

    if(array_key_exists("submit", $_POST)) {
        if($secret == $_POST['secret']) {
        print "Access granted. The password for natas7 is <censored>";
    } else {
        print "Wrong secret";
    }
    }
?>
```
- `if($secret == $_POST['secret']) {` & `include "includes/secret.inc";`
- Visit: `view-source:http://natas6.natas.labs.overthewire.org/includes/secret.inc`

```
<?
$secret = "FOEIUWGHFEEUHOFUOIU";
?>
```

- Input: `FOEIUWGHFEEUHOFUOIU`
- Boom!

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148732668-66910677-45f3-4440-90c4-a7699ee1d1fc.png width=500px>
</div>

- Access granted. The password for natas7 is `7z3hEENjQtflzgnT29q7wAvMNfZdh0i9`
