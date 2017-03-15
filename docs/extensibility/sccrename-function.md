---
title: "SccRename 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRename"
helpviewer_keywords: 
  - "SccRename 函数"
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccRename 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数在源代码管理系统中重命名文件。  
  
## 语法  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpFileName  
 \[\] in要重命名该文件的完全限定的文件名。  
  
 lpNewName  
 \[\] in完全限定的新名称。 如果目录路径不同，则该文件已移动从一个子目录到另一个。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|重命名操作已成功完成。|  
|SCC\_E\_PROJNOTOPEN|未受源代码管理打开项目。|  
|SCC\_E\_FILENOTCONTROLLED|文件不是源代码管理下。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。|  
|SCC\_E\_NOTAUTHORIZED|未授权用户来完成此操作。|  
|SCC\_E\_COULDNOTCREATEPROJECT|重命名过程的一部分，无法创建该项目。|  
|SCC\_E\_OPNOTPERFORMED|不执行该操作。|  
|SCC\_E\_NONSPECIFICERROR|未指定或为常规时出错。|  
  
## 备注  
 此函数可用于重命名文件或它从一个位置移动到另一个源控制系统中。 源代码管理插件不应尝试访问磁盘上的文件。 它是 IDE 的责任，若要重命名本地文件。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)