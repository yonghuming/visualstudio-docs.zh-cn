---
title: "使用严格指令 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- strict_JavaScriptKeyword
- use strict
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict directive
- use strict
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd951255f5d5719c3aa216965605840ba12010d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="use-strict-directive"></a>使用严格指令
限制 JavaScript 中的一些功能的使用。 在 Internet Explorer 10 中支持和[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]的应用程序。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
use strict  
```  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的代码导致语法错误，因为在严格模式下必须使用声明所有变量`var`。  
  
```JavaScript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [Strict Mode](../../javascript/advanced/strict-mode-javascript.md)