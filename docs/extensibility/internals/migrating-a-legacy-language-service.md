---
title: "迁移早期语言服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语言服务迁移"
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 迁移早期语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

你可以通过更新项目并向项目中添加源 source.extension.vsixmanifest 文件迁移到更高版本的 Visual Studio 的遗留语言服务。 语言服务本身将继续像以前一样，因为 Visual Studio 编辑器中采用它。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方法的详细信息，请参阅 [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## 迁移到更高版本的 Visual Studio 2008 语言服务解决方案  
 以下步骤演示如何改编名为 RegExLanguageService 的 Visual Studio 2008 示例。 您可以找到此示例在 Visual Studio 2008 SDK 安装中，在 *Visual Studio SDK 安装路径*\\VisualStudioIntegration\\Samples\\IDE\\CSharp\\Example.RegExLanguageService\\ 文件夹。  
  
> [!IMPORTANT]
>  如果您的语言服务没有定义颜色，必须显式设置 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> 到 `true` VSPackage 上︰  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### 若要将 Visual Studio 2008 语言服务迁移到更高版本  
  
1.  安装 Visual Studio 和 Visual Studio SDK 的较新版本。 有关如何安装 SDK 的详细信息，请参阅 [安装 Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md)。  
  
2.  编辑 RegExLangServ.csproj 文件 （而无需在 Visual Studio 中加载它。  
  
     在 `Import` 引用 Microsoft.VsSDK.targets 文件的节点值替换为以下文本。  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  保存该文件，然后将其关闭。  
  
4.  打开 RegExLangServ.sln 解决方案。  
  
5.  **单向升级** 显示窗口。 单击“确定”。  
  
6.  更新的项目属性。 打开 **项目属性** 窗口，通过选择中的项目节点 **解决方案资源管理器**, 、 右键单击，然后选择 **属性**。  
  
    -   在 **应用程序** 选项卡上，更改 **目标框架** 到 **4.6.1**。  
  
    -   在 **调试** 选项卡上，在 **启动外部程序** 框中，键入 **\< Visual Studio 安装路径 \> \\Common7\\IDE\\devenv.exe。**。  
  
         在 **命令行参数** 框中，键入 \/**rootsuffix Exp**。  
  
7.  更新以下引用︰  
  
    -   删除对 Microsoft.VisualStudio.Shell.9.0.dll 的引用，然后添加对 Microsoft.VisualStudio.Shell.14.0.dll 和 Microsoft.VisualStudio.Shell.Immutable.11.0.dll 引用。  
  
    -   删除对 Microsoft.VisualStudio.Package.LanguageService.9.0.dll 的引用，然后添加对 Microsoft.VisualStudio.Package.LanguageService.14.0.dll 的引用。  
  
    -   添加对 Microsoft.VisualStudio.Shell.Interop.10.0.dll 的引用。  
  
8.  打开 VsPkg.cs 文件并将的值更改 `DefaultRegistryRoot` 属性设为  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. 原始示例不会注册其语言服务，服务，因此必须将以下属性添加到 VsPkg.cs。  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. 您必须添加源 source.extension.vsixmanifest 文件。  
  
    -   将此文件从现有扩展插件复制到您的项目目录。 \(若要获取此文件的一种方法是创建一个 VSIX 项目 \(在下 **文件**, ，请单击 **新建**, ，然后单击 **项目**。 在 Visual Basic 或 C\# 请单击 **扩展性**, ，则可以选择 **VSIX 项目**。\)  
  
    -   将文件添加到你的项目。  
  
    -   在文件的 **属性**, ，请设置 **生成操作** 到 **无**。  
  
    -   打开文件 **VSIX 清单编辑器中**。  
  
    -   更改以下字段︰  
  
    -   **ID**: RegExLangServ  
  
    -   **产品名称**: RegExLangServ  
  
    -   **说明**︰ 正则表达式语言服务。  
  
    -   在下 **资产**, ，单击 **新建**, ，选择 **类型** 到 **Microsoft.VisualStudio.VsPackage**, ，请设置 **源** 到 **当前解决方案中的项目**, ，然后设置 **项目** 到 **RegExLangServ**。  
  
    -   保存并关闭文件。  
  
11. 生成解决方案。 生成的文件部署到 **%USERPROFILE%\\AppData\\Local\\Microsoft\\VisualStudio\\14.0Exp\\Extensions\\MSIT\\ RegExLangServ\\**。  
  
12. 开始调试。 打开 Visual Studio 的第二个实例。  
  
## 请参阅  
 [遗留语言服务可扩展性](../../extensibility/internals/legacy-language-service-extensibility.md)