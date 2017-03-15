---
title: "“选项”->“文本编辑器”->“C/C++”->“实验”| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a1edc88394193474b273968d8435e8df06415044
ms.openlocfilehash: a3fcafe5c191987668dc6e0dce8835d748742ed7

---
# <a name="options-text-editor-cc-experimental"></a>选项, 文本编辑器, C/C++, 实验
通过更改这些选项，你可以在用 C 或 C++ 进行编程时更改与 IntelliSense 和浏览数据库有关的行为。  
  
 若要访问此页，请在“选项”  对话框的左窗格中，展开“文本编辑器” ，再展开“C/C++” ，然后选择“实验” 。  
  
 这些功能在 Visual Studio 2015 Update 1 RC 安装中可用。  
  
> [!NOTE]
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## <a name="browsingnavigation"></a>浏览/导航  
 **启用新的数据库引擎**  
 这将会自动提高数据库填充速度，并使所有数据库操作更快（且不会降低准确性），例如“转到定义”  和“查找所有引用” 等操作。 （只需关闭并重新打开你的解决方案即可应用所做的更改；不需要重新启动 Visual Studio。）  
  
## <a name="intellisense"></a>IntelliSense  
 **成员列表的点到箭头替换**  
 当可用于成员列表时，将“.”替换为“->”。  
  
## <a name="refactoring"></a>重构  
 **启用提取函数**  
 提取所选代码到它自身函数并将代码替换为到新函数的调用。 若要访问此功能，请右键单击所选代码并选择“快速操作” ，或只需按默认快捷键 Ctrl + 点 [Ctrl+.]。  
  
 **启用更改签名**  
 添加、重新排列和删除函数的参数并将更改传播到所有调用站点。 若要访问此功能，请右键单击任何函数使用情况并选择“快速操作” ，或只需按默认快捷键 Ctrl + 点 [Ctrl+.]。  
  
## <a name="text-editor"></a>文本编辑器  
 **启用展开作用域**  
 如果启用，你可以用大括号将所选文本括起来，方法是在文本编辑器中输入“{”。  
  
 **启用展开优先级**  
 如果启用，你可以用括号将所选文本括起来，方法是在文本编辑器中输入“(”。  
  
 有关 Visual Studio 库上的其他文本编辑器功能，请参阅 [此处](http://go.microsoft.com/fwlink/?LinkId=692016)列表。 一个示例是 [C++ 快速修补](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)，它支持以下内容：  
  
-   **添加缺少的 #include** - 建议对你代码中的未知符号使用相关的 #include  
  
-   **添加 using namespace/Fully qualify symbol** - 与上一项类似，但是是用于命名空间  
  
-   **添加缺少的分号**  
  
-   **MSDN 帮助** - 搜索用于你的错误消息的 MSDN  
  
 你可以将鼠标悬停在波浪线上以获取灯泡，或者使用默认键盘快捷键 Ctrl+点 (Ctrl+.)。 注意，对于键盘快捷方式，你的插入点无需定位在特定的错误或令牌上；你只需将其与错误置于同一行，以调用该行上任何内容的建议。  
  
## <a name="see-also"></a>另请参阅  
 [设置语言特定的编辑器选项](../../ide/reference/setting-language-specific-editor-options.md)   
 [在 C++ 中重构（VC 博客）](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)



<!--HONumber=Feb17_HO4-->


