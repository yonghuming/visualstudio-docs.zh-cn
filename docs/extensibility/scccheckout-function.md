---
title: "SccCheckout 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCheckout
helpviewer_keywords: SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de22bd4722df1cd78472fd9e180fdb8132401828
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="scccheckout-function"></a>SccCheckout 函数
给定的完全限定的文件名的列表，此函数将它们签出到本地驱动器。 注释适用于被签出的所有文件。该注释参数可以是`null`字符串。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 nFiles  
 [in]选择要签出的文件的数量。  
  
 lpFileNames  
 [in]要签出的文件的完全限定的本地路径名称的数组。  
  
 lpComment  
 [in]要应用于每个被签出所选文件的注释。  
  
 fOptions  
 [in]命令标志 (请参阅[Bitflags 使用特定命令](../extensibility/bitflags-used-by-specific-commands.md))。  
  
 pvOptions  
 [in]源代码管理插件特定选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功签出。|  
|SCC_E_FILENOTCONTROLLED|所选的文件不是源代码管理下。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。 未签出文件。|  
|SCC_E_ALREADYCHECKEDOUT|用户已签出该文件。|  
|SCC_E_FILEISLOCKED|文件被锁定，禁止新版本的创建。|  
|SCC_E_FILEOUTEXCLUSIVE|另一个用户完成对此文件的独占方式签出。|  
|SCC_I_OPERATIONCANCELED|在完成之前已取消操作。|  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令使用的位标志](../extensibility/bitflags-used-by-specific-commands.md)