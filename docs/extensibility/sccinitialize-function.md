---
title: "SccInitialize 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccInitialize
helpviewer_keywords: SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e688d30d2367236cfcf5b2d14b36eb602832fc0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccinitialize-function"></a>SccInitialize 函数
此函数初始化源代码管理插件，并提供功能和集成的开发环境 (IDE) 的限制。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppvContext`  
 [in]此处用于源代码管理插件可以放置指向其上下文结构的指针。  
  
 `hWnd`  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 `lpCallerName`  
 [in]调用插件的源控件的程序的名称。  
  
 `lpSccName`  
 [在中，out]源代码管理插件其中放入其自己的名称的缓冲区 (不能超过`SCC_NAME_LEN`)。  
  
 `lpSccCaps`  
 [out]返回的源控件即插即用接程序的功能标志。  
  
 `lpAuxPathLabel`  
 [在中，out]源代码管理插件其中将一个字符串，描述缓冲区`lpAuxProjPath`参数返回[SccOpenProject](../extensibility/sccopenproject-function.md)和[SccGetProjPath](../extensibility/sccgetprojpath-function.md) (不能超过`SCC_AUXLABEL_LEN`)。  
  
 `pnCheckoutCommentLen`  
 [out]返回签出注释的最大允许长度。  
  
 `pnCommentLen`  
 [out]返回其他注释的最大允许长度。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|源控件初始化成功。|  
|SCC_E_INITIALIZEFAILED|无法初始化系统。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行指定的操作。|  
|SCC_E_NONSPECFICERROR|非特定故障;未初始化源代码管理系统。|  
  
## <a name="remarks"></a>备注  
 它首次加载源代码管理插件时，IDE 将调用此函数。 它使 IDE 将某些信息，如调用方名称、 到该插件。 IDE 还会让某些信息如注释和即插即用接程序的功能的最大允许长度。  
  
 `ppvContext`指向`NULL`指针。 源代码管理插件可以分配为自己使用的结构并将存储到中该结构的指针`ppvContext`。 IDE 将此将指针传递给每个其他 VSSCI API 函数时，允许插件而无需进行全局存储中具有可用的上下文信息和支持的插件的多个实例。 此结构应释放时[SccUninitialize](../extensibility/sccuninitialize-function.md)调用。  
  
 `lpCallerName`和`lpSccName`参数启用 IDE 和源代码管理插件交换名称。 这些名称只可用于区分多个实例，或它们可能会实际出现在菜单或对话框。  
  
 `lpAuxPathLabel`参数是为一个注释用于标识辅助项目路径，存储在解决方案文件并到源代码管理插件对的调用中传递一个字符串[SccOpenProject](../extensibility/sccopenproject-function.md)。 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]使用字符串"SourceSafe 项目:";其他源控件插件应避免使用此特定的字符串。  
  
 `lpSccCaps`参数给出源代码管理插件一个位置来存储 bitflags，该值指示即插即用接程序的功能。 (有关功能 bitflags 的完整列表，请参阅[功能标志](../extensibility/capability-flags.md))。 例如，如果将结果写入到一个调用方提供的回调函数，该插件会设置功能的插件计划位 SCC_CAP_TEXTOUT。 这将指示 IDE 以为版本控制结果创建窗口。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [功能标志](../extensibility/capability-flags.md)