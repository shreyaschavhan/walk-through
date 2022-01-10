`Link` : `https://overthewire.org/wargames/natas/natas3.html`
## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟐 - 𝐋𝐞𝐯𝐞𝐥 𝟑
## 𝐆𝐢𝐯𝐞𝐧

- Username: natas3
- URL:      `http://natas3.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit - `http://natas3.natas.labs.overthewire.org`
- Notice that there is nothing you could find in all the URLs/Js files/css files/ cookies etc.
- Think! We can do common directory or file busrting
- Wordlist: `https://github.com/v0re/dirb/blob/master/wordlists/common.txt`
![image](https://user-images.githubusercontent.com/68887544/148722312-b4ad4739-a04e-459f-8231-acf39b8e0013.png)
- Notice: `robots.txt`
- Check response
```
User-agent: *
Disallow: /s3cr3t/

```
- Visit `/s3cr3t/`
- Notice `users.txt`

```
natas4:Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ
```
- `natas4:Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ`
