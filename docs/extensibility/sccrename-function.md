---
title: "SccRename 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRename
helpviewer_keywords: SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2936c2ea4425ad6eaccc2d23853f4174e1c9c2a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccrename-function"></a>SccRename 函数
此函数中的源控制系统重命名文件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpFileName  
 [in]重命名文件的完全限定的文件名。  
  
 lpNewName  
 [in]完全限定的新名称。 如果不同的目录路径，然后该文件已移动从一个子目录到另一个。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功完成重命名操作。|  
|SCC_E_PROJNOTOPEN|项目不是受源代码管理打开的。|  
|SCC_E_FILENOTCONTROLLED|文件不是在源代码管理下。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。|  
|SCC_E_NOTAUTHORIZED|用户无权完成此操作。|  
|SCC_E_COULDNOTCREATEPROJECT|重命名过程的一部分，无法创建项目。|  
|SCC_E_OPNOTPERFORMED|未执行操作。|  
|SCC_E_NONSPECIFICERROR|未指定或常规时出错。|  
  
## <a name="remarks"></a>备注  
 此函数可用于重命名文件或它从一个位置移动到另一个的源控制系统中。 源代码管理插件不应尝试访问磁盘上的文件。 它是 IDE 的责任，若要重命名本地文件。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)