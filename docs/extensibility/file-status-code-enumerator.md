---
title: "文件状态代码枚举器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "已命名的常数，SccStatus 枚举器"
  - "源代码管理插件，文件状态枚举"
  - "SccStatus 枚举器"
  - "文件状态代码枚举器"
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 文件状态代码枚举器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`SccStatus` 枚举器包含在源代码管理系统中指定的文件的状态的已命名常量值。 此枚举由 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 和 `POPLISTFUNC` 回调函数 \(请参阅 [POPLISTFUNC](../extensibility/poplistfunc.md) 有关的详细信息\)。  
  
## 语法  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## 成员  
 SCC\_STATUS\_INVALID  
 无法获取状态;不依赖于它。  
  
 SCC\_STATUS\_NOTCONTROLLED  
 文件不是源代码管理下。  
  
 SCC\_STATUS\_CONTROLLED  
 文件是在源代码管理下。  
  
 SCC\_STATUS\_CHECKEDOUT  
 由本地磁盘上的当前用户签出。  
  
 SCC\_STATUS\_OUTOTHER  
 由另一个用户签出文件。  
  
 SCC\_STATUS\_OUTEXCLUSIVE  
 以独占方式签出文件。  
  
 SCC\_STATUS\_OUTMULTIPLE  
 由多个用户签出文件。  
  
 SCC\_STATUS\_OUTOFDATE  
 文件不是最新的。  
  
 SCC\_STATUS\_DELETED  
 从项目已被删除文件。  
  
 SCC\_STATUS\_LOCKED  
 文件被锁定则不允许使用更多的版本。  
  
 SCC\_STATUS\_MERGED  
 已合并文件，但还没有固定\/验证。  
  
 SCC\_STATUS\_SHARED  
 在项目之间共享文件。  
  
 SCC\_STATUS\_PINNED  
 文件共享到某个显式版本。  
  
 SCC\_STATUS\_MODIFIED  
 文件已被修改\/中断\/违反。  
  
 SCC\_STATUS\_OUTBYUSER  
 由当前用户签出文件。  
  
 SCC\_STATUS\_NOMERGE  
 永远不会与合并并以不需要在 GET 之前保存文件。  
  
 SCC\_STATUS\_RESERVED\_1  
 保留以供内部使用。  
  
 SCC\_STATUS\_RESERVED\_2  
 保留以供内部使用。  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)