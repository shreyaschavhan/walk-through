`Link` : `https://overthewire.org/wargames/natas/natas4.html`
## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟑 - 𝐋𝐞𝐯𝐞𝐥 𝟒
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas4
- URL:      `http://natas4.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit: `http://natas4.natas.labs.overthewire.org`
- Notice that it says: 
  - `Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"`
- What can be done?
  - Notice, it says `index.php` in page source. We can do directory brute force with extension specifying `.php`. Try - it won't work and you will find nothing new.
  - Notice, the front page again. It says ` You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"`. What does that mean? There is some variable or something whose value should be "http://natas5.natas.labs.overthewire.org/". Let's intercept the request and see what can be done!
- Notice referer header!

<div align='center'>
  <img src="https://user-images.githubusercontent.com/68887544/148728683-6fd4851c-cbb0-4764-8bd0-32ff375cd6cb.png" width=500px >  
</div>


- It means request is coming from `http://natas4.natas.labs.overthewire.org/`
- It should come from `http://natas5.natas.labs.overthewire.org/`. Let's change that and forward the request. Boom! Solved.

<div align='center'>
  <img src="https://user-images.githubusercontent.com/68887544/148728799-adb4ed21-0837-42a9-b936-00f6b3c2dfdb.png" width=600px >  
</div>



- Access granted. The password for natas5 is `iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq`

 
