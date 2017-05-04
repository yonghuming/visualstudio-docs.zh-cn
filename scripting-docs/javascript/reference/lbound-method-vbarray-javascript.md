---
title: "lbound 方法 (VBArray) (JavaScript) | Microsoft Docs"
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
  - "lbound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lbound 方法"
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# lbound 方法 (VBArray) (JavaScript)
将 VBArray 的指定维度中使用的最小索引值返回。  
  
## 语法  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## 参数  
 *safeArray*  
 必需。  一个 VBArray 对象。  
  
 `dimension`  
 可选。  VBArray 的要获知其索引下限的维度。  如果忽略此参数，`lbound` 将该参数视为 1。  
  
## 备注  
 若 VBArray 为空，`lbound` 方法将返回未定义。  如果 `dimension` 大于 VBArray 的维度数或为负，该方法将生成“下标超出范围”错误。  
  
## 示例  
 下面的示例由三部分组成。  第一部分是创建 Visual Basic 安全数组的 VBScript 代码。  第二部分是用于确定安全数组的维数和每一维度的下限的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码。  由于该安全数组是在 VBScript 中而不是在 Visual Basic 中创建的，因此下限将始终为零。  这两部分都位于 HTML 页的 \<HEAD\> 区域。  第三部分是位于 \<BODY\> 区域内用于运行其他两个部分的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码。  
  
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
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## 要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准、Internet Explorer 7 标准、Internet Explorer 8 标准、Internet Explorer 9 标准和 Internet Explorer 10 标准。  在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] app 中不受支持。  请参见[版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **应用于**：[VBArray 对象](../../javascript/reference/vbarray-object-javascript.md)  
  
## 请参阅  
 [dimensions 方法 \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem 方法 \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray 方法 \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound 方法 \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)