---
title: "IDebugDisassemblyStream2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Seek"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Seek"
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

将反汇编流中读取的指针命令的许多相对一个指定的位置。  
  
## 语法  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```c#  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### 参数  
 `dwSeekStart`  
 \[in\] 从指定该相对位置开始查找的 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md) 枚举的值处理。  
  
 `pCodeContext`  
 \[in\] 表示代码上下文的 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 对象查找操作相对。  使用此参数，仅当 `dwSeekStart` \= `SEEK_START_CODECONTEXT`;否则，此参数将被忽略可以为 null 值。  
  
 `uCodeLocationId`  
 \[in\] 代码位置标识符查找操作相对。  使用此参数，如果 `dwSeekStart` \= `SEEK_START_CODELOCID`;否则，此参数将被忽略可以设置为 0。  为代码位置标识符的声明中 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) 方法参见 " 备注 " 节。  
  
 `iInstructions`  
 \[in\] 命令数移动相对于 `dwSeekStart`指定的位置。  此值可以是负值向后移动。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果任何位置是可用于可用的命令外，列表中的一个点返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 备注  
 如果希望对位置，在列表的开头，则读取的位置设置为前面列出的第一命令。  如果看到对位置，在列表的末尾，则读取的位置设置为列表中的最后一个命令。  
  
## 请参阅  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)