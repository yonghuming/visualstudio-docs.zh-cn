---
title: "演练：在 VSTO 外接程序项目中绑定到服务中的数据 | Microsoft Docs"
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
  - "数据库 [Visual Studio 中的 Office 开发]，滚动记录"
  - "记录 [Visual Studio 中的 Office 开发]，滚动"
  - "数据 [Visual Studio 中的 Office 开发]，滚动数据库记录"
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 演练：在 VSTO 外接程序项目中绑定到服务中的数据
  可以将数据绑定到 VSTO 外接程序项目中的宿主控件。 本演练演示如何在运行时将控件添加到 Microsoft Office Word 文档中、将控件绑定到从 MSDN Content Service 检索到的数据以及响应事件。  
  
 **适用于：**本主题中的信息适用于 Word 2010 的应用程序级项目。 有关更多信息，请参见[按 Office 应用程序和项目类型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。  
  
 本演练阐释了以下任务：  
  
-   在运行时将 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 控件添加到文档中。  
  
-   将 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 控件绑定到 Web 服务中的数据。  
  
-   响应 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 控件的 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> 事件。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 创建新项目  
 第一步是创建 Word VSTO 外接程序项目。  
  
#### 创建新项目  
  
1.  使用 Visual Basic 或 C\# 创建一个名为 **MTPS Content Service** 的 Word VSTO 外接程序项目。  
  
     有关详细信息，请参阅[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 会打开 `ThisAddIn.vb` 或 `ThisAddIn.cs` 文件并将项目添加到“解决方案资源管理器”中。  
  
## 添加 Web 服务  
 对于本演练，请使用名为 MTPS Content Service 的 Web 服务。 此 Web 服务以 XML 字符串或纯文本的形式返回指定 MSDN 文章中的信息。 下一步演示如何在内容控件中显示返回的信息。  
  
#### 将 MTPS Content Service 添加到项目中  
  
1.  在**“数据”**菜单上，单击**“添加新数据源”**。  
  
2.  在“数据源配置向导”中单击“服务”，再单击“下一步”。  
  
3.  在“地址”字段中键入下面的 URL：  
  
     **http:\/\/services.msdn.microsoft.com\/ContentServices\/ContentService.asmx**  
  
4.  单击**“转到”**。  
  
5.  在“命名空间”字段中键入“ContentService”，再单击“确定”。  
  
6.  在“添加引用向导”对话框中单击“完成”。  
  
## 在运行时添加内容控件并绑定到数据  
 在 VSTO 外接程序项目中，在运行时添加和绑定控件。 对于本演练，请将内容控件配置为当用户在该控件内单击时检索 Web 服务中的数据。  
  
#### 添加内容控件并绑定到数据  
  
1.  在 `ThisAddIn` 类中，分别为 MTPS Content Service、内容控件和数据绑定声明变量。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#2)]  
  
2.  将以下方法添加到 `ThisAddIn` 类。 此方法会在活动文档的开始处创建一个内容控件。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#4)]  
  
3.  将以下方法添加到 `ThisAddIn` 类。 此方法会初始化需要创建的对象并向 Web 服务发送一个请求。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#6)]  
  
4.  创建一个事件处理程序，当用户在内容控件内单击时检索有关内容控件的 MSDN Library 文档，并将数据绑定到内容控件。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#5)]  
  
5.  从 `ThisAddIn_Startup` 方法调用 `AddRichTextControlAtRange` 和 `InitializeServiceObjects` 方法。 对于 C\# 程序员，添加一个事件处理程序。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#3)]  
  
## 测试外接程序  
 打开 Word 后，<xref:Microsoft.Office.Tools.Word.RichTextContentControl> 控件会随即显示。 当在该控件内单击时，该控件中的文本会发生变化。  
  
#### 若要测试 VSTO 外接程序  
  
1.  按 F5。  
  
2.  在内容控件内单击。  
  
     随即从 MTPS Content Service 下载信息并将信息显示在内容控件中。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  