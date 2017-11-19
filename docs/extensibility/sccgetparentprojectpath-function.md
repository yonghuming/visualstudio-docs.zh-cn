---
title: "SccGetParentProjectPath 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetParentProjectPath
helpviewer_keywords: SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 47cf6ee34738e8830705c0bed30891223efcd103
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath 函数
此函数可确定指定的项目的父项目路径。 用户将 Visual Studio 项目添加到源代码管理时，调用此函数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件的上下文指针。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpUser  
 [在中，out]（最多 SCC_USER_SIZE，包括 NULL 终止符) 的用户名。  
  
 lpProjPath  
 [in]标识 （最多 SCC_PRJPATH_SIZE，包括 NULL 终止符) 的项目路径的字符串。  
  
 lpAuxProjPath  
 [在中，out]标识项目 （最多 SCC_PRJPATH_SIZE，包括 NULL 终止符) 的辅助字符串。  
  
 lpParentProjPath  
 [在中，out]标识 （最多 SCC_PRJPATH_SIZE，包括 NULL 终止符) 的父项目路径的输出字符串。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功获得父项目路径。|  
|SCC_E_INITIALIZEFAILED|无法初始化项目。|  
|SCC_E_INVALIDUSER|用户无法记录到源代码管理插件。|  
|SCC_E_UNKNOWNPROJECT|项目是未知的源代码管理插件。|  
|SCC_E_INVALIDFILEPATH|无效或不可用的文件路径。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_PROJSYNTAXERR|无效的项目语法。|  
|SCC_E_CONNECTIONFAILURE|存储连接问题。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 此函数返回的成功或失败的代码，并且如果成功，填充变量`lpParentProjPath`替换为指定的项目的完整项目路径。  
  
 此函数返回的父项目路径的现有项目。 对于根项目中，函数将返回中传递的项目路径 （即，同一根项目路径）。 请注意，项目路径仅对源代码管理插件有意义的字符串。  
  
 IDE 已准备好接受对更改`lpUser`和`lpAuxProjPath`以及参数。 IDE 将保留这些字符串并将它们传递给[SccOpenProject](../extensibility/sccopenproject-function.md)当用户打开此项目在将来。 这些字符串，因此，插件用来与项目关联的跟踪信息的源控件提供一种方法。  
  
 此函数是类似于[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，只不过它不会提示用户选择一个项目。 它也不只能与一个现有项目创建一个新的项目，但工作原理。  
  
 当`SccGetParentProjectPath`调用时，`lpProjPath`和`lpAuxProjPath`将不能为空，并且将对应于有效的项目。 这些字符串通常接收由从上次调用 IDE`SccGetProjPath`函数。  
  
 `lpUser`自变量是用户名称。 IDE 将传入以前已收到来自同一用户名称`SccGetProjPath`函数和源代码管理插件应默认情况下使用该名称。 如果用户已有的打开连接使用插件，然后插件应尝试消除任何提示，若要确保函数以无提示方式处理。 但是，如果登录失败，该插件应提示用户登录名并在它接收的有效登录，通过名称重新`lpUser`。 因为插件可能会更改此字符串，IDE 将始终分配缓冲区的大小 (`SCC_USER_LEN`+ 1)。 如果更改了字符串，新的字符串必须是有效的登录名 （至少为有效旧的字符串形式）。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 和 SccGetParentProjectPath 的技术说明  
 将解决方案和项目添加到源代码管理，简化了在 Visual Studio 中尽量减少的系统会提示用户在源代码管理系统中选择位置的次数。 如果源代码管理插件支持这两个新的功能，这些更改激活由 Visual Studio [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)和`SccGetParentProjectPath`函数。 但是，可以使用以下注册表项以禁用这些更改并还原到以前的 Visual Studio (源控件插件 API 版本 1.1) 行为：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword: 00000001  
  
 如果此注册表项不存在，或设置为 00000000 时表示，尝试使用新的功能，Visual Studio`SccCreateSubProject`和`SccGetParentProjectPath`。  
  
 如果注册表项设置为 dword: 00000001，Visual Studio 不会尝试使用这些新的功能，和之前版本的 Visual Studio 中一样，将添加到源代码管理的操作正常工作。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)