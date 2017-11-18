---
title: "getItem 方法 (VBArray) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>getItem 方法 (VBArray) (JavaScript)
返回位于指定位置的项。  
  
## <a name="syntax"></a>语法  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>参数  
 *safeArray*  
 必需。 VBArray 对象。  
  
 *dimension1, ..., dimensionN*  
 指定 VBArray 所需元素的确切位置。 *n* 等于 VBArray 中的维数。  
  
## <a name="example"></a>示例  
 下面的示例由三部分组成。 第一部分是用于创建 Visual Basic 安全数组的 VBScript 代码。 第二部分是用于循环访问 Visual Basic 安全数组并输出每个元素的内容的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码。 这两部分进入\<H e a d > 的 HTML 页的部分。 第三部分是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]代码中，\<正文 > 部分，以便运行其他两个部分。  
  
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
  
## <a name="requirements"></a>要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中不受支持。 请参阅 [版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**： [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [dimensions 方法 (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [lbound 方法 (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray 方法 (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound 方法 (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)