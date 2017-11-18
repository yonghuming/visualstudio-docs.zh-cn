---
title: "ScriptEngineMajorVersion 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngineMajorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngineMajorVersion function
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815e6fb92744fc2145cae2cbaa6a5574c3ea3ecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginemajorversion-function-javascript"></a>ScriptEngineMajorVersion 函数 (JavaScript)
获取使用中脚本引擎的主版本号。  
  
## <a name="syntax"></a>语法  
  
```  
ScriptEngineMajorVersion()  
```  
  
## <a name="remarks"></a>备注  
 返回值直接对应正在使用的脚本语言的动态链接库 (DLL) 中包含的版本信息。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `ScriptEngineMajorVersion` 函数的用法：  
  
```JavaScript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [ScriptEngine 函数](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion 函数](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion 函数](../../javascript/reference/scriptengineminorversion-function-javascript.md)