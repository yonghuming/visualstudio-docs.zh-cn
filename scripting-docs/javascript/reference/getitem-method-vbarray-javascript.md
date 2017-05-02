---
title: "getItem 方法 (VBArray) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "getItem"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getItem 方法"
  - "Item 属性"
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getItem 方法 (VBArray) (JavaScript)
返回位于指定位置的项。  
  
## 语法  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)  
```  
  
## 参数  
 *safeArray*  
 必需。 VBArray 对象。  
  
 *dimension1, ..., dimensionN*  
 指定 VBArray 所需元素的确切位置。*n* 等于 VBArray 中的维数。  
  
## 示例  
 下面的示例由三部分组成。 第一部分是用于创建 Visual Basic 安全数组的 VBScript 代码。 第二部分是用于循环访问 Visual Basic 安全数组并输出每个元素的内容的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码。 这两部分都位于 HTML 页面的 \<HEAD\> 节中。 第三部分是位于 \<BODY\> 节中的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码，用于运行其他两部分。  
  
```javascript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## 要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。 请参阅[版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**：[VBArray 对象](../../javascript/reference/vbarray-object-javascript.md)  
  
## 请参阅  
 [dimensions 方法 \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [lbound 方法 \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray 方法 \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound 方法 \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)