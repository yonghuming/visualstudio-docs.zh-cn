---
title: "为解决方案创建的父容器文件夹 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "创建父容器的解决方案"
  - "源代码管理插件，创建父容器"
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 为解决方案创建的父容器文件夹
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在源代码管理插件 API 1.2 版中，用户可以为解决方案中的所有 Web 项目指定单个根源代码管理目标。  此单个根调用 super 统一的根 \(SUR\)。  
  
 在源代码管理插件 API 1.1 版，因此，如果用户添加了一个 multiproject 解决方案添加到源代码管理，提示用户为每个 Web 项目指定一个源代码管理目标。  
  
## 新功能标志  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## 新增功能  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 ，当将解决方案添加到源代码管理时， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 几乎总是创建一个 SUR 文件夹。  具体而言，它因此在以下情况下:  
  
-   该项是文件共享 Web 项目。  
  
-   具有项目和解决方案文件的驱动器上。  
  
-   具有项目和解决方案文件的不同共享。  
  
-   项目分别添加了 \(在源代码管理解决方案\)。  
  
 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 建议不带扩展名，名称 SUR 文件夹与解决方案的名称。  下表总结了两个版本的行为。  
  
|功能|tSource 管理插件 API 1.1 版|源代码管理插件 API 1.2 版|  
|--------|----------------------------|-----------------------|  
|将解决方案添加到 SCC|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccOpenProject\(\)|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccOpenProject\(\)|  
|将项添加到源代码管理解决方案|SccGetProjPath\(\)<br /><br /> OpenProject\(\)|SccGetParentProjectPath\(\)<br /><br /> SccOpenProject\(\) **Note:**  Visual Studio 假定，解决方案是 SUR 的直接子级。|  
  
## 示例  
 下表列出了两个示例。  在这两种情况下，提示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 用户输入解决方案的目标位置在源代码管理下，直到*user\_choice* 指定为目标。当 user\_choice 指定时，解决方案和两个项目都会添加，而不会提示源代码管理目标的用户。  
  
|解决方案包含|磁盘位置|数据库默认结构|  
|------------|----------|-------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C: \\Solutions \\ sln1<br /><br /> C: \\Inetpub\\wwwroot\\Web 1<br /><br /> \\ \\ server \\ wwwroot$ \\ web2|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/C\/Web1<br /><br /> $*user\_choice*\/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C: \\Solutions \\ sln1<br /><br /> D: \\Inetpub\\wwwroot\\Web 1<br /><br /> C: \\solutions\\sln1\\Win 1|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/D\/web1<br /><br /> $*user\_choice*\/sln1\/win1|  
  
 SUR 文件夹和子文件夹中创建无论操作是否已取消或失败由于错误。  它们在撤消或错误状态不会自动移除。  
  
 ，如果源代码管理插件未返回 `SCC_CAP_CREATESUBPROJECT` 和 `SCC_CAP_GETPARENTPROJECT` 功能标志，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 默认为 1.1 版行为。  此外， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的用户可以选择还原到 1.1 版行为通过设置以下键的值到大小: 00000001:  
  
 \[HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl " \=dword: 00000001  
  
## 请参阅  
 [什么是源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)