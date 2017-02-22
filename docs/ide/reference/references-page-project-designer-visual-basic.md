---
title: "项目设计器 -&gt;“引用”页 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesReference"
  - "vb.ProjectPropertiesUnusedReference"
  - "vb.ProjectPropertiesReferencePaths"
helpviewer_keywords: 
  - "项目设计器中的“引用”页"
  - "项目设计器, “引用”页"
  - "“未使用的引用”对话框"
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 项目设计器 -&gt;“引用”页 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用**“项目设计器”**的**“引用”**页可以管理项目中的引用、Web 引用和导入的命名空间。  项目能够包含对 COM 组件、XML Web services、.NET Framework 类库或程序集以及其他类库的引用。  有关使用引用的更多信息，请参见 [管理项目中的引用](../../ide/managing-references-in-a-project.md)。  
  
 访问 **引用** 页上，选择项目节点 \(不是 **解决方案** 节点\)。**解决方案资源管理器**。  然后选择 **项目**，在菜单栏上 **属性**。  在项目设计器出现时，单击 **引用** 选项。  
  
## UIElement 列表  
 以下选项使您可以在项目中选择或移除引用和导入的命名空间。  
  
 **未使用的引用**  
 单击此按钮以访问 **未使用的引用** 对话框。  
  
 **“未使用的引用”**对话框允许您移除包含在您的项目中但实际上未被代码使用的引用。  它包含列表 **引用名称**，**路径**，并且，有关未使用的命名空间的其他信息在项目中引用的网格。  在该网格中，选择希望从项目中移除的命名空间引用，然后单击**“移除”**。  
  
 **引用路径**  
 单击此按钮以访问 **引用路径** 对话框。  
  
> [!NOTE]
>  当项目系统查找一个引用程序集时，系统将查找引用解析在以下位置，则按下面的顺序：  
>   
>  1.  项目文件夹。  当 **显示所有文件** 实际上时，不是项目文件夹文件显示在 **解决方案资源管理器**。  
> 2.  在 **引用路径** 对话框中指定的文件夹。  
> 3.  显示在 **添加引用** 对话框的文件的文件夹。  
> 4.  项目的 obj 文件夹。  \(在添加对 COM 时引用添加到项目中，一个或多个程序集可以添加到项目的 obj 文件夹。\)  
  
 **引用**  
 此列表显示项目中的所有引用，包括使用的和未使用的。  
  
 **添加**  
 单击此按钮可将引用或 Web 引用添加到**“引用”**列表中。  
  
 选择**“引用”**可使用“添加引用”对话框将引用添加到项目中。  
  
 选择**“Web 引用”**可使用“添加 Web 引用”对话框将 Web 引用添加到项目中。  
  
 **移除**  
 在**“引用”**列表中选择一个或多个引用，然后单击此按钮可将其删除。  
  
 **更新 Web 引用**  
 在**“引用”**列表中选择一个 Web 引用，单击此按钮可更新该引用。  
  
 **导入的命名空间**  
 可以在此框中键入自己的命名空间，然后单击**“添加用户导入”**以将其添加到命名空间列表。  
  
 可以为用户导入的命名空间创建别名。  为此，可以使用“*别名*\=*命名空间*”格式输入别名和命名空间。  使用很长的命名空间时此格式十分有用，例如：`Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`。  
  
 **添加用户导入**  
 单击此按钮可以将在**“导入的命名空间”**框中指定的命名空间添加到导入的命名空间的列表。  只有在所指定的命名空间已不在列表中时此按钮才是活动的。  
  
 **命名空间列表**  
 此列表显示所有可用命名空间。  您的项目中包含的命名空间对应的复选框会被选中。  
  
 **更新用户导入**  
 在命名空间列表中选择一个用户指定的命名空间，在**“导入的命名空间”**框中键入要替换它的名称，然后单击此按钮以更改为新的命名空间。  只有所选的命名空间是通过使用**“添加用户导入”**按钮添加到列表时按钮才是活动的。  可以添加：  
  
-   类或命名空间，例如 <xref:System.Math?displayProperty=fullName>。  
  
-   别名导入，如 `VB=Microsoft.VisualBasic`。  
  
-   XML 命名空间，如 `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`。  
  
## 请参阅  
 [如何：使用“添加引用”对话框添加或移除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [如何：添加或移除导入的命名空间 \(Visual Basic\)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [“添加 Web 引用”对话框](http://msdn.microsoft.com/zh-cn/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports 语句（XML 命名空间）](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)