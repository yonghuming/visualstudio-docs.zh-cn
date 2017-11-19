---
title: "SccDirDiff 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDirDiff
helpviewer_keywords: SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea335ef6bcb2a27b4312c613062be0d365711cbc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccdirdiff-function"></a>SccDirDiff 函数
此函数显示在客户端磁盘上的当前本地目录和在源代码管理下的相应项目之间的差异。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpDirName  
 [in]到要显示可见的差异的本地目录的完全限定的路径。  
  
 dwFlags  
 [in]命令标志 (请参阅备注部分)。  
  
 pvOptions  
 [in]源代码管理插件特定选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|磁盘上的目录是与源代码管理中的项目相同。|  
|SCC_I_FILESDIFFER|磁盘上的目录是不同的源代码管理中的项目。|  
|SCC_I_RELOADFILE|需要重新加载文件或项目。|  
|SCC_E_FILENOTCONTROLLED|目录不是源代码管理下。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特定的失败。|  
|SCC_E_FILENOTEXIST|找不到本地目录。|  
  
## <a name="remarks"></a>备注  
 使用此函数以指示源代码管理插件以向用户显示更改到指定的目录的列表。 该插件，则将自己的窗口，打开中的格式为其选择，以显示在磁盘上的用户的目录和版本控制下的相应项目之间的差异。  
  
 如果插件支持在所有的目录的比较，它必须按文件名称支持的目录的比较，即使不支持"快速差异"选项。  
  
|`dwFlags`|解释|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|（可能为快速比较或视觉对象使用） 的不区分大小写比较。|  
|SCC_DIFF_IGNORESPACE|将忽略空白 （可能为快速比较或视觉对象使用）。|  
|SCC_DIFF_QD_CONTENTS|如果受源代码管理插件，以无提示方式将目录中，逐字节进行比较。|  
|SCC_DIFF_QD_CHECKSUM|如果插件支持，以无提示方式比较校验和，通过目录，或者不受支持，如果回退到 SCC_DIFF_QD_CONTENTS。|  
|SCC_DIFF_QD_TIME|如果插件支持，以无提示方式比较其时间戳，通过目录或者，如果不支持，将回退 SCC_DIFF_QD_CHECKSUM 或 SCC_DIFF_QD_CONTENTS 上。|  
  
> [!NOTE]
>  此函数使用相同的命令标志作为[SccDiff](../extensibility/sccdiff-function.md)。 但是，源代码管理插件可以选择不支持目录的"快速差异"操作。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)