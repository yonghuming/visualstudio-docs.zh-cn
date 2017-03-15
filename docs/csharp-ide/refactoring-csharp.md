---
title: "重构 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.preview"
  - "vs.csharp.refactoring.issues"
  - "vs.csharp.refactoring.buildwarning"
  - "VS.PreviewChanges"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "重构 [C#]"
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 重构 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

重构是在编写代码后在不更改代码的外部行为的前提下通过更改代码的内部结构来改进代码的过程。  
  
 Visual C\# 在**“重构”**菜单上提供了以下重构命令：  
  
-   [提取方法重构 \(C\#\)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [重命名重构 \(C\#\)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [封装字段重构 \(C\#\)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [提取接口重构 \(C\#\)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [移除参数重构 \(C\#\)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [重新排列参数重构 \(C\#\)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## 多项目重构  
 Visual Studio 支持对位于同一解决方案中的项目进行多项目重构。  更正文件间的引用的所有重构操作也会更正同一语言的所有项目间的引用。  这适用于所有项目间的引用。  例如，如果具有一个引用类库的控制台应用程序，则当您重命名类库类型（使用 `Rename` 重构操作）时，也将更新该控制台应用程序中对类库类型的引用。  
  
## 更改预览  
 许多重构操作都可提供这样的机会：在提交引用更改之前，检查重构操作将对代码执行的所有引用更改。  对于这些重构操作，将在重构对话框中显示**“预览引用更改”**选项。  选择该选项并接受重构操作后，将显示**“预览更改”**对话框。  请注意，**“预览更改”**对话框具有两个视图。  底部视图将显示代码，其中包含了因重构操作而进行的所有引用更新。  按下**“预览更改”**对话框中的**“取消”**将停止重构操作，并且不会对代码进行任何更改。  
  
## 重构警告  
 如果编译器没有完全理解您的程序，因此重构引擎可能不会更新所有适当的引用，这时将显示警告对话框。  此警告对话框也为您提供了在提交更改之前在**“预览更改”**对话框中预览代码的机会。  
  
> [!NOTE]
>  如果方法中包含语法错误（IDE 以红色波浪下划线指示），则重构引擎将不会更新该方法中对元素的任何引用。  下面的示例阐释了此行为。  
  
 默认情况下，如果执行重构操作而不预览引用更改，并且在程序中检测到编译错误，则开发环境将显示此警告对话框。  
  
 如果执行已启用**“预览引用更改”**的重构操作，并在程序中检测到编译错误，则开发环境将在**“预览更改”**对话框的底部显示下面的警告消息，而不会显示**“重构警告”**对话框：  
  
 **当前未生成项目或其中一个依赖项。  可能未更新引用。**  
  
 此重构警告只可用于提供**“预览引用更改”**选项的重构操作。  
  
## 容错重构和验证结果  
 重构可以容错。  换言之，可以在无法生成的项目中执行重构。  但是，在这些情况下，重构过程可能不会正确更新不明确的引用。  
  
 如果重构引擎检测到编译错误或发现重构操作意外导致代码引用绑定到与原始绑定目标不同的目标（重新绑定问题），则**“验证结果”**对话框会向您发送相应通知。  
  
 若要启用验证结果功能，请在**“工具”**菜单上单击**“选项”**。  在**“选项”**对话框中，展开**“文本编辑器”**，然后展开**“C\#”**。  单击**“高级”**，并选中**“验证重构结果”**复选框。  
  
 **“验证结果”**对话框区分两种重新绑定问题的差异。  
  
### 其定义将不再是重命名的符号的引用  
 如果引用指的不再是已重命名的符号，则会出现这种重新绑定问题。  例如，考虑以下代码：  
  
```c#  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 如果使用重构功能将 `a` 重命名为 `b`，则将显示此对话框。  现在，对重命名变量 `a` 的引用绑定到传递到构造函数的参数，而不是绑定到字段。  
  
### 其定义现在将成为重命名的符号的引用  
 如果以前指的并不是重命名的符号的引用现在指的是重命名的符号，则将出现这种重新绑定问题。  例如，考虑以下代码：  
  
```c#  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 如果您使用重构功能将 `OtherMethod` 重命名为 `Method`，则将显示此对话框。  现在，`Main` 中的引用指的是接受 `int` 参数的重载方法，而不是接受 `object` 参数的重载方法。  
  
## 请参阅  
 [使用 Visual C\# 开发环境](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [如何：还原 C\# 重构代码段](../Topic/How%20to:%20Restore%20C%23%20Refactoring%20Snippets.md)