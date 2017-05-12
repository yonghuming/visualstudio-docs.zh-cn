---
title: "如何：向 VBA 公开 Visual C# 项目中的代码"
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
  - "VBA [Visual Studio 中的 Office 开发], 公开文档级自定义项中的代码"
  - "Visual C# [Visual Studio 中的 Office 开发], 向 VBA 公开代码"
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：向 VBA 公开 Visual C# 项目中的代码
  如果想让 Visual C\# 项目中的代码与 Visual Basic for Applications \(VBA\) 代码相互交互，则可以向后者公开前者。  
  
 Visual C\# 进程不同于 Visual Basic 进程。  有关更多信息，请参见[如何：向 VBA 公开 Visual Basic 项目中的代码](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 公开 Visual C\# 项目中的代码  
 若要使 VBA 代码能够调用 Visual C\# 项目中的代码，请修改代码使其对于 COM 可见，然后在设计器中将**“ReferenceAssemblyFromVbaProject”**属性设置为**“True”**。  
  
 有关演示如何从 VBA 中调用 Visual C\# 项目中的方法的演练，请参见[演练：在 Visual C&#35; 项目中调用 VBA 中的代码](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)。  
  
#### 向 VBA 公开 Visual C\# 项目中的代码  
  
1.  打开或创建一个文档级项目，该项目须基于支持宏的 Word 文档、Excel 工作簿或 Excel 模板并且已经包含 VBA 代码。  
  
     有关支持宏的文档文件格式的更多信息，请参见[结合 VBA 和文档级自定义项](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  此功能无法在 Word 模板项目中使用。  
  
2.  确保在不提示用户启用宏的情况下允许运行文档中的 VBA 代码。  通过在 Word 或 Excel 的“信任中心”设置中将 Office 项目的位置添加到受信任位置列表中，可以信任要运行的 VBA 代码。  
  
3.  将希望向 VBA 公开的成员添加至项目中的公共类，并将新成员声明为 **public**。  
  
4.  将以下 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 和 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 特性应用于要向 VBA 公开的类。  这些特性使类对于 COM 可见，但不生成类接口。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  重写项目中宿主项类的 **GetAutomationObject** 方法以返回要向 VBA 公开的类的实例：  
  
    -   如果要向 VBA 公开宿主项类，请重写属于此类的 **GetAutomationObject** 方法，并返回类的当前实例。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   如果要向 VBA 公开非宿主项的类，请重写项目中任一宿主项的 **GetAutomationObject** 方法，并返回非宿主项类的实例。  例如，以下代码假设要向 VBA 公开一个名为 `DocumentUtilities` 的类。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     有关宿主项的更多信息，请参见[宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)。  
  
6.  从要向 VBA 公开的类中提取接口。  在**“提取接口”**对话框中，选择希望包括在接口声明中的公共成员。  有关更多信息，请参见[提取接口重构 &#40;C&#35;&#41;](../csharp-ide/extract-interface-refactoring-csharp.md)。  
  
7.  将 **public** 关键字添加到接口声明中。  
  
8.  通过将以下 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 特性添加到接口中以使接口对 COM 可见。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的设计器中打开文档（Word 文档）或工作表（Excel 工作表）。  
  
10. 在**“属性”**窗口中，选择**“ReferenceAssemblyFromVbaProject”**属性，并将值更改为**“True”**。  
  
    > [!NOTE]  
    >  如果工作簿或文档尚未包含 VBA 代码，或者运行文档中的 VBA 代码时不信任该代码，则在将**“ReferenceAssemblyFromVbaProject”**属性设置为**“True”**时将收到一条错误消息。  这是因为在这种情况下 Visual Studio 无法修改文档中的 VBA 项目。  
  
11. 在显示的消息中单击**“确定”**。  此消息提醒您在从 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中运行项目时如果将 VBA 代码添加到工作簿或文档中，则在下一次生成该项目时 VBA 代码将丢失。  这是因为每次生成项目时都会覆盖生成输出文件夹中的文档。  
  
     此时，Visual Studio 会配置项目，以便 VBA 项目可以调入程序集。  Visual Studio 还将名为 `GetManagedClass` 的方法添加到 VBA 项目。  可以从 VBA 项目的任何位置调用此方法以访问向 VBA 公开的类。  
  
12. 生成项目。  
  
## 请参阅  
 [如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [结合 VBA 和文档级自定义项](../vsto/combining-vba-and-document-level-customizations.md)   
 [演练：在 Visual C&#35; 项目中调用 VBA 中的代码](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [如何：向 VBA 公开 Visual Basic 项目中的代码](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  