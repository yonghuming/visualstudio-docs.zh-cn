---
title: "在网页中显示文本 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, 编写"
  - "JavaScript, 编写文本"
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# 在网页中显示文本 (JavaScript)
可通过多种方式在网页中显示文本。  每种方式都有优点和缺点，并且支持特定的用途。  
  
## 显示文本  
  
-   用于显示文本的建议方式是创建一个元素并写入其 [textContent](http://msdn.microsoft.com/zh-cn/e530667f-f8fa-4b6d-a47c-4d5c75e71265) 属性：  
  
    ```javascript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     在此示例中，`text` 的值为“my text”。  但是，通过获取或设置父节点上的 [textContent](http://msdn.microsoft.com/zh-cn/e530667f-f8fa-4b6d-a47c-4d5c75e71265) 属性所获得的值可能包括节点子级的文本内容。  以下示例演示了在子节点上设置的 [textContent](http://msdn.microsoft.com/zh-cn/e530667f-f8fa-4b6d-a47c-4d5c75e71265) 包含在父节点的 [textContent](http://msdn.microsoft.com/zh-cn/e530667f-f8fa-4b6d-a47c-4d5c75e71265) 的值中：  
  
    ```javascript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     在此示例中，`text` 的值为“\[nested\]”。  
  
-   你也可以创建一个元素并写入该元素的 [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) 或 [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) 属性。  设置这些属性只会影响元素自己包含的文本，而不会影响元素的子级所包含的文本。  但是，这些属性也存在一些缺陷：  
  
    -   [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) 属性并不适用于所有浏览器，因此出于兼容性原因，你可能需要避免使用该属性。  
  
    -   [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) 属性受 CSS 样式影响，并且在该元素隐藏时不会显示。  
  
    -   [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) 属性获取和设置嵌套的节点及文本。  如果该属性未受到保护，则可将其用于脚本注入攻击。  此外，若将其设置为不带 HTML 标记的文本，则将移除先前设置的所有节点。  
  
-   你可使用 `document.write` 方法，而无需创建元素。  但是，使用此方法会导致整个网页被清除，这可能不是你想得到的结果。  
  
     以下示例演示使用 `document.write` 所带来的缺点之一。  脚本意在每 5 秒显示一次时间，但它只显示时间两次。  在第二次调用 `document.write` 时，页面完成加载，然后 `document.write` 清除整个页面（称为 `document.open`）。  此时，`ShowTime` 函数不再存在。  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     若要修复前面的代码，请移除包含 `document.write` 的代码行，然后取消其后面的两行注释。  
  
-   也可使用 `alert` `prompt`或 `confirm` 函数，这将在弹出窗口中显示消息。  大多数情况下，建议不要在 Web 浏览器中使用弹出窗口。  大多数现代浏览器具有自动阻止弹出窗口的设置，因此你的消息可能不会显示。  此外，可以在使用弹出窗口时进入无限循环，从而使用户无法通过常规方式关闭网页。