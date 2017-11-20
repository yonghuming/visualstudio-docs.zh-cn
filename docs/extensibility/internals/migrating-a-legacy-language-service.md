---
title: "迁移旧语言服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5b114cb060f4a689f2712dbaf323e6d2ee327c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="migrating-a-legacy-language-service"></a>将旧语言服务迁移
你可以通过更新项目并向项目添加 source.extension.vsixmanifest 文件迁移到更高版本的 Visual Studio 的旧语言服务。 语言服务本身将继续工作和前面一样，因为 Visual Studio 编辑器采用它。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方式的详细信息，请参阅[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>将 Visual Studio 2008 语言服务解决方案迁移到更高版本  
 以下步骤演示如何改编名为 RegExLanguageService 的 Visual Studio 2008 示例。 你可以找到此示例在 Visual Studio 2008 SDK 安装中，在*Visual Studio SDK 安装路径*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ 文件夹。  
  
> [!IMPORTANT]
>  如果你的语言服务未定义颜色，您必须显式设置<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A>到`true`VSPackage 上：  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>若要迁移到更高版本的 Visual Studio 2008 语言服务  
  
1.  安装 Visual Studio 和 Visual Studio SDK 的较新的版本。 有关如何安装 SDK 的详细信息，请参阅[安装 Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md)。  
  
2.  编辑 RegExLangServ.csproj 文件 （而无需在 Visual Studio 中加载。  
  
     在`Import`引用 Microsoft.VsSDK.targets 文件的节点将值替换为以下文本。  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  保存该文件，，然后关闭它。  
  
4.  打开 RegExLangServ.sln 解决方案。  
  
5.  **单向升级**窗口随即显示。 单击“确定”。  
  
6.  更新的项目属性。 打开**项目属性**窗口，通过选择中的项目节点**解决方案资源管理器**、 右键单击，然后选择**属性**。  
  
    -   上**应用程序**选项卡上，更改**目标框架**到**4.6.1**。  
  
    -   上**调试**选项卡上，在**启动外部程序**框中，键入 **\<Visual Studio 安装路径 > \Common7\IDE\devenv.exe。**。  
  
         在**命令行自变量**框中，键入 /**rootsuffix Exp**。  
  
7.  更新以下引用：  
  
    -   删除对 Microsoft.VisualStudio.Shell.9.0.dll 的引用，然后添加对 Microsoft.VisualStudio.Shell.14.0.dll 和 Microsoft.VisualStudio.Shell.Immutable.11.0.dll 引用。  
  
    -   删除对 Microsoft.VisualStudio.Package.LanguageService.9.0.dll 的引用，然后添加对 Microsoft.VisualStudio.Package.LanguageService.14.0.dll 的引用。  
  
    -   添加对 Microsoft.VisualStudio.Shell.Interop.10.0.dll 的引用。  
  
8.  打开 VsPkg.cs 文件并将更改的值`DefaultRegistryRoot`属性设为  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. 原始示例未注册其语言服务，因此必须将以下属性添加到 VsPkg.cs。  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. 你必须添加 source.extension.vsixmanifest 文件。  
  
    -   现有扩展插件中的此文件复制到你的项目目录。 (若要获取此文件的一种方法是创建 VSIX 项目 (下**文件**，单击**新建**，然后单击**项目**。 在 Visual Basic 或 C# 单击**扩展性**，然后选择**VSIX 项目**。)  
  
    -   将文件添加到你的项目。  
  
    -   在文件的**属性**，将其设置**生成操作**到**无**。  
  
    -   打开具有文件**VSIX 清单编辑器**。  
  
    -   更改以下字段：  
  
    -   **ID**: RegExLangServ  
  
    -   **产品名称**: RegExLangServ  
  
    -   **说明**： 正则表达式语言服务。  
  
    -   下**资产**，单击**新建**，选择**类型**到**Microsoft.VisualStudio.VsPackage**，将其设置**源**到**当前解决方案中的项目**，然后设置**项目**到**RegExLangServ**。  
  
    -   保存并关闭文件。  
  
11. 生成解决方案。 生成的文件部署到**%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**。  
  
12. 开始调试。 打开 Visual Studio 的第二个实例。  
  
## <a name="see-also"></a>另请参阅  
 [旧版语言服务扩展性](../../extensibility/internals/legacy-language-service-extensibility.md)