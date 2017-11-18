---
title: "标记语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="labeled-statement-javascript"></a>Labeled 语句 (JavaScript)
提供语句的标识符。  
  
## <a name="syntax"></a>语法  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>参数  
 *标签*  
 必需。 当引用的标记语句时使用唯一标识符。  
  
 `statements`  
 可选。 与相关联的一个或多个语句*标签*。  
  
## <a name="remarks"></a>备注  
 使用标签**中断**和**继续**语句，以指定向其语句**中断**和**继续**应用。  
  
## <a name="example"></a>示例  
 在下面的代码中，**继续**语句是指**为**前面是循环`Inner:`语句。 当`j`为 24，**继续**语句使**为**循环转到下一个迭代。 在每个行上打印数字 21 到 23 和 25 到 30。  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)