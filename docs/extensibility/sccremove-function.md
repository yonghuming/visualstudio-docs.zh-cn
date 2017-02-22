---
title: "SccRemove 函数 | Microsoft Docs"
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
  - "SccRemove"
helpviewer_keywords: 
  - "SccRemove 函数"
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccRemove 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数从源代码管理系统中删除文件。  
  
## 语法  
  
```cpp#  
SCCRTN SccRemove(  
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
 \[\] in中指定的文件数 `lpFileNames` 数组。  
  
 lpFileNames  
 \[\] in要删除的文件的完全限定的本地路径名称的数组。  
  
 lpComment  
 \[\] in要应用于每个文件被删除的注释。  
  
 选项  
 \[\] in命令的标志 \(未使用\)。  
  
 pvOptions  
 \[\] in源代码管理插件特定选项。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|删除成功。|  
|SCC\_E\_FILENOTCONTROLLED|所选的文件不受源代码管理中。|  
|SCC\_E\_OPNOTSUPPORTED|源代码管理系统不支持此操作。|  
|SCC\_E\_ISCHECKEDOUT|无法删除文件，因为用户当前已将其签。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_NONSPECIFICERROR|模糊失败;不删除文件。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前取消了操作。|  
  
## 备注  
 此函数从源代码管理系统中删除文件，而不会从用户的本地硬盘删除它们。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)