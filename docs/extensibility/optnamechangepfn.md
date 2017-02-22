---
title: "OPTNAMECHANGEPFN | Microsoft Docs"
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
  - "OPTNAMECHANGEPFN"
helpviewer_keywords: 
  - "OPTNAMECHANGEPFN 回调函数"
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

这是对调用中指定一个回调函数 [SccSetOption](../extensibility/sccsetoption-function.md) \(使用选项 `SCC_OPT_NAMECHANGEPFN`\)，用于告知名称所做的更改源代码管理插件回 IDE。  
  
## 签名  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)( LPVOID pvCallerData, LPCSTR pszOldName, LPCSTR pszNewName );  
```  
  
## 参数  
 pvCallerData  
 \[\] in对上一个调用中指定的用户值 [SccSetOption](../extensibility/sccsetoption-function.md) \(使用选项 `SCC_OPT_USERDATA`\)。  
  
 pszOldName  
 \[\] in原始文件的名称。  
  
 pszNewName  
 \[\] in文件的名称已重命名为。  
  
## 返回值  
 无。  
  
## 备注  
 在源代码管理操作期间将重命名文件，如果源代码管理插件可以通知通过该回调的名称更改的相关 IDE。  
  
 如果 IDE 不支持此回调，它将不会调用 [SccSetOption](../extensibility/sccsetoption-function.md) 指定它。 如果该插件不支持此回调，它将返回 `SCC_E_OPNOTSUPPORTED` 从 `SccSetOption` IDE 来尝试设置该回调时的功能。  
  
## 请参阅  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)