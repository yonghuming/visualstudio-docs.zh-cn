---
title: "文档级自定义项编程 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
ms.assetid: 6c421055-7bea-4db4-a4c9-539b8c78d4ee
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 68135e13a0e78e0250b087713ab459825018ff84
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="programming-document-level-customizations"></a>对文档级自定义项进行编程
  在使用文档级自定义项扩展 Microsoft Office Word 或 Microsoft Office Excel 时，可以执行以下任务：  
  
-   通过使用应用程序的对象模型对其进行自动化。  
  
-   向文档图面添加控件。  
  
-   从自定义程序集调用文档中的 Visual Basic for Applications (VBA) 代码。  
  
-   从 VBA 调用自定义程序集中的代码。  
  
-   在文档位于未安装 Microsoft Office 的服务器上时管理其特定方面。  
  
-   自定义应用程序的用户界面 (UI)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 在文档级项目中编写代码与在 Visual Studio 中编写其他类型项目的代码在某些方面存在不同。 其中许多差异是由 Office 对象模型公开给托管代码的方式引起的。 有关详细信息，请参阅 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)。  
  
 有关文档级自定义项和其他类型的解决方案可以通过使用 Visual Studio 中的 Office 开发工具创建的常规信息，请参阅[Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-generated-classes-in-document-level-projects"></a>使用文档级项目中生成的类  
 创建文档级项目时，Visual Studio 将在项目中自动生成一个可用开始编写代码的类。 Visual Studio 针对 Word 和 Excel 生成不同的类：  
  
-   在 Word 文档级项目中，默认情况下此类称为 `ThisDocument` 。  
  
-   Excel 文档级项目具有多个生成的类：一个用于工作簿本身，一个用于每一工作表。 默认情况下，这些类具有以下名称：  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 生成的类包含在打开或关闭文档时调用的事件处理程序。 若要在打开文档时运行代码，请将代码添加到 `Startup` 事件处理程序。 若要在关闭文档后立即运行代码，请将代码添加到 `Shutdown` 事件处理程序。 有关详细信息，请参阅 [Events in Office Projects](../vsto/events-in-office-projects.md)。  
  
### <a name="understanding-the-design-of-the-generated-classes"></a>了解生成的类的设计  
 在目标为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的项目中， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 中的宿主项类型为接口，因此生成的类不能从中派生其实现。 相反，生成的类从以下基类中派生其大多数成员：  
  
-   `ThisDocument`：派生自 <xref:Microsoft.Office.Tools.Word.DocumentBase>。  
  
-   `ThisWorkbook`：派生自 <xref:Microsoft.Office.Tools.Excel.WorkbookBase>。  
  
-   `Sheet` *n*：派生自 <xref:Microsoft.Office.Tools.Excel.WorksheetBase>。  
  
 这些基类将对其成员的所有调用重定向到 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]中相应宿主项接口的内部实现。 例如，如果你调用 <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> 类的 `ThisDocument` 方法，则 <xref:Microsoft.Office.Tools.Word.DocumentBase> 类将此调用重定向搭配 <xref:Microsoft.Office.Tools.Word.Document> 中的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]接口的内部实现。  
  
## <a name="accessing-the-object-model-of-the-host-application"></a>访问主机应用程序的对象模型  
 若要访问主机应用程序的对象模型，请在项目中使用生成的类的成员。 每个类均对应于 Excel 或 Word 对象模型中一个对象，并包含大多数相同的属性、方法和事件。 例如，Word 文档级别项目中的 `ThisDocument` 类提供与 Word 对象模型中的 <xref:Microsoft.Office.Interop.Word.Document> 对象所提供的大多数相同的成员。  
  
 以下代码示例演示如何使用 Word 对象模型来保存作为 Word 文档级自定义项的一部分的文档。 此示例应从 `ThisDocument` 类运行。  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 若要从 `ThisDocument` 类的外部执行相同操作，请使用 `Globals` 对象访问 `ThisDocument` 类。 例如，如果希望在操作窗格 UI 中包括“保存”  按钮，你可以将此代码添加到操作窗格代码文件中。  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 由于 `ThisDocument` 类从 <xref:Microsoft.Office.Tools.Word.Document> 宿主项中获取了其大多数成员，所以在此代码中调用的 `Save` 方法实际上是 <xref:Microsoft.Office.Tools.Word.Document.Save%2A> 宿主项的 <xref:Microsoft.Office.Tools.Word.Document> 方法。 此方法与 Word 对象模型中 <xref:Microsoft.Office.Interop.Word._Document.Save%2A> 对象的 <xref:Microsoft.Office.Interop.Word.Document> 方法相对应。  
  
 有关使用 Word 和 Excel 对象模型的详细信息，请参阅 [Word Object Model Overview](../vsto/word-object-model-overview.md) 和 [Excel Object Model Overview](../vsto/excel-object-model-overview.md)。  
  
 有关详细信息`Globals`对象，请参阅[对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)。  
  
## <a name="adding-controls-to-documents"></a>向文档添加控件  
 若要自定义文档的 UI，可以向文档图面添加 Windows 窗体控件或 *宿主控件* 。 通过组合不同的控件集并编写代码，可将控件绑定到数据、从用户处收集信息并响应用户操作。  
  
 宿主控件是用于扩展 Word 和 Excel 对象模型中某些对象的类。 例如， <xref:Microsoft.Office.Tools.Excel.ListObject> 宿主控件提供了 Excel 中的 <xref:Microsoft.Office.Interop.Excel.ListObject> 的所有功能。 但是， <xref:Microsoft.Office.Tools.Excel.ListObject> 宿主控件还具有其他事件和数据绑定功能。  
  
 有关详细信息，请参阅 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) 和 [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
## <a name="combining-vba-and-document-level-customizations"></a>结合 VBA 和文档级自定义项  
 可以在属于文档级自定义项的文档中使用 VBA 代码。 可以从自定义程序集文档中调用 VBA 代码，也可以将项目配置为使文档中的 VBA 代码能够调用自定义程序集中的代码。  
  
 有关更多信息，请参见 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)。  
  
## <a name="managing-documents-on-a-server"></a>在服务器上管理文档  
 你可以在未安装 Microsoft Office Word 或 Microsoft Office Excel 的服务器上管理文档级自定义项的几个不同方面。 例如，你可以访问和修改文档数据缓存中的数据。 还可以管理与文档相关联的自定义程序集。 例如，你可以以编程方式从文档中删除程序集以使该文档不再运行你的代码，或者以编程方式将程序集附加到文档。  
  
 有关详细信息，请参阅 [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>自定义 Microsoft Office 应用程序的用户界面  
 使用文档级自定义项，你可以通过下列方式自定义 Word 和 Excel 的 UI：  
  
-   向文档图面添加宿主控件或 Windows 窗体控件。  
  
     有关详细信息，请参阅 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)、 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)和 [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
-   将操作窗格添加到文档。  
  
     有关更多信息，请参见 [Actions Pane Overview](../vsto/actions-pane-overview.md)。  
  
-   向功能区添加自定义选项卡。  
  
     有关详细信息，请参阅[功能区概述](../vsto/ribbon-overview.md)。  
  
-   向功能区上的内置选项卡添加自定义组。  
  
     有关详细信息，请参阅 [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md)。  
  
 有关自定义 UI 的 Microsoft Office 应用程序的详细信息，请参阅[Office UI 自定义项](../vsto/office-ui-customization.md)。  
  
## <a name="getting-extended-objects-from-native-office-objects-in-document-level-customizations"></a>从文档级自定义项中的本机 Office 对象中获取扩展的对象  
 许多 Office 事件的事件处理程序可接受本机 Office 对象，这些对象表示工作簿、工作表或引发事件的文档。 在某些情况下，可能仅当工作簿或文档级自定义项中的文档引发事件时，才需要运行某些代码。 例如，在 Excel 文档级自定义项中，当用户激活自定义工作簿中的一个工作表时可能需要运行某些代码，而当用户激活当时恰好处于打开状态的其他工作簿中的工作表时则不运行。  
  
 具有本机 Office 对象时，你可以测试该对象是否已扩展为文档级自定义项中的 *宿主项* 或 *宿主控件* 。 宿主项和宿主控件是由 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 提供的类型，可向以本机方式存在于 Word 或 Excel 对象模型中的对象（称为 *本机 Office 对象*）添加功能。 宿主项和宿主控件又统称 *扩展的对象*。 有关宿主项和宿主控件的详细信息，请参阅 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
## <a name="understanding-the-getvstoobject-and-hasvstoobject-methods"></a>了解 GetVstoObject 和 HasVstoObject 方法  
 若要测试本机 Office 对象，请在你的项目中使用的 HasVstoObject 和 GetVstoObject 方法：  
  
-   如果你想要确定本机 Office 对象是否在你的自定义具有扩展的对象，请使用 HasVstoObject 方法。 如果本机 Office 对象具有扩展的对象，则此方法返回 **true** ，否则返回 **false** 。  
  
-   如果你想要将本机 Office 对象中获取扩展的对象，请使用 GetVstoObject 方法。 如果指定的本机 Office 对象具有扩展的对象，则此方法返回 <xref:Microsoft.Office.Tools.Excel.ListObject>、 <xref:Microsoft.Office.Tools.Excel.Workbook>、 <xref:Microsoft.Office.Tools.Excel.Worksheet>或 <xref:Microsoft.Office.Tools.Word.Document> 对象。 否则，返回 GetVstoObject **null**。 例如，GetVstoObject 方法返回<xref:Microsoft.Office.Tools.Word.Document>如果指定<xref:Microsoft.Office.Interop.Word.Document>是 Word 文档项目中的文档的基础对象。  
  
 在文档级项目中，你不能使用 GetVstoObject 方法创建一个新<xref:Microsoft.Office.Tools.Excel.Workbook>， <xref:Microsoft.Office.Tools.Excel.Worksheet>，或<xref:Microsoft.Office.Tools.Word.Document>在运行时主机项。 此方法仅用于在设计时访问项目中现有的已生成宿主项。 如果想要在运行时创建新的宿主项，则必须开发 VSTO 外接程序项目。 有关详细信息，请参阅 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) 和 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## <a name="using-the-getvstoobject-and-hasvstoobject-methods"></a>使用 GetVstoObject 和 HasVstoObject 方法  
 若要调用的 HasVstoObject 和 GetVstoObject 方法，请使用 Globals.Factory.GetVstoObject 或 Globals.Factory.HasVstoObject 方法，和的本机 Word 或 Excel 对象中传递 (如<xref:Microsoft.Office.Interop.Word.Document>或<xref:Microsoft.Office.Interop.Excel.Worksheet>)，你想要测试。  
  
## <a name="see-also"></a>另请参阅  
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [使用 ServerDocument 类管理服务器上的文档](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)  
  
  