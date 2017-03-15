---
title: "模板目录说明 (。Vsdir) 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".vsdir 文件"
  - "VSDIR 文件"
  - "模板目录说明文件"
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 模板目录说明 (。Vsdir) 文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

模板目录说明文件 (.vsdir) 是一个文本文件，使集成的开发环境 (IDE) 显示文件夹、 向导.vsz 文件和与你在对话框中的项目相关联的模板文件。 内容包括每个文件或文件夹的一个记录。 引用位置中的所有.vsdir 文件会都合并，尽管只有一个.vsdir 文件通常用于描述多个文件夹，向导或模板文件。  
  
 文件夹 （子目录） 中.vsdir 文件中，而是.vsdir 文件本身引用的文件位于同一目录中上。 IDE 当运行向导或显示的文件夹或文件中的 **新项目** 或 **添加新项** 对话框框中，IDE 将检查包含执行的文件，以确定是否存在.vsdir 文件的目录。 如果找到.vsdir 文件，则 IDE 将读取它来确定其是否包含的执行或显示的文件夹或文件的条目。 如果找到的项，IDE 将在向导的执行或内容的显示中使用的信息。  
  
 下面的代码示例摘自文件 SourceFiles.vsdir 中 \< EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems\Source_Files 注册表项︰  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 在这种情况下，两个记录为一个文件中。 新行 （回车符） 分隔每个记录。 每行代表不同的文件类型。 管道 (&#124;) 字符分隔每个记录中的字段。 单个目录可以包含多个具有不同的文件名称的.vsdir 文件或者你可以为每个文件类型的一个.vsdir 文件。  
  
## <a name="fields"></a>字段  
 下表列出了为每个记录指定的字段。  
  
|字段|描述|  
|-----------|-----------------|  
|相对路径名称 (RelPathName)|文件夹、 模板或.vsz 文件，如 HeaderFile.h 或 MyWizard.vsz 的名称。 此字段也可以用于表示的文件夹的名称。|  
|{clsidPackage}|启用对本地化的字符串，如 LocalizedName、 描述、 IconResourceId，和 SuggestedBaseName，在 VSPackage 的附属动态链接库 (DLL) 资源的访问的 VSPackage 的 GUID。 如果未提供 DLLPath，适用 IconResourceId。 **注意︰**  此字段是可选的除非一个或多个以前的字段的资源标识符。 此字段为对于与第三方向导，使其不本地化其文本相对应的.vsdir 文件通常为空。|  
|LocalizedName|向导的模板文件的本地化的名称。 此字段可以是字符串或窗体"#ResID"的资源标识符。 此名称显示在 **添加新项** 对话框。 **注意︰**  如果 LocalizedName 是资源的标识符，则 {clsidPackage} 是必需的。|  
|SortPriority|一个整数，表示此模板文件或向导的相对优先级。 例如，如果此项具有值为 1，此项是具有值其他项的 1 和之前所有项排序值 2 或更大的旁边显示。<br /><br /> 排序优先级是相对于同一目录中的项。 位于同一目录中可能有多个.vsdir 文件。 在这种情况下，从所有项 *。*该目录中的 vsdir 文件进行合并。 具有相同优先级的项中的显示名称不区分大小写字典中的顺序列出。  `_wcsicmp` 函数用于的项进行排序。<br /><br /> .Vsdir 文件中未介绍的项包括一个大于.vsdir 文件中列出的最高优先级编号的优先级。 结果是这些项位于而不考虑其名称显示列表的末尾。|  
|描述|模板文件或向导的本地化的说明。 此字段可以是字符串或窗体"#ResID"的资源标识符。 此字符串会显示在 **新项目** 或 **添加新项** 对话框中选择项目时。|  
|DLLPath 或者 {clsidPackage}|用于加载的模板文件或向导的图标。 通过使用 IconResourceId 情况下，为.dll 或.exe 文件的资源加载图标。 可以识别此.dll 或.exe 文件，通过使用完整路径或使用 VSPackage 的 GUID。 实现的 VSPackage 的 DLL 用于加载图标 （不附属 DLL）。|  
|IconResourceId|中的 DLL 或 VSPackage 的实现确定要显示的图标的 DLL 的资源标识符。|  
|标志 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|用于禁用或启用 **名称** 和 **位置** 字段上 **添加新项** 对话框。 值 **标志** 字段是必需的位标志的组合的十进制等效项。<br /><br /> 当用户选择一项上 **新建** 选项卡上，项目将决定是否名称字段和位置字段显示时 **添加新项** 第一次显示对话框。 某一项，通过.vsdir 文件，可以控制仅选择项目时是否将字段启用与已禁用。|  
|SuggestedBaseName|表示文件、 向导或模板的默认名称。 此字段为字符串或窗体"#ResID"的资源标识符。 IDE 使用此值提供项目的默认名称。 一个整数值，以使名称唯一的如 MyFile21.asp 追加此基的值。<br /><br /> 在前面的列表中，说明、 DLLPath、 IconResourceId、 标志和 SuggestedBaseNumber 仅适用于模板和向导文件。 这些字段不适用于文件夹。 BscPrjProjectItems 文件中的代码中阐释这一事实 \< EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems 注册表项。 此文件包含每个记录的四个字段具有三个记录 （一个用于每个文件夹）︰ RelPathName，{clsidPackage} LocalizedName 和 SortPriority。<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 当你创建向导文件时，你还应考虑以下问题。  
  
-   没有有意义的数据的任何非必填的字段应作为占位符包含 0 （零）。  
  
-   如果未不提供任何本地化的名称，向导文件中使用的相对路径名称。  
  
-   DLLPath 重写 clsidPackage 图标位置。  
  
-   如果未定义图标，IDE 会替换该扩展名的文件的默认图标。  
  
-   如果未不提供任何建议的基名称，则使用项目。  
  
-   如果你删除.vsz 文件和文件夹或模板文件，你还必须从.vsdir 文件删除其关联的记录。  
  
## <a name="see-also"></a>请参阅  
 [向导](../../extensibility/internals/wizards.md)   
 [向导 (。Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)