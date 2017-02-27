---
title: "SccGetParentProjectPath 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetParentProjectPath"
helpviewer_keywords: 
  - "SccGetParentProjectPath 函数"
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccGetParentProjectPath 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数可确定指定的项目的父项目路径。 当用户 Visual Studio 项目添加到源代码管理时，调用此函数。  
  
## 语法  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文指针。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpUser  
 \[in、 out\]\(最多 SCC\_USER\_SIZE，包括 NULL 结束符\) 的用户名。  
  
 lpProjPath  
 \[\] in标识 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 结束符\) 的项目路径的字符串。  
  
 lpAuxProjPath  
 \[in、 out\]标识 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 结束符\) 项目的辅助字符串。  
  
 lpParentProjPath  
 \[in、 out\]标识父项目路径 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 结束符\) 的输出字符串。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功获取父项目路径。|  
|SCC\_E\_INITIALIZEFAILED|无法初始化项目。|  
|SCC\_E\_INVALIDUSER|用户不可以登录到源代码管理插件。|  
|SCC\_E\_UNKNOWNPROJECT|项目是未知的源代码管理插件。|  
|SCC\_E\_INVALIDFILEPATH|无效或不可用的文件路径。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_PROJSYNTAXERR|无效的项目的语法。|  
|SCC\_E\_CONNECTIONFAILURE|存储连接问题。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|非特定故障。|  
  
## 备注  
 此函数将返回成功或失败的代码，并且如果成功，填充该变量 `lpParentProjPath` 替换为指定的项目的完整项目路径。  
  
 此函数返回的父项目路径的现有项目。 对于根项目中，函数将返回传入的项目路径 \(即，同一根项目路径\)。 请注意，项目路径仅对源代码管理插件有意义的字符串。  
  
 IDE 已准备好接受对更改 `lpUser` 和 `lpAuxProjPath` 以及参数。 IDE 将保留这些字符串并将它们传递给 [SccOpenProject](../extensibility/sccopenproject-function.md) 当用户打开此项目在将来。 这些字符串，因此，提供一种方法进行源代码管理插件，它需要与项目关联的跟踪信息。  
  
 此函数是类似于 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ，只不过它不会提示用户选择一个项目。 它也不只与一个现有项目创建一个新的项目，但有效。  
  
 当 `SccGetParentProjectPath` 调用时， `lpProjPath` 和 `lpAuxProjPath` 不能为空，并将对应于有效的项目。 这些字符串通常收到的以前调用从 ide `SccGetProjPath` 函数。  
  
 `lpUser` 参数是用户名称。 IDE 将相同的用户名称，它必须从以前接收传入 `SccGetProjPath` 函数，并且源代码管理插件应该使用的名称作为默认值。 如果用户已打开的连接使用该插件，然后该插件应尝试清除任何提示，以确保函数以静默方式工作。 但是，如果登录失败，该插件应提示用户的登录名中，并在收到有效登录名，传递回名称时 `lpUser`。 因为该插件可能会更改此字符串，IDE 会始终分配大小的缓冲区 \(`SCC_USER_LEN`\+ 1\)。 如果此字符串已更改，新的字符串必须是有效的登录名 \(至少一样有效旧的字符串\)。  
  
## 适用于 SccCreateSubProject 和 SccGetParentProjectPath 技术说明  
 将解决方案和项目添加到源代码管理进行了简化在 Visual Studio 中尽量减少的系统会提示用户选择在源代码管理系统中的位置的次数。 如果源代码管理插件支持这两个新的功能，这些更改由 Visual Studio 激活 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) 和 `SccGetParentProjectPath` 函数。 但是，可以使用以下注册表项来禁用这些更改并还原到以前的 Visual Studio \(源控制插件 API 版本 1.1\) 行为:  
  
 \[\] HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl"DoNotCreateSolutionRootFolderInSourceControl"\= dword: 00000001  
  
 如果此注册表项不存在，或设为 00000000 时表示，尝试使用新的功能，Visual Studio `SccCreateSubProject`和`SccGetParentProjectPath`。  
  
 如果注册表项设置为 dword: 00000001，Visual Studio 不会尝试使用这些新函数，并操作添加到源代码管理的工作方式与在先前版本的 Visual Studio。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)