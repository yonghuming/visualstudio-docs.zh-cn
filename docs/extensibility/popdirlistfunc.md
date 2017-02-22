---
title: "POPDIRLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPLISTFUNC"
helpviewer_keywords: 
  - "POPDIRLISTFUNC 回调函数"
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

这是一个回调函数，得出到 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 函数来更新目录和 \(可选\) 要找出哪些是源代码管理下的文件名称的集合。  
  
 `POPDIRLISTFUNC` 回调应调用仅对这些目录和文件名 \(在列表中提供给 `SccPopulateDirList` 函数\)，实际上是在源代码管理下。  
  
## 签名  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)( LPVOID pvCallerData, BOOL bFolder, LPCSTR lpDirectoryOrFileName );  
```  
  
## 参数  
 pvCallerData  
 \[\] in用户值提供给 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)。  
  
 bFolder  
 \[in\] `TRUE` 如果在名称 `lpDirectoryOrFileName` 是一个目录中; 否则该名称是一个文件名。  
  
 lpDirectoryOrFileName  
 \[\] in向源代码管理下的目录或文件名称的完整的本地路径。  
  
## 返回值  
 IDE 将返回相应的错误代码:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|继续进行处理。|  
|SCC\_I\_OPERATIONCANCELED|停止处理。|  
|SCC\_E\_xxx|任何适当的源控制错误应停止处理。|  
  
## 备注  
 如果 `fOptions` 参数 `SccPopulateDirList` 函数包含 `SCC_PDL_INCLUDEFILES` 标志，则该列表可能包含文件的名称，以及目录的名称。  
  
## 请参阅  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [错误代码](../extensibility/error-codes.md)