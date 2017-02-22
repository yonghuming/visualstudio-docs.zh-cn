---
title: "如何︰ 使用 Visual Studio 扩展基于规则的 UI 上下文 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 7
caps.handback.revision: 6
ms.author: "gregvanl"
---
# 如何︰ 使用 Visual Studio 扩展基于规则的 UI 上下文
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 允许加载 Vspackage 时某些人所熟知 <xref:Microsoft.VisualStudio.Shell.UIContext>s 被激活。 但是，这些 UI 上下文不是极其精细粒度，离开扩展插件作者无选择来选择可用的 UI 上下文激活的点之前，他们确实想要加载 VSPackage。 已知 UI 上下文中的列表，请参阅 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>。  
  
 加载包会产生性能影响并不是在需要更快地加载它们不是最佳做法。 Visual Studio 2015 引入了基于规则的 UI 上下文中，一种机制，允许扩展插件作者可以定义在其下 UI 上下文被激活并关联的 VSPackages 迁移加载的精确条件的概念。  
  
## 基于规则的 UI 上下文  
 "规则"包含新 UI 上下文 \(GUID\)，并且引用一个或多个"术语"的布尔表达式结合逻辑"and"、"，"不是"操作。 在运行时的"术语"动态地计算和表达式是重新计算，只要任何其条款更改。 表达式的计算结果为 true，将激活相关联的 UI 上下文。 否则，将取消激活 UI 上下文。  
  
 基于规则的 UI 上下文可以采用多种方式︰  
  
1.  指定命令和工具窗口的可见性的限制。 您可以隐藏命令\/工具窗口，直到满足 UI 上下文规则。  
  
2.  作为自动加载约束︰ 自动加载包仅当满足规则  
  
3.  延迟的任务︰ 延迟加载之前指定的时间间隔过后以及是否仍然满足该规则。  
  
 可能由任何 Visual Studio 扩展中使用的机制。  
  
## 创建基于规则的用户界面的上下文  
 假设您具有名为 TestPackage，它提供了菜单命令，将仅适用于文件扩展名".config"的扩展。 VS2015 之前, 是最佳选择是加载 TestPackage 时 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> UI 上下文已激活。 这并非有效，因为已加载的解决方案甚至可能不包含某一.config 文件。 告诉我们，请参阅如何使用基于规则的 UI 上下文来激活 UI 上下文仅当具有.config 扩展名的文件选择后，，并激活该 UI 上下文时加载 TestPackage。  
  
1.  定义一个新的 UIContext GUID，并将添加到 VSPackage 类 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>。  
  
     例如，假设新 UIContext"UIContextGuid"是要添加。 创建的 GUID \(可以通过单击工具创建 GUID\-\> 创建 guid\) 是"8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B"。 然后添加以下包类中︰  
  
    ```c#  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     对于属性，添加以下项: （这些属性的详细信息将稍后解释）  
  
    ```c#  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     这些元数据定义新的 UIContext GUID \(8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B\) 和一个表达式，该表达式引用单个字词，"DotConfig"。 "DotConfig"一词的计算结果为 true，只要活动层次结构中的当前所选内容具有匹配正则表达式模式"\\.config$"（使用".config"结尾） 的名称。 （默认） 值定义可用于调试的规则的可选名称。  
  
     该属性的值将添加到 pkgdef 期间生成时间之后生成。  
  
2.  在 VSCT 文件中为 TestPackage 的命令，将"DynamicVisibility"标志添加到相应的命令︰  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  在 VSCT 可见性部分中，将绑定到新 UIContext GUID \#1 中定义相应的命令︰  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  在符号部分中，添加 UIContext 的定义︰  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     现在，解决方案资源管理器中的选定的项是".config"文件且在选择其中一个命令之前，将不会加载包时，仅，\*.config 文件的上下文菜单命令将不可见。  
  
 接下来，让我们来使用调试器来确认包加载仅当我们预期的那样。 若要调试 TestPackage:  
  
1.  中设置断点 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
2.  生成 TestPackage 并启动调试。  
  
3.  创建一个项目或打开一个。  
  
4.  选择任何文件扩展名不.config。 应该不会命中断点。  
  
5.  选择的 App.Config 文件。  
  
 TestPackage 加载，并在断点处停止。  
  
## 为 UI 上下文中添加更多的规则  
 由于 UI 上下文规则是布尔表达式，您可以添加更受限制的规则进行 UI 上下文。 例如，在上面的 UI 上下文中，可以指定应用规则，仅在加载了项目的解决方案时。 这种方式，这些命令不会显示是否您打开".config"文件作为独立的文件，而不是项目的一部分。  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 现在该表达式引用了这三个术语。 前两个术语，"SingleProject"和"MultipleProjects"，请参阅其他人所熟知 UI 上下文中 （由其 Guid\)。 第三个术语中，"DotConfig"是我们之前定义的基于规则的 UI 上下文。  
  
## 延迟的激活  
 规则可以具有可选的"延迟"。 以毫秒为单位指定延迟时间。 如果存在，延迟将导致激活或停用的规则的 UI 上下文会由于这段时间间隔发生延迟。 如果将规则更改回复之前的延迟间隔，则没有任何变化。 此机制可用于"错开"初始化步骤\-尤其是一次性初始化而不依赖计时器或注册空闲通知。  
  
 例如，可以指定您测试的负载规则具有 100 毫秒的延迟︰  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## 字词类型  
 下面是术语的支持各种类型:  
  
|||  
|-|-|  
|{nnnnnnnn nnnn\-nnnn\-如下}|GUID 是指 UI 上下文。 UI 上下文否则处于活动状态且 false 时，都会 true 一词。|  
|HierSingleSelectionName: \< 模式 \>|只要活动层次结构中的所选内容的单个项并且所选的项的名称匹配给定"模式"的.Net 正则表达式，该术语将为 true。|  
|UserSettingsStoreQuery: \< 查询 \>|"查询"表示计算结果必须为非零值的用户设置存储到的完整路径。 该查询拆分为"集合"和"属性名称"，在最后一个斜杠。|  
|ConfigSettingsStoreQuery: \< 查询 \>|"查询"表示计算结果必须为非零值的配置设置存储到的完整路径。 该查询拆分为"集合"和"属性名称"，在最后一个斜杠。|  
|ActiveProjectFlavor: \< projectTypeGuid \>|只要当前选定的项目风格术语将为 true （聚合） 和具有风格匹配给定的项目类型 GUID。|  
|ActiveEditorContentType: \< contentType \>|如果所选的文档的给定的内容类型的文本编辑器，术语将为，则返回 true。|  
|ActiveProjectCapability: \< 表达式 \>|当活动项目功能与所提供的表达式匹配时，术语是，则返回 true。 表达式可以是类似于 VB &#124;CSharp|  
|SolutionHasProjectCapability: \< 表达式 \>|在解决方案中包含与表达式匹配任何加载的项目时，与上述相似，但术语是，则返回 true。|  
  
## 扩展名跨版本兼容性  
 基于的 UI 上下文是在 Visual Studio 2015 的新增功能，并将不能移植到更早版本的规则。 这将创建面向多个版本的 Visual Studio 必须将自动加载，在 Visual Studio 2013 和早期版本中，但可以受益于基于规则 UI 上下文，以防止正在自动加载 Visual Studio 2015 中的扩展\/包有问题。  
  
 若要支持此类的包，AutoLoadPackages 注册表中的项现在可以提供一个标志以指示应在 Visual Studio 2015 及更高版本时跳过该条目的值字段中。 这可以通过添加对标志选项完成 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>。 现在可以添加 Vspackage **SkipWhenUIContextRulesActive** 选项设为其 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 特性以指示应忽略该条目，在 Visual Studio 2015 及更高版本。  
  
## 可扩展 UI 上下文规则  
 有时，包不能使用 UI 上下文的静态规则。 例如，假设您有支持可扩展性，以便命令状态取决于导入 MEF 提供程序都支持的编辑器类型的包。 如果没有支持当前的编辑类型的扩展，则会启用命令。 在这种情况下包本身不能使用静态 UI 上下文规则，因为这些条款将发生更改，具体取决于哪个 MEF 提供了扩展。  
  
 若要支持此类的包，基于规则 UI 上下文支持硬编码表达式"\*"，该值指示所有下面的条款将与联接或者。 这允许访问主包以定义为已知的规则基于 UI 上下文，并将其命令状态为此上下文关联在一起。 以后针对主包任何 MEF 扩展可以为它不会影响其他术语或主表达式支持的编辑器添加其中的条款。  
  
 构造函数 <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> 文档显示可扩展 UI 上下文规则的语法。