
---

**前端：ajax不会唤起浏览器下载窗口，所以使用a标签**

```html
<a href="/demo/picturedownload">download</a>
```

---

**controller：**

```javascript
package com.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

import javax.servlet.http.HttpServletResponse;
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.URLEncoder;

@Controller
@RequestMapping("/demo")
public class FileDownloadController {
    @RequestMapping("/picturedownload")
    @ResponseBody
    public String pictureupload(HttpServletResponse response) throws Exception {
        //要下载的图片地址
        String path = "D:/springmvcIMG";
        String fileName = "aaa.png";

        response.reset(); //设置页面不缓存,清空buffer
        response.setCharacterEncoding("UTF-8"); //字符编码
        response.setContentType("multipart/form-data"); //二进制传输数据
        response.setHeader("Content-Disposition", "attachment;fileName=" + URLEncoder.encode(fileName, "UTF-8"));

        File file = new File(path, fileName);
        InputStream input = new FileInputStream(file);
        OutputStream out = response.getOutputStream();
        byte[] buff = new byte[1024];
        int index = 0;
        while ((index = input.read(buff)) != -1) {
            out.write(buff, 0, index);
            out.flush();
        }
        out.close();
        input.close();
        return null;
    }
}

```

---

![[Pasted image 20240704221227.png]]
