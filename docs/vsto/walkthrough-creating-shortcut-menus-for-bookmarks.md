---
title: "演练：创建书签的快捷菜单"
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
  - "Bookmark 控件, 事件"
  - "上下文菜单, Word"
  - "菜单, 在 Office 应用程序中创建"
  - "快捷菜单, Word"
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 演练：创建书签的快捷菜单
  本演练演示如何在 Word 的文档级自定义项中创建 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件的快捷菜单。  用户右击书签中的文本时，将出现一个快捷菜单，它为用户提供用于设置文本格式的选项。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   [创建项目](#BKMK_CreateProject)。  
  
-   [向文档中添加文本和书签](#BKMK_addtextandbookmarks)。  
  
-   [将命令添加到快捷菜单](#BKMK_AddCmndsShortMenu)。  
  
-   [设置书签文本格式](#BKMK_formattextbkmk)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> 创建项目  
 第一步是在 Visual Studio 中创建 Word 文档项目。  
  
#### 创建新项目  
  
-   创建一个名为“我的书签快捷菜单”的 Word 文档项目。  在向导中，选择**“创建新文档”**。  有关详细信息，请参阅 [如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开一个新的 Word 文档，并将**“我的书签快捷菜单”**项目添加到**“解决方案资源管理器”**中。  
  
##  <a name="BKMK_addtextandbookmarks"></a> 向文档中添加文本和书签  
 向文档中添加一些文本，然后添加两个重叠书签。  
  
#### 向文档中添加文本  
  
-   中显示您的项目设计器的文档，请键入以下文本。  
  
     这是一个示例，将演示如何创建一个在右击书签中的文本时出现的快捷菜单。  
  
#### 向文档中添加 Bookmark 控件  
  
1.  在 **工具箱**，从 **Word 控件** 选项，则的一个 <xref:Microsoft.Office.Tools.Word.Bookmark> 添加宿主控件拖动。  
  
     将出现**“添加书签控件”**对话框。  
  
2.  选择“创建快捷菜单的单词，当您右击该文本”，则单击 **确定**。  
  
     `bookmark1` 便被添加到文档中。  
  
3.  添加另一个 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件添加到文字“中右击书签中的文本”。  
  
     `bookmark2` 便被添加到文档中。  
  
    > [!NOTE]  
    >  运行“右击该文本”在 `bookmark1` 和 `bookmark2`。  
  
 在设计时向文档中添加书签时，将创建一个 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。  可以对一些书签事件进行编程。  可以在书签的 <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> 事件中编写代码，以便在用户右击书签中的文本时出现一个快捷菜单。  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> 将命令添加到快捷菜单  
 将按钮添加到显示的快捷菜单，当您右击文档。  
  
#### 将命令添加到快捷菜单  
  
1.  添加一个 **功能区 XML** 项添加到项目中。  有关详细信息，请参阅 [如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在 **解决方案资源管理器**，选择 **ThisDocument.cs** 或 **ThisDocument.vb**。  
  
3.  在菜单栏上，依次选择 **视图**，**代码**。  
  
     **ThisDocument** 选件类文件将在代码编辑器中打开。  
  
4.  将以下代码添加到 **ThisDocument** 选件类。  这段代码重写 CreateRibbonExtensibilityObject 方法，将功能区 XML 类返回给 Office 应用程序。  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#1)]  
  
5.  在 **解决方案资源管理器**，选择功能区 XML 文件。  默认情况下，功能区 XML 文件名为 Ribbon1.xml。  
  
6.  在菜单栏上，依次选择 **视图**，**代码**。  
  
     功能区 XML 文件将在代码编辑器中打开。  
  
7.  在代码编辑器中，用以下代码替换功能区 XML 文件的内容。  
  
    ```  
  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     此代码添加两个按钮。显示的快捷菜单，当您右击文档。  
  
8.  在**“解决方案资源管理器”**中，右击 `ThisDocument`，然后单击**“查看代码”**。  
  
9. 声明以下变量和书签变量在选件类级别。  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#2)]  
  
10. 在 **解决方案资源管理器**，选择功能区代码文件。  默认情况下，功能区代码文件名为 **Ribbon1.cs** 或 **Ribbon1.vb**。  
  
11. 在菜单栏上，依次选择 **视图**，**代码**。  
  
     功能区代码文件会在代码编辑器中打开。  
  
12. 在功能区代码文件中，添加以下方法。  这是添加到文档的快捷菜单的两个按钮一个回调方法。  此方法确定这些按钮是否显示在快捷菜单。  只有 \+ 当您右击在书签中，的文本以粗体和斜体的按钮显示。  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> 设置书签文本格式  
  
#### 设置书签中文本的格式  
  
1.  在功能区代码文件中，添加一个 `ButtonClick` 事件处理程序将格式应用于书签。  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#6)]  
  
2.  **解决方案资源管理器**、选择 **ThisDocument.cs** 或 **ThisDocument.vb**。  
  
3.  在菜单栏上，依次选择 **视图**，**代码**。  
  
     **ThisDocument** 选件类文件将在代码编辑器中打开。  
  
4.  将以下代码添加到 **ThisDocument** 选件类。  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  必须编写代码来处理书签重叠的情况。  否则，默认情况下将为所选内容中的所有书签调用代码。  
  
5.  在 C\# 中，必须将书签控件的事件处理程序添加到 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。  有关创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#4)]  
  
## 测试应用程序  
 测试文档验证粗体和斜体的菜单项显示在快捷菜单上，在中右击书签中的文本，并且文本格式正确。  
  
#### 测试文档  
  
1.  按 F5 运行项目。  
  
2.  右击第一个书签，然后单击**“粗体”**。  
  
3.  验证 `bookmark1` 中的所有文本是否都已设置为粗体格式。  
  
4.  右击书签重叠处的文本，然后单击**“斜体”**。  
  
5.  验证 `bookmark2` 中的所有文本是否为斜体，并验证与 `bookmark2` 重叠的 `bookmark1` 中是否只有部分文本为斜体。  
  
## 后续步骤  
 以下是接下来可能要执行的一些任务：  
  
-   编写代码以响应 Excel 中的宿主控件事件。  有关详细信息，请参阅 [演练：根据 NamedRange 控件的事件进行编程](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)。  
  
-   使用复选框更改书签中的格式设置。  有关详细信息，请参阅 [演练：使用 CheckBox 控件更改文档格式设置](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
## 请参阅  
 [使用 Word 的演练](../vsto/walkthroughs-using-word.md)   
 [Office UI 自定义](../vsto/office-ui-customization.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark 控件](../vsto/bookmark-control.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  