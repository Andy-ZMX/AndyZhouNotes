
---

```javascript
<head>
    <script type="text/javascript" src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    <script type="text/javascript" src="https://cdn.bootcss.com/jquery.qrcode/1.0/jquery.qrcode.min.js"></script>
</head>

<body>
    <div id="qrcode"></div>
    <script>
        let name = '周库里'
        let newname = utf16to8(name)
        let url = "https://www.baidu.com"

        $('#qrcode').qrcode({ width: 100, height: 100, correctLevel: 0, text: url });

        function utf16to8(str) {
            let out = "";
            for (let i = 0; i < str.length; i++) {
                let c = str.charCodeAt(i);
                if ((c >= 0x0001) && (c <= 0x007F)) {
                    out += str.charAt(i);
                } else if (c > 0x07FF) {
                    out += String.fromCharCode(0xE0 | ((c >> 12) & 0x0F));
                    out += String.fromCharCode(0x80 | ((c >> 6) & 0x3F));
                    out += String.fromCharCode(0x80 | ((c >> 0) & 0x3F));
                } else {
                    out += String.fromCharCode(0xC0 | ((c >> 6) & 0x1F));
                    out += String.fromCharCode(0x80 | ((c >> 0) & 0x3F));
                }
            }
            return out;
        }
    </script>
</body>
```