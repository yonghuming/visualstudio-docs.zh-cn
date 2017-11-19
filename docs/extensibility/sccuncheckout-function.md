---
title: "SccUncheckout 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUncheckout
helpviewer_keywords: SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e210f239c543da84a1e80833f03b684099155ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccuncheckout-function"></a>SccUncheckout 函数
此函数撤消一个以前的签出操作，从而将所选的文件或文件的内容还原到之前签出的状态。 签出以来对文件所做的所有更改都都将丢失。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
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
 [in]要撤消签出文件的完全限定的本地路径名称的数组。  
  
 fOptions  
 [in]（未使用） 的命令标志。  
  
 pvOptions  
 [in]源代码管理插件特定选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|撤消签出成功。|  
|SCC_E_FILENOTCONTROLLED|所选的文件不是源代码管理下。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。 撤消签出未成功。|  
|SCC_E_NOTCHECKEDOUT|用户没有签出该文件。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_PROJNOTOPEN|尚未从源代码管理打开项目。|  
|SCC_I_OPERATIONCANCELED|在完成之前已取消操作。|  
  
## <a name="remarks"></a>备注  
 在此操作，`SCC_STATUS_CHECKEDOUT`和`SCC_STATUS_MODIFIED`标志将同时清除在其上执行撤消签出文件。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)