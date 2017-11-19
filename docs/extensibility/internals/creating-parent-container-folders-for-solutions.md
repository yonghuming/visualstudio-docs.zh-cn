---
title: "为解决方案创建父容器文件夹 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ea901fe4e380fd867db1c63e44bc1cb6e144feb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-parent-container-folders-for-solutions"></a>为解决方案创建父容器文件夹
在源控件插件 API 版本 1.2，用户可以指定单个根源控件目标的解决方案中的所有 Web 项目。 此单个根称为超级统一根 (SUR)。  
  
 在源控件插件 API 版本 1.1，如果该用户添加到源代码管理的多项目解决方案已提示用户指定为每个 Web 项目的一个源控件目标。  
  
## <a name="new-capability-flags"></a>新功能标志  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>新的函数  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]时将解决方案添加到源代码管理后，IDE 将几乎始终创建 SUR 文件夹。 具体而言，它会在以下情况：  
  
-   项目是 Web 项目的文件共享。  
  
-   有不同的驱动器，项目和解决方案文件。  
  
-   没有不同共享项目和解决方案文件。  
  
-   将项目添加单独 （在受源代码管理解决方案中）。  
  
 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]建议 SUR 文件夹的名称为不带扩展名的解决方案名称相同。 下表总结了中的两个版本的行为。  
  
|功能|tSource 控件插件 API 版本 1.1|源代码管理插件的 API 版本 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|将解决方案添加到源代码管理|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|将项目添加到受源代码管理解决方案|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()**注意：** Visual Studio 假定的解决方案是 SUR.的直接子级|  
  
## <a name="examples"></a>示例  
 下表列出了两个示例。 在这两种情况下，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]都提示用户提供之前的源代码管理下的解决方案的目标位置*user_choice*指定为目标。当指定 user_choice 时，而不提示用户输入源控件目标添加解决方案和两个项目。  
  
|解决方案包含|有关磁盘位置|数据库默认结构|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 无论该操作已取消还是因出错而失败情况下，会创建 SUR 文件夹和子文件夹。 它们不会自动删除在取消或错误条件。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如果源代码管理插件不返回默认为版本 1.1 行为`SCC_CAP_CREATESUBPROJECT`和`SCC_CAP_GETPARENTPROJECT`功能标志。 此外，用户的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以选择通过将以下项的值设置为 dword: 00000001 恢复到版本 1.1 行为：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword: 00000001  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)