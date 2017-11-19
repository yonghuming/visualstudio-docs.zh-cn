---
title: "演练： 创建书签的快捷菜单 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: "57"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8dbb248fdaab10aaef6146ae68e36a64b60bb453
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-shortcut-menus-for-bookmarks"></a>演练：创建书签的快捷菜单
  本演练演示如何创建快捷菜单<xref:Microsoft.Office.Tools.Word.Bookmark>Word 的文档级自定义项中的控件。 用户右键单击在书签中的文本，快捷菜单将显示，且提供了用于设置文本格式的用户选项。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   [创建项目](#BKMK_CreateProject)。  
  
-   [向文档添加文本和书签](#BKMK_addtextandbookmarks)。  
  
-   [将命令添加到快捷菜单](#BKMK_AddCmndsShortMenu)。  
  
-   [设置在书签中的文本格式](#BKMK_formattextbkmk)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a>创建项目  
 第一步是在 Visual Studio 中创建的 Word 文档项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
-   创建同名的 Word 文档项目**我书签的快捷菜单**。 在向导中，选择**创建新文档**。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Word 文档和添加**我书签的快捷菜单**项目合并为**解决方案资源管理器**。  
  
##  <a name="BKMK_addtextandbookmarks"></a>向文档添加文本和书签  
 向文档添加一些文本，然后再添加两个重叠书签。  
  
#### <a name="to-add-text-to-your-document"></a>若要向文档添加文本  
  
-   在文档中显示在你项目的设计器中，键入以下文本。  
  
     **这是创建快捷菜单上，右键单击在书签中的文本时的示例。**  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>若要向文档添加书签控件  
  
1.  在**工具箱**，从**Word 控件**选项卡上，拖动<xref:Microsoft.Office.Tools.Word.Bookmark>到您的文档的控制。  
  
     **添加书签控件**对话框随即出现。  
  
2.  选择"创建快捷菜单，右键单击文本时"的单词，然后单击**确定**。  
  
     `bookmark1`将添加到文档。  
  
3.  添加另一个<xref:Microsoft.Office.Tools.Word.Bookmark>控制对单词"右键单击在书签中的文本"。  
  
     `bookmark2`将添加到文档。  
  
    > [!NOTE]  
    >  "右击的文本"会同时出现在单词`bookmark1`和`bookmark2`。  
  
 当在设计时向文档添加书签<xref:Microsoft.Office.Tools.Word.Bookmark>创建控件。 你可用于编程的书签的多个事件。 你可以在编写代码<xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>事件的书签，以便当用户右键单击书签的地方中的文本将出现快捷菜单。  
  
##  <a name="BKMK_AddCmndsShortMenu"></a>将命令添加到快捷菜单  
 向右键单击该文档时，将出现的快捷菜单添加按钮。  
  
#### <a name="to-add-commands-to-a-shortcut-menu"></a>将命令添加到快捷菜单  
  
1.  添加**功能区 XML**到项目的项。 有关详细信息，请参阅 [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在**解决方案资源管理器**，选择**ThisDocument.cs**或**ThisDocument.vb**。  
  
3.  在菜单栏上，依次选择 **“视图”**、 **“代码”**。  
  
     **ThisDocument**类文件随即在代码编辑器中打开。  
  
4.  以下代码添加到**ThisDocument**类。 此代码重写 CreateRibbonExtensibilityObject 方法，并返回到 Office 应用程序的功能区 XML 类。  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  在“解决方案资源管理器” 中，选择功能区 XML 文件。 默认情况下，功能区 XML 文件命名为 Ribbon1.xml。  
  
6.  在菜单栏上，依次选择 **“视图”**、 **“代码”**。  
  
     功能区 XML 文件随即在代码编辑器中打开。  
  
7.  在代码编辑器中，将功能区 XML 文件的内容替换为以下代码。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
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
  
     此代码将两个按钮添加到的快捷菜单中右键单击该文档时，将出现。  
  
8.  在**解决方案资源管理器**，右键单击`ThisDocument`，然后单击**查看代码**。  
  
9. 声明以下变量和在类级别的书签变量。  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. 在**解决方案资源管理器**，选择功能区代码文件。 默认情况下，功能区代码文件命名为**Ribbon1.cs**或**Ribbon1.vb**。  
  
11. 在菜单栏上，依次选择 **“视图”**、 **“代码”**。  
  
     功能区代码文件将在代码编辑器中打开。  
  
12. 在功能区代码文件中，添加以下方法。 这是已添加到文档的快捷菜单的两个按钮的回叫方法。 此方法可确定这些按钮是否出现在快捷菜单。 仅当您右键单击该书签中的文本，将显示加粗和倾斜按钮。  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a>设置在书签中的文本格式  
  
#### <a name="to-format-the-text-in-the-bookmark"></a>若要设置格式在书签中的文本  
  
1.  在功能区代码文件中，添加`ButtonClick`事件处理程序来将格式应用于该书签。  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **解决方案资源管理器**，选择**ThisDocument.cs**或**ThisDocument.vb**。  
  
3.  在菜单栏上，依次选择 **“视图”**、 **“代码”**。  
  
     **ThisDocument**类文件随即在代码编辑器中打开。  
  
4.  以下代码添加到**ThisDocument**类。  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  你必须编写代码以处理书签重叠的情况。 如果不希望这样做，默认情况下，代码将调用所选内容中的所有书签中。  
  
5.  必须在 C# 中，添加事件处理程序的书签控件<xref:Microsoft.Office.Tools.Word.Document.Startup>事件。 有关创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 测试文档，以验证右键单击书签中的文本时，粗体和斜体菜单项将出现在快捷菜单和文本的格式正确。  
  
#### <a name="to-test-your-document"></a>测试文档  
  
1.  按 F5 运行项目。  
  
2.  在第一个书签中，右键单击，然后单击**加粗**。  
  
3.  验证所有中的文本`bookmark1`设置为粗体。  
  
4.  右键单击书签的重叠处的文本，然后单击**斜体**。  
  
5.  验证所有中的文本`bookmark2`为斜体，并只有的部分中的文本`bookmark1`重叠`bookmark2`为斜体。  
  
## <a name="next-steps"></a>后续步骤  
 以下是接下来可能要执行的一些任务：  
  
-   编写代码以响应在 Excel 中的主机控件的事件。 有关更多信息，请参见 [Walkthrough: Programming Against Events of a NamedRange Control](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)。  
  
-   使用复选框来更改格式设置在书签中。 有关详细信息，请参阅[演练： 更改文档格式使用复选框控件](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Word 的演练](../vsto/walkthroughs-using-word.md)   
 [Office UI 自定义项](../vsto/office-ui-customization.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark 控件](../vsto/bookmark-control.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  