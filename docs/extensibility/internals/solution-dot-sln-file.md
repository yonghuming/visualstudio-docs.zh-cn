---
title: "解决方案 (。Sln) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 13
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d9b2d052f86cf76dcd9e2f97f2ee03eaf07dcf5b
ms.lasthandoff: 02/22/2017

---
# <a name="solution-sln-file"></a>解决方案 (。Sln) 文件
一种解决方案是用于组织项目在 Visual Studio 中的结构。 该解决方案维护基于文本的 (共享） 的.sln 和.suo （二进制、 特定于用户的解决方案选项） 文件中的项目的状态信息。 .Suo 文件的详细信息，请参阅[解决方案用户选项 (。Suo) 文件](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
 如果由于被引用中的.sln 文件中加载你的 VSPackage，环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>来读取中的.sln 文件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>  
  
 .Sln 文件包含在环境来查找和加载持久化的数据和它所引用的 Vspackage 项目的名称 / 值参数中使用的基于文本的信息。 当用户打开一个解决方案时，该环境进行循环`preSolution`， `Project`，和`postSolution`项目解决方案中的.sln 文件加载的解决方案中的信息和持久化的任何信息附加到该解决方案。  
  
 每个项目文件包含由环境来填充该项目的项的层次结构中读取的其他信息。 由项目; 控制层次结构数据持久性尽管数据是不通常存储在.sln 文件中，您可以故意项目信息写入.sln 文件如果您选择这样做。 与持久性相关的详细信息，请参阅[项目持久性](../../extensibility/internals/project-persistence.md)和[打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="solution-file-contents"></a>解决方案文件的内容  
 下面的代码中所示的.sln 文件几个部分组成。  
  
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
  
 若要加载一个解决方案，该环境，请执行以下一系列的任务。  
  
1.  环境读取.sln 文件的 Global 部分并处理标记的所有部分`preSolution`。 在这种情况下，还有一个此类语句︰  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     当该环境中读取`GlobalSection('name')`标记，它将名称映射到使用注册表 VSPackage。 注册表中应存在的键名 [HKLM\\<Application id="" registry=""></Application>\>\SolutionPersistence\AggregateGUIDs]。 密钥的默认值为编写条目 VSPackage 的包 GUID (REG_SZ)。  
  
2.  环境加载 VSPackage 调用`QueryInterface`上为 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>接口并调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>以便 VSPackage 可以将数据存储部分中的数据的方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> 环境的每个都重复此过程`preSolution`部分。  
  
3.  该环境将遍历项目永久性块。 在这种情况下，没有一个项目。  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     此语句包含唯一的项目的 GUID 和项目类型 GUID。 环境使用此信息来查找属于该解决方案的项目文件和 VSPackage 所需的每个项目。 项目的 GUID 传递给<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>若要加载特定的 VSPackage 与项目相关，然后加载该项目是通过 VSPackage。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 在这种情况下，为此项目加载 VSPackage 采用 Visual Basic。  
  
     每个项目可以保留非唯一项目的实例 ID，以便可以根据需要由解决方案中的其他项目进行访问。 理想情况下，如果源代码管理下的解决方案和项目，项目的路径应相对于解决方案的路径。 当第一次加载解决方案时，项目文件不能为用户的计算机上。 通过使在相对于解决方案文件服务器上存储的项目文件，是要找出并复制到用户的计算机上的项目文件的相对简单。 然后，再将复制，并将加载所需的项目文件的其余部分。  
  
4.  根据在项目部分中的.sln 文件中包含的信息，该环境将加载每个项目文件。 项目本身负责，然后填充项目层次结构，并加载任何嵌套的项目。  
  
5.  .Sln 文件的所有部分进行都处理后，该解决方案将显示在解决方案资源管理器，并可供用户修改。  
  
 如果实现一个项目在解决方案中任何 VSPackage 无法加载，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>调用方法和解决方案中的每个其他项目被授权者提供机会忽略可能会在加载期间所做的更改。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> 如果出现分析错误，尽可能多的信息将保留的解决方案文件，并且环境显示一个对话框，警告用户该解决方案已损坏。  
  
 当保存的解决方案或将其关闭，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>方法调用该方法并传递给层次结构，以查看是否到需要输入到.sln 文件中的解决方案进行更改。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Null 值，在传递给`QuerySaveSolutionProps`中<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>，该值指示解决方案保留信息。</xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> 如果值不为 null，保持的信息是针对某个特定项目，将指针与通过确定<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
 如果没有要保存信息<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>接口调用的指针使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>方法然后由要检索从名称-值对的环境`IPropertyBag`接口，并将信息写入.sln 文件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>  
  
 `SaveSolutionProps`和`WriteSolutionProps`对象调用该环境以检索用于从保存的信息以递归方式`IPropertyBag`接口之前的所有更改都已都输入到.sln 文件。 这种方式，可以确保这些信息将被保留的解决方案和可用的下一次，打开解决方案。  
  
 每个加载的 VSPackage 枚举以查看如果有任何内容将保存到.sln 文件。 它是仅在注册表项将会询问的加载时间。 环境知道有关所有已加载的包，因为它们是在保存解决方案时在内存中。  
  
 只有.sln 文件包含中的条目`preSolution`和`postSolution`部分。 没有类似的节中有.suo 文件由于解决方案需要此信息才能正确加载。 .Suo 文件包含特定于用户的选项，如不应共享或放置在源代码管理下的私人的便笺。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [解决方案用户选项 (。Suo) 文件](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [解决方案](../../extensibility/internals/solutions.md)
