---
title: "SccAdd 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAdd
helpviewer_keywords: SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8cd55986d7f4597030830906485ba1d7c1b3389
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccadd-function"></a>SccAdd 函数
此函数将新文件添加到源代码管理系统。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 nFiles  
 [in]选择要添加到当前项目的中指定的文件数`lpFileNames`数组。  
  
 lpFileNames  
 [in]要添加的文件的完全限定本地名称的数组。  
  
 lpComment  
 [in]要应用于正在添加的文件的所有注释。  
  
 pfOptions  
 [in]命令标志，在每个文件基础上提供的数组。  
  
 pvOptions  
 [in]源代码管理插件特定选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|添加操作已成功。|  
|SCC_E_FILEALREADYEXISTS|所选的文件已位于源代码管理下。|  
|SCC_E_TYPENOTSUPPORTED|（例如，二进制） 文件的类型不受源代码管理系统。|  
|SCC_E_OPNOTSUPPORTED|源代码管理系统不支持此操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_NONSPECIFICERROR|非特定故障;添加不执行。|  
|SCC_I_OPERATIONCANCELED|在完成之前已取消操作。|  
|SCC_I_RELOADFILE|需要重新加载文件或项目。|  
|SCC_E_FILENOTEXIST|找不到本地文件。|  
  
## <a name="remarks"></a>备注  
 常规`fOptions`此处替换为数组、 `pfOptions`，具有一个`LONG`选项每个文件规范。 这是因为文件类型可能会有所不同多个文件。  
  
> [!NOTE]
>  无效同时指定`SCC_FILETYPE_TEXT`和`SCC_FILETYPE_BINARY`是未指定有效的同一文件中，但它的选项。 设置都不等同于设置`SCC_FILETYPE_AUTO`，在这种情况下，源代码管理插件自动检测的文件类型。  
  
 下面是在中使用的标志的列表`pfOptions`数组：  
  
|选项|值|含义|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|源代码管理插件应该会检测到的文件类型。|  
|SCC_FILETYPE_TEXT|0x01|指示一个 ASCII 文本文件。|  
|SCC_FILETYPE_BINARY|0x02|指示文件类型而非 ASCII 文本。|  
|SCC_ADD_STORELATEST|0x04，则|存储仅该文件，没有的增量可以保持的最新副本。|  
|SCC_FILETYPE_TEXT_ANSI|0x08|将该文件视为 ANSI 文本。|  
|SCC_FILETYPE_UTF8|0x10|将文件视作 UTF8 格式中的 Unicode 文本。|  
|SCC_FILETYPE_UTF16LE|0x20|将文件视作中 UTF16 Unicode 文本稍有 Endian 格式。|  
|SCC_FILETYPE_UTF16BE|0x40|将文件另存为中 UTF16 Big Endian Unicode 文本格式。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)