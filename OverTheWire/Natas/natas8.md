`Link` : `https://overthewire.org/wargames/natas/natas8.html`
## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟕 - 𝐋𝐞𝐯𝐞𝐥 𝟖

## 𝐆𝐢𝐯𝐞𝐧

- Username: natas8
- URL:      `http://natas8.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:      `http://natas8.natas.labs.overthewire.org`
- Notice, `view sourcecode` button

```
<?

$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
    } else {
    print "Wrong secret";
    }
}
?>
```
- Analyze the code
- Notice: `if(encodeSecret($_POST['secret']) == $encodedSecret) {`
- That means - when input string encoded using `encodeSecret` function matches `encodedSecret` variable, it will print password.
- Means we have to reverse engineer `$encodedSecret = "3d3d516343746d4d6d6c315669563362";` to match input string.

```
bin2hex(strrev(base64_encode($secret))); = "3d3d516343746d4d6d6c315669563362";
strrev(base64_encode($secret))) = decode bin2hex("3d3d516343746d4d6d6c315669563362";)
strrev(base64_encode($secret))) = ==QcCtmMml1ViV3b
base64_encode($secret) = strrev(==QcCtmMml1ViV3b)
$secret = base64_decode(b3ViV1lmMmtCcQ==)
$secret = oubWYf2kBq

```

- Submit this secret key: `oubWYf2kBq`
- Boom!

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148761477-9eb3d09c-979c-4819-adf9-dec4a4ed2fa7.png width=500px>
</div>

- Access granted. The password for natas9 is `W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl`
