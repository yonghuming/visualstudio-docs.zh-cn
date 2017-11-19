---
title: "解决方案 (。Sln) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7be9b3bf7783980cfbbe1abfc44fe1748dd20a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="solution-sln-file"></a>解决方案 (。Sln) 文件
一种解决方案是用于组织 Visual Studio 中的项目的结构。 解决方案维护基于文本的 (共享） 的.sln 和.suo （二进制、 特定于用户的解决方案选项） 文件中的项目的状态信息。 .Suo 文件的详细信息，请参阅[解决方案用户选项 (。Suo) 文件](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
 如果你的 VSPackage 中加载结果中的.sln 文件正在引用，则环境将调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>读取中的.sln 文件。  
  
 .Sln 文件包含该环境使用来查找和加载持久化的数据和它所引用的 Vspackage 中的项目的名称-值参数的基于文本的信息。 当用户打开解决方案时，环境会循环访问`preSolution`， `Project`，和`postSolution`项目解决方案中的.sln 文件加载的解决方案中的信息和持久化的任何信息附加到解决方案。  
  
 每个项目的文件包含读取由环境来填充该项目的项的层次结构的其他信息。 由项目; 控制层次结构数据暂留尽管数据是不通常存储在.sln 文件中，你可以有意项目信息写入.sln 文件如果你选择这样做。 与永久性相关的详细信息，请参阅[项目持久性](../../extensibility/internals/project-persistence.md)和[打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="solution-file-contents"></a>解决方案文件内容  
 .Sln 文件包含多个部分组成，如下面的代码中所示。  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 若要加载的解决方案，该环境，请执行下面的任务序列。  
  
1.  环境读取.sln 文件的全局部分并处理所有标记的节`preSolution`。 在这种情况下，没有一个此类语句：  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     当环境读取`GlobalSection('name')`标记，它将名称映射到使用注册表 VSPackage。 下面的注册表中都应存在密钥名称 [HKLM\\< 应用程序 ID 注册表根目录\>\SolutionPersistence\AggregateGUIDs]。 密钥的默认值为编写条目的 VSPackage 的包 GUID (REG_SZ)。  
  
2.  环境加载 VSPackage，调用`QueryInterface`上有关 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>接口，并调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>使 VSPackage 可以将数据存储部分中的数据的方法。 环境为每个重复此过程`preSolution`部分。  
  
3.  环境循环访问项目永久性块。 在这种情况下，没有一个项目。  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     此语句包含 GUID 的唯一项目和项目类型 GUID。 环境使用此信息来查找的项目文件或文件属于该解决方案，并 VSPackage 的所需的每个项目。 GUID 传递给项目<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>若要加载特定的 VSPackage 相关的项目，然后加载该项目是由 VSPackage。 在这种情况下，为此项目加载 VSPackage 是 Visual Basic。  
  
     每个项目可以保留一个唯一项目的实例 ID，以便可以根据需要由其他解决方案中的项目进行访问。 理想情况下，如果解决方案和项目源代码管理下，项目的路径应为相对于解决方案的路径。 当首次加载解决方案时，项目文件无法在用户的计算机上。 通过使存储相对于解决方案文件服务器上的项目文件，它是相对简单要找出并复制到用户的计算机上的项目文件。 然后将复制，并且加载所需的项目文件的其余部分。  
  
4.  根据项目部分中的.sln 文件中包含的信息，环境将加载每个项目文件。 项目本身负责，然后填充项目层次结构，并加载任何嵌套的项目。  
  
5.  在处理.sln 文件的所有部分之后，该解决方案将显示在解决方案资源管理器，并可供用户修改。  
  
 如果任何 VSPackage 实现项目解决方案中无法加载，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>调用方法和解决方案中的其他每个项目有机会忽略可能在加载过程所做的更改。 如果出现分析错误，尽可能多的信息可能保留与解决方案文件并环境显示一个对话框，警告用户解决方案已损坏。  
  
 保存或关闭，解决方案时<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>调用方法并将其传递到层次结构，以查看是否到的解决方案中需要输入到.sln 文件进行了更改。 空值，在传递给`QuerySaveSolutionProps`中<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>，指示解决方案保留信息。 如果值不为 null，已保存的信息是针对某个特定项目，指向由确定<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>接口。  
  
 如果没有要保存信息<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>接口称为的指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>方法。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>方法然后调用由环境后，若要检索的名称-值对从`IPropertyBag`接口，并将信息写入.sln 文件。  
  
 `SaveSolutionProps`和`WriteSolutionProps`对象以递归方式调用由环境以检索用于保存从信息`IPropertyBag`接口之前的所有更改都已都输入到.sln 文件。 这种方式，可以确保将使用的解决方案和可用下次打开解决方案时保留的信息。  
  
 每个加载的 VSPackage 枚举以查看是否有任何内容将保存到.sln 文件。 它是仅在注册表项都查询的加载时间。 因为它们在内存中保存解决方案时，则环境知道有关的所有加载的包。  
  
 只有.sln 文件包含中的条目`preSolution`和`postSolution`部分。 没有类似部分.suo 文件中由于解决方案需要此信息来正确加载。 .Suo 文件包含特定于用户的选项，例如，不应共享或放置在源代码管理下的私人便笺。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [解决方案用户选项 (。Suo) 文件](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [解决方案](../../extensibility/internals/solutions.md)