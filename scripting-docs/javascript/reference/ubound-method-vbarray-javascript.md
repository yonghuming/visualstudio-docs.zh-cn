---
title: "ubound 方法 (VBArray) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ubound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ubound method
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfb87cf3fd552c329635a3ca3e974c84a1324bfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ubound-method-vbarray-javascript"></a>ubound 方法 (VBArray) (JavaScript)
返回 VBArray 指定维度中使用的最大索引值。  
  
## <a name="syntax"></a>语法  
  
```  
  
safeArray.ubound(dimension)   
```  
  
## <a name="parameters"></a>参数  
 *safeArray*  
 必需。 VBArray 对象。  
  
 `dimension`  
 可选。 需要具有更大边界的索引的 VBArray 的维度。 如果省略， `ubound` 的行为方式与传递了 1 时相同。  
  
## <a name="remarks"></a>备注  
 如果 VBArray 为空， `ubound` 方法返回未定义。 如果 `dim` 大于 VBArray 的维数或者为负，此方法将生成“下标超出范围”错误。  
  
## <a name="example"></a>示例  
 下面的示例由三部分组成。 第一部分是用于创建 Visual Basic 安全数组的 VBScript 代码。 第二部分是一段 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码，用于确定维数是否在安全数组和每个维度的上限内。 这两部分进入\<H e a d > 的 HTML 页的部分。 第三部分是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]代码中，\<正文 > 部分，以便运行其他两个部分。  
  
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
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
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
  
## <a name="requirements"></a>要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中不受支持。 请参阅 [版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**： [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [dimensions 方法 (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem 方法 (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound 方法 (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray 方法 (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)