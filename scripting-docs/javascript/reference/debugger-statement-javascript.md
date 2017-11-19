---
title: "调试器语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugger-statement-javascript"></a>debugger 语句 (JavaScript)
挂起执行。  
  
## <a name="syntax"></a>语法  
  
```  
debugger  
```  
  
## <a name="remarks"></a>备注  
 你可以将放置`debugger`语句暂停执行的过程中的任何位置。 使用`debugger`语句是相似的代码中设置断点。  
  
 `debugger`语句挂起执行，但它不会关闭任何文件或清除任何变量。  
  
> [!NOTE]
>  `debugger`语句无任何效果，除非正在调试脚本。  
  
## <a name="example"></a>示例  
 此示例使用`debugger`语句暂停执行以便每个循环访问`for`循环。  
  
> [!NOTE]
>  若要运行此示例，你必须安装脚本调试程序和脚本必须在调试模式下运行。  
>   
>  Internet Explorer 8 包括[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]调试器。 如果使用的是 Internet Explorer 的早期版本，请参阅 [如何：从 Internet Explorer 启用和启动脚本调试](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [JavaScript 语句](../../javascript/reference/javascript-statements.md)   
 [条件编译](../../javascript/advanced/conditional-compilation-javascript.md)