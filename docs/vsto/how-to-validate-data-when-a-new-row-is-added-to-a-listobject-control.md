---
title: "如何：在向 ListObject 控件添加新行时验证数据 | Microsoft Docs"
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
  - "控件 [Visual Studio 中的 Office 开发]，验证数据"
  - "ListObject 控件，新行"
  - "ListObject 控件，验证数据"
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：在向 ListObject 控件添加新行时验证数据
  用户可以向绑定到数据的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加新行。 可以在将更改提交到数据源之前验证用户数据。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 数据验证  
 每当向绑定到数据的 <xref:Microsoft.Office.Tools.Excel.ListObject> 添加行时，便会引发 <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> 事件。 可以处理此事件以执行数据验证。 例如，如果应用程序要求只能向数据源添加年龄在 18 岁与 65 岁之间的员工，则可以在添加行之前验证输入的年龄是否处于该范围内。  
  
> [!NOTE]  
>  除了在客户端上，还应始终在服务器上检查用户输入。 有关详细信息，请参阅[安全客户端应用程序](http://msdn.microsoft.com/library/6239592e-fa7d-4dea-9f00-d296d0048b01)。  
  
#### 在向数据绑定 ListObject 添加新行时验证数据  
  
1.  在类级别为 ID 和 <xref:System.Data.DataTable> 创建变量。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#8)]  
  
2.  在 `Sheet1` 类（文档级项目中）或 `ThisAddIn` 类（VSTO 外接程序项目中）的 `Startup` 事件处理程序中创建一个新 <xref:System.Data.DataTable> 并添加示例列和数据。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#9)]  
  
3.  向 `list1_BeforeAddDataBoundRow` 事件处理程序添加代码以检查输入的年龄是否处于可接受的范围内。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#10)]  
  
## 编译代码  
 此代码示例假定在此代码出现的工作表中有一个名为 `list1` 的现有 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
## 请参阅  
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject 控件](../vsto/listobject-control.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何：将 ListObject 列映射到数据](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  