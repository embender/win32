---
Description: .
ms.assetid: 1cb0456d-501a-4272-b89d-35e79d29d13a
title: User Agent String
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# User Agent String

The *User Agent String* contains information about a browser's identity. The User Agent String is reported to the web server as an HTTP header every time that a browser makes a request to a web server. You can also access it through a client-side script. For example, you can display the User Agent String by typing the following URL into the Windows Internet Explorer 8 address bar: "javascript:alert(navigator.userAgent)". The following illustration shows the typical resulting dialog box from Internet Explorer 8 running on Windows 7.

![screen shot of the internet explorer diaog box that has the user agent string](https://www.bing.com/search?q=screen shot of the internet explorer diaog box that has the user agent string)

Typically, the User Agent String is parsed specifically for the MSIE substring. Based on the reported version of the browser, the client-side or server-side programming logic takes a different action. For more information about the User Agent String, see [What Will Windows Internet Explorer Report as the User-Agent String?](http://msdn.microsoft.com/en-us/library/cc817582.aspx) in the MSDN Library.

## Related topics

<dl> <dt>

[Fixing Compatibility Issues in Web Applications by Using Compatibility View](remediating-web-applications-and-add-ons.md)
</dt> </dl>

 

 


