---
title: "“选项”->“文本编辑器”->“C/C++”->“实验”| Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
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
author: gewarren
ms.author: gewarren
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
ms.technology:
- vs-ide-general
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 1677db7d5af93db8a378d598332e6a6d52f09bdd
ms.contentlocale: zh-cn
ms.lasthandoff: 08/14/2017

---
# <a name="options-text-editor-cc-experimental"></a>选项, 文本编辑器, C/C++, 实验
通过更改这些选项，你可以在用 C 或 C++ 进行编程时更改与 IntelliSense 和浏览数据库有关的行为。 这些功能实际上是实验性的，且可能会在 Visual Studio 将来版本中进行修改或删除。 本主题介绍 Visual Studio 2017 中的各选项。 有关 Visual Studio 2015 的信息，请参阅[“选项”->“文本编辑器”->“C/C++”->“实验”](https://msdn.microsoft.com/library/mt591979.aspx) 
  
 若要访问此属性页，请按 **Control+Q**，激活 `Quick Launch`，然后键入“实验”。 在键入前几个字母后，快速启动将查找该页面。 此外，还可以选择**工具 | 选项**，依次展开“文本编辑器”和“C/C++”，再选择“实验”。  

 这些功能在 Visual Studio 2017 安装中可用。  
  
> [!NOTE]
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 请参阅[个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="enable-predictive-intellisense"></a>启用预测 Intellisense
预测 IntelliSense 限制 IntelliSense 下拉列表中显示的结果数，以便你仅看到与上下文相关的结果。 例如，如果键入 <code>int x =</code> 并调用 IntelliSense 下拉列表，只会看到整数或返回整数的函数。 预测 IntelliSense 在默认情况下是关闭的。

## <a name="enable-faster-project-load"></a>启用更快的项目加载 
Visual Studio 2017 版本 15.3 及更高版本：此功能当前被称为“启用项目缓存”，并已被移至 [VC++ 项目设置](vcpp-project-settings-projects-and-solutions-options-dialog-box.md)属性页。
此选项使 Visual Studio 能缓存项目数据，以便下次打开该项目时，它能直接加载缓存的数据，而无需通过项目文件重新对其计算。 使用缓存数据可显著缩短项目加载时间。  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Visual Studio 库中的其他功能
有关 Visual Studio 库中的其他文本编辑器功能，请参阅[此处](http://go.microsoft.com/fwlink/?LinkId=692016)的列表。 一个示例是 [C++ 快速修补](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)，它支持以下内容：  
  
-   **添加缺少的 #include** - 建议对你代码中的未知符号使用相关的 #include  
  
-   **添加 using namespace/Fully qualify symbol** - 与上一项类似，但是是用于命名空间  
  
-   **添加缺少的分号**  
  
-   **MSDN 帮助** - 搜索用于你的错误消息的 MSDN  
  
 你可以将鼠标悬停在波浪线上以获取灯泡，或者使用默认键盘快捷键 Ctrl+点 (Ctrl+.)。 注意，对于键盘快捷方式，你的插入点无需定位在特定的错误或令牌上；你只需将其与错误置于同一行，以调用该行上任何内容的建议。  
  
## <a name="see-also"></a>另请参阅  
 [设置语言特定的编辑器选项](../../ide/reference/setting-language-specific-editor-options.md)   
 [在 C++ 中重构（VC 博客）](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)

