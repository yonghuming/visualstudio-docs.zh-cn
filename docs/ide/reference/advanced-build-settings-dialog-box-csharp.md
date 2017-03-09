---
title: "“高级生成设置”对话框 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 82ec5d2db35da72beb017e15d1c271f751b5f56b
ms.lasthandoff: 02/22/2017

---
# <a name="advanced-build-settings-dialog-box-c"></a>“高级生成设置”对话框 (C#)
使用“项目设计器”的“高级生成设置”对话框来指定项目的高级生成配置属性。 此对话框仅适用于 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 项目。  
  
## <a name="general"></a>常规  
 通过以下选项可以设置常规高级设置。  
  
 **语言版本**  
 指定要使用的语言版本。 每个版本中的功能集是不同的，因此，可使用此选项强制编译器仅允许已实现功能的子集，或仅启用与现有标准兼容的功能。 此设置具有以下选项：  
  
-   **ISO-1**  
  
     面向 ISO-1 标准功能。  
  
-   **default**  
  
     面向当前版本。  
  
 有关详细信息，请参阅 [/langversion（C# 编译器选项）](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)。  
  
 **内部编译器错误报告**  
 指定是否向 Microsoft 报告编译器错误。 如果设置为“提示”（默认），则在发生内部编译器错误时将收到提示，可以选择向 Microsoft 发送电子版错误报告。 如果设置为“发送”，则将自动发送错误报告。 如果设置为“队列”，则错误报告将排入队列。 如果设置为“无”，将仅在编译器的文本输出中报告错误。 有关详细信息，请参阅 [/errorreport（C# 编译器选项）](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)。  
  
 **检查运算上溢/下溢**  
 针对整数算法语句不在 [checked](/dotnet/csharp/language-reference/keywords/checked) 或 [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) 关键字范围内并且产生的值超出数据类型范围的情况，指定此时是否会导致运行时异常。有关详细信息，请参阅 [/checked（C# 编译器选项）](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)。  
  
 **不引用 mscorlib.dll**  
 指定是否将 mscorlib.dll 导入程序，从而定义整个 <xref:System> 命名空间。 如果想要定义或创建自己的 <xref:System> 命名空间和对象，请选中此框。 有关详细信息，请参阅 [/nostdlib（C# 编译器选项）](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option)。  
  
## <a name="output"></a>输出  
 使用以下选项可以指定高级输出选项。  
  
 **调试信息**  
 指定编译器生成的调试信息的类型。 有关如何配置应用程序的调试性能的信息，请参阅[令映像更易于调试](http://msdn.microsoft.com/Library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3)。 此设置具有以下选项：  
  
-   **none**  
  
     指定不会生成任何调试信息  
  
-   **full**  
  
     允许将调试器附加到正在运行的程序。  
  
-   **pdbonly**  
  
     允许在调试器中启动程序时进行源代码调试，但仅在正在运行的程序附加到调试器时才显示汇编程序。  
  
 有关详细信息，请参阅 [/debug (C# 编译器选项)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)。  
  
 **文件对齐**  
 指定输出文件中各节的大小。 有效值为 **512**、**1024**、**2048**、**4096** 和 **8192**。 这些值以字节为单位。 每一节都在边界（此值的倍数）上对齐，这会影响输出文件的大小。 有关详细信息，请参阅 [/filealign（C# 编译器选项）](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)。  
  
 **DLL 基址**  
 指定要加载 DLL 的首选基址。 DLL 的默认基址由 [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] 公共语言运行时设置。 有关详细信息，请参阅 [/baseaddress（C# 编译器选项）](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option)。  
  
## <a name="see-also"></a>另请参阅  
 [（C# 编译器选项）](/dotnet/csharp/language-reference/compiler-options/index)   
 [“项目设计器”->“生成”页 (C#)](../../ide/reference/build-page-project-designer-csharp.md)
