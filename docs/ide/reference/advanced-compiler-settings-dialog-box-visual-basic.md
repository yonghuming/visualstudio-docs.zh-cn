---
title: "“高级编译器设置”对话框 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedCompile"
helpviewer_keywords: 
  - "“高级编译器设置”对话框"
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# “高级编译器设置”对话框 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用**“项目设计器”**的**“高级编译器设置”**对话框可以指定项目的高级生成配置属性。  此对话框仅适用于 Visual Basic 项目。  
  
### 访问此对话框  
  
1.  在 **解决方案资源管理器**，选择项目节点 \(不是 **解决方案** 节点\)。  
  
2.  在**“项目”**菜单上，单击**“属性”**。  当**“项目设计器”**出现时，单击**“编译”**选项卡。  
  
3.  在 [“编译”页, 项目设计器 \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md) 中，选择**“配置”**和**“平台”**。  在简化生成配置中，不显示**“配置”**和**“平台”**列表。  有关更多信息，请参见[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)。  
  
4.  单击**“高级编译选项”**。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## 优化  
 以下选项指定了一些优化，在某些情况下这些优化可以使程序文件变得更小，使程序更快地运行或加速生成进程。  
  
 **取消整数溢出检查**  
 默认情况下，清除此复选框可使整数溢出检查。  选中此复选框取消整数溢出检查。  如果选中此复选框，整数计算可能更快。  但是，在中，如果取消溢出检查和数据类型容量溢出，不正确的结果可能存储，而不会引发的错误。  
  
 如果溢出条件签出和整数运算溢出，<xref:System.OverflowException> 引发异常。  如果溢出条件不会检查，整数运算溢出不引发异常。  
  
 **启用优化**  
 默认情况下，此复选框被清除以禁用编译器优化。  选中此复选框可启用编译器优化。  编译器优化可以使输出文件更小、速度更快并且更有效率。  但是，在中，由于优化原因在输出文件的代码重新排列，编译器优化可以使调试困难。  
  
 **DLL 基址**  
 此文本框用十六进制格式显示默认的 DLL 基址。  在类库和控件库项目中，可以使用此文本框来指定要在创建 DLL 时所使用的基址。  
  
 **生成调试信息**  
 从列表中选择**“None”**、**“Full”**或**“pdb\-only”**。  **“None”**指定不生成任何调试信息。  **“Full”**指定生成全部的调试信息，而**“pdb\-only”**指定只生成 PDB 调试信息。  默认情况下，此选项设置为**“Full”**。  
  
## 编译常数  
 条件编译常数也有作用类似于使用 [\#Const](/dotnet/visual-basic/language-reference/directives/const-directive) 预处理器指令在源文件，除此之外，定义的常数是公共的并且适用于在项目的所有文件。  可以使用 [\#If… then…else \#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) 指令一起使用条件编译常数有条件地编译源文件。  请参见 [条件编译](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)。  
  
 **定义 DEBUG 常数**  
 默认情况下，选中此复选框以指定设置一个 DEBUG 常数。  
  
 **定义 TRACE 常数**  
 默认情况下，选中此复选框以指定设置一个 TRACE 常数。  
  
 **自定义常数**  
 在此文本框中输入应用程序的任何自定义常数。  应用逗号将各项分隔开来，形式如下：Name1\="Value1",Name2\="Value2",Name3\="Value3"。  
  
## 其他设置  
 **生成序列化程序集**  
 此设置可以指定编译器是否创建 XML 序列化程序集。  序列化程序集可以提高 <xref:System.Xml.Serialization.XmlSerializer> 的启动性能，前提是您已使用该类对代码中的类型进行了序列化。  默认情况下，此选项被设置为**“自动”**，它指定该序列化程序集只能在您已经使用 <xref:System.Xml.Serialization.XmlSerializer> 将代码中的类型编码为 XML 才能生成。  **“关”**指定无论您的代码是否使用 <xref:System.Xml.Serialization.XmlSerializer>，该序列化程序集都将不会生成。  **“开”**指定通常都会生成该序列化程序集。  序列化程序集被命名为 `TypeName`.XmlSerializers.dll。  
  
## 请参阅  
 [“编译”页, 项目设计器 \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)