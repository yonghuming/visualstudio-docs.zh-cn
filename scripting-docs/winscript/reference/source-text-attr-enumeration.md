---
title: "SOURCE_TEXT_ATTR 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR 枚举
描述单个源文本字符的特性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>成员  
  
|成员|值|描述|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|从 0x0001|字符是一个语言关键字，例如，VBScript 关键字的一部分`While`。|  
|SOURCETEXT_ATTR_COMMENT|0x0002|字符是一个注释块的一部分。|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|字符不是编译的语言源文本的一部分。 例如，HTML 周围的脚本块。|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|字符是一个语言运算符的一部分。 例如:，算术运算符 **+** 。|  
|SOURCETEXT_ATTR_NUMBER|0x0010|字符是一个语言数值常量的一部分。  例如，常量 3.14159。|  
|SOURCETEXT_ATTR_STRING|0x0020|字符是语言字符串常量的一部分。 例如，字符串"Hello World"。|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|字符表示函数块的起始位置|  
  
## <a name="remarks"></a>备注  
 通常情况下， `IDebugDocumentHost::GetScriptTextAttributes`， `IActiveScriptDebug::GetScriptletTextAttributes`，和`IActiveScriptDebug::GetScriptTextAttributes`方法返回一个文本属性，每个字符，除非：  
  
-   设置 GETATTRTYPE_DEPSCAN 标志，在这种情况下，该方法可能返回 SOURCETEXT_ATTR_IDENTIFIER 和 SOURCETEXT_ATTR_MEMBERLOOKUP 标志  
  
-   设置 GETATTRFLAG_THIS 标志，在这种情况下，该方法可能返回 SOURCETEXT_ATTR_THIS 标志  
  
-   设置 GETATTRFLAG_HUMANTEXT 标志，在这种情况下，该方法可能返回 SOURCETEXT_ATTR_HUMANTEXT 标志。  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)