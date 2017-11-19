---
title: "调试 SharePoint 解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, debugging
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14a3c7a2676c786e631b4c8b471272185b81e36c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-sharepoint-solutions"></a>调试 SharePoint 解决方案
  您可以通过使用调试 SharePoint 解决方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]调试器。 当开始调试，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将项目文件部署到 SharePoint 服务器，然后打开在浏览器中的 SharePoint 网站的实例。 以下各节说明如何调试 SharePoint 应用程序[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   [启用调试](#EnableDebug)  
  
-   [F5 调试和部署过程](#Deployment)  
  
-   [SharePoint 项目功能](#Features)  
  
-   [调试工作流](#Workflow)  
  
-   [调试功能事件接收器](#FeatureEvents)  
  
-   [启用增强的调试信息](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a>启用调试  
 当你第一次调试 SharePoint 解决方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，对话框中向你发出警报的 web.config 文件未配置为启用调试。 （在安装 SharePoint server 时，都会创建 web.config 文件。 有关详细信息，请参阅[使用 Web.config 文件](http://go.microsoft.com/fwlink/?LinkID=149266)。)对话框中显示的任一运行项目，而调试或修改 web.config 文件的选项，以启用调试。 如果选择第一个选项，则项目会正常运行。 如果选择第二个选项，则 web.config 文件将配置为：  
  
-   在调用堆栈上打开 (`CallStack="true"`)  
  
-   禁用中的自定义错误[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](`<customErrors mode="Off" />`)  
  
-   启用编译调试 (`<compilation debug="true">`)  
  
 生成的 web.config 文件如下：  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
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
  
 若要撤消所做的更改并禁用调试，进行以下更改[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]web.config 文件中：  
  
-   请关闭调用堆栈 (`CallStack="false"`)  
  
-   启用的自定义错误[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](`<customErrors mode="On" />`)  
  
-   禁用编译调试 (`<compilation debug="false">`)  
  
##  <a name="Deployment"></a>F5 调试和部署过程  
 在调试模式下运行你的 SharePoint 项目时，SharePoint 部署过程将执行以下任务：  
  
1.  运行的可自定义预先部署命令。  
  
2.  通过使用创建 Web 解决方案包 (.wsp) 文件[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]命令。 .Wsp 文件包含的所有必需的文件和功能。 有关详细信息，请参阅[解决方案概述](http://go.microsoft.com/fwlink/?LinkID=128154)。  
  
3.  如果 SharePoint 解决方案，场解决方案回收[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]指定站点的应用程序池[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]。 此步骤将释放由锁定的文件[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]工作进程。  
  
4.  如果以前版本的包已存在，将收回以前版本的功能和.wsp 文件中的文件。 此步骤停用了功能、 卸载解决方案包，然后删除 SharePoint 服务器上的解决方案包。  
  
5.  .Wsp 文件中安装的功能和文件的当前版本。 此步骤将添加，并在 SharePoint 服务器上安装解决方案。  
  
6.  对于工作流，会安装工作流程序集。 你可以通过更改其位置*程序集的位置*属性。  
  
7.  如果范围为站点或 Web，激活 SharePoint 中的项目的功能。 未激活场和 web 应用程序的作用域中的功能。  
  
8.  对于工作流，工作流将与相关联的 SharePoint 库、 列表中或在中选择的站点**SharePoint 自定义向导**。  
  
    > [!NOTE]  
    >  仅当你选择，则会发生此关联**自动相关联的工作流**向导中。  
  
9. 运行的可自定义后期部署命令。  
  
10. 将 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 调试器附加到 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 进程 (w3wp.exe)。 如果项目类型允许您更改*沙盒解决方案*属性，并且其值设置**true**，调试器会附加到另一进程 (SPUCWorkerProcess.exe)。 有关详细信息，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
11. 如果 SharePoint 解决方案已部署场解决方案，请启动 JavaScript 调试器。  
  
12. 在 Web 浏览器中显示相应的库、 列表或网站页。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]每个任务完成后，请在输出窗口中显示的状态消息。 如果无法完成任务，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]在错误列表窗口中显示一条错误消息。  
  
##  <a name="Features"></a>SharePoint 项目功能  
 一个功能是功能的一个可移植的站点修改使用简化的站点定义的模块化单元。 它也是一个软件包[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)](WSS) 元素的特定作用域可以激活，以帮助用户完成特定目标或任务。 模板作为功能进行部署。  
  
 当在调试模式下运行项目时，部署过程将创建的文件夹中*功能*在 %COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES 目录。 功能名称具有格式*项目名称*_Feature*x*，如 TestProject_Feature1。  
  
 功能目录中的解决方案的文件夹包含*功能定义*文件和一个*工作流定义*文件。 将功能定义文件 (Feature.xml) 描述的文件在项目的功能。 项目定义文件 (Elements.xml) 描述项目模板。 在找不到 Elements.xml**解决方案资源管理器**，但 Feature.xml 在创建解决方案包时生成。 有关这些文件的详细信息，请参阅[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
##  <a name="Workflow"></a>调试工作流  
 调试工作流项目时[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将 （具体取决于其类型） 的工作流模板添加到库或列表。 手动或通过添加或更新项，你可以随后启动工作流模板。 然后，可以使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]调试工作流。  
  
> [!NOTE]  
>  如果添加对其他程序集的引用，请确保这些程序集安装在全局程序集缓存 ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)])。 否则，该工作流解决方案将会失败。 有关如何安装程序集的信息，请参阅[手动对文档或项中启动工作流](http://go.microsoft.com/fwlink/?LinkID=79938)。  
  
 但是，在部署过程不会启动工作流。 从 SharePoint 网站，必须启动工作流。 通过使用的客户端应用程序，例如 Microsoft Office Word 2010，或通过使用单独的服务器端代码，你还可以启动工作流。 使用中指定的方法之一**SharePoint 自定义向导**。  
  
 例如，如果你指定在工作流可以手动启动，请直接从库或列表中的项中启动工作流。 有关如何手动启动工作流的详细信息，请参阅[手动对文档项启动工作流](http://go.microsoft.com/fwlink/?LinkID=79938)。  
  
##  <a name="FeatureEvents"></a>调试功能事件接收器  
 默认情况下，当你运行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 应用程序，它的功能自动激活为你在 SharePoint 服务器上。 但是，这会导致问题在调试功能事件接收器，因为当通过激活功能[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，它在不同于调试器进程中运行。 这意味着某些调试功能，如断点，将无法在正常工作。  
  
 若要禁用自动激活 SharePoint 中的功能并允许进行适当的调试功能事件接收器，项目的值设置**活动部署配置**属性**无激活**之前调试。 然后，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中开始调试 SharePoint 应用程序后，在 SharePoint 中手动激活此功能。 若要激活该功能，请打开**站点操作**在 SharePoint 中，菜单中，选择**站点设置**，选择**管理站点功能**链接，然后依次**激活**功能，以继续调试恢复为正常旁边的按钮。  
  
##  <a name="EnhancedDebug"></a>启用增强的调试信息  
 由于之间不时地进行复杂的交互[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]过程 (devenv.exe) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 主机进程 (vssphost4.exe)、 SharePoint 和 WCF 层，可以是诊断构建、 部署和等时，会出现的错误挑战。 若要帮助你解决此类错误，可以启用增强的调试信息。 若要执行此操作，请转到 Windows 注册表中的以下注册表项：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools]  
  
 如果"EnableDiagnostics" **REG_DWORD**值不已不存在，请手动创建它。 "EnableDiagnostics"将值设置为"1。  
  
 将此密钥值设置为 1 的原因堆栈跟踪信息显示在**输出**窗口项目系统错误发生运行时的任何时候[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 若要禁用增强的调试信息，请将 EnableDiagnostics 设置回 0 或者删除该值。  
  
 有关其他 SharePoint 注册表项的详细信息，请参阅[调试 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  