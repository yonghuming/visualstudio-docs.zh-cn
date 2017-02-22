---
title: "常量（调试接口访问 SDK） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常量, DIA SDK"
  - "DIA SDK, 常量"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 常量（调试接口访问 SDK）
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

这些字符串常数可用于标识程序的不同部分。 DIA SDK 调试数据库 \(PDB 文件。\)  
  
## 常量  
 下面的声明为 C\/C\+\+ 宏。  
  
|宏|值|  
|-------|-------|  
|`DiaTable_Symbols`|L " symbol”|  
|`DiaTable_Sections`|L " section”|  
|`DiaTable_SrcFiles`|L " SourceFiles”|  
|`DiaTable_LineNums`|L " LineNumbers”|  
|`DiaTable_SegMap`|L " SegmentMap”|  
|`DiaTable_Dbg`|L " Dbg”|  
|`DiaTable_InjSrc`|L " InjectedSource”|  
|`DiaTable_FrameData`|L " FrameData”|  
  
## 示例  
 使用这些符号之一，这是一个示例:  
  
```cpp#  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## 要求  
 标题:dia2.h  
  
## 请参阅  
 [参考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)