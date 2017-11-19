---
title: "从其他 Office 解决方案调用 VSTO 外接程序中的代码 |Microsoft 文档"
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
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
ms.assetid: c1f16b4c-9291-49ed-9694-a83a37109612
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38508a664ff94628dfd3fd5ec00eacb32fbb1187
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="calling-code-in-vsto-add-ins-from-other-office-solutions"></a>从其他 Office 解决方案调用 VSTO 外接程序中的代码
  可以向其他解决方案（包括其他 Microsoft Office 解决方案）公开 VSTO 外接程序中的对象。 如果 VSTO 外接程序提供了你希望使其他解决方案能够使用的服务，这一点非常有用。 例如，如果某个 Microsoft Office Excel VSTO 外接程序从 Web 服务中执行财务数据计算，则其他解决方案可以通过在运行时调入该 Excel VSTO 外接程序来执行这些计算。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 此过程包括以下两个主要步骤：  
  
-   在 VSTO 外接程序中，向其他解决方案公开对象。  
  
-   在其他解决方案中，访问由 VSTO 外接程序公开的对象，然后调用对象的成员。  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>可调用外接程序代码的解决方案类型  
 可以向以下类型的解决方案公开 VSTO 外接程序中的对象：  
  
-   在与 VSTO 外接程序相同的应用程序进程中加载的文档中的 Visual Basic for Applications (VBA) 代码。  
  
-   在与 VSTO 外接程序相同的应用程序进程中加载的文档级自定义项。  
  
-   使用 Visual Studio 中的 Office 项目模板创建的其他 VSTO 外接程序。  
  
-   COM VSTO 外接程序（即直接实现 <xref:Extensibility.IDTExtensibility2> 接口的 VSTO 外接程序）。  
  
-   在不同于 VSTO 外接程序的进程中运行的任何解决方案（这些类型的解决方案也称为 *进程外客户端*）。 其中包括使 Office 应用程序实现自动化的应用程序（例如 Windows 窗体或控制台应用程序），以及在其他进程中加载的 VSTO 外接程序。  
  
## <a name="exposing-objects-to-other-solutions"></a>向其他解决方案公开对象  
 若要向其他解决方案公开 VSTO 外接程序中的对象，请在 VSTO 外接程序中执行下列步骤：  
  
1.  定义要向其他解决方案公开的类。  
  
2.  重写 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 类中的 `ThisAddIn` 方法。 返回要向其他解决方案公开的类的实例。  
  
### <a name="defining-the-class-you-want-to-expose-to-other-solutions"></a>定义要向其他解决方案公开的类  
 要公开的类必须至少是公共类，必须将 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性设置为 **true**，并且必须公开 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) 接口。  
  
 建议通过执行以下步骤公开 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) 接口：  
  
1.  定义一个接口，该接口声明要向其他解决方案公开的成员。 可以在 VSTO 外接程序项目中定义此接口。 但是，如果要向非 VBA 解决方案公开类，以便调用 VSTO 外接程序的解决方案无需引用 VSTO 外接程序项目即可引用此接口，则可能需要在单独的类库项目中定义此接口。  
  
2.  将 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性应用到此接口，并将此属性设置为 **true**。  
  
3.  修改你的类以实现此接口。  
  
4.  应用<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>特性到该类，并将此属性设置为无的值<xref:System.Runtime.InteropServices.ClassInterfaceType>枚举。  
  
5.  如果要向进程外客户端公开类，可能还需要执行以下操作：  
  
    -   从 <xref:System.Runtime.InteropServices.StandardOleMarshalObject>派生类。 有关详细信息，请参阅 [向进程外客户端公开类](#outofproc)。  
  
    -   在定义此接口的项目中设置“为 COM 互操作注册”  属性。 仅当你希望让客户端使用早期绑定来调入 VSTO 外接程序时，才有必要这么做。  
  
 下面的代码示例演示一个 `AddInUtilities` 类，该类具有可由其他解决方案调用的 `ImportData` 方法。 若要查看此代码的更大的演练上下文中，请参阅[演练： 在 VSTO 外接程序中从 VBA 调用代码](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)。  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
 [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="exposing-classes-to-vba"></a>向 VBA 公开类  
 执行上述步骤时，VBA 代码只能调用在接口中声明的方法。 VBA 代码无法调用类中的任何其他方法，包括类从基类（如 <xref:System.Object>）中获取的方法。  
  
 或者，您可以公开[IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)接口通过设置<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性设为的 AutoDispatch 或 AutoDual 值<xref:System.Runtime.InteropServices.ClassInterfaceType>枚举。 如果执行此操作，则不必在单独的接口中声明方法。 不过，VBA 代码可以调用类中的任何公共方法和非静态方法，包括从基类（如 <xref:System.Object>）获取的方法。 此外，使用早期绑定的进程外客户端不能调用你的类。  
  
###  <a name="outofproc"></a> 向进程外客户端公开类  
 如果要向进程外客户端公开 VSTO 外接程序中的类，则应从 <xref:System.Runtime.InteropServices.StandardOleMarshalObject> 派生该类，以确保进程外客户端可以调用公开的 VSTO 外接程序对象。 否则，尝试在进程外客户端中获取已公开对象的实例可能会意外失败。  
  
 这是因为对 Office 应用程序的对象模型的所有调入都必须在主 UI 线程上执行，但从进程外客户端对你的对象进行的调用则可以在任意 RPC（远程过程调用）线程上执行。 .NET Framework 中的 COM 封送处理机制不会切换线程，而是尝试将对你的对象的调用封送到传入 RPC 线程（而不是主 UI 线程）中。 如果你的对象是从 <xref:System.Runtime.InteropServices.StandardOleMarshalObject>派生的类的实例，则对你的对象的传入调用会自动封送到用于创建公开对象的线程中，该线程将是主机应用程序的主 UI 线程。  
  
 有关在 Office 解决方案中使用线程的详细信息，请参阅 [Threading Support in Office](../vsto/threading-support-in-office.md)。  
  
### <a name="overriding-the-requestcomaddinautomationservice-method"></a>重写 RequestComAddInAutomationService 方法  
 以下代码示例演示了如何重写 VSTO 外接程序中 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 类中的 `ThisAddIn` 。 此示例假设你已经定义了一个要向其他解决方案公开的名为 `AddInUtilities` 的类。 若要查看此代码的更大的演练上下文中，请参阅[演练： 在 VSTO 外接程序中从 VBA 调用代码](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)。  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 加载 VSTO 外接程序后， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 将调用 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 方法。 运行时将返回的对象分配给 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 对象（用于表示你的 VSTO 外接程序）的 <xref:Microsoft.Office.Core.COMAddIn> 属性。 此 <xref:Microsoft.Office.Core.COMAddIn> 对象可供其他 Office 解决方案以及使 Office 实现自动化的解决方案使用。  
  
## <a name="accessing-objects-from-other-solutions"></a>从其他解决方案中访问对象  
 若要调用 VSTO 外接程序中公开的对象，请在客户端解决方案中执行下列步骤：  
  
1.  获取表示公开的 VSTO 外接程序的 <xref:Microsoft.Office.Core.COMAddIn> 对象。 客户端可以访问所有可用的 VSTO 外接在主机 Office 应用程序的对象模型中使用 Application.COMAddIns 属性。  
  
2.  访问 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 对象的 <xref:Microsoft.Office.Core.COMAddIn> 属性。 此属性从 VSTO 外接程序返回公开的对象。  
  
3.  调用已公开对象的成员。  
  
 对于 VBA 客户端和非 VBA 客户端， <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 属性返回值的使用方法是不同的。 对于进程外客户端，需要其他代码以避免可能的争用情况。  
  
### <a name="accessing-objects-from-vba-solutions"></a>从 VBA 解决方案中访问对象  
 以下代码示例演示了如何使用 VBA 调用由 VSTO 外接程序公开的方法。 此 VBA 宏将调用一个名为 `ImportData` 的方法，该方法是在名为 **ExcelImportData**的 VSTO 外接程序中定义的。 若要查看此代码的更大的演练上下文中，请参阅[演练： 在 VSTO 外接程序中从 VBA 调用代码](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)。  
  
```  
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="accessing-objects-from-non-vba-solutions"></a>从非 VBA 解决方案中访问对象  
 在非 VBA 解决方案中，必须将 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 属性值转换为它实现的接口，然后可以针对接口对象调用已公开的方法。 以下代码示例演示了如何从不同的 VSTO 外接程序中调用 `ImportData` 方法，这些外接程序是通过使用 Visual Studio 中的 Office 开发人员工具创建的。  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 在此示例中，如果你尝试将 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 属性的值转换为 `AddInUtilities` 类而不是 `IAddInUtilities` 接口，则该代码将引发 <xref:System.InvalidCastException>。  
  
## <a name="see-also"></a>另请参阅  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [演练： VSTO 外接程序中从 VBA 调用代码](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [开发 Office 解决方案](../vsto/developing-office-solutions.md)   
 [如何： 在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)   
 [使用扩展性接口自定义 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  