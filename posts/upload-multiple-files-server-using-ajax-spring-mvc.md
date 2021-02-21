---
title: How to upload multiple files to server using Ajax and Spring mvc
created: 2016-10-06T12:45:13+05:30
author: ashishdoneriya
description: javascript file upload. Example to upload multiple files to server using ajax, javascript, html while remain on the same page for any server side langauge.
permalink: /upload-multiple-files-server-using-ajax-spring-mvc.html
tags:
  - java
updated: 2016-10-06T12:45:13+05:30
categories:
  - java
---

In one of my projects, I had to upload the files to server using javascript file upload. So after a lot of hit and trials here is the code snippet that I used to upload multiple files to server while remain on the same page in client using ajax and spring mvc. In this example we are submitting the form through javascript instead of directly from html.

#### HTML Code

```html
<form class="form-horizontal" id="myForm" method="POST" enctype="multipart/form-data">
  <fieldset>
    <!-- File Button -->
    <div class="form-group">
      <label class="col-md-4 control-label" for="papers">
        Add Files
      </label>
      <div class="col-md-4">
        <input name="papers" id="modalPapers" type="file" class="filestyle" multiple data-input="false">
      </div>
    </div>
    <!-- Button -->
    <div class="form-group">
      <label class="col-md-4 control-label" for="submit"></label>
      <div class="col-md-4">
        <input type="button" value="Submit" name="submit" onclick="submitForm()" class="btn btn-success">
      </div>
    </div>
  </fieldset>
</form>
```


#### Javascript Code

```javascript
function submitForm() {

  var paperElement = document.getElementById("modalPapers");

  if (!paperElement.value) {
    console.log("No files selected.")
    return;
  }
  var form = document.getElementById("myForm");
  var formData = new FormData(form);
  var xhr = getXMLHTTP();
  xhr.open('POST', "submitFiles");
  xhr.onreadystatechange = function() {
    if (xhr.readyState == 4 && xhr.status == 200) {
      console.log("Files Uploaded")
    }
  }
  xhr.send(formData);
}
```


#### Java Code

(server side)

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.ResponseBody;
import org.springframework.web.multipart.MultipartFile;
import org.springframework.web.multipart.MultipartHttpServletRequest;
import org.apache.commons.io.IOUtils;

@Controller
public class MyController {

  @ResponseBody
  @RequestMapping(value = "submitFiles", method = RequestMethod.POST)
  public String submitPapers(MultipartHttpServletRequest request) {
    List &lt; MultipartFile &gt; papers = request.getFiles("papers");
    try {
      saveFilesToServer(papers);
    } catch (Exception e) {
      return "error";
    }
    return "success";
  }

  public void saveFilesToServer(List&lt;MultipartFile&gt; multipartFiles) throws IOException {
  	String directory = "/home/user/uploadedFilesDir/";
	File file = new File(directory);
	file.mkdirs();
	for (MultipartFile multipartFile : multipartFiles) {
		file = new File(directory + multipartFile.getOriginalFilename());
		IOUtils.copy(multipartFile.getInputStream(), new FileOutputStream(file));
	}
  }

}

```


You can use any other language also in server side but the html code and javascript code remains the same.
