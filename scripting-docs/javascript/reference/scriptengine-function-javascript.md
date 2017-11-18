---
title: "ScriptEngine 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngine
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngine function
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d441fcce065677f7b673a9979acff9cf9aa2ce90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengine-function-javascript"></a>ScriptEngine 函数 (JavaScript)
获取正在使用的脚本语言的名称。  
  
## <a name="syntax"></a>语法  
  
```  
ScriptEngine()  
```  
  
## <a name="remarks"></a>备注  
 `ScriptEngine` 函数返回“JScript”，它指示 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 是当前脚本引擎。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `ScriptEngine` 函数的用法：  
  
```JavaScript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [ScriptEngineBuildVersion 函数](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion 函数](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion 函数](../../javascript/reference/scriptengineminorversion-function-javascript.md)