---
title: "SccRunScc 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRunScc
helpviewer_keywords: SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9ac82ac0363428ade1b6010a9060e15284db224
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccrunscc-function"></a>SccRunScc 函数
此函数将调用源代码管理管理工具。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 nFiles  
 [in]中指定的文件数`lpFileNames`数组。  
  
 lpFileNames  
 [in]所选的文件名称的数组。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功调用了源代码管理管理工具。|  
|SCC_I_OPERATIONCANCELED|已取消该操作。|  
|SCC_E_INITIALIZEFAILED|无法初始化源代码管理系统。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。|  
|SCC_E_CONNECTIONFAILURE|无法连接到的源控制系统。|  
|SCC_E_FILENOTCONTROLLED|所选的文件不在源控件下。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 此函数允许调用方通过外部管理工具访问的完整范围的源控制系统的功能。 如果源代码管理系统没有用户界面，源代码管理插件可以实现接口，以执行必要的管理功能。  
  
 使用计数和当前所选文件的文件名的数组调用此函数。 如果管理工具支持它，可以使用的文件列表预先选择管理界面中; 中的文件否则，可以忽略列表。  
  
 当用户选择通常调用此函数**启动\<源代码管理服务器 >**从**文件** -> **源代码管理**菜单。 这**启动**菜单选项可始终处于禁用状态或甚至隐藏通过设置注册表项。 请参阅[如何： 安装源代码管理插件](../extensibility/internals/how-to-install-a-source-control-plug-in.md)有关详细信息。 仅当调用此函数[SccInitialize](../extensibility/sccinitialize-function.md)返回`SCC_CAP_RUNSCC`功能位 (请参阅[功能标志](../extensibility/capability-flags.md)有关此选项及其他功能位的详细信息)。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [如何： 安装了源代码管理插件](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [功能标志](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)