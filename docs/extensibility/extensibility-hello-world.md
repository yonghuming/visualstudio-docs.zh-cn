---
title: "Hello World |Microsoft 文档"
ms.custom: 
ms.date: 07/10/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18a0e18589574c689ebbddbaf28448cf5539ad96
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-your-first-extension-hello-world"></a>创建第一个扩展： Hello World

此 Hello World 示例将指导你完成为 Visual Studio 中创建第一个扩展。 本教程将演示如何将新的命令添加到 Visual Studio。

在此过程中，你将了解如何：

* **[创建一个扩展性项目](#create-an-extensibility-project)**
* **[添加自定义命令](#add-a-custom-command)**
* **[修改的源代码](#modify-the-source-code)**
* **[运行它](#run-it)**

对于此示例中，你将使用 Visual C# 来添加自定义菜单按钮名为"说出 Hello World ！" 如下所示：

![你好 world 命令](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>先决条件

在开始之前，请确保已安装**Visual Studio 扩展开发**包括 VSIX 模板将需要和示例代码的工作负荷。

注意： 你可以使用任何版本的 Visual Studio （Community、 Professional 或 Enterprise） 创建 Visual Studio 扩展性项目。

## <a name="create-an-extensibility-project"></a>创建一个扩展性项目

步骤 1。 从**文件**菜单上，单击**新项目**。 在屏幕的底部，可以输入你的项目的名称。

步骤 2。 从**模板**菜单上，单击**Visual C#**，单击**扩展性**，然后单击**VSIX 项目**。

![新建项目](media/hello-world-new-project.png)

你现在应看到的入门页和一些示例资源。

如果你需要将本教程中，返回到它，你可以在上找到新 HelloWorld 项目**起始页**中**最近**部分。

## <a name="add-a-custom-command"></a>添加自定义命令

步骤 1。 如果你选择的清单，你可以看到哪些选项都可更改，为实例、 元数据、 说明和版本。

步骤 2。 右键单击项目 （而不是解决方案）。 在上下文菜单上，单击**添加**，然后单击**用户控件**。

步骤 3。 返回到**扩展性**部分，并依次**自定义命令**。

步骤 4。 在**名称**底部字段中，为其提供一个名称，例如 Command.cs。

![自定义命令](media/hello-world-custom-command.png)

您的新命令将被列入**解决方案资源管理器**下**资源**分支。 这是你可以找到与你的命令，例如如果你想要修改映像 PNG 和 ICO 文件相关的其他文件。

## <a name="modify-the-source-code"></a>修改的源代码

此时，你要添加的按钮为非常泛型。 你将需要修改的 VSCT 文件和 CS 文件，如果你想要进行更改。

* VSCT 文件是其中你可以重命名你的命令，以及定义目的地 Visual Studio 命令系统中。 你浏览的 VSCT 文件，你将注意到大量的注释说明哪些每个部分代码控制的代码。

* CS 文件是你可以在其中定义操作，如 click 处理程序。

步骤 1。 在**解决方案资源管理器**，找到您的新命令的 VSCT 文件。 在这种情况下，它将调用 CommandPackage.vsct。

![命令包 vsct](media/hello-world-command-package-vsct.png)

步骤 2。 更改`ButtonText`"说出 Hello World ！"的参数

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

步骤 3。 返回到**解决方案资源管理器**，查找 Command.cs 文件。 更改字符串`message`命令`string.Format(..)`到"Hello World ！"

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

请确保将所做的更改保存到每个文件。

## <a name="run-it"></a>运行它

你现在可以在 Visual Studio 实验实例中运行的源代码。

步骤 1。 单击**启动**工具栏中。 这将生成项目并启动调试器，启动调用的 Visual Studio 的新实例**实验实例**。

你将看到在 Visual Studio 标题栏中的"实验实例"一词。

![实验实例标题栏](media/hello-world-exp-instance.png)

步骤 2。 上**工具**菜单**实验实例**，单击**Say Hello World ！**。

![最终结果](media/hello-world-final-result.png)

您应从您的新自定义命令，在这种情况下在中心对话框为你提供"Hello World ！"的屏幕中看到的输出 消息。

## <a name="next-steps"></a>后续步骤

既然你知道使用 Visual Studio 扩展性的基础知识，下面是可以从何处了解详细信息：

* [开始开发 Visual Studio 扩展到](starting-to-develop-visual-studio-extensions.md)的示例，教程。 和发布你的扩展。
* [What's New in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -Visual Studio 自 2017 年中的新扩展功能
* [在 Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -了解 Visual Studio 扩展性的详细信息