---
title: "SccRunScc 函数 | Microsoft Docs"
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
  - "SccRunScc"
helpviewer_keywords: 
  - "SccRunScc 函数"
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccRunScc 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将调用的源代码管理工具。  
  
## 语法  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
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
 \[\] in选定的文件名称的数组。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功调用的源代码管理工具。|  
|SCC\_I\_OPERATIONCANCELED|已取消该操作。|  
|SCC\_E\_INITIALIZEFAILED|无法初始化源代码管理系统。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。|  
|SCC\_E\_CONNECTIONFAILURE|无法连接到源代码管理系统。|  
|SCC\_E\_FILENOTCONTROLLED|所选的文件不受源代码管理中。|  
|SCC\_E\_NONSPECIFICERROR|非特定故障。|  
  
## 备注  
 此函数允许调用方通过外部管理工具访问的完整范围的源控制系统功能。 如果源代码管理系统有没有用户界面，源代码管理插件可以实现接口，以执行必要的管理功能。  
  
 此函数调用计数、 当前所选文件的文件名称的数组。 如果管理工具支持，可以使用的文件列表预先选择管理界面; 中的文件否则，可以忽略列表。  
  
 当用户选择通常调用此函数 **启动 \< 源代码管理服务器 \>** 从 **文件** \-\> **源代码管理** 菜单。 这 **启动** 菜单选项可以始终处于禁用状态或甚至隐藏通过注册表项设置。 有关详细信息，请参阅[如何: 安装了源代码管理插件](../extensibility/internals/how-to-install-a-source-control-plug-in.md)。 仅当调用此函数 [SccInitialize](../extensibility/sccinitialize-function.md) 返回 `SCC_CAP_RUNSCC` 功能位 \(请参阅 [功能标志](../extensibility/capability-flags.md) 有关这和其他功能的详细信息\)。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [如何: 安装了源代码管理插件](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [功能标志](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)