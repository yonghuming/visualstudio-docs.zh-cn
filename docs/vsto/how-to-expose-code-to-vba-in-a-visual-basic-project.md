---
title: "如何：向 VBA 公开 Visual Basic 项目中的代码"
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
  - "文档级自定义项 [Visual Studio 中的 Office 开发], 公开代码"
  - "向 VBA 公开代码"
  - "宿主项 [Visual Studio 中的 Office 开发], 向 VBA 公开代码"
  - "VBA [Visual Studio 中的 Office 开发], 公开文档级自定义项中的代码"
  - "Visual Basic [Visual Studio 中的 Office 开发], 向 VBA 公开代码"
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：向 VBA 公开 Visual Basic 项目中的代码
  如果想让 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 项目中的代码与 Visual Basic for Applications \(VBA\) 代码相互交互，则可以向后者公开前者。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic 进程不同于 Visual C\# 进程。  有关更多信息，请参见[如何：向 VBA 公开 Visual C&#35; 项目中的代码](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)。  
  
 用于宿主项类中的代码的过程与用于其他类中的代码的过程不同：  
  
-   [公开宿主项类中的代码](#HostItemCode)  
  
-   [公开不在宿主项类中的代码](#NonHostItem)  
  
 ![链接到视频](~/docs/data-tools/media/playvideo.gif "链接到视频") 有关相关的视频演示，请参见 [How Do I: Call VSTO Code from VBA?](http://go.microsoft.com/fwlink/?LinkId=136757)（如何实现：从 VBA 调用 VSTO 代码）。  
  
##  <a name="HostItemCode"></a> 公开宿主项类中的代码  
 为了使 VBA 代码能够调用宿主项类中的 Visual Basic 代码，请将宿主项的**“EnableVbaCallers”**属性设置为**“True”**。  
  
 有关演示如何公开宿主项类的方法然后从 VBA 中调用该方法的演练，请参见[演练：在 Visual Basic 项目中调用 VBA 中的代码](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)。  有关宿主项的更多信息，请参见[宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)。  
  
#### 向 VBA 公开宿主项中的代码  
  
1.  打开或创建一个文档级 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 项目，该项目须基于支持宏的 Word 文档、Excel 工作簿或 Excel 模板并且已经包含 VBA 代码。  
  
     有关支持宏的文档文件格式的更多信息，请参见[结合 VBA 和文档级自定义项](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  此功能无法在 Word 模板项目中使用。  
  
2.  确保在不提示用户启用宏的情况下允许运行文档中的 VBA 代码。  通过在 Word 或 Excel 的“信任中心”设置中将 Office 项目的位置添加到受信任位置列表中，可以信任要运行的 VBA 代码。  
  
3.  将要向 VBA 公开的属性、方法或事件添加到项目中的某个宿主项类中，并将新成员声明为 **Public**。  类的名称取决于应用程序：  
  
    -   在 Word 项目中，宿主项类默认情况下名为 `ThisDocument`。  
  
    -   在 Excel 项目中，宿主项类默认情况下名为 `ThisWorkbook`、`Sheet1`、`Sheet2` 和 `Sheet3`。  
  
4.  将宿主项的**“EnableVbaCallers”**属性设置为**“True”**。  当宿主项在设计器中打开时，此属性在**“属性”**窗口中可用。  
  
     设置了此属性后，Visual Studio 会自动将**“ReferenceAssemblyFromVbaProject”**属性设置为**“True”**。  
  
    > [!NOTE]  
    >  如果工作簿或文档尚未包含 VBA 代码，或者如果运行文档中的 VBA 代码时不信任该代码，则在将**“EnableVbaCallers”**属性设置为**“True”**时将收到一条错误消息。  这是因为在这种情况下 Visual Studio 无法修改文档中的 VBA 项目。  
  
5.  在显示的消息中单击**“确定”**。  此消息提醒您在从 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中运行项目时如果将 VBA 代码添加到工作簿或文档中，则在下一次生成该项目时 VBA 代码将丢失。  这是因为每次生成项目时都会覆盖生成输出文件夹中的文档。  
  
     此时，Visual Studio 会配置项目，以便 VBA 项目可以调入程序集。  Visual Studio 还将名为 `CallVSTOAssembly` 的属性添加到 VBA 项目中的 `ThisDocument`、`ThisWorkbook`、`Sheet1`、`Sheet2` 或 `Sheet3` 模块中。  您可以使用此属性来访问您向 VBA 公开的类的公共成员。  
  
6.  生成项目。  
  
##  <a name="NonHostItem"></a> 公开不在宿主项类中的代码  
 为了使 VBA 代码能够调用不在宿主项类中的 Visual Basic 代码，请修改代码以使其对于 VBA 可见。  
  
#### 向 VBA 公开不在宿主项类中的代码  
  
1.  打开或创建一个文档级 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 项目，该项目须基于支持宏的 Word 文档、Excel 工作簿或 Excel 模板并且已经包含 VBA 代码。  
  
     有关支持宏的文档文件格式的更多信息，请参见[结合 VBA 和文档级自定义项](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  此功能无法在 Word 模板项目中使用。  
  
2.  确保在不提示用户启用宏的情况下允许运行文档中的 VBA 代码。  通过在 Word 或 Excel 的“信任中心”设置中将 Office 项目的位置添加到受信任位置列表中，可以信任要运行的 VBA 代码。  
  
3.  将希望向 VBA 公开的成员添加至项目中的公共类，并将新成员声明为 **public**。  
  
4.  将以下 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 和 <xref:Microsoft.VisualBasic.ComClassAttribute> 特性应用于要向 VBA 公开的类。  这些特性使得类对于 VBA 可见。  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  重写项目中宿主项类的 **GetAutomationObject** 方法以返回要向 VBA 公开的类的实例。  下面的代码示例假定您向 VBA 公开名为 `DocumentUtilities` 的类。  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中打开文档（Word 文档）或工作表（Excel 工作表）的设计器。  
  
7.  在**“属性”**窗口中，选择**“ReferenceAssemblyFromVbaProject”**属性，并将值更改为**“True”**。  
  
    > [!NOTE]  
    >  如果工作簿或文档尚未包含 VBA 代码，或者如果运行文档中的 VBA 代码时不信任该代码，则在将**“ReferenceAssemblyFromVbaProject”**属性设置为**“True”**时将收到一条错误消息。  这是因为在这种情况下 Visual Studio 无法修改文档中的 VBA 项目。  
  
8.  在显示的消息中单击**“确定”**。  此消息提醒您在从 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中运行项目时如果将 VBA 代码添加到工作簿或文档中，则在下一次生成该项目时 VBA 代码将丢失。  这是因为每次生成项目时都会覆盖生成输出文件夹中的文档。  
  
     此时，Visual Studio 会配置项目，以便 VBA 项目可以调入程序集。  Visual Studio 还将名为 `GetManagedClass` 的方法添加到 VBA 项目。  可以从 VBA 项目的任何位置调用此方法以访问向 VBA 公开的类。  
  
9. 生成项目。  
  
## 请参阅  
 [如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [结合 VBA 和文档级自定义项](../vsto/combining-vba-and-document-level-customizations.md)   
 [演练：在 Visual Basic 项目中调用 VBA 中的代码](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [如何：向 VBA 公开 Visual C&#35; 项目中的代码](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  