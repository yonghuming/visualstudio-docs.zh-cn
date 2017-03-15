---
title: "使用依赖项关系图验证代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 82
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: 831452f0c06a42550f64c84e88395ca7a1d3c85e
ms.openlocfilehash: 0c4368d0f88f6f5c508b9945abd89c5e94a53d8a
ms.lasthandoff: 02/22/2017

---
# <a name="validate-code-with-dependency-diagrams"></a>使用依赖项关系图验证代码

**最新新闻**︰ 请参阅[这篇博客文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/)。

[视频︰ 验证实时您体系结构的依赖关系](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

## <a name="why-use-dependency-diagrams"></a>为什么使用依赖项关系图？

若要确保代码不与其设计冲突，请验证您的代码与 Visual Studio 中的依赖项关系图。 这可帮助你：  
  
-   依赖项关系图上查找在代码中的依赖关系和依赖项之间的冲突。  
  
-   查找建议的更改可能会影响的依赖项。  
  
     例如，您可以编辑依赖项关系图来显示潜在的体系结构更改，然后验证代码，以查看受影响的依赖项。  
  
-   将代码重构或迁移到其他设计。  
  
     查找在将代码移动到其他体系结构时需要工作的代码或依赖项。  
  
 **要求**  
  
-   Visual Studio  
  
-   Team Foundation Build 服务器上的 Visual Studio，用于使用 Team Foundation Build 自动验证代码  
  
-   一个具有建模项目和依赖项关系图的解决方案。 此依赖项关系图必须链接到你想要验证的 Visual C#.NET 或 Visual Basic.NET 项目中的项。 请参阅[从您的代码创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)。  
  
 若要查看哪些版本的 Visual Studio 支持此功能，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 你可以验证代码手动从 Visual Studio 中打开的依赖项关系图或从命令提示符。 你还可以在运行本地生成或 Team Foundation Build 时自动验证代码。 请参阅[第 9 频道视频︰ 设计和验证体系结构使用依赖项关系图](http://go.microsoft.com/fwlink/?LinkID=252073)。  
  
> [!IMPORTANT]
>  如果想要使用 Team Foundation Build 运行层验证，则还必须在生成服务器上安装相同版本的 Visual Studio。  
  
-   [确定项是否支持验证](#SupportsValidation)  
  
-   [包括其他.NET 程序集和项目以进行验证](#IncludeReferences)  
  
-   [手动验证代码](#ValidateManually)  
  
-   [自动验证代码](#ValidateAuto)  
  
-   [层验证问题疑难解答](#TroubleshootingValidation)  
  
-   [了解和解决层验证错误](#UnderstandingValidationErrors)  

## <a name="live-dependency-validation"></a>实时的依赖项验证

在此版本的 Visual Studio 中，依赖项验证在实际时间，并且错误将立即显示在 Visual Studio 错误列表窗口。

* 对于 C# 和 Visual Basic.NET 支持实时验证。 

* 若要使用实时依赖项验证时，请启用完整的解决方案分析，请从金牌栏显示在错误列表打开选项设置。 
 - 如果您不感兴趣解决方案中的所有体系结构问题，您可以永久地消除此金色栏。
 - 如果未启用完整的解决方案分析，分析仅对正在编辑的文件中完成。<p /> 

* 在升级项目以启用实时验证，一个对话框将显示转换的进度。

* 更新以进行实时的依赖项验证项目，NuGet 包的版本升级为相同的所有项目，它正在使用的最高版本。 

* 添加新的依赖项验证项目触发器项目更新。 
  
##  <a name="a-namesupportsvalidationa-see-if-an-item-supports-validation"></a><a name="SupportsValidation"></a>确定项是否支持验证  
 你可以将层链接到网站、Office 文档、纯文本文件和项目中跨多个应用共享的文件，但验证过程不包含这些内容。 如果引用的项目或程序集链接到单独的层，而且这些层之间没有依赖关系出现，则将不会出现验证错误。 除非代码使用此类引用，否则这些引用不被视为依赖项。  
  
1.  在依赖项关系图中，选择一个或多个层，用鼠标右键单击您的选择，然后单击**查看链接**。  
  
2.  在**层资源管理器**，看看**支持验证**列。 如果该值为 false，则项不支持验证。  
  
##  <a name="a-nameincludereferencesa-include-other-net-assemblies-and-projects-for-validation"></a><a name="IncludeReferences"></a>包括其他.NET 程序集和项目以进行验证  
 当将项目拖到依赖项关系图中时，对相应的.NET 程序集或项目的引用将自动添加到**层引用**建模项目中的文件夹。 此文件夹包含对验证过程中分析的程序集和项目的引用。 不将它们手动拖到依赖项关系图的情况下，可以包括其他.NET 程序集和项目以进行验证。  
  
1.  在**解决方案资源管理器**，用鼠标右键单击建模项目或**层引用**文件夹，，然后单击**添加引用**。  
  
2.  在**添加引用**对话框中，选择所需的程序集或项目，，然后单击**确定**。  
  
##  <a name="a-namevalidatemanuallya-validate-code-manually"></a><a name="ValidateManually"></a>手动验证代码  
 如果您有一个链接到解决方案项的打开的依赖项关系图，您可以运行**验证**从关系图的快捷方式命令。 您可以使用命令提示符处运行**msbuild**命令**/p:ValidateArchitecture**自定义属性设置为**True**。 例如，在对代码进行更改时，请定期执行层验证以便能够提前捕获依赖项冲突。  
  
#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>若要从一个打开的依赖项关系图验证代码   
  
1.  右键单击关系图面，然后单击**验证体系结构**。  
  
    > [!NOTE]
    >  默认情况下，**生成操作**依赖项关系图 (.layerdiagram) 文件的属性设置为**验证**以便在验证过程中包括关系图。  
  
     **错误列表**窗口会报告出现的任何错误。 有关验证错误的详细信息，请参阅[了解和纠正层验证错误](#UnderstandingValidationErrors)。  
  
2.  若要查看每个错误的根源，请双击中的错误**错误列表**窗口。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可能会显示代码映射，而不是显示错误的根源。 该代码不依赖项关系图中，由指定的程序集具有依赖项或代码缺少依赖项关系图中由指定的依赖项时，将发生这种情况。 评审代码图或代码，以确定此依赖关系是否应该存在。 有关代码图的详细信息，请参阅[映射解决方案之间的依赖关系](../modeling/map-dependencies-across-your-solutions.md)。  
  
3.  若要管理错误，请参阅[管理验证错误](#ManageErrors)。  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>在命令提示符处验证代码  
  
1.  打开 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令提示。  
  
2.  选择以下选项之一：  
  
    -   若要对照解决方案中的特定建模项目验证代码，请使用下面的自定义属性运行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]。  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - 或 -  
  
         浏览到包含建模的文件夹的项目 (.modelproj) 文件和依赖项关系图，然后运行[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]使用下面的自定义属性︰  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   若要对照解决方案中的所有建模项目验证代码，请使用下面的自定义属性运行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]：  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - 或 -  
  
         浏览到解决方案文件夹，必须包含建模项目包含依赖项关系图，然后运行[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]使用下面的自定义属性︰  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     将列出发生的任何错误。 有关详细信息[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]，请参阅[MSBuild](../msbuild/msbuild1.md)和[MSBuild 任务](../msbuild/msbuild-task.md)。  
  
 有关验证错误的详细信息，请参阅[了解和纠正层验证错误](#UnderstandingValidationErrors)。  
  
###  <a name="a-namemanageerrorsa-manage-validation-errors"></a><a name="ManageErrors"></a>管理验证错误  
 在开发过程中，你可能需要在验证期间禁止显示报告的某些冲突。 例如，你可能希望禁止显示你已解决或与特定情形不相关的错误。 禁止显示错误时，最好在 [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] 中记录工作项。  
  
> [!WARNING]
>  必须已连接到 TFS 源代码管理 (SCC) 才可创建或链接到工作项。 如果尝试打开到其他 TFS SCC 的连接，则 Visual Studio 会自动关闭当前解决方案。 请先确保已连接到相应的 SCC，然后再尝试创建或链接到工作项。 在更高版本的 Visual Studio 中，如果未连接到 SCC，则菜单命令不可用。  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>为验证错误创建工作项  
  
-   在**错误列表**窗口中，右击错误，指向**创建工作项**，然后单击你想要创建的工作项的类型。  
  
 使用以下任务来管理中的验证错误**错误列表**窗口︰  
  
|**若要**|**请按照下列步骤**|  
|------------|----------------------------|  
|禁止在验证过程中显示选定的错误|右键单击一个或多个所选的错误，指向**管理验证错误**，然后单击**禁止显示错误**。<br /><br /> 禁止显示的错误在显示时均带有删除线格式。 在你下次运行验证时，这些错误将不会显示。<br /><br /> 禁止显示的错误中相应的依赖项关系图文件的.suppressions 文件进行跟踪。|  
|停止禁止显示选定的错误|右键单击所选的禁止显示的错误，指向**管理验证错误**，然后单击**停止禁止显示错误**。<br /><br /> 在你下次运行验证时，这些所选的禁止显示的错误将会显示。|  
|还原所有禁止显示的错误中**错误列表**窗口|右键单击任意位置**错误列表**窗口中，依次指向**管理验证错误**，然后单击**显示所有禁止显示的错误**。|  
|隐藏所有禁止显示的错误从**错误列表**窗口|右键单击任意位置**错误列表**窗口中，依次指向**管理验证错误**，然后单击**隐藏所有禁止显示的错误**。|  
  
##  <a name="a-namevalidateautoa-validate-code-automatically"></a><a name="ValidateAuto"></a>自动验证代码  
 每次运行本地生成时，都可以执行层验证。 如果你的团队使用 Team Foundation Build，则可使用能够通过创建自定义 MSBuild 任务指定的封闭签入来执行层验证，并使用生成报告来收集验证错误。 若要创建封闭的签入生成，请参阅[使用封闭的签入生成过程以验证更改](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)。  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>在本地生成期间自动验证代码  
  
-   使用文本编辑器打开建模项目 (.modelproj) 文件，然后包括以下属性：  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- 或 -  
  
1.  在**解决方案资源管理器**，右键单击包含依赖项关系图或关系图，该建模项目，然后单击**属性**。  
  
2.  在**属性**窗口中，将建模项目**验证体系结构**属性设置为**True**。  
  
     这将在验证过程中包括建模项目。  
  
3.  在**解决方案资源管理器**，单击你想要用于验证的依赖项关系图 (.layerdiagram) 文件。  
  
4.  在**属性**窗口中，请确保关系图的**生成操作**属性设置为**验证**。  
  
     这包括在验证过程的依赖项关系图。  
  
 若要管理错误列表窗口中的错误，请参阅[管理验证错误](#ManageErrors)。  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>在 Team Foundation Build 期间自动验证代码  
  
1.  在**团队资源管理器**，双击生成定义，然后单击**过程**。  
  
2.  在下**生成过程参数**，展开**编译**，并键入以下内容中的**MSBuild 参数**参数︰  
  
     `/p:ValidateArchitecture=true`  
  
 有关验证错误的详细信息，请参阅[了解和纠正层验证错误](#UnderstandingValidationErrors)。 有关 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 的详细信息，请参阅：  
  
-   [生成应用程序](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [为您的生成过程中使用默认模板](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [修改基于 UpgradeTemplate.xaml 旧生成](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [自定义生成过程模板](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [监视正在运行的生成的进度](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="a-nametroubleshootingvalidationa-troubleshoot-layer-validation-issues"></a><a name="TroubleshootingValidation"></a>层验证问题疑难解答  
 下表描述了层验证问题及其解决方法。 这些问题不同于代码与设计发生冲突而导致出现的错误。 有关这些错误的详细信息，请参阅[了解和纠正层验证错误](#UnderstandingValidationErrors)。  
  
|**问题**|**可能的原因**|**解决方法**|  
|---------------|------------------------|--------------------|  
|验证错误不按预期发生。|从解决方案资源管理器中的其他依赖项关系图复制，在同一建模项目中的依赖项关系图时，验证不起作用。 在这种方式中复制的依赖项关系图包含与原始的依赖项关系图相同的引用。|将新的依赖项关系图添加到建模项目。<br /><br /> 源依赖项关系图中的元素复制到新关系图中。|  
  
##  <a name="a-nameunderstandingvalidationerrorsa-understanding-and-resolving-layer-validation-errors"></a><a name="UnderstandingValidationErrors"></a>了解和解决层验证错误  
 验证依赖项关系图的代码，该代码与设计发生冲突时会发生验证错误。 例如，以下情况可能导致发生验证错误：  
  
-   将项目指派给了错误的层。 在这种情况下，请移动项目。  
  
-   项目（例如类）以与你的体系结构相冲突的方式使用了其他类。 在这种情况下，请重构代码以移除依赖关系。  
  
 若要解决这些错误，请更新代码，直至验证过程中不出现其他错误为止。 可以反复执行此任务。  
  
 以下各节描述这些错误中使用的语法，解释了这些错误的含义，并提供了纠正或管理这些错误的方法。  
  
|**语法**|**描述**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN*是依赖项关系图上与相关联的项目。<br /><br /> *ArtifactTypeN*是一种*ArtifactN*，如**类**或**方法**，例如︰<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*命名空间名称 n*|命名空间的名称。|  
|*层名称 n*|依赖项关系图上的名称。|  
|*DependencyType*|之间的依赖关系类型*Artifact1*和*Artifact2*。 例如， *Artifact1*具有**调用**交加*Artifact2*。|  
  
|**错误语法**|**错误说明**|  
|----------------------|---------------------------|  
|DV0001:**无效的依赖关系**|代码元素 （命名空间、 类型和成员） 映射到层引用映射到另一层的代码元素，但这些依赖项验证关系图包含此层中的各层之间并没有依赖项箭头时，将报告此问题。 这是一个依赖项约束冲突。|  
|DV1001:**无效的命名空间名称**|与层了"允许 Namespace 名称"属性不包含在其中定义该代码元素的命名空间关联的代码元素上报告此问题。 这是一个命名约束冲突。 请注意，"允许 Namespace 名称"的语法为要在哪个代码中与关联的元素的层的命名空间的分号分隔列表都允许进行定义。|  
|DV1002: **unreferenceable 命名空间上的依赖关系**|代码元素与层关联，并引用另一个图层的"Unreferenceable Namespace"属性中定义的命名空间中定义的代码元素上报告此问题。 这是一个命名约束冲突。 请注意，"Unreferenceable 命名空间"属性被定义为不应与此层相关联的代码元素中引用的命名空间的以分号分隔列表。|  
|DV1003:**不被允许的命名空间名称**|与"不允许使用 Namespace 名称"属性包含在其中定义该代码元素的命名空间的层关联的代码元素上报告此问题。 这是一个命名约束冲突。 请注意，"不允许命名空间名称"属性被定义为命名空间中的代码不应定义与此层相关联的元素的以分号分隔列表。|  
|DV3001:**缺少的环节**|层*LayerName*链接到*项目*找不到它。 是否缺少程序集引用?|*LayerName*链接到找不到的项目。 例如，由于建模项目缺少对包含某个类的程序集的引用，因此可能缺少指向该类的链接。|  
|DV9001:**体系结构分析找到出现内部错误**|结果可能不完整。 有关详细信息，请参阅详细的生成事件日志或输出窗口。|有关更多详细信息，请参阅生成事件日志或输出窗口。|  

 
## <a name="see-also"></a>另请参阅  
 [在开发过程中验证您的系统](../modeling/validate-your-system-during-development.md)   
 [视频︰ 验证实时您体系结构的依赖关系](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   

