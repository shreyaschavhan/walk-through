`Link` : `https://overthewire.org/wargames/natas/natas23.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟐𝟐 - 𝐋𝐞𝐯𝐞𝐥 𝟐𝟑
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas23
- URL:      `http://natas23.natas.labs.overthewire.org`
## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:       `http://natas23.natas.labs.overthewire.org`
- `view source`

```

<?php
    if(array_key_exists("passwd",$_REQUEST)){
        if(strstr($_REQUEST["passwd"],"iloveyou") && ($_REQUEST["passwd"] > 10 )){
            echo "<br>The credentials for the next level are:<br>";
            echo "<pre>Username: natas24 Password: <censored></pre>";
        }
        else{
            echo "<br>Wrong!<br>";
        }
    }
    // morla / 10111
?>  
```

- Notice: `if(strstr($_REQUEST["passwd"],"iloveyou") && ($_REQUEST["passwd"] > 10 )){`
- The `strstr` function searches for the first occurence of "iloveyou" and returns anything written before it
- Let's write a password which satisfies above condition
- The condition is password should contain `iloveyou` and whatever written before it should be greater than 10.
- The password will be : `XXiloveyou` where `XX > 10`, let's say `XX = 11`
- Boom! Solved

![image](https://user-images.githubusercontent.com/68887544/150110926-24ebb9e2-6c24-4dea-b138-5291a56b2d59.png)

- `Username: natas24 Password: OsRmXFguozKpTZZ5X14zNO43379LZveg`

## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- php strstr function
