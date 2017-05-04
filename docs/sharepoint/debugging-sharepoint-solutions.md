---
title: "调试 SharePoint 解决方案 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.WebConfigModificationDialog"
  - "VS.SharePointTools.Project.DebuggingNotEnabled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 调试"
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 调试 SharePoint 解决方案
  可以使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 调试器来调试 SharePoint 解决方案。  启动调试后，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将项目文件部署到 SharePoint Server，然后在 Web 浏览器中打开 SharePoint 网站的一个实例。  以下各节说明如何在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中调试 SharePoint 应用程序。  
  
-   [启用调试](#EnableDebug)  
  
-   [F5 调试和部署过程](#Deployment)  
  
-   [SharePoint 项目功能](#Features)  
  
-   [调试工作流](#Workflow)  
  
-   [调试功能事件接收器](#FeatureEvents)  
  
-   [启用增强的调试信息](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a> 启用调试  
 当您首次在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中调试 SharePoint 解决方案时，将会出现一个对话框，警告您 web.config 文件尚未配置为启用调试。（web.config 文件是在安装 SharePoint Server 时创建的。  有关详细信息，请参见 [与 Web.config 文件一起使用](http://go.microsoft.com/fwlink/?LinkID=149266)。此对话框为您提供了两种选项：运行项目而不进行调试；修改 web.config 文件以启用调试。  如果您选择第一个选项，则项目会正常运行。  如果您选择第二个选项，则 web.config 文件将被配置为：  
  
-   启用调用堆栈 \(`CallStack="true"`\)  
  
-   禁用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的自定义错误 \(`<customErrors mode="Off" />`\)  
  
-   启用编译调试 \(`<compilation debug="true">`\)  
  
 生成的 web.config 文件如下所示：  
  
```  
  
<configuration>  
    ...  
    <SharePoint>  
        <SafeMode MaxControls="200"  
            CallStack="true"  
            DirectFileDependencies="10"  
            TotalFileDependencies="50"  
            AllowPageLevelTrace="false">  
            ...  
        </SafeMode>  
    ...  
    </SharePoint>  
    <system.web>  
        ...  
        <customErrors mode="Off" />  
        ...  
        <compilation debug="true">  
        ...  
        </compilation>  
        ...  
    </system.web>  
    ...  
</configuration>  
```  
  
 若要撤消更改并禁用调试，请在 web.config 文件中更改以下 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]：  
  
-   关闭调用堆栈 \(`CallStack="false"`\)  
  
-   启用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的自定义错误 \(`<customErrors mode="On" />`\)  
  
-   禁用编译调试 \(`<compilation debug="false">`\)  
  
##  <a name="Deployment"></a> F5 调试和部署过程  
 在调试模式下运行 SharePoint 项目时，SharePoint 部署过程将执行以下任务：  
  
1.  运行可自定义的预先部署命令。  
  
2.  使用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 命令来创建 Web 解决方案包 \(.wsp\) 文件。  该 .wsp 文件包括所有必要的文件和功能。  有关更多信息，请参见[解决方案概述](http://go.microsoft.com/fwlink/?LinkID=128154)。  
  
3.  如果 SharePoint 解决方案是场解决方案，则回收指定网站 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 的 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 应用程序池。  此步骤将释放 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 辅助进程锁定的文件。  
  
4.  如果已存在早期版本的包，则收回 .wsp 文件中早期版本的功能和文件。  此步骤将停用功能，卸载解决方案包并在 SharePoint Server 上删除解决方案包。  
  
5.  安装 .wsp 文件中当前版本的功能和文件。  此步骤会在 SharePoint Server 上添加和安装解决方案。  
  
6.  对于工作流，安装工作流程序集。  可以使用 *Assembly Location* 属性更改程序集的位置。  
  
7.  如果作用域是网站或 Web，则激活 SharePoint 中的项目功能。  不激活场和 Web 应用程序作用域内的功能。  
  
8.  对于工作流，将工作流与您在**“SharePoint 自定义向导”**中选择的 SharePoint 库、列表或网站相关联。  
  
    > [!NOTE]  
    >  此关联仅当您在该向导中选择**“是否自动与工作流关联”**时发生。  
  
9. 运行可自定义的后期部署命令。  
  
10. 将[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 调试器附加到[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 进程\(w3wp.exe\)中。  如果项目类型允许您更改 *Sandboxed Solution*属性，并且将其值设置为**true**，则调试器会附加到一个不同的进程 \(SPUCWorkerProcess.exe\)中。  有关详细信息，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
11. 如果 SharePoint 解决方案是场解决方案，则启动 JavaScript 调试器。  
  
12. 在 Web 浏览器中显示相应的库、列表或网站页。  
  
 在每个任务完成后，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 都会在“输出”窗口中显示状态消息。  如果某个任务无法完成，则 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会在“错误列表”窗口中显示错误消息。  
  
##  <a name="Features"></a> SharePoint 项目功能  
 功能是一个可移植的模块化功能单元，它通过使用网站定义简化了网站修改工作。  功能还是一个 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] \(WSS\) 元素包，可以在特定的作用域内激活这些元素，以帮助用户完成特定目标或任务。  模板将作为功能进行部署。  
  
 在调试模式下运行项目时，部署过程将在 %COMMONPROGRAMFILES%\\Microsoft Shared\\web server extensions\\14\\TEMPLATE\\FEATURES 的功能目录下创建一个文件夹。  功能名称的格式为：*project name*\_Feature*x*，如 TestProject\_Feature1。  
  
 功能目录的解决方案的文件夹中包含一个功能定义文件和一个工作流定义文件。  功能定义文件 \(Feature.xml\) 描述项目功能中的文件。项目定义文件 \(Elements.xml\) 描述项目模板。  可在**“解决方案资源管理器”**中找到 Elements.xml，但 Feature.xml 是在创建解决方案包时生成的。  有关这些文件的更多信息，请参见 [SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
##  <a name="Workflow"></a> 调试工作流  
 在调试工作流项目时，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将工作流模板（取决于其类型）添加到库或列表中。  然后，您可以通过添加或更新项来以手动方式启动工作流模板。  之后，您可以使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 调试工作流。  
  
> [!NOTE]  
>  如果添加对其他程序集的引用，请确保这些程序集安装在全局程序集缓存 \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\) 中。  否则工作流解决方案将失败。  有关如何安装程序集的信息，请参见[在文档或项上手动启动工作流](http://go.microsoft.com/fwlink/?LinkID=79938)。  
  
 但部署过程不会启动工作流。  必须从 SharePoint 网站启动工作流。  还可以通过使用客户端应用程序（例如 Microsoft Office Word 2010）或使用单独的服务器端代码来启动工作流。  使用在**“SharePoint 自定义向导”**中指定的某一种方法。  
  
 例如，如果您指定可以手动启动工作流，则直接从库或列表中的项启动工作流。  有关如何手动启动工作流的详细信息，请参见 [手动启动文档项的工作流](http://go.microsoft.com/fwlink/?LinkID=79938)。  
  
##  <a name="FeatureEvents"></a> 调试功能事件接收器  
 默认情况下，在运行 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 应用程序时，将在 SharePoint Server 上自动为您激活该应用程序的功能。  不过，在调试功能事件接收器时，这会导致问题，原因是当 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 激活某个功能时，该功能会在不同于调试器的进程中运行。  这意味着，一些调试功能（如断点）将无法正常工作。  
  
 若要在 SharePoint 中禁用功能的自动激活并允许对功能事件接收器进行适当的调试，请在调试之前将项目的**“活动部署配置”**属性的值设置为**“无激活”**。  然后在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中开始调试 SharePoint 应用程序，在 SharePoint 中手动激活此功能。  为此，请单击 SharePoint 中“网站操作”菜单上的“网站设置”，再单击“管理网站功能”链接，然后单击“功能”旁边的“激活”按钮，将调试恢复为正常状态。  
  
##  <a name="EnhancedDebug"></a> 启用增强的调试信息  
 由于 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 进程 \(devenv.exe\)、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 宿主进程 \(vssphost4.exe\) 、SharePoint 和 WCF 层之间的交互有时会很复杂，因此对生成、部署时出现的错误进行诊断会非常困难。  可以通过启用增强的调试信息来帮助您解决此类错误。  为此，请转至 Windows 注册表中的以下注册表项：  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools\]  
  
 如果“EnableDiagnostics”**REG\_DWORD** 值已不存在，请手动创建它。  设置“EnableDiagnostics”值为“1.”。  
  
 在将此键值设置为 1 后，只要在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中运行时出现项目系统错误，**“输出”**窗口中就会显示堆栈跟踪信息。  若要禁用增强的调试信息，请将 EnableDiagnostics 设置回 0或者删除该值。  
  
 有关其他 SharePoint 注册表项的更多信息，请参见 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  