`Link` : `https://overthewire.org/wargames/natas/natas11.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟎 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟏

## 𝐆𝐢𝐯𝐞𝐧
- Username: natas11
- URL:      `http://natas11.natas.labs.overthewire.org`


## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit: `http://natas11.natas.labs.overthewire.org`
- `view pagesource`

```
<?

$defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");

function xor_encrypt($in) {
    $key = '<censored>';
    $text = $in;
    $outText = '';

    // Iterate through each character
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}

function loadData($def) {
    global $_COOKIE;
    $mydata = $def;
    if(array_key_exists("data", $_COOKIE)) {
    $tempdata = json_decode(xor_encrypt(base64_decode($_COOKIE["data"])), true);
    if(is_array($tempdata) && array_key_exists("showpassword", $tempdata) && array_key_exists("bgcolor", $tempdata)) {
        if (preg_match('/^#(?:[a-f\d]{6})$/i', $tempdata['bgcolor'])) {
        $mydata['showpassword'] = $tempdata['showpassword'];
        $mydata['bgcolor'] = $tempdata['bgcolor'];
        }
    }
    }
    return $mydata;
}

function saveData($d) {
    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
}

$data = loadData($defaultdata);

if(array_key_exists("bgcolor",$_REQUEST)) {
    if (preg_match('/^#(?:[a-f\d]{6})$/i', $_REQUEST['bgcolor'])) {
        $data['bgcolor'] = $_REQUEST['bgcolor'];
    }
}

saveData($data);



?>

<h1>natas11</h1>
<div id="content">
<body style="background: <?=$data['bgcolor']?>;">
Cookies are protected with XOR encryption<br/><br/>

<?
if($data["showpassword"] == "yes") {
    print "The password for natas12 is <censored><br>";
}

?>

```

- Notice: 
```
if($data["showpassword"] == "yes") {
    print "The password for natas12 is <censored><br>";
}
```
- means if `showpassord=yes` in cookie then password will appear.
- Again, it says `Cookies are protected with XOR encryption`
- XOR encryption works like:
  - plain-text ^ key = cipher
  - if we have any two, we can get the rest.
  - We have plain-text: `json_encode(array( "showpassword"=>"no", "bgcolor"=>"#ffffff");)`
  - plain-text: `{"showpassword":"no","bgcolor":"#ffffff"}`
  - cipher: `ClVLIh4ASCsCBE8lAxMacFMZV2hdVVotEhhUJQNVAmhSEV4sFxFeaAw=`
  - key? we don't know the key
- Use: `https://gchq.github.io/CyberChef/ ` to encrypt decrypt from everything to everything

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148797329-ef11aaec-0327-4f45-9522-fccf1563d71a.png width=700px>
</div>

- We got the key: `qw8J`
- Let's change `showpassword=yes`

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148797793-846d69f0-3a22-4e04-9d93-d622138b6ebb.png width=700px>
</div>

- `ClVLIh4ASCsCBE8lAxMacFMOXTlTWxooFhRXJh4FGnBTVF4sFxFeLFMK`
- Intercept the request, change the cookie value and BOOM! Done

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148798102-6006c79d-500b-4282-a21e-91041539b4ce.png width=500px>
</div>

- The password for natas12 is `EDXp0pS26wLKHZy1rDBPUZk0RKfLGIR3`
