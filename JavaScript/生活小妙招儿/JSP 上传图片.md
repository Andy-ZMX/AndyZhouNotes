
---

**jsp:**

```html
<input id="input" type="file"/>
<img id="img"/>

<style>
    #input {
        position: absolute;
        top: 8px;
        left: 8px;
        width: 100px;
        height: 100px;
        opacity: 0;
        cursor: pointer;
    }

    #img {
        width: 100px;
        height: 100px;
    }
</style>
```

------------

**js:**

```javascript
$(document).ready(function () {
    $('#input').change(function () {
        uploadPicture(this)
    })

    function uploadPicture(picture) {
        var fileData = picture.files[0]
        let formData = new FormData()
        formData.append('AndyPicture', picture.files[0], picture.files[0].name)

        $.ajax({
            type: "post",
            url: "/demo/pictureupload",
            dataType: "JSON",
            data: formData,
            contentType: false,
            processData: false,
            success: function (returndata) {
                console.log(returndata)
            }
        })

        var reader = new FileReader()
        reader.readAsDataURL(fileData)
        reader.onload = function () {
            document.getElementById('img').setAttribute("src", this.result)
        }
    }
});
```

------------

**FileUploadController.java:**

```javascript
package com.controller;

import com.returnObj.ReturnObject;
import com.service.FileUploadService;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.ResponseBody;
import org.springframework.web.multipart.MultipartFile;

import javax.annotation.Resource;
import java.io.IOException;

@Controller
@RequestMapping("/demo")
public class FileUploadController {
    @Resource
    private FileUploadService fileUploadService;

    @RequestMapping("/pictureupload")
    @ResponseBody
    public ReturnObject pictureupload(@RequestParam(value = "AndyPicture") MultipartFile file) throws IOException {
        return fileUploadService.pictureUpload(file);
    }
}

```

------------

**FileUploadService.java:**

```javascript
package com.service;

import com.returnObj.ReturnObject;
import org.springframework.stereotype.Service;
import org.springframework.web.multipart.MultipartFile;

import java.io.File;
import java.io.IOException;

@Service
public class FileUploadService {
    public ReturnObject pictureUpload(MultipartFile file) throws IOException {
        String filename = file.getOriginalFilename();
        String filepath = "D:/springmvcIMG";
        File picture = new File(filepath + "/" + filename);
        file.transferTo(picture);
        ReturnObject returnObject = new ReturnObject();
        returnObject.setMessage("success");
        return returnObject;
    }
}
```

------------

**ReturnObject.java:**

```javascript
package com.returnObj;

import lombok.Data;

@Data
public class ReturnObject {
    private String message;
}
```

---

![[Pasted image 20240704221035.png]]