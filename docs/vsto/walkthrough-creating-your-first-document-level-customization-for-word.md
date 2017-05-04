---
title: "演练：创建您的第一个 Word 文档级自定义项 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "文档级自定义项 [Visual Studio 中的 Office 开发], 创建您的第一个项目"
  - "Visual Studio 中的 Office 开发, 创建您的第一个项目"
  - "Word [Visual Studio 中的 Office 开发], 创建您的第一个项目"
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 演练：创建您的第一个 Word 文档级自定义项
  本介绍性演练演示了如何创建 Microsoft Office Word 的文档级自定义项。  仅在特定文档处于打开状态时，才可提供你在这种解决方案中创建的功能。  不能使用文档级自定义项进行应用程序范围的更改，例如在任何文档处于打开状态时显示新“功能区”选项卡。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   创建 Word 文档项目。  
  
-   将文本添加到 Visual Studio 设计器中托管的文档。  
  
-   编写代码，使用 Word 对象模型在自定义文档时打开时向其中添加文本。  
  
-   生成并运行项目，以对其进行测试。  
  
-   清理项目，以便从开发计算机删除不必要的生成文件和安全设置。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## 创建项目  
  
#### 在 Visual Studio 中创建新的 Word 文档项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在**“文件”**菜单上，指向**“新建”**，然后单击**“项目”**。  
  
3.  在模板窗格中，展开**“Visual C\#”**或**“Visual Basic”**，然后展开**“Office\/SharePoint”**。  
  
4.  在展开的**“Office\/SharePoint”**节点下方，选择**“Office 外接程序”**节点。  
  
5.  在项目模板列表中，选择 Word VSTO 文档项目。  
  
6.  在**“名称”**框中，键入 **FirstDocumentCustomization**。  
  
7.  单击“确定”。  
  
     将打开“Visual Studio Tools for Office 项目向导”。  
  
8.  选择**“创建新文档”**，然后单击**“确定”**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 创建 **FirstDocumentCustomization** 项目，并将 **FirstDocumentCustomization** 文档和 ThisDocument 添加到项目的代码文件。  **FirstDocumentCustomization** 文档将在设计器中自动打开。  
  
## 关闭并重新打开设计器中的文档  
 如果开发项目时有意或无意关闭了设计器中的文档，则可以重新打开它。  
  
#### 若要关闭并重新打开设计器中的文档  
  
1.  通过单击设计器窗口的**“关闭”**\(X\) 按钮关闭文档。  
  
2.  在**“解决方案资源管理器”**中，右键单击**“ThisDocument”**代码文件，然后单击**“查看设计器”**。  
  
     \- 或 \-  
  
     在**“解决方案资源管理器”**中，双击**“ThisDocument.vb”**代码文件。  
  
## 向设计器中的文档添加文本  
 可以通过修改在设计器中打开的文档来设计自定义的用户界面 \(UI\)。  例如，可以添加文本、表格或 Word 控件。  有关如何使用设计器的详细信息，请参阅 [Visual Studio 环境中的 Office 项目](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
#### 使用设计器将文本添加到文档  
  
1.  在已在设计器中打开的文档中键入以下文本。  
  
     **This text was added by using the designer.**  
  
## 以编程方式向文档添加文本  
 接下来，将代码添加到 ThisDocument 代码文件。  新代码使用 Word 对象模型向文档添加文本的第二个段落。  默认情况下，ThisDocument 代码文件包含以下生成的代码：  
  
-   `ThisDocument` 类的部分定义，用于表示文档的编程模型，并提供对 Word 对象模型的访问权限。  有关详细信息，请参阅[文档宿主项](../vsto/document-host-item.md)和 [Word 对象模型概述](../vsto/word-object-model-overview.md)。  `ThisDocument` 类的其余部分是在隐藏代码文件中定义的，不应修改该代码文件。  
  
-   `ThisDocument_Startup` 和 `ThisDocument_Shutdown` 事件处理程序。  将在打开或关闭文档时调用这些事件处理程序。  使用这些事件处理程序，可在打开文档时对其进行初始化，并在关闭文档时清理自定义项所使用的资源。  有关详细信息，请参阅 [Office 项目中的事件](../vsto/events-in-office-projects.md)。  
  
#### 若要使用代码向文档添加文本的第二个段落  
  
1.  在**“解决方案资源管理器”**中右键单击**“ThisDocument”**，然后单击**“查看代码”**。  
  
     将在 Visual Studio 中打开代码文件。  
  
2.  将 `ThisDocument_Startup` 事件处理程序替换为以下代码。  当打开文档时，此代码会将文本第二个段落添加到文档中。  
  
     [!code-csharp[Trin_WordDocumentTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_WordDocumentTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/VB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  此代码使用索引值 1 来访问 <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> 属性的第一个段落。  尽管 Visual Basic 和 Visual C\# 使用从 0 开始的数组，但 Word 对象模型中大多数集合的数组下限都是 1。  有关详细信息，请参阅[在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)。  
  
## 测试项目  
  
#### 测试文档  
  
1.  按 **F5** 生成并运行项目。  
  
     生成项目时，会将代码编译到与该文档相关联的程序集中。  Visual Studio 将该文档和程序集的副本放入项目的生成输出文件夹中，并将开发计算机上的安全设置配置为允许自定义项运行。  有关详细信息，请参阅 [生成 Office 解决方案](../vsto/building-office-solutions.md)。  
  
2.  验证文档中具有以下文本。  
  
     **This text was added by using the designer.**  
  
     **This text was added by using code.**  
  
3.  关闭文档。  
  
## 清理项目  
 完成项目开发后，应删除生成输出文件夹中的文件和由生成过程创建的安全设置。  
  
#### 在开发计算机上清理已完成的项目  
  
1.  在 Visual Studio 中，在**“生成”**菜单上，单击**“清理解决方案”**。  
  
## 后续步骤  
 既然你已经创建了一个基本的 Word 文档级自定义项，你就可以从下面这些主题中了解有关如何开发自定义项的详细信息：  
  
-   可以在文档级自定义项中执行的常规编程任务：[对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)。  
  
-   特定于 Word 文档级自定义项的编程任务：[Word 解决方案](../vsto/word-solutions.md)。  
  
-   使用 Word 的对象模型：[Word 对象模型概述](../vsto/word-object-model-overview.md)。  
  
-   自定义 Word 的 UI，例如通过向功能区添加自定义选项卡或创建自己的操作窗格：[Office UI 自定义](../vsto/office-ui-customization.md)。  
  
-   使用由 Visual Studio 中的 Office 解决方案提供的扩展 Word 对象，执行无法通过使用 Word 对象模型执行的任务（例如，在文档上承载托管的控件以及使用 Windows 窗体数据绑定模型将 Word 控件绑定到数据）：[使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)。  
  
-   生成和调试 Word 文档级自定义项：[生成 Office 解决方案](../vsto/building-office-solutions.md)。  
  
-   部署 Word 文档级自定义项：[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
## 请参阅  
 [Office 解决方案开发概述 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word 解决方案](../vsto/word-solutions.md)   
 [对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)   
 [Word 对象模型概述](../vsto/word-object-model-overview.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [Office UI 自定义](../vsto/office-ui-customization.md)   
 [生成 Office 解决方案](../vsto/building-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [Office 项目模板概述](../vsto/office-project-templates-overview.md)  
  
  