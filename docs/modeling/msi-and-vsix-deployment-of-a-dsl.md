---
title: "MSI 和 VSIX 部署的 DSL |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: dafee91f26cf45d780f1b222d8daf5977980a3f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL 的 MSI 和 VSIX 部署
在你自己的计算机或其他计算机上，你可以安装的域特定语言。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]已必须在目标计算机上安装。  
  
##  <a name="which"></a>VSIX 和 MSI 部署之间进行选择  
 有两种方法可以部署域特定语言：  
  
|方法|优点|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]扩展)|非常易于部署： 复制和执行**.vsix** DslPackage 项目文件。<br /><br /> 有关详细信息请参阅[安装和使用 VSX 卸载 DSL](#Installing)。|  
|MSI （安装程序文件）|-允许用户打开[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]通过双击 DSL 文件。<br />-将图标与目标计算机中的 DSL 文件类型关联。<br />-将 XSD （XML 架构） 与 DSL 文件类型关联。 这样可避免警告，当文件加载到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。<br /><br /> 必须将安装项目添加到解决方案以创建 MSI。<br /><br /> 有关详细信息，请参阅[使用 MSI 文件部署 DSL](#msi)。|  
  
##  <a name="Installing"></a>安装和使用 VSX 卸载 DSL  
 此方法安装 DSL 后，用户可以从内打开 DSL 文件[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，但不能从 Windows 资源管理器中打开该文件。  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>若要使用 VSX 安装 DSL  
  
1.  在你的计算机，找到**.vsix**由 DSL 包项目生成的文件。  
  
    1.  在**解决方案资源管理器**，右键单击**DslPackage**项目，，然后单击**在 Windows 资源管理器中打开文件夹**。  
  
    2.  找到文件**bin\\\*\\***YourProject***。DslPackage.vsix**  
  
2.  复制**.vsix**到你想要安装 DSL 目标计算机的文件。 该计算机可以是自己的计算机或其他计算机。  
  
    -   目标计算机必须具有的版本之一[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]Dsl 支持在运行时。 有关详细信息，请参阅[的可视化和建模 SDK 支持 Visual Studio 版本](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)。  
  
    -   目标计算机必须具有的版本之一[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中指定**DslPackage\source.extensions.manifest**。  
  
3.  在目标计算机上，双击**.vsix**文件。  
  
     “” 将会打开并安装扩展。  
  
4.  启动或重启 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。  
  
5.  若要测试 DSL，使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]以创建新的文件扩展名为 DSL 定义。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>若要卸载 DSL 都通过使用 VSX 安装  
  
1.  上**工具**菜单上，单击**扩展管理器**。  
  
2.  展开“已安装的扩展” 。  
  
3.  选择在其中定义 DSL，该扩展，然后单击**卸载**。  
  
 在极少数情况下，有错误的扩展无法加载并在错误窗口中创建报告，但不显示在扩展管理器中。 在这种情况下，可以通过从以下位置删除文件来删除扩展：  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="msi"></a>部署中 MSI DSL  
 通过为 DSL 定义 MSI (Windows Installer) 文件，你可以允许用户从 Windows 资源管理器中打开 DSL 文件。 您还可以与你的文件扩展名关联的图标和简短说明。 此外，MSI 可以安装可以用于验证 DSL 文件 XSD。 如果你想，也可以将其他组件添加到将在同一时间安装 MSI。  
  
 有关 MSI 文件和其他部署选项的详细信息，请参阅[部署应用程序、 服务和组件](../deployment/deploying-applications-services-and-components.md)。  
  
 若要生成 MSI，则安装程序将项目添加到你[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]解决方案。 创建安装项目的最简单方法是使用 CreateMsiSetupProject.tt 模板，你可以从下载[VMSDK 站点](http://go.microsoft.com/fwlink/?LinkID=186128)。  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>若要部署在 MSI DSL  
  
1.  设置`InstalledByMsi`扩展清单中。 这样可以防止 VSX 正在安装和卸载除 MSI。 这是重要信息： 如果将将其他组件包括在 MSI。  
  
    1.  打开 DslPackage\source.extension.tt  
  
    2.  以下行之前插入行`<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  创建或编辑将表示在 Windows 资源管理器 DSL 的图标。 例如，编辑**DslPackage\Resources\File.ico**  
  
3.  确保正确 DSL 的以下属性：  
  
    -   DSL 资源管理器中单击根节点中，并在属性窗口中，查看：  
  
        -   描述  
  
        -   版本  
  
    -   单击**编辑器**节点，然后在属性窗口中，单击**图标**。 设置值以引用中的图标文件**DslPackage\Resources**，如**File.ico**  
  
    -   上**生成**菜单上，打开**Configuration Manager**，并选择你想要构建，例如配置**版本**或**调试**.  
  
4.  转到[可视化和建模 SDK 主页](http://go.microsoft.com/fwlink/?LinkID=186128)，和从**下载**选项卡上，下载**CreateMsiSetupProject.tt**。  
  
5.  添加**CreateMsiSetupProject.tt**到 Dsl 项目。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]将创建名为的文件**CreateMsiSetupProject.vdproj**。  
  
6.  在 Windows 资源管理器，复制 Dsl\\*.vdproj 到新的文件夹名为安装程序。  
  
     （如果你想，你可以现在 CreateMsiSetupProject.tt 从项目中排除 Dsl。）  
  
7.  在**解决方案资源管理器**，添加**安装\\\*.vdproj**作为现有项目。  
  
8.  上**项目**菜单上，单击**项目依赖项**。  
  
     在**项目依赖项**对话框框中，选择的安装程序项目。  
  
     选中框旁边**DslPackage**。  
  
9. 重新生成解决方案。  
  
10. 在 Windows 资源管理器，找到安装程序项目中生成的 MSI 文件。  
  
     将 MSI 文件复制到你想要安装 DSL 的计算机。 双击该 MSI 文件。 安装会运行。  
  
11. 在目标计算机，创建具有 DSL 的文件扩展名的新文件。 请验证：  
  
    -   在 Windows 资源管理器列表视图中，该文件将显示使用图标和你定义的说明。  
  
    -   当你双击该文件，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]启动，并在 DSL 编辑器中打开 DSL 文件。  
  
 如果你愿意，你可以安装项目手动创建，而不是使用文本模板。 有关包括此过程的演练，请参阅的第 5 章：[可视化和建模 SDK 实验室](http://go.microsoft.com/fwlink/?LinkId=208878)。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>若要卸载从 MSI 安装 DSL  
  
1.  在 Windows 中，打开**程序和功能**控制面板。  
  
2.  卸载 DSL。  
  
3.  重新启动 Visual Studio。