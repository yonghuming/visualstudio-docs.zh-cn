---
title: "Microsoft 语言界面包 (LIP) 和 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语言切换 [Visual Studio]"
  - "语言, 多语言支持"
  - "MUI [Visual Studio]"
  - "多语言用户界面 [Visual Studio]"
  - "多语言支持 [Visual Studio SDK]"
  - "文本 [Visual Studio], 多种语言"
  - "UI 文本语言 [Visual Studio]"
  - "Windows 多语言用户界面"
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
caps.handback.revision: 28
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Microsoft 语言界面包 (LIP) 和 Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过使用 Windows 语言界面包 \(LIP\)，可以安装某个语言版本的 Windows，然后安装各种用户界面语言包。  用户界面语言包为操作系统提供本地化用户界面 \(UI\)。  例如，可以在英语版本的 Windows 基础上安装日语语言界面包，然后在日语与英语之间切换 Windows UI 语言。  通过使用 LIP，可以在一台计算机上安装多个语言版本的 Windows。  
  
 在安装了 LIP 和多个语言版本的 Visual Studio 的计算机上，如果安装了匹配语言包，则更改 Windows 显示语言设置会同时设置 Windows 和 Visual Studio。  
  
## 多语言安装的限制  
 在同一台计算机上安装不同语言版本的 Visual Studio 时，只能在匹配版本之间切换语言。  例如，如果安装了英语速成版、德语速成版和专业版，则只能针对速成版切换语言，而不能针对专业版切换。  
  
 Visual Studio 使用统一的语言包。  若要安装这些产品的多个语言版本，必须首先安装某个完整语言产品，然后安装一个或多个语言包。  
  
> [!NOTE]
>  Visual Studio 不支持在同一台计算机上安装多个语言版本的完整语言产品。  安装一个完整语言产品之后，必须使用语言包添加语言版本。  仍可以在同一台计算机上安装速成版的多个完整语言产品。  
  
### 代码页支持  
 当文本包含不在当前代码页中的字符时，某些 Visual Studio 工具无法正确显示文本。  而是会显示问号或文本损坏。  以下工具或区域会受到影响：  
  
-   使用 FTP 部署的站点。  
  
-   某些控件中的非 ASCII 计算机名。  
  
-   在 Visual Studio 外部运行的命令行工具。  
  
-   Visual Basic 迁移向导。  
  
-   ActiveX 控件测试容器。  
  
-   OLE\/COM 对象查看器。  
  
-   ISAPI Web 调试工具。  
  
-   具有 HTML 帮助内容的 MFC 应用程序项目。  
  
-   Visual SourceSafe\/SCCI UI 会在存在不兼容的代码页时回退到英语。  
  
-   Visual SourceSafe 不支持 Unicode 文件名。  
  
-   最终用户定义的字符（专用区域）不能用作标记\/标识符。  
  
-   当 Windows 代码页设置为东亚语言时，拉丁语扩展 B 字符在某些 Visual Studio 工具窗口中无法显示。  
  
-   由多个语言脚本中的字符组成的文本运行可能会对某些字符显示默认字形。  
  
-   将复杂脚本字符串复制并粘贴到公共控件中可能会导致字符形状丢失。  请改用对应的语言键盘输入文本。  
  
##### 正确显示未包含在当前代码页中的字符  
  
1.  单击**“开始”**，单击**“控制面板”**，然后打开**“区域和语言选项”**（在 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 中为**“区域”**）。  
  
    > [!NOTE]
    >  必须是计算机上的管理员才能执行这些步骤。  
  
2.  单击**“高级”**选项卡。  
  
3.  在**“选择一种语言，使之与您想使用的非 Unicode 程序的语言版本相匹配”**列表中，选择当前所用的语言。  
  
4.  单击“确定”。  
  
## 更改在 Visual Studio 中用于 UI 文本的语言  
 在同一台计算机上安装多个语言版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] UI 默认为**“与 Microsoft Windows 相同”**。  此设置指示 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会使用指定为操作系统显示语言的语言来显示 UI 文本。  
  
> [!NOTE]
>  如果 Visual Studio 设置为使用**“与 Microsoft Windows 相同”**，并且未安装匹配的 Visual Studio 语言包，则 Visual Studio 会使用第一个 Visual Studio 安装的语言。  
  
#### 设置在 Visual Studio 中用于 UI 文本的语言  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  在**“选项”**对话框中，展开**“环境”**，然后单击**“区域设置”**。  
  
3.  在**“语言”**列表中，选择应在开发环境中用于显示 UI 文本的语言。  
  
     若要使 IDE 中的 UI 文本与操作系统显示语言设置匹配，请选择**“与 Microsoft Windows 相同”**。  
  
 还可以使用 devenv 命令设置用于 UI 的语言。  有关详细信息，请参阅 [\/LCID](../ide/reference/lcid-devenv-exe.md)。  
  
## 请参阅  
 [“选项”对话框 \-\>“环境”\-\>“区域设置”](../ide/reference/international-settings-environment-options-dialog-box.md)