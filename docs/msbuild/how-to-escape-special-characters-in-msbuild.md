---
title: "如何：转义 MSBuild 中的特殊字符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "转义的特殊字符"
  - "转义的字符"
  - "转义字符"
  - "MSBuild，转义特殊字符"
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>如何：转义 MSBuild 中的特殊字符
某些字符在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件中具有特殊意义。 这些字符的示例包括分号 (;) 和星号 (*)。 有关这些特殊字符的完整列表，请参阅 [MSBuild 特殊字符](../msbuild/msbuild-special-characters.md)。  
  
 要将这些特殊字符用作项目文件中的文本，必须使用语法 %*xx* 来指定它们，其中 *xx* 表示字符的 ASCII 十六进制值。  
  
## <a name="msbuild-special-characters"></a>MSBuild 特殊字符  
 一个使用特殊字符的例子便是项列表的 `Include` 属性。 例如，以下项列表声明两个项：`MyFile.cs` 和 `MyClass.cs`。  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 如果要声明其名称中包含分号的项，则必须使用 %*xx* 语法来转义分号，阻止 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 声明两个单独的项。 例如，以下项转义分号，并且声明一个名为 `MyFile.cs;MyClass.cs` 的项。  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>将 MSBuild 特殊字符用作文本字符  
  
-   使用表示法 %*xx* 替换特殊字符，其中 *xx* 表示 ASCII 字符的十六进制值。 例如，如需将星号 (*) 用作原义字符，可使用值 `%2A`。  
  
## <a name="see-also"></a>另请参阅  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)
 [项](../msbuild/msbuild-items.md)


<!--HONumber=Feb17_HO4-->


