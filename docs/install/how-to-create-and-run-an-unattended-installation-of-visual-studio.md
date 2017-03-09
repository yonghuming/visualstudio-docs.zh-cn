---
title: "如何：创建和运行 Visual Studio 的无人参与安装 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安装 Visual Studio, 无人参与"
  - "无人参与的安装, Visual Studio"
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
caps.handback.revision: 32
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 如何：创建和运行 Visual Studio 的无人参与安装
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

你可以将 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的安装应用程序作为无人参与（即自定义无提示）安装通过 Intranet 而不是从媒体（如 DVD）运行。 本主题演示如何准备 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以便从网络共享安装此类型。  
  
## 创建网络映像  
 首先，创建 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 媒体的网络映像。  
  
#### 创建网络映像  
  
1.  在服务器上创建文件夹（例如，*Drive*:\\IDEinstall\\）。  
  
2.  执行以下步骤之一：  
  
    -   下载 Web 引导程序，然后运行 *Product*.exe \/Layout *Drive*:\\IDEinstall\\。  
  
         或  
  
    -   将 Visual Studio 的媒体的内容复制到 IDEinstall 文件夹中。 在复制内容后，将仍需要下载想要安装的所有第三方软件。  
  
3.  在网络上共享 IDEinstall 文件夹并设置适当的安全设置。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的安装应用程序的网络路径类似于 \\\\*ServerName*\\IDEinstall\\*Product*.exe。  
  
    > [!NOTE]
    >  如果任何路径和文件名的组合超过 260 个字符，则安装可能失败。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的路径的最大长度为 221 个字符。  本地路径名称不应超过 70 个字符，并且网络路径名称不应超过 39 个字符。  
  
     如果路径中的文件夹名称包含嵌入的空格（例如，“\\\\*ServerName*\\IDE install”或 \\\\*ServerName*\\Visual Studio\\），则安装也可能失败。  
  
## 在无人参与模式下部署 Visual Studio  
 若要在无人参与模式下部署 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，则必须修改 AdminDeployment.xml 文件。 若要执行此操作，必须首先使用 `/CreateAdminFile <file location>` 命令行参数创建 AdminDeployment.xml 文件。 然后，可以使用此文件将 Visual Studio 的部署推送到你的网络或拉入安装（如果将该文件放入 *Drive*:\\IDEinstall\\packages 目录中）。 AdminDeployment.xml 文件对于某个操作系统、体系结构、Visual Studio 版本或操作系统语言不是唯一的。  
  
> [!CAUTION]
>  有时，依照 AdminDeployment.xml 文件中的所选内容而列出的项无法安装。 若要解决此问题，将标记为“Selected\="yes"”的项放在 AdminDeployment.xml 文件的**末尾**。  
>   
>  如果不想安装某项的可选依赖项，则必须首先选中父级，然后取消选中父级后的可选依赖项，如下面的屏幕快照中所示：  
>   
>  ![AdminDeployment.xml 文件末尾的安装项](../install/media/vs2015_install_endoffileadmindeploy.png "vs2015\_Install\_EndOfFileAdminDeploy")  
>   
>  执行此操作的另一个方法是省略可选父级的子级 \- 换而言之，不要包括任何“Selected\=”no””项，但你仍须将所有“Selected\=”yes””项放在 AdminDeployment.xml 文件末尾。  
  
> [!IMPORTANT]
>  在安装期间，计算机可能会自动重启一次或多次。 重启后，必须使用相同的用户帐户重新登录，以进行安全，然后再重启计算机。 在运行无人参与安装之前安装系统必备组件，可以避免自动重启。 有关详细信息，请参阅 [Visual Studio 管理员指南](../install/visual-studio-administrator-guide.md) 中标题为“安装期间避免重启”的部分。  
  
 AdminDeployment 文件架构包含下列元素：  
  
|元素|特性|值|说明|  
|--------|--------|-------|--------|  
|BundleCustomizations|TargetDir|*路径*|行为与在安装应用程序的用户界面中重写路径相同。 如果已安装 Visual Studio，则忽略此元素。|  
|BundleCustomizations|NoWeb|yes&#124;default|如果此元素的值为“yes”，则安装应用程序永远不会尝试在安装操作期间转到 Web。|  
|SelectableItemCustomization|Hidden|Yes&#124;No|如果此元素的值为“Yes”，则将隐藏自定义树中的可选项。|  
|SelectableItemCustomization|已选定|Yes&#124;No|选择或清除自定义树中的可选项。|  
|BundleCustomizations|源|路径|用户想要使用的源的位置。  此源用于计算机上的后续修改操作（默认情况下为“Default”）。|  
|BundleCustomizations|SuppressRefreshPrompt|yes&#124;default|将阻止提示用户在存在较新可用安装程序的情况下刷新安装程序。|  
|BundleCustomizations|NoRefresh|yes&#124;default|如果有较新的可用安装程序则不会刷新。|  
|BundleCustomizations|NoCacheOnlyMode|yes&#124;default|阻止包缓存的预填充。|  
  
> [!WARNING]
>  安装应用程序将遵守 SelectableItem 的选定状态，即使它被隐藏。 例如，如果你想要始终安装某个可选项，可以将其标记为隐藏和已选定。  
  
#### 创建 Visual Studio 的无人参与安装  
  
1.  在 *Drive*:\\IDEinstall\\AdminDeployment.xml 文件中，将 BundleCustomizations 元素的 NoWeb 属性的值从“default”更改为“yes”，如以下示例所示：  
  
     将 `<BundleCustomizations TargetDir="default" NoWeb="default"/>` 更改为 `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`  
  
2.  根据可选组件的需要更改 SelectableItemCustomization 属性，然后保存该文件。  
  
## 运行无人参与安装  
 可以通过在客户端计算机上自动运行 Visual Studio 的安装应用程序或通过允许用户使用你定义的设置自己运行该应用程序来运行无人参与安装。  
  
#### 在客户端计算机上运行无人参与安装  
  
-   打开“开始”菜单，选择“运行”，然后输入 `\\ServerName\IDEinstall\vs_Product.exe /adminfile PathOfTheAdmindeployment.xmlFile` *AdditionalParametersAsNeeded*  
  
     例如，可以指定以下命令行：`\\server1\IDEinstall\vs_ultimate.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
#### 使客户端能够使用预定义的设置手动安装 Visual Studio  
  
1.  将自定义的 AdminDeployment.xml 文件复制到只读的网络共享（例如，\\\\*ServerName*\\IDEinstall\\packages\\AdminDeployment.xml）。  
  
2.  使用户能够从该共享安装。  
  
## 维护安装  
 如果打开**“控制面板”**并重新运行安装应用程序，则可以修改 Visual Studio 的功能、卸载编程语言以及修复或卸载 Visual Studio。  
  
> [!NOTE]
>  你必须在本地计算机上具有管理凭据才能使用维护模式。  
  
#### 维护客户端计算机上的安装  
  
-   打开**“控制面板”**，然后选择**“程序和功能”**。  
  
-   选择 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，然后选择**“更改”**。  
  
#### 在已安装 Visual Studio 之后更改客户端计算机上的 AdminDeployment 设置  
  
1.  根据需要更新 AdminDeployment.xml。  
  
2.  打开**“开始”**菜单，然后选择**“运行”**。  
  
3.  输入以下文本：  
  
     `\\ServerName\IDEinstall\vs_Product.exe /AdminFile PathToAdmindeployment.xmlFile` AdditionalParametersAsNeeded  
  
     例如，可以指定以下命令行：`\\server1\IDEinstall\vs_ultimate.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
 安装 Visual Studio 之后，修复是默认参数。 如果使用更新的 \/AdminFile 修复 Visual Studio，则更新的 AdminDeployment.xml 调用的设置将替代当前的管理员部署设置。  
  
## 注册产品  
 安装完成后，可以从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内部注册 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的副本。  
  
#### 注册  
  
1.  打开**“帮助”**菜单，然后选择**“注册产品”**。  
  
2.  输入产品密钥。  
  
## 请参阅  
 [安装 Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)