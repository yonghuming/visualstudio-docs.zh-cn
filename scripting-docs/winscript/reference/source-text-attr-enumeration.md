---
title: "SOURCE_TEXT_ATTR 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SOURCE_TEXT_ATTR 常量"
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# SOURCE_TEXT_ATTR 枚举
描述源文本单个字符的属性。  
  
## 语法  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR  
{  
    SOURCETEXT_ATTR_KEYWORD    = 0x0001,  
    SOURCETEXT_ATTR_COMMENT    = 0x0002,  
    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,  
    SOURCETEXT_ATTR_OPERATOR   = 0x0008,  
    SOURCETEXT_ATTR_NUMBER    = 0x0010,  
    SOURCETEXT_ATTR_STRING    = 0x0020,  
    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040  
};  
  
```  
  
## 成员  
  
|成员|值|说明|  
|--------|-------|--------|  
|SOURCETEXT\_ATTR\_KEYWORD|0x0001|字符是语言关键字，例如，VBScript关键字 `While`的一部分。|  
|SOURCETEXT\_ATTR\_COMMENT|0x0002|字符是注释的部分块。|  
|SOURCETEXT\_ATTR\_NONSOURCE|0x0004|字符不是语言生成源文本的部分。  例如，用脚本的HTML块。|  
|SOURCETEXT\_ATTR\_OPERATOR|0x0008|字符是语言运算符的一部分。  例如:，算术运算符 **\+**。|  
|SOURCETEXT\_ATTR\_NUMBER|0x0010|字符是语言数值常数的一部分。  例如，常数3.14159。|  
|SOURCETEXT\_ATTR\_STRING|0x0020|字符是语言字符串常数的一部分。  例如，字符串“hello world”。|  
|SOURCETEXT\_ATTR\_FUNCTION\_START|0x0040|字符指示函数块的开头|  
  
## 备注  
 通常，`IDebugDocumentHost::GetScriptTextAttributes`、 `IActiveScriptDebug::GetScriptletTextAttributes`和 `IActiveScriptDebug::GetScriptTextAttributes` 方法返回每个字符的文本，特性，除非：  
  
-   在方法中，可以返回SOURCETEXT\_ATTR\_IDENTIFIER和SOURCETEXT\_ATTR\_MEMBERLOOKUP标志情况下，GETATTRTYPE\_DEPSCAN设置了标志，  
  
-   在方法中，可以返回SOURCETEXT\_ATTR\_THIS标志情况下，GETATTRFLAG\_THIS设置了标志，  
  
-   在方法中，可以返回SOURCETEXT\_ATTR\_HUMANTEXT标志情况下，GETATTRFLAG\_HUMANTEXT标志设置为。  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)