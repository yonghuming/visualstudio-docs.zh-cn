---
title: "打开选项页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "打开选项页"
  - "工具选项"
  - "选项页"
ms.assetid: 6f24cbfa-288a-4a57-831b-bc82587de255
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 打开选项页
可以以编程方式显示选项页，以便包的用户可以在安装期间进行配置。 若要在安装包后更改设置，用户仍然可以使用“选项”对话框访问选项页。  
  
### 若要显示自定义选项页  
  
1.  创建选项页。 有关详细信息，请参阅[创建选项页](../extensibility/internals/creating-options-pages.md)。  
  
2.  通过将 `typeof` 关键字应用于定义选项页的类的名称来获取选项页的 <xref:System.Type>。  
  
3.  通过将选项页的 <xref:System.Type> 用作参数来调用 <xref:Microsoft.VisualStudio.Shell.Package.ShowOptionPage%2A> 方法。  
  
     以下示例显示了名为 **HelloWorldOptions** 的选项页。  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/CSharp/opening-an-options-page_1.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/VisualBasic/opening-an-options-page_1.vb)]  
  
### 若要显示由 Visual Studio 定义的选项页  
  
1.  在注册表子项 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\ToolsOptionsPages\\ 中，找到你想要显示的选项页的节点，然后复制其 GUID，它是页面键的值。  
  
2.  创建具有常量 <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> 并将 <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> 作为参数的 <xref:System.ComponentModel.Design.CommandID> 实例。  
  
     此操作会指定“选项”对话框。  
  
3.  通过将 <xref:System.ComponentModel.Design.CommandID> 实例和 GUID 字符串用作参数来调用 <xref:System.ComponentModel.Design.MenuCommandService.GlobalInvoke%2A> 方法。  
  
     以下示例显示了“文本编辑器”选项页的“常规”选项卡。  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/CSharp/opening-an-options-page_2.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/VisualBasic/opening-an-options-page_2.vb)]