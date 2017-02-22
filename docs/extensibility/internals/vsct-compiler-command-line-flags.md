---
title: "VSCT 编译器命令行标志 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 文件编译"
  - "命令表文件编译 （VSCT 文件）"
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# VSCT 编译器命令行标志
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 命令表 (VSCT) 编译器提供了命令行开关，以确保成功编译的.vsct 文件。  
  
## <a name="command-line-parameters"></a>命令行参数  
 若要查看从基本 VSCT 帮助 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **命令** 窗口中，导航到 *Visual Studio SDK 安装路径*\VisualStudioIntegration\Tools\Bin\ 文件夹，然后键入︰  
  
```  
vsct /?  
```  
  
 这将返回︰  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  字符-（连字符） 和 / （正斜杠） 是这两个接受的表示法，该值指示命令行参数。  
  
 可接受的标志和它们的含义如下所示。  
  
|开关|描述|  
|------------|-----------------|  
|-D|指定已定义的任何其他符号。|  
|-I|指示附加的包含应在解析文件引用时使用的路径。|  
|-L|指定 <xref:System.Globalization.CultureInfo> 区域性名称，例如"EN-US"。|  
|-E|发出命令项后, 跟 [C &#124; 的指定命名空间中的 C# 对象H &#124;N]:*filename*其中 C = C#，H = c + + 标头，N = 命名空间。 需要适用于 C# 命名空间。|  
|-v|详细输出。|  
  
 -L 开关将指示编译器选择字符串以产生二进制.cto 文件对应于一组给定 <xref:System.Globalization.CultureInfo> 区域性名称。 指定的区域性名称应与一个或多个语言特性匹配 [字符串元素](../../extensibility/strings-element.md) .vsct 文件中。 如果字符串元素不具有任何语言的属性，它从包含继承 [CommandTable 元素](../../extensibility/commandtable-element.md)。  
  
 .Vsct 文件可能具有多个字符串元素，并且每个可能具有不同的 Language 特性。 全球化被通过运行多次的 VSCT 编译器并更改每个区域性名称-L 交换机。  
  
 如果通过使用-L 开关指定的区域性名称不匹配任何字符串元素的 Language 特性，编译器将尝试匹配的语言和不的区域。 例如，如果找不到"EN-US"，编译器将改为尝试"en"。 如果不成功，它将尝试的操作系统的当前区域性。 如果不成功，它将找到的第一个字符串元素进行编译。  
  
 若要发出包含通过命令表中，使用的符号的 C 样式标头文件或发出包含命令符号的对象的 C# 文件，可以使用-E 开关。  
  
 -D 和 – 我交换机都有具有相同名称的 Cl.exe C 预处理器标志的语法。 – D 具有 X = Y 的格式定义用于基于 XML 的扩展 \< 定义> 中测试 `Condition` 属性。 – 我包括路径用于解析 \< 包括>, ，\< Extern> 和 \< 位图> 文件引用。 有关详细信息，请参阅 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)。  
  
 VSCT 编译器还可以反编译以前生成的二进制文件。 若要执行此操作，提供的二进制文件 \< infile>。   如果二进制文件由 VSCT 编译器生成的它将包含已嵌入其符号，并且将生成与中的符号名称的输出 \< 符号> 部分的输出。 如果二进制文件由 CTC 编译器生成的则输出将包含实际的 Guid 和 Id。 如果生成的当前版本的 Ctc.exe *.ctsym 文件处于与二进制输入文件相同的文件夹，则将该文件中加载符号，并将其用于输出。  
  
## <a name="see-also"></a>请参阅  
 [Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)   
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)