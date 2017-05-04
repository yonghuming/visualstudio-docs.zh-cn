---
title: "toArray 方法 (VBArray) (JavaScript) | Microsoft Docs"
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
  - "toArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toArray 方法"
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# toArray 方法 (VBArray) (JavaScript)
返回一个从 VBArray 转换来的标准 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组。  
  
## 语法  
  
```  
  
safeArray.toArray( )  
```  
  
## 备注  
 所需的 *safeArray* 引用是 VBArray 对象。  
  
 该转换将多维 VBArray 转换成一维 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组。 每个连续的维度将追加到上一个维度的末尾。 例如，一个三维且每一维有三个元素的 VBArray 将被转换为如下所示的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组：  
  
 假定 VBArray 包含：\(1, 2, 3\)、\(4, 5, 6\) 和 \(7, 8, 9\)。 转换之后，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组包含：1、2、3、4、5、6、7、8 和 9。  
  
 目前还没有将 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组转换为 VBArray 的方法。  
  
## 示例  
 下面的示例由三部分组成。 第一部分是用于创建 Visual Basic 安全数组的 VBScript 代码。 第二部分是用于将 Visual Basic 安全数组转换为 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码。 这两部分都位于 HTML 页面的 \<HEAD\> 节中。 第三部分是位于 \<BODY\> 节中的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码，用于运行其他两部分。  
  
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
         a(j, i) = k  
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
function VBArrayTest(vbarray)  
{  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## 要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。 请参阅[版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**：[VBArray 对象](../../javascript/reference/vbarray-object-javascript.md)  
  
## 请参阅  
 [dimensions 方法 \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem 方法 \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound 方法 \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [ubound 方法 \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)