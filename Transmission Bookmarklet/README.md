# Transmission Bookmarklet
Allows remote adding of torrents via bookmarlet.
## Description
There is some prep required, then you'll be able to tap a bookmarklet to change links to auto add.
## Getting Started
1. Copy all files to the folder
```
/Applications/Transmission.app/Contents/Resources/public_html/
```
2. Edit this link (the server address and port in the beginning of the link needs to changed to your local static transmission address), then create a bookmarklet with the link:
```
javascript:(function()%7Bvar%20versionNum%20=%20%220.8%22;var%20serverAddress%20=%20%22192.168.4.101:9091%22;function%20LipoCookie()%7Bvar%20sCookie%20=%22%22;var%20aCookie%20=%20document.cookie.split(/;%5B%5Cs%5CxA0%5D*/);if%20(aCookie%20!=%20%22%22)%7Bfor%20(var%20i=0;%20i%20%3C%20aCookie.length;%20i++)%7Bif%20(aCookie%5Bi%5D.search(/(%5E__utm%7C%5E__qc)/)%20==%20-1)%7BsCookie%20=%20sCookie%20+%20aCookie%5Bi%5D%20+%20%27;%20%27;%7D%7D%7DsCookie=sCookie.replace(/;%5Cs+$/,%22%22);return%20sCookie;%7Dvar%20cookieString%20=%20LipoCookie();var%20a=document.getElementsByTagName(%27a%27);for(var%20i=0,j=a.length;i%3Cj;i++)%7Bvar%20linkurl%20=%20a%5Bi%5D.href;var%20testUrl%20=%20linkurl.substring(linkurl.lastIndexOf(%27/%27)%20+%201,%20linkurl.length);var%20testResult%20=%20testUrl.search(/(%5C.torrent$)/i);if%20(testResult%20==%20-1)%7Bvar%20testResult%20=%20linkurl.search(/(magnet:%5C?%7C%5C/get%7C%5C/download%7C%5C/dl%7C%5C/torrent)/i);%7Dif%20(testResult%20!=%20-1)%7Ba%5Bi%5D.setAttribute(%27target%27,%27_blank%27);a%5Bi%5D.setAttribute(%27href%27,%22http://%22%20+%20serverAddress%20+%20%22/transmission/web/fetchtorrent.html?torrentlink=%22%20+%20encodeURIComponent(linkurl)%20+%20%22&cs=%22%20+%20encodeURIComponent(cookieString)%20+%20%22&version=%22%20+%20versionNum%20);var%20img=document.createElement(%27img%27);img.setAttribute(%27class%27,%20%27new-window%27);img.setAttribute(%27src%27,%27data:image/gif;base64,%27+%27R0lGODlhEAAMALMLAL66tBISEjExMdTQyBoaGjs7OyUlJWZmZgAAAMzMzP///////wAAAAAAAAAAAAAA%27+%27ACH5BAEAAAsALAAAAAAQAAwAAAQ/cMlZqr2Tps13yVJBjOT4gYairqohCTDMsu4iHHgwr7UA/LqdopZS%27+%27DBBIpGG5lBQH0GgtU9xNJ9XZ1cnsNicRADs=%27);img.setAttribute(%27style%27,%27width:16px!important;height:12px!important;border:none!important;%27);a%5Bi%5D.appendChild(img);%7D%7D%7D)();
```
3. Edit the static address in the fetchtorrent.html file.
4. Ensure you are on your local network or VPN’d in, find a torrent that has a magnet or torrent link, and launch the bookmarklet. You should see the links change and now open/launch in a new window. 
 
## Notes
I am fairly certain that the bookmarklet folder code is just extra and that just the images are referenced. 

## Credit
This was entirely based/modified from someone else's code:

[https://github.com/bulljit/Transmission-Add-Torrent-Bookmarkelet](https://github.com/bulljit/Transmission-Add-Torrent-Bookmarkelet)

How is this newer one different?

- automatically redirects to transmission web view after adding
- updated icons
- fix for new Transmission file structure

