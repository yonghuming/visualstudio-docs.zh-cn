---
title: "SccCreateSubProject 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCreateSubProject"
helpviewer_keywords: 
  - "SccCreateSubProject 函数"
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# SccCreateSubProject 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数创建具有给定名称在指定的现有父项目下的子项目 `lpParentProjPath` 参数。  
  
## 语法  
  
```cpp#  
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
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文指针。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpUser  
 \[in、 out\]\(最多 SCC\_USER\_SIZE，包括 NULL 结束符\) 用户名。  
  
 lpParentProjPath  
 \[\] in标识父项目 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 结束符\) 的路径的字符串。  
  
 lpSubProjName  
 \[\] in建议的子项目名称 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 结束符\)。  
  
 lpAuxProjPath  
 \[in、 out\]标识 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 结束符\) 项目的辅助字符串。  
  
 lpSubProjPath  
 \[in、 out\]输出用于标识子项目 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 结束符\) 的路径字符串。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|已成功创建子项目。|  
|SCC\_E\_INITIALIZEFAILED|无法初始化父项目。|  
|SCC\_E\_INVALIDUSER|用户不可以登录到源代码管理系统。|  
|SCC\_E\_COULDNOTCREATEPROJECT|无法创建子项目。|  
|SCC\_E\_PROJSYNTAXERR|无效的项目的语法。|  
|SCC\_E\_UNKNOWNPROJECT|父项目是未知的源代码管理插件。|  
|SCC\_E\_INVALIDFILEPATH|无效或不可用的文件路径。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_CONNECTIONFAILURE|没有源控制插件的连接问题。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|非特定故障。|  
  
## 备注  
 如果已存在同名的子项目，该函数可以更改默认名称，以创建一个唯一的活动，例如通过添加"\_ \< 编号 \>"。 调用方必须准备好接受对更改 `lpUser`, ，`lpSubProjPath`, ，和 `lpAuxProjPath`。`lpSubProjPath` 和`lpAuxProjPath` 然后对的调用中使用参数 [SccOpenProject](../extensibility/sccopenproject-function.md)。 它们不应由调用方返回时修改。 这些字符串提供一种方法的源代码管理插件来跟踪它需要与项目关联的信息。 调用方 IDE 不会显示返回时，这两个参数，因为该插件可以使用可能不适合进行查看的格式化的字符串。 该函数将返回成功或失败的代码，并且如果成功，填充该变量 `lpSubProjPath` 替换为新项目的完整项目路径。  
  
 此函数是类似于 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ，只不过它以静默方式创建一个项目，而不是提示用户选择其中一个。 当 `SccCreateSubProject` 调用函数时， `lpParentProjName` 和 `lpAuxProjPath` 不能为空，并将对应于有效的项目。 这些字符串通常收到的以前调用从 ide `SccGetProjPath` 函数或 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)。  
  
 `lpUser` 参数是用户名称。 IDE 将相同的用户名称，它必须从以前接收传入 `SccGetProjPath`, ，和源代码管理插件应该使用的名称作为默认值。 如果用户已打开的连接使用该插件，然后该插件应尝试清除任何提示，以确保函数以静默方式工作。 但是，如果登录失败，该插件应提示用户的登录名中，并在收到有效登录名，传递回名称时 `lpUser`。 因为该插件可能会更改此字符串，IDE 会始终分配的缓冲区大小 \(SCC\_USER\_LEN \+ 1 或 SCC\_USER\_SIZE，包括 null 终止符的空间\)。 如果此字符串已更改，新的字符串必须是有效的登录名 \(至少一样有效旧的字符串\)。  
  
## 适用于 SccCreateSubProject 和 SccGetParentProjectPath 技术说明  
 将解决方案和项目添加到源代码管理进行了简化在 Visual Studio 中尽量减少的系统会提示用户选择在源代码管理系统中的位置的次数。 如果源代码管理插件支持这两个新的功能，这些更改由 Visual Studio 激活 `SccCreateSubProject` 和 `SccGetParentProjectPath`。 但是，可以使用以下注册表项来禁用这些更改并还原到以前的 Visual Studio \(源控制插件 API 版本 1.1\) 行为:  
  
 \[\] HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl"DoNotCreateSolutionRootFolderInSourceControl"\= dword: 00000001  
  
 如果此注册表项不存在，或设为 00000000 时表示，尝试使用新的功能，Visual Studio `SccCreateSubProject` 和 `SccGetParentProjectPath`。  
  
 如果注册表项设置为 dword: 00000001，Visual Studio 不会尝试使用这些新函数，并操作添加到源代码管理的工作方式与在先前版本的 Visual Studio。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)