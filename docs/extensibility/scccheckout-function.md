---
title: "SccCheckout 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCheckout"
helpviewer_keywords: 
  - "SccCheckout 函数"
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCheckout 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

给定的完全限定的文件名列表，此函数将它们签出到的本地驱动器。 注释适用于被签出的所有文件。 注释参数可以是 `null` 字符串。  
  
## 语法  
  
```cpp#  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 nFiles  
 \[\] in选择要签出文件的数量。  
  
 lpFileNames  
 \[\] in签出文件的完全限定的本地路径名称的数组。  
  
 lpComment  
 \[\] in若要应用于每个被签出所选文件的注释。  
  
 选项  
 \[\] in命令标志 \(请参阅 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md)\)。  
  
 pvOptions  
 \[\] in源代码管理插件特定选项。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|签出成功。|  
|SCC\_E\_FILENOTCONTROLLED|所选的文件不是源代码管理下。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_NONSPECIFICERROR|非特定故障。 不签出该文件。|  
|SCC\_E\_ALREADYCHECKEDOUT|用户已签出该文件。|  
|SCC\_E\_FILEISLOCKED|文件被锁定，因此禁止创建的新版本。|  
|SCC\_E\_FILEOUTEXCLUSIVE|另一个用户对此文件已经以独占签出。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前取消了操作。|  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md)