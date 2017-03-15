---
title: "将“用户控件”置于“工具窗口”中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具窗口, 添加用户控件"
  - "用户控件 [Visual Studio SDK], 添加到工具窗口"
  - "用户控件 [Visual Studio SDK]"
ms.assetid: 869f3195-e152-4e61-802c-51d6b7ba3e36
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# 将“用户控件”置于“工具窗口”中
本演练演示了如何将用户控件添加到工具窗口。  
  
 用户控件是一同绑定在某个控件中的 Windows 控件的集合。 若要将用户控件添加到工具窗口，你实际只需让用户控件在“工具箱”中显示。 本演练中所用的用户控件是在[演练：使用 Visual C\# 创作复合控件](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)中开发的时钟控件。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 创建用户控件  
  
1.  请按照[演练：使用 Visual C\# 创作复合控件](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)中的步骤创建时钟控件。 不要创建闹钟控件。  
  
> [!NOTE]
>  以下步骤假定你已将时钟控件命名为 `ctlClock`。  
  
## 创建工具窗口扩展  
  
1.  创建一个名为 `MyToolWindowPackageUC` 的 VSIX 项目，其具有名为 `MyToolWindow` 的工具窗口。 如果你在执行此操作时需要帮助，请参阅[使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## 添加用户控件  
  
1.  在“解决方案资源管理器”中，右键单击“MyToolWindowPackageUC”解决方案，指向“添加”，然后单击“现有项目”。  
  
2.  在“添加现有项目”对话框中，打开 ctlClockLib 项目并选择 ctlClock.lib.csproj 项目文件。 单击“确定”。 这将启用可在设计器中使用的用户控件。  
  
3.  在“解决方案资源管理器”中，右键单击“MyToolWindowControl.cs”并选择“视图设计器”。 这将打开窗体设计器，其中显示为工具窗口生成的控件。  
  
4.  打开“工具箱”，找到标记为“ctlClockLib 组件”的部分，然后单击此部分中的“ctlClock”控件，以将控件添加到窗体中。 在隐藏“工具箱”后，会立即看到工具窗口窗体中显示有时间。  
  
5.  在设计器中，选择刚添加的时钟控件，并将“定位点”属性更改为只在“顶部”。  
  
6.  在“解决方案资源管理器”中，右键单击 ctlClockLib 项目节点，然后单击“属性”。  
  
7.  在“签名”选项卡上，选择“为程序集签名”。 在“选择强名称密钥文件”框中，单击“\<浏览\>”，并导航到“MyToolWindowPackageUC”项目文件夹中的 key.snk 文件。  
  
8.  编译此程序，并确保没有任何错误。 此步骤使用 Visual Studio 注册 VSPackage 及其工具窗口。  
  
9. 按“F5”，在实验性配置单元中打开 Visual Studio 的实例。  
  
10. 在实验性 Visual Studio 的“视图”菜单上，指向“其他窗口”，然后单击“MyToolWindow”。 这将显示出现运行时间的工具窗口。  
  
## 请参阅  
 [演练：使用 Visual C\# 创作复合控件](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)