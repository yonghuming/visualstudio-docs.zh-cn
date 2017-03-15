---
title: "命令处理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的命令处理"
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 命令处理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

你的编辑器可以定义新的命令。 在菜单中，在工具栏上，或在上下文菜单中，通常会显示命令。  
  
 有关定义命令和菜单的详细信息，请参阅 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 语言服务可以控制哪些上下文菜单显示在编辑器中，可通过截获过程 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 枚举。 或者，你可以控制基于每个标记的上下文菜单。 有关详细信息请参阅 [语言服务筛选器的重要命令](../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>将命令添加到编辑器上下文菜单  
 若要将命令添加到上下文菜单中，必须首先定义一组属于特定组的菜单命令。 下面的示例取自作为本演练的一部分生成的.vsct 文件 [演练︰ 添加功能到自定义编辑器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \< 菜单 guid ="guidCustomEditorCmdSet"id ="IDMX_RTF"优先级 ="0x0000"type ="上下文">  
  
 \< 父 guid ="guidCustomEditorCmdSet"id ="0"/>  
  
 \< 字符串>  
  
 \< ButtonText>CustomEditor 上下文菜单 \< / ButtonText>  
  
 \< CommandName>CustomEditorContextMenu \< / CommandName>  
  
 \< / 字符串>  
  
 \< / 菜单>  
  
 \< / 菜单>  
  
 上面的文本将添加具有文本的上下文菜单命令 **CustomEditor 上下文菜单**。 菜单 GUID 是创建使用此编辑器的命令集和该类型是"上下文"。  
  
 你还可以使用无需在.vsct 文件中定义的预定义的命令。 例如，如果您检查 EditorPane.cs 文件以生成由 Visual Studio 包模板，您发现的一组预定义命令，如 <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> 由定义 <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, ，会在命令处理程序，如 onSelectAll 方法中处理。  
  
## <a name="see-also"></a>请参阅  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)