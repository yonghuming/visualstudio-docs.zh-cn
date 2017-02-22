---
title: "“编译”页, 项目设计器 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesCompile"
helpviewer_keywords: 
  - "编译, Visual Basic 项目"
  - "编译, 选项 [Visual Basic]"
  - "编译器, Visual Basic 选项"
  - "编译, 指令 [Visual Basic]"
  - "编译器选项, Visual Basic"
  - "项目设计器, “编译”页"
  - "项目设计器中的“编译”页"
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 60
caps.handback.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “编译”页, 项目设计器 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用项目设计器的**“编译”**页可以指定编译说明。  还可以在此页上指定高级编译器选项和预先生成或后期生成事件。  
  
 访问 **编译** 页上，选择项目节点 \(不是 **解决方案** 节点\)。**解决方案资源管理器**。  然后选择 **项目**，在菜单栏上 **属性**。  当项目设计器出现时，单击**“编译”**选项卡。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## 配置和平台  
 通过以下设置可以选择要显示或修改的配置和平台。  
  
> [!NOTE]
>  通过简化的生成配置，项目系统确定是生成调试版本还是发布版本。  因此，不显示**“配置”**和**“平台”**列表。  有关更多信息，请参见[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)。  
  
 **配置**  
 指定要显示或修改的配置设置。  设置为**“调试”**（默认值）、**“发布”**，或**“所有配置”**。  有关更多信息，请参见[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)和[如何：创建和编辑配置](../../ide/how-to-create-and-edit-configurations.md)。  
  
 **平台**  
 指定要显示或修改的平台设置。  您可以指定 **任何 CPU** \(默认值\)，**x64**或 **x86**。  有关更多信息，请参见[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)。  
  
## 编译器配置选项  
 可以使用以下设置来设置编译器配置选项。  
  
 **生成输出路径**  
 指定该项目配置的输出文件的位置。  在此框中键入生成输出的路径，或单击**“浏览”**按钮来选择路径。  注意，此路径是相对路径；如果输入绝对路径，它将保存为相对路径。  默认路径是 bin\\Debug\\ 或 bin\\Release\\。  有关更多信息，请参见[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)。  
  
 通过简化的生成配置，项目系统确定是生成调试版本还是发布版本。  **“调试”**菜单上的**“生成”**命令 \(F5\) 会将生成版本放置在调试位置，而与指定的**“输出路径”**无关。  但是，**“生成”**菜单上的**“生成”**会将生成版本放置在指定的位置。  有关更多信息，请参见[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)。  
  
 **Option Explicit**  
 指定是否允许隐式声明变量。  选择“开启” 对变量进行显式声明。  这将使编译器在变量使用之前尚未声明的情况下报告错误。  选择**“Off”**可允许隐式声明变量。  
  
 此设置对应于 [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) 编译器选项。  
  
 如果源代码文件包含 [Option Explicit 语句](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)，则语句中 `On` 或 `Off` 值将重写 **Option Explicit** 设置，该设置在 **编译页面** 上。  
  
 当您创建新项目时，**“编译页”**选项卡上的**“Option Explicit”**设置将在**“Options”**对话框中设为**“Option Explicit”**设置值。  要在此对话框中查看或更改设置，请在“工具”菜单上单击“选项”。  在**“选项”**对话框中展开**“项目和解决方案”**，然后单击**“VB 默认值”**。  **“VB 默认值”**中 **Option Explicit** 的初始默认设置为**“开启”**。  
  
 通常将 `Off` 设置成**“可选直白”** 是不恰当的操作。  您可能在一个或多个位置拼错了变量名，这在程序运行时，可能会导致意外的结果。  
  
 **Option Strict**  
 指定是否强制实施严格类型语义。  当“Option Strict”为“On”时，以下情况将导致编译时错误：  
  
-   隐式收缩转换  
  
-   后期绑定  
  
-   在 `Object` 类型中隐式键入结果  
  
 当存在为收缩转换的隐式数据类型转换时，出现隐式收缩转换错误。  有关更多信息，请参见[Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)、[隐式转换和显式转换](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)和[扩大转换和收缩转换](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)。  
  
 如果某个对象被分配给声明为 `Object` 类型的变量的属性或方法，该对象就是后期绑定的。  有关更多信息，请参见[Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)和[早期绑定和后期绑定](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding)。  
  
 适当的类型无法推断为已声明的变量时出现隐式对象类型错误，因此将推断 `Object` 类型。  这主要发生在您使用 `Dim` 语句（而不使用 `As` 子句）声明一个变量，并且 `Option Infer` 处于关闭状态的情况。  有关更多信息，请参见[Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)、[Option Infer 语句](/dotnet/visual-basic/language-reference/statements/option-infer-statement) 和 [Visual Basic 语言规范](/dotnet/visual-basic/reference/language-specification)。  
  
 **Option Strict** 设置对应于 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) 编译器选项。  
  
 如果源代码文件包含 [Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)，则语句中 `On` 或 `Off` 值将重写  **Option Strict** 设置，该设置在 **编译页面** 上。  
  
 创建项目时，**“编译”**页上的**“选项严格”**设置将在**“选项”**对话框中设置为**“选项严格”**设置的值。  要在此对话框中查看或更改设置，请在“工具”菜单上单击“选项”。  在**“选项”**对话框中展开**“项目和解决方案”**，然后单击**“VB 默认值”**。  **“VB 默认值”**中 **Option Strict** 的初始默认设置为**“关闭”**。  
  
 **选择严格的个别警告。 “编译页面”**的**“警告配置”**有与 `Option Strict` 开启时引起编译时间错误的三种情况相对应的设置。  这些设置如下：  
  
-   **隐式转换**  
  
-   **后期绑定；调用在运行时可能失败**  
  
-   **隐式类型；假定的对象**  
  
 将**“选项严格”**设置为**“开启”**时，所有这三个警告配置设置都将被设置为**“错误”**。  将**“选项严格”**设置为**“关闭”**时，所有这三个设置都被设置为**“无”**。  
  
 可单独将各警告配置设置更改为**“无”**、**“警告”**或**“错误”**。  如果三个警告配置都设置为 **出错**，则 `On` 会出现在 `Option strict` 框中。  如果三个都设置为 **无**，则 `Off` 会出现在此框中。  对于这些配置的任何其他组合，显示 **“（自定义）”**。  
  
 **Option Compare**  
 指定要使用的字符串比较的类型。  选择**“二进制”**以指示编译器使用二进制的区分大小写的字符串比较。  选择**“Text”**则使用特定于区域设置的、不区分大小写的文本字符串比较。  
  
 此设置对应于 [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) 编译器选项。  
  
 如果源代码文件包含 [Option Compare 语句](/dotnet/visual-basic/language-reference/statements/option-compare-statement)，则语句中 `Binary` 或 `Text` 值将重写 **比较选项** 设置，该设置在 **编译页面** 上。  
  
 创建项目时，**“编译”**页上的**“选项比较”**设置将在**“选项”**对话框中设置为**“选项比较”**设置的值。  要在此对话框中查看或更改设置，请在“工具”菜单上单击“选项”。  在**“选项”**对话框中展开**“项目和解决方案”**，然后单击**“VB 默认值”**。  **“VB 默认值”**中 **Option Compare** 的初始默认设置为**“二进制”**。  
  
 **Option Infer**  
 指定是否允许变量声明中的局部类型推理。  选择**“开启”**，允许使用局部类型推理。  选择**“Off”**可阻止局部类型推理。  
  
 此设置对应于 [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) 编译器选项。  
  
 如果源代码文件包含 [Option Infer 语句](/dotnet/visual-basic/language-reference/statements/option-infer-statement)，则语句中 `On` 或 `Off` 值重  **Option Infer** 设置，该设置在 **编译页面** 上。  
  
 创建项目时，**“编译”**页上的**“选项推断”**设置将在**“选项”**对话框中设置为**“选项推断”**设置的值。  要在此对话框中查看或更改设置，请在“工具”菜单上单击“选项”。  在**“选项”**对话框中展开**“项目和解决方案”**，然后单击**“VB 默认值”**。  **“VB 默认值”**中 **Option Infer** 的初始默认设置为**“开启”**。  
  
 **目标 CPU**  
 指定输出文件面向的目标处理器。  为所有 32 位 Intel 兼容处理器指定任何 64 位 Intel 兼容处理器的 **x86**，所有 ARM 处理器的 **x64**，**ARM** 或 **任何 CPU** 指定任何处理器是可以接受的。  因为它在硬件类型，的最大允许应用程序运行**任何 CPU** 是新项目的默认值。  
  
 有关更多信息，请参见[\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform)。  
  
 **首选 32 位**  
 如果 **Prefer32\-bit** 复选框，应用程序运行为窗口中的 32 位和 64 位版本的 32 位应用程序。  否则，应用程序身份运行在 32 位版本的 windows 上 32 位应用程序将在 64 位版本的 windows 上为 64 位应用程序。  
  
 运行，因为为 64 位应用程序加倍指针大小和可能导致兼容性问题由于完整 32 位的库。  它只有 \+ 当快很多方式运行还是需要多内存，4 GB 很有意义运行应用程序标记为 64 位。  
  
 只有 \+ 当满足以下所有条件，此复选框可用：  
  
-   在 **编译页**，**目标 CPU** 列出其设置为 **任何 CPU**。  
  
-   在 **应用程序页**，**应用程序类型** 列表指定该项是应用程序。  
  
-   在 **应用程序页**，**目标框架** 列表指定 .NET framework 4.5。  
  
 **警告配置**  
 此表列出了生成条件以及对应于每个条件的通知级别（**“无”**、**“警告”**或**“错误”**）。  
  
 默认情况下，在编译期间，所有编译器警告都被添加到任务列表中。  选择**“禁用所有警告”**可以指示编译器不发出警告或错误。  如果想要编译器将警告视为必须修复的错误，请选中**“将所有警告都视为错误”**。  
  
 **禁用所有警告**  
 指定是否允许编译器按照此文档中前面所述的**“条件和通知”**表中的指定发出通知。  默认情况下会清除此复选框。  选中此复选框可以指示编译器不发出警告或错误。  
  
 此设置对应于 [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) 编译器选项。  
  
 **将所有警告视为错误**  
 指定如何处理警告。  默认情况下，此复选框会被清除，以便所有警告通知仍设置为**“警告”**。  选中此复选框可将所有警告通知更改为**“错误”**。  
  
 此选项只有在清除**“禁用所有警告”**时才可用。  
  
 **生成 XML 文档文件**  
 指定是否生成文档信息。  默认情况下，此复选框处于选中状态，指示编译器生成文档信息并将这些信息包含在一个 XML 文件中。  清除此复选框可指示编译器不创建任何文档。  
  
 此设置对应于 [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) 编译器选项。  
  
 **注册 COM 互操作**  
 指定托管应用程序是否将公开一个 COM 对象（可调用 COM 的包装），以使 COM 对象可以与托管应用程序进行交互。  
  
 默认情况下，此复选框会被清除，以指定应用程序不允许 COM 互操作。  选中此复选框可允许 COM 互操作。  
  
 对于“Windows 应用程序”或“控制台应用程序”项目，此选项不可用。  
  
 **生成事件**  
 单击此按钮可访问**“生成事件”**对话框。  使用此对话框可以为项目指定预先生成或后期生成配置说明。  此对话框仅适用于 Visual Basic 项目。  有关更多信息，请参见[“生成事件”对话框 \(Visual Basic\)](../../ide/reference/build-events-dialog-box-visual-basic.md)。  
  
 **高级编译选项**  
 单击此按钮可访问**“高级编译器设置”**对话框。  使用**“高级编译器设置”**对话框可以指定项目的高级生成配置属性。  此对话框仅适用于 Visual Basic 项目。  有关更多信息，请参见[“高级编译器设置”对话框 \(Visual Basic\)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)。  
  
## 请参阅  
 [Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)   
 [Managing Compilation Properties](http://msdn.microsoft.com/zh-cn/94308881-f10f-4caf-a729-f1028e596a2c)   
 [如何：指定生成事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Visual Basic 命令行编译器](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [如何：创建和编辑配置](../../ide/how-to-create-and-edit-configurations.md)