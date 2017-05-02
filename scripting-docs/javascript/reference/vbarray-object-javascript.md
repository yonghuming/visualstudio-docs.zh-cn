---
title: "VBArray 对象 (JavaScript) | Microsoft Docs"
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
  - "VBArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "VBArray 对象常量"
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# VBArray 对象 (JavaScript)
提供对 Visual Basic 安全数组的访问。  
  
> [!WARNING]
>  此对象仅在 Internet Explorer 中受支持，在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中不受支持。  
  
## 语法  
  
```  
  
varName = new VBArray(safeArray)  
```  
  
## 参数  
 `varName`  
 必需。 VBArray 分配到的变量名称。  
  
 *safeArray*  
 必需。 VBArray 值。  
  
## 备注  
 VBArray 是只读的，不能直接创建。*safeArray* 参数在传递到 VBArray 构造函数之前，必须获取一个 VBArray 值。 只有从现有的 ActiveX 或其他对象进行检索，才能获取该值。  
  
 VBArray 可以有多个维度。 每个维度的索引都可能不同。**dimensions** 方法检索数组中的维数；`lbound` 和 `ubound` 方法检索每个维度所使用的索引范围。  
  
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
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
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
  
## 属性  
 `VBArray` 对象没有属性。  
  
## 方法  
 [dimensions 方法](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [getItem 方法](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [lbound 方法](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [toArray 方法](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [ubound 方法](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## 要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。 请参阅[版本信息](../../javascript/reference/javascript-version-information.md)。  
  
## 请参阅  
 [Array 对象](../../javascript/reference/array-object-javascript.md)