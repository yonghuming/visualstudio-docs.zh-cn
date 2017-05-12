---
title: "EX_DBGPROP_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: EX_DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "EX_DBGPROP_INFO_FLAGS"
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# EX_DBGPROP_INFO_FLAGS
用于指定 `ExtendedDebugPropertyInfo` 字段。  
  
## 语法  
  
```  
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## 成员  
 EX\_DBGPROP\_INFO\_ID  
 初始化属性的标识符。  
  
 EX\_DBGPROP\_INFO\_NTYPE  
 初始化属性的类型。  
  
 EX\_DBGPROP\_INFO\_NVALUE  
 初始化属性的值。  
  
 EX\_DBGPROP\_INFO\_LOCKBYTES  
 初始化 `plb` 字段。  
  
 EX\_DBGPROP\_INFO\_DEBUGEXTPROP  
 初始化包含一 `IDebugExtendedProperty` 接口的 `pDebugExtProp` 字段。  
  
## 请参阅  
 [ExtendedDebugPropertyInfo 结构](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [IDebugExtendedProperty 接口](../../winscript/reference/idebugextendedproperty-interface.md)