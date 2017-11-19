---
title: "SccHistory 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccHistory
helpviewer_keywords: SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93c32d9eaa3549529a649472550ec8268cd0f6e5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="scchistory-function"></a>SccHistory 函数
此函数将显示指定的文件的历史记录。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pvContext`  
 [in]源控件插件上下文结构。  
  
 `hWnd`  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 `nFiles`  
 [in]中指定的文件数`lpFileName`数组。  
  
 `lpFileName`  
 [in]文件的完全限定名称的数组。  
  
 `fOptions`  
 [in]（当前未使用） 的命令标志。  
  
 `pvOptions`  
 [in]源代码管理插件特定选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功获得版本历史记录。|  
|SCC_I_RELOADFILE|源代码管理系统实际上在情况下修改磁盘上的文件提取历史记录 （例如，通过获取它的旧版本），因此 IDE 应重新加载此文件。|  
|SCC_E_FILENOTCONTROLLED|文件不是在源代码管理下。|  
|SCC_E_OPNOTSUPPORTED|源代码管理系统不支持此操作。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_PROJNOTOPEN|项目是尚未打开。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。 无法获取文件历史记录。|  
  
## <a name="remarks"></a>备注  
 源代码管理插件可以显示其自己的对话框来显示每个文件的历史记录使用`hWnd`父窗口。 或者，可选的文本输出回调函数提供给[SccOpenProject](../extensibility/sccopenproject-function.md)可以使用，如果支持它。  
  
 请注意，在某些情况下，此调用的执行期间发生更改可能要检查的文件。 例如， [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] history 命令使用户可以首先获取对旧版本的文件。 在这种情况下，源代码管理插件返回`SCC_I_RELOAD`来警告 IDE 需要对其进行重新加载该文件。  
  
> [!NOTE]
>  如果源代码管理插件不支持数组的文件的此函数，可以显示仅的第一个文件文件历史记录。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)