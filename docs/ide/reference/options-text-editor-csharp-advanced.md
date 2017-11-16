---
title: "“选项”->“文本编辑器”->“C#”->“高级”| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7537b4fc3fec90808c6bdc4a982fe3b7ff37a1d5
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2017
---
# <a name="options-text-editor-c-advanced"></a>选项，文本编辑器，C#，高级
使用此对话框可修改 Visual C# 的编辑器格式设置、代码重构设置和 XML 文档注释设置。 若要访问此对话框，请在“工具菜单”上单击“选项”，展开“文本编辑器”文件夹，再展开“C#”，然后单击“高级”。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="outlining"></a>大纲显示  
 打开文件时进入大纲模式  
 选中后，会自动大纲显示代码文件，这将创建可折叠代码块。 首次打开文件时，#region 块和非活动代码块处于折叠状态。  
  
## <a name="editor-help"></a>编辑器帮助  
 在编辑器中用下划线标出错误  
 标识代码中的生成错误。 选中此选项后，不同颜色的波浪下划线具有不同的特定含义：  
  
-   分析错误为红色。  
  
-   生成错误为蓝色。  
  
-   生成警告为绿色。  
  
-   无效的[编辑并继续](../../debugger/edit-and-continue.md)编辑为紫色。  
  
将指针移到用下划线标出的代码段，可查看包含错误相关信息的工具提示。  
  
显示实时语义错误  
标识某些没有显式编译的编译错误，例如，声明和使用未知类型或引用未知属性。  
  
突出显示对光标下符号的引用  
光标定位在符号内，或单击某个符号时，将突出显示代码文件中该符号的所有实例。  
  
## <a name="refactoring"></a>重构  
 验证重构结果  
 尝试重构含有生成错误的代码，或重构会导致将代码引用绑定到与其原始绑定不同的内容时，系统会显示“验证结果”对话框。  
  
 对具有编译器生成的引用的成员发出警告  
 尝试重构的成员具有与编译器生成的引用相同的名称时，会显示警告对话框。  
  
## <a name="xml-documentation-comments"></a>XML 文档注释  
 为 /// 生成 XML 文档注释  
 选中后，将在键入 /// 注释说明后自动为 XML 文档注释插入 \<摘要> 开始和结束标记。 有关 XML 文档注释的详细信息，请参阅 [XML 文档注释](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)。  
  
## <a name="implement-interface"></a>实现接口  
 使用 #region 环绕生成的代码  
 使用实现接口或显式实现接口时，将在方法周围插入 #region \<接口名称> 成员。  
  
## <a name="organize-usings"></a>组织用法  
 对 using 排序时将“System”指令排在第一位  
 选中后，`System` using 指令将出现在其他 using 指令之前。 有关详细信息，请参阅 [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md#automatic-code-generation) 中的组织 using。  
  
## <a name="see-also"></a>另请参阅  
 [XML 文档注释](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [设置语言特定的编辑器选项](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)