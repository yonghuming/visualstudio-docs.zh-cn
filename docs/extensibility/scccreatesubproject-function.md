---
title: "SccCreateSubProject 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCreateSubProject
helpviewer_keywords: SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce9c4ec33a76afbba1b334fdc5bac5aee17e334
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject 函数
此函数创建具有给定名称指定现有父项目下的子项目`lpParentProjPath`自变量。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件的上下文指针。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpUser  
 [在中，out]（最多 SCC_USER_SIZE，包括 NULL 结束符) 用户名。  
  
 lpParentProjPath  
 [in]标识父项目 （最多 SCC_PRJPATH_SIZE，包括 NULL 终止符) 的路径的字符串。  
  
 lpSubProjName  
 [in]（最多 SCC_PRJPATH_SIZE，包括 NULL 结束符) 建议的子项目名称。  
  
 lpAuxProjPath  
 [在中，out]标识项目 （最多 SCC_PRJPATH_SIZE，包括 NULL 终止符) 的辅助字符串。  
  
 lpSubProjPath  
 [在中，out]标识 （最多 SCC_PRJPATH_SIZE，包括 NULL 结束符) 子项目的路径的输出字符串。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功创建子项目。|  
|SCC_E_INITIALIZEFAILED|无法初始化父项目。|  
|SCC_E_INVALIDUSER|用户不无法登录到源代码管理系统所造成。|  
|SCC_E_COULDNOTCREATEPROJECT|无法创建子项目。|  
|SCC_E_PROJSYNTAXERR|无效的项目语法。|  
|SCC_E_UNKNOWNPROJECT|父项目是未知的源代码管理插件。|  
|SCC_E_INVALIDFILEPATH|无效或不可用的文件路径。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_CONNECTIONFAILURE|没有源控件插件的连接问题。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 如果已存在同名子项目，该函数可以更改默认名称创建一个唯一的活动，例如通过添加"_\<编号 >"到它。 调用方必须准备好接受更改`lpUser`， `lpSubProjPath`，和`lpAuxProjPath`。 `lpSubProjPath`和`lpAuxProjPath`自变量然后用于调用[SccOpenProject](../extensibility/sccopenproject-function.md)。 不应由调用方返回后修改它们。 这些字符串提供一种方法的源代码管理插件来跟踪它需要与项目关联的信息。 调用方 IDE 将显示返回时，这两个参数，因为该插件可以使用可能不适合进行查看的格式化的字符串。 该函数返回的成功或失败的代码，并且如果成功，填充变量`lpSubProjPath`替换为新项目的完整项目路径。  
  
 此函数是类似于[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，只不过它会以无提示方式创建一个项目，而不是提示用户选择一个。 当`SccCreateSubProject`调用函数时，`lpParentProjName`和`lpAuxProjPath`将不能为空，并且将对应于有效的项目。 这些字符串通常接收由从上次调用 IDE`SccGetProjPath`函数或[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)。  
  
 `lpUser`自变量是用户名称。 IDE 将传入以前已收到来自同一用户名称`SccGetProjPath`，和源代码管理插件应使用的默认名称。 如果用户已有的打开连接使用插件，然后插件应尝试消除任何提示，若要确保函数以无提示方式处理。 但是，如果登录失败，该插件应提示用户登录名并在它接收的有效登录，通过名称重新`lpUser`。 因为插件可能会更改此字符串，IDE 将始终分配的缓冲区大小 （SCC_USER_LEN + 1 或 SCC_USER_SIZE，其中包括 null 终止符的占用空间）。 如果更改了字符串，新的字符串必须是有效的登录名 （至少为有效旧的字符串形式）。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 和 SccGetParentProjectPath 的技术说明  
 将解决方案和项目添加到源代码管理，简化了在 Visual Studio 中尽量减少的系统会提示用户在源代码管理系统中选择位置的次数。 如果源代码管理插件支持这两个新的功能，这些更改激活由 Visual Studio`SccCreateSubProject`和`SccGetParentProjectPath`。 但是，可以使用以下注册表项以禁用这些更改并还原到以前的 Visual Studio (源控件插件 API 版本 1.1) 行为：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword: 00000001  
  
 如果此注册表项不存在，或设置为 00000000 时表示，尝试使用新的功能，Visual Studio`SccCreateSubProject`和`SccGetParentProjectPath`。  
  
 如果注册表项设置为 dword: 00000001，Visual Studio 不会尝试使用这些新的功能，和之前版本的 Visual Studio 中一样，将添加到源代码管理的操作正常工作。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)