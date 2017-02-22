---
title: "代码段选择器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.expansionpicker"
helpviewer_keywords: 
  - "代码段选择器"
  - "代码段, 代码段选择器"
  - "IntelliSense 代码段, 代码段选择器"
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 25
caps.handback.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 代码段选择器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 代码编辑器提供了**“代码段选择器”**，使用它，单击几下鼠标就可将现成的代码块插入到活动文档中。  
  
 显示**“代码段选择器”**的过程根据您所使用的语言会有所不同。  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] \-\- 在“代码编辑器”中所需的位置处右击，以显示快捷菜单，然后选择**“插入代码段”**。  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] \-\- 在“代码编辑器”中所需的位置处右击，以显示快捷菜单，然后单击**“插入代码段”**或**“外侧代码”**。  
  
-   [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] \-\- **“代码段选择器”**不可用。  
  
-   Visual F\# \-**“代码段选择器”**不可用。  
  
-   [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)] \-\- 在“代码编辑器”中所需的位置处右击，以显示快捷菜单，再单击**“插入代码段”**或**“外侧代码”**。  
  
-   XML \-\- 在“代码编辑器”中所需的位置处右击，以显示快捷菜单，再单击**“插入代码段”**或**“外侧代码”**。  
  
-   HTML \-\- 在“代码编辑器”中所需的位置处右击，以显示快捷菜单，再单击**“插入代码段”**或**“外侧代码”**。  
  
-   SQL \- 在“代码编辑器”中所需的位置处右击，以显示快捷菜单，然后单击**“插入代码段”**。  
  
 在大多数 Visual Studio 开发语言，您可以使用**代码段管理器** 添加到文件夹 **文件夹列表** 的 **代码段选择器**扫描 XML 代码段文件。  还可以创建要添加到列表中的自己的代码段。  有关更多信息，请参见 [演练：创建代码段](../../ide/walkthrough-creating-a-code-snippet.md)。  
  
## UIElement 列表  
 项名  
 可编辑文本字段，显示在**“项列表”**中选定的项的名称。  若要执行渐进式搜索以查找所需的项，请首先在此字段中键入其名称。  继续添加字母，直到在**“项列表”**中选择了所需的项。  
  
 项列表  
 可以插入的代码段的列表，或包含代码段的文件夹的列表。  若要插入代码段或展开文件夹，请选择所需的项，然后按 Enter。  
  
## 请参阅  
 [有关使用代码段的最佳做法](../../ide/best-practices-for-using-code-snippets.md)   
 [Visual Basic IntelliSense 代码段](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [在代码中设置书签](../../ide/setting-bookmarks-in-code.md)   
 [如何：使用外侧代码段](../Topic/How%20to:%20Use%20Surround-with%20Code%20Snippets.md)