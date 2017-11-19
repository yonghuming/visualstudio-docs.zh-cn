---
title: "如何： 向 Visual C# 项目中的 VBA 公开代码 |Microsoft 文档"
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
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a52060f1a1b2200109c5003321857915d95bd12a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>如何：向 VBA 公开 Visual C# 项目中的代码
  如果你想要进行相互交互的代码的两个类型，可以公开 Visual C# 项目到 Visual Basic for Applications (VBA) 代码中的代码。  
  
 Visual C# 过程是不同的 Visual Basic 过程。 有关详细信息，请参阅[如何： 向 Visual Basic 项目中的 VBA 公开代码](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>公开 Visual C# 项目中的代码  
 若要使 VBA 代码能够调用 Visual C# 项目中的代码，修改代码，因此对于 COM 可见，并将**ReferenceAssemblyFromVbaProject**属性**True**设计器中。  
  
 有关演示如何从 VBA 调用 Visual C# 项目中的方法的演练，请参阅[演练： 从 VBA 中 Visual C &#35; 调用代码项目](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)。  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>若要公开到 VBA Visual C# 项目中的代码  
  
1.  打开或创建基于的 Word 文档、 Excel 工作簿或 Excel 模板支持宏，并且已经包含 VBA 代码的文档级项目。  
  
     有关支持宏的文档文件格式的详细信息，请参阅[结合 VBA 和文档级自定义项](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  此功能无法在 Word 模板项目中使用。  
  
2.  确保文档中的 VBA 代码允许在不提示用户启用宏的情况下运行。 通过在 Word 或 Excel 的“信任中心”设置中将 Office 项目的位置添加到受信任位置列表中，可以信任要运行的 VBA 代码。  
  
3.  添加你想要向 VBA 公开到你的项目中的公共类的成员并将声明将新成员**公共**。  
  
4.  将应用以下<xref:System.Runtime.InteropServices.ComVisibleAttribute>和<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>到要向 VBA 公开的类属性。 这些特性使类对于 COM 可见，但不生成类接口。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  重写**GetAutomationObject**以返回你公开的类的实例，向 VBA 项目中某个主机项类的方法：  
  
    -   如果你将公开到 VBA 某个主机项类，重写**GetAutomationObject**属于此类，并返回类的当前实例的方法。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   如果你将公开到 VBA 是主机项类，重写**GetAutomationObject**方法的任何主机项在项目中，并返回非主机项类的实例。 例如，以下代码假定你将公开一个名为类`DocumentUtilities`向 VBA。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     有关宿主项的详细信息，请参阅 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
6.  从要向 VBA 公开的类中提取一个接口。 在**提取接口**对话框框中，选择你想要在接口声明中包含的公共成员。 有关详细信息，请参阅[提取接口重构 &#40;C &#35; &#41;](/visualstudio/csharp-ide/extract-interface-refactoring-csharp).  
  
7.  添加**公共**到接口声明关键字。  
  
8.  通过将以下内容添加，使该接口对于 COM 可见<xref:System.Runtime.InteropServices.ComVisibleAttribute>特性给接口。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. 在设计器中打开 （对于 Word) 的文档或工作表 （针对 Excel) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
10. 在 **“属性”** 窗口中，选择 **“ReferenceAssemblyFromVbaProject”** 属性，并将值更改为 **“True”**。  
  
    > [!NOTE]  
    >  如果工作簿或文档尚未包含 VBA 代码，或者如果文档中的 VBA 代码不受信任运行，在你设置时，你将收到一条错误消息**ReferenceAssemblyFromVbaProject**属性**True**. 这是因为在这种情况下，Visual Studio 无法修改文档中的 VBA 项目。  
  
11. 在显示的消息中单击 **“确定”** 。 此消息提醒你如果你添加 VBA 代码到工作簿或文档时运行项目，从[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，下次生成项目时，将丢失的 VBA 代码。 这是因为中生成的文档输出每个时，生成项目时，会覆盖文件夹。  
  
     在这种情况下，Visual Studio 将项目配置，以便入程序集可以调用 VBA 项目。 Visual Studio 还将添加一个名为方法`GetManagedClass`到 VBA 项目。 你可以从任何位置调用此方法在 VBA 项目以访问你向 VBA 公开的类。  
  
12. 生成项目。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [演练： 从 VBA 中 Visual C &#35; 的调用代码项目](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [如何：在 Visual Basic 项目中向 VBA 公开代码](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  