---
title: "SccCheckin 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b082ca831c17dcab3fbc95f8dd547da23a1f8982
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="scccheckin-function"></a>SccCheckin 函数
此函数签入到源代码管理系统，存储所做的更改和创建新版本的以前的签出文件。 使用计数和要签入的文件的名称的数组调用此函数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用插件 SCC，则 IDE 窗口的句柄。  
  
 nFiles  
 [in]选择要签入的文件的数量。  
  
 lpFileNames  
 [in]要签入的文件的完全限定的本地路径名称的数组。  
  
 lpComment  
 [in]要应用于每个签入所选文件的注释。 这是`NULL`如果源代码管理插件应提示输入注释。  
  
 fOptions  
 [in]命令标志，或者 0 或`SCC_KEEP_CHECKEDOUT`。  
  
 pvOptions  
 [in]SCC 插件特定的选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功签入的文件。|  
|SCC_E_FILENOTCONTROLLED|所选的文件不是源代码管理下。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。 未签入的文件。|  
|SCC_E_NOTCHECKEDOUT|用户不具有签出文件，因此无法将其签入。|  
|SCC_E_CHECKINCONFLICT|无法执行签入，因为：<br /><br /> 的另一个用户签入提前和`bAutoReconcile`是 false。<br /><br /> - 或 -<br /><br /> 的 （例如，当文件是二进制文件），不能完成自动合并。|  
|SCC_E_VERIFYMERGE|文件已自动合并，但具有尚未签入挂起的用户验证。|  
|SCC_E_FIXMERGE|文件已自动合并，但不是检入由于必须手动解决合并冲突。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_I_OPERATIONCANCELED|在完成之前已取消操作。|  
|SCC_I_RELOADFILE|需要重新加载文件或项目。|  
|SCC_E_FILENOTEXIST|找不到本地文件。|  
  
## <a name="remarks"></a>备注  
 注释适用于要签入的所有文件。 该注释参数可以是`null`源代码管理插件可以在这种情况下提示用户输入每个文件的注释字符串的字符串。  
  
 `fOptions`参数可以为其赋值的`SCC_KEEP_CHECKEDOUT`标志，用于指示要检查文件，并再次将它签出的用户的意图。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)
