---
title: "如何： 使用 Visual Studio 扩展基于规则的 UI 上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
ms.openlocfilehash: d1307f63464b0e652a97e9b06314b08112d8b097
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>如何： 使用 Visual Studio 扩展基于规则的 UI 上下文
Visual Studio 允许加载 Vspackage 时某些已知<xref:Microsoft.VisualStudio.Shell.UIContext>s 被激活。 但是，这些 UI 上下文不是精细粒度，离开无选择的扩展插件作者但选取可用的 UI 上下文的点之前，激活就确实需要小心 VSPackage 加载。 有关的已知 UI 上下文的列表，请参阅<xref:Microsoft.VisualStudio.Shell.KnownUIContexts>。  
  
 加载包可以对性能有影响，并且不是在需要更快地加载它们不是最佳做法。 Visual Studio 2015 引入了基于规则的 UI 上下文，一种机制，允许扩展作者定义的精确条件在其下激活 UI 上下文和关联的 Vspackage 加载的概念。  
  
## <a name="rule-based-ui-context"></a>基于规则的 UI 上下文  
 "规则"包含新的 UI 上下文 (GUID) 和引用一个或多个"条款"的布尔表达式结合逻辑"和"，"，"not"操作。 在运行时的"条款"动态评估和表达式会重新评估，每当任何其条款更改。 表达式的计算结果为 true，将激活关联的 UI 上下文。 否则，为取消激活 UI 上下文。  
  
 各种不同的方式，可以使用基于规则的 UI 上下文：  
  
1.  指定对命令和工具窗口的可见性约束。 您可以隐藏命令/工具窗口，直到满足 UI 上下文规则。  
  
2.  为自动加载约束： 自动负载包仅当满足规则  
  
3.  延迟的任务： 延迟加载之前指定的间隔过后以及是否仍满足该规则。  
  
 可能通过任何 Visual Studio 扩展中使用的机制。  
  
## <a name="create-a-rule-based-ui-context"></a>创建基于规则的 UI 上下文  
 假设你具有调用 TestPackage，它提供一个菜单命令，这仅适用于具有".config"扩展名的文件扩展名。 在 VS2015 之前, 是加载 TestPackage 最佳选项时<xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A>UI 上下文已激活。 这是不高效，因为加载的解决方案甚至可能不包含.config 文件。 告诉我们，请参阅如何使用基于规则的 UI 上下文来激活 UI 上下文仅带.config 扩展名的文件选择时，，和加载 TestPackage 激活该 UI 上下文时。  
  
1.  定义新的 UIContext GUID 并将添加到 VSPackage 类<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>。  
  
     例如，假设新 UIContext"UIContextGuid"是要添加。 创建的 GUID (你可以通过单击工具来创建 GUID-> 创建 guid) 是"8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"。 然后添加以下包类中：  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     对于属性，添加以下项: （这些属性的详细信息将后面介绍）  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     这些元数据定义新的 UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) 和引用单个字词，"DotConfig"的表达式。 "DotConfig"术语计算结果为 true，只要 active 层次结构中的当前选择已与正则表达式模式匹配的名称"\\.config$"（".config"结束）。 （默认） 值定义可用于调试的规则的可选名称。  
  
     属性的值将添加到 pkgdef 期间生成时间之后生成。  
  
2.  VSCT 文件中 TestPackage 的命令，将"DynamicVisibility"标志添加到适当的命令：  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  中的 VSCT 可见性部分中，将新 UIContext #1 中定义的 GUID 到适当的命令：  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  在符号部分中，添加 UIContext 的定义：  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     现在，仅在解决方案资源管理器中的选定的项是一个".config"文件，直到选中其中一个命令将不加载包时，*.config 文件的上下文菜单命令将可以看到。  
  
 接下来，让我们使用调试程序确认包加载仅当我们预期的那样。 若要调试 TestPackage:  
  
1.  中设置断点<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
2.  生成 TestPackage 并启动调试。  
  
3.  创建项目或打开一个。  
  
4.  选择任何文件扩展名不.config。应不会命中断点。  
  
5.  选择的 App.Config 文件。  
  
 TestPackage 加载并在断点处停止。  
  
## <a name="adding-more-rules-for-ui-context"></a>为 UI 上下文中添加更多的规则  
 由于 UI 上下文规则是布尔表达式，你可以为 UI 上下文添加更受限制的规则。 例如，在上面的 UI 上下文中，可以指定该规则仅在加载了项目的解决方案时适用。 在这种方式，命令不会显示是否你打开".config"文件作为独立文件，而不是项目的一部分。  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 现在该表达式引用这三个术语。 前两个术语，"SingleProject"和"MultipleProjects"，请参阅其他已知的 UI 上下文 （由其 Guid)。 第三个词，"DotConfig"是基于规则的 UI 上下文，此我们之前定义。  
  
## <a name="delayed-activation"></a>延迟的激活  
 规则可以具有的可选"延迟"。 以毫秒为单位指定延迟。 如果存在，延迟将导致该激活或停用的规则的 UI 上下文会延迟由该时间间隔。 如果规则更改回之前的延迟间隔，然后会执行任何操作。 此机制可以用于"错开"初始化步骤-尤其是一次性初始化而无需依赖于计时器或注册的空闲通知。  
  
 例如，你可以指定你测试的负载规则具有 100 毫秒延迟：  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>字词类型  
 下面是术语的支持各种类型:  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID 是指 UI 上下文。 只要 UI 上下文否则处于活动状态，false，则将为 true 术语。|  
|HierSingleSelectionName:\<模式 >|每当 active 层次结构中的所选内容的单个项并且所选的项的名称匹配给定由"模式"的.Net 正则表达式时，术语将为 true。|  
|UserSettingsStoreQuery:\<查询 >|"查询"到用户设置存储必须计算为非零值表示完整路径。 查询拆分为"集合"和"属性名称"，在最后一个斜杠。|  
|ConfigSettingsStoreQuery:\<查询 >|"查询"到配置设置存储区必须计算为非零值表示完整路径。 查询拆分为"集合"和"属性名称"，在最后一个斜杠。|  
|ActiveProjectFlavor:\<projectTypeGuid >|术语将为 true，只要风格当前选定的项目 （聚合） 并且具有与给定的项目类型 GUID 匹配风格。|  
|ActiveEditorContentType:\<contentType >|如果选定的文档是与给定的内容类型的文本编辑器，术语将为 true。|  
|ActiveProjectCapability:\<表达式 >|活动项目功能与提供的表达式匹配时，术语是如此。 表达式可以有类似 VB &#124;CSharp|  
|SolutionHasProjectCapability:\<表达式 >|在解决方案中包含的表达式匹配任何加载的项目时，与上述相似，但术语是如此。|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|每当解决方案有风格 （聚合） 的项目，并且具有与给定的项目类型 GUID 匹配风格，术语将为 true。|


  
## <a name="compatibility-with-cross-version-extension"></a>与跨版本扩展的兼容性  
 规则基于的 UI 上下文是 Visual Studio 2015 中的新功能并不将移植到早期版本。 这将创建面向多个版本的 Visual Studio 将一定要在 Visual Studio 2013 中自动加载和更早版本，但可以受益于基于规则的 UI 上下文，以防止自动-中正在加载 Visual Studio 2015/扩展包有问题。  
  
 为了支持此类包，AutoLoadPackages 注册表中的项现在可以提供以指示应在 Visual Studio 2015 及更高版本时跳过该条目与其值字段中的标志。 这可以通过添加到标志选项完成<xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>。 现在可以添加 Vspackage **SkipWhenUIContextRulesActive**选项设为其<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>特性以指示应忽略该条目，在 Visual Studio 2015 及更高版本。  
  
## <a name="extensible-ui-context-rules"></a>可扩展的 UI 上下文规则  
 有时，包不能使用 UI 上下文的静态规则。 例如，假设有这样的： 命令状态取决于导入 MEF 提供程序支持的编辑器类型支持扩展性包。 如果没有支持当前的编辑类型的扩展，则启用该命令。 在这种情况下包本身无法使用静态的 UI 上下文规则，因为条款将更改具体取决于哪些 MEF 提供了扩展。  
  
 为了支持此类包，基于规则的 UI 上下文支持硬编码表达式"*"，该值指示所有以下条款将被加入与或者。 这允许主包来定义已知的规则基于 UI 上下文以及如何关联到此上下文其命令状态。 以后针对主包任何 MEF 扩展可将其条款添加为它支持不会影响其他条款或主表达式编辑器。  
  
 构造函数<xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>文档显示可扩展 UI 上下文规则的语法。