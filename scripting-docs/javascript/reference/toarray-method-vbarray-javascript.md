---
title: "toArray 方法 (VBArray) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="toarray-method-vbarray-javascript"></a>toArray 方法 (VBArray) (JavaScript)
返回一个从 VBArray 转换来的标准 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组。  
  
## <a name="syntax"></a>语法  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>备注  
 所需的 *safeArray* 引用是 VBArray 对象。  
  
 该转换将多维 VBArray 转换成一维 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组。 每个连续的维度将追加到上一个维度的末尾。 例如，一个三维且每一维有三个元素的 VBArray 将被转换为如下所示的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组：  
  
 假定 VBArray 包含：(1, 2, 3)、(4, 5, 6) 和 (7, 8, 9)。 转换之后， [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组包含：1、2、3、4、5、6、7、8 和 9。  
  
 目前还没有将 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组转换为 VBArray 的方法。  
  
## <a name="example"></a>示例  
 下面的示例由三部分组成。 第一部分是用于创建 Visual Basic 安全数组的 VBScript 代码。 第二部分是用于将 Visual Basic 安全数组转换为 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 数组的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码。 这两部分进入\<H e a d > 的 HTML 页的部分。 第三部分是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]代码中，\<正文 > 部分，以便运行其他两个部分。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中不受支持。 请参阅 [版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**： [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [dimensions 方法 (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem 方法 (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound 方法 (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [ubound 方法 (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)