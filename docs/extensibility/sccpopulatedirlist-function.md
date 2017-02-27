---
title: "SccPopulateDirList 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateDirList"
helpviewer_keywords: 
  - "SccPopulateDirList 函数"
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# SccPopulateDirList 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数可确定哪个目录和 \(可选\) 文件存储在源代码管理，提供要检查的目录列表。  
  
## 语法  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文指针。  
  
 nDirs  
 \[\] in目录路径中的数量 `lpDirPaths` 数组。  
  
 lpDirPaths  
 \[\] in若要检查的目录路径的数组。  
  
 pfnPopulate  
 \[\] in要为每个目录路径和 \(可选\) 中的文件名调用的回调函数 `lpDirPaths` \(请参阅 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 有关的详细信息\)。  
  
 pvCallerData  
 \[\] in要传递的值未更改的回调函数。  
  
 选项  
 \[\] in控制如何处理这些目录的值的组合 \(请参阅的"PopulateDirList flags"一节 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md) 有关可能的值\)。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|成功完成该操作。|  
|SCC\_E\_UNKNOWNERROR|出现错误。|  
  
## 备注  
 只有那些目录和 \(可选\) 实际上是在源代码控制存储库中的文件名传递给回调函数。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [错误代码](../extensibility/error-codes.md)