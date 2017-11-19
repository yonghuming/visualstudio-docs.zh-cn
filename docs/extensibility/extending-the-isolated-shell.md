---
redirect_url: shell/extending-the-isolated-shell
title: "扩展独立的 Shell |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ebd219beb28fc183d876e0391192390da03f8ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-isolated-shell"></a>扩展独立的 Shell
你可以通过将 VSPackage、 Managed Extensibility Framework (MEF) 组件过程中或泛型的 VSIX 项目添加到你的独立的 shell 应用程序扩展 Visual Studio 独立 shell。  
  
> [!NOTE]
>  以下步骤 presuppose 通过使用 Visual Studio Shell 隔离的项目模板创建了一个基本的独立的 shell 应用程序。 有关此项目模板的详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 包项目模板的位置  
 可在“新建项目”  对话框中的三个不同位置找到 Visual Studio 包项目模板：  
  
1.  下**Visual Basic**，**扩展性**。 项目的默认语言为 Visual Basic。  
  
2.  下**Visual C#**，**扩展性**。 项目的默认语言为 C#。  
  
3.  下**其他项目类型**，**扩展性**。 项目的默认语言为 C++。  
  
## <a name="adding-a-vspackage"></a>添加 VSPackage  
 可以将 VSPackage 添加到你的独立的 shell 应用程序。 以下步骤演示如何创建一个添加菜单命令。  
  
#### <a name="to-add-a-new-vspackage"></a>若要添加新的 VSPackage  
  
1.  添加一个名为的 Visual Studio 包项目`MenuCommandsPackage`。  
  
2.  上**基本 VSPackage 信息**页的向导中，设置**公司名称**到`Fabrikam`和**VSPackage 名称**到`FabrikamMenuCommands`。 选择**下一步**按钮。  
  
3.  在下一页上，选择**菜单命令**，然后选择**下一步**。  
  
4.  在下一页上，设置**命令名称**到`Fabrikam Command`和**命令 ID**到`cmdidFabrikamCommand`，然后选择**下一步**。  
  
5.  上**选择测试项目选项**页上，清除测试选项，然后选择**完成**按钮。  
  
6.  在 ShellExtensionsVSIX 项目中，打开 source.extension.vsixmanifest 文件。  
  
     **资产**部分应包含 VSShellStub.AboutBoxPackage 项目的条目。  
  
7.  选择**新建**按钮。  
  
8.  在**添加新资产**窗口，请在**类型**列表中，选择**Microsoft.VisualStudio.VsPackage**。  
  
9. 在**源**列表中，请确保**当前解决方案中的项目**选择。 在**项目**列表框中，选择**MenuCommandsPackage**。  
  
10. 保存并关闭文件。  
  
11. 重新生成解决方案并启动调试独立的 shell。  
  
12. 在菜单栏上，选择**工具**菜单，然后**Fabrikam 命令**。  
  
     应出现一个消息框。  
  
13. 停止调试应用程序。  
  
## <a name="adding-a-mef-component-part"></a>添加某一 MEF 组件部分  
 以下步骤显示如何将某一 MEF 组件部分添加到你的独立的 shell 应用程序。  
  
#### <a name="to-add-a-mef-component"></a>若要添加一个 MEF 组件  
  
1.  在**添加新项目**对话框中，在**Visual C#**，**扩展性**，使用**编辑器边距**模板中添加项目。 将其命名为 `ShellEditorMargin`。  
  
2.  在 ShellExtensionsVSIX 项目中，打开 Source.extension.vsixmanifest 文件中的在设计视图中，不是代码视图。  
  
3.  在`Asset`部分中，选择**添加内容**。  
  
4.  在**添加新资产**窗口，请在**类型**列表中，选择**Microsoft.VisualStudio.MefComponent**。  
  
5.  在**源**列表中，请确保**当前解决方案中的项目**选择。 在**项目**列表框中，选择**ShellEditorMargin**。  
  
6.  保存并关闭文件。  
  
7.  重新生成解决方案并启动调试独立的 shell。  
  
8.  打开一个文本文件。  
  
     绿色边距，其中包含单词"Hello world ！" 应显示在文本文件窗口的底部。  
  
9. 停止调试应用程序。  
  
## <a name="adding-a-generic-vsix-project"></a>添加泛型 VSIX 项目  
  
#### <a name="to-add-a-generic-vsix-project"></a>若要添加的一般的 VSIX 项目  
  
1.  在**添加新项目**对话框中，在**Visual C#**，**扩展性**，使用**VSIXProject**模板中添加项目。 将其命名为 `EmptyVSIX`。  
  
2.  在 ShellExtensionsVSIX 项目中，打开设计视图中，不是代码视图中的 Source.extensions.vsixmanifest 文件。  
  
3.  在`Assets`部分中，选择**新建**。  
  
4.  在**添加新资产**窗口，请在**类型**列表中，选择你想要添加的内容的类型。  
  
5.  在**源**，请确保**当前解决方案中的项目**选项。 列表框中，选择你的 VSIX 项目的名称。  
  
6.  保存并关闭文件。  
  
7.  如果此项目包含已编译的代码，则必须编辑项目，以便在输出中包括程序集。  
  
    1.  卸载该 VSIX 项目并打开项目文件。  
  
    2.  在第一个`<PropertyGroup>`块中，更改的值`<CopyBuildOutputToOutputDirectory>`到`true`。  
  
    3.  保存并重新加载项目。  
  
8.  生成和运行解决方案。  
  
## <a name="see-also"></a>另请参阅  
 [演练：创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)