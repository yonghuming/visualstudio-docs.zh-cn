---
title: "自定义生成 | Microsoft Docs"
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: zh-cn
ms.lasthandoff: 06/15/2017

---
# <a name="customize-your-build"></a>自定义生成
在 MSBuild 15 版之前的版本中，如果要向解决方案中的项目提供新的自定义属性，必须手动向解决方案中的每个项目文件添加一个针对该属性的引用。 另外，还必须在 .props 文件中定义属性，在解决方案的每个项目中显式导入该 .props 文件。

但现在通过在存储库根目录下名为 Directory.Build.props 的单个文件中定义一个新属性，只需一步即可向每个项目添加该属性。 MSBuild 运行时，Microsoft.Common.props 会搜索 Directory.Build.props 文件的目录结构（Microsoft.Common.targets 将查找 Directory.Build.targets）。 如果找到，就会导入该属性。 Directory.Build.props 是用户定义文件，对目录下的项目提供自定义选项。

## <a name="directorybuildprops-example"></a>Directory.Build.props 示例
例如，如果想要使所有项目都可以访问新的 Roslyn /deterministic 功能（属性 `$(Deterministic)` 在 Roslyn CoreCompile 目标中公开了此功能），可以执行以下操作。

1. 在存储库根目录中创建一个名为 Directory.Build.props 的新文件。
2. 将以下 XML 添加到此文件。

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. 运行 MSBuild。 项目现有的 Microsoft.Common.props 和 Microsoft.Common.targets 导入会找到该文件并将其导入。

## <a name="search-scope"></a>搜索范围
搜索 Directory.Build.props 文件时，MSBuild 将从项目位置 ($(MSBuildProjectFullPath)) 向上搜索目录结构，找到 Directory.Build.props 文件后停止。 例如，如果 $(MSBuildProjectFullPath) 为 c:\users\username\code\test\case1，MSBuild 将从该位置开始搜索，然后向上搜索目录结构，直到找到 Directory.Build.props 文件，如以下目录结构中所示。

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
解决方案文件的位置与 Directory.Build.props 无关。

## <a name="import-order"></a>导入顺序

Directory.Build.props 很早便已导入 Microsoft.Common.props，因此它无法使用后来定义的属性。 因此，请避免引用尚未定义的属性（否则计算结果将为空）。

从 NuGet 包导入 .targets 文件后，会从 Microsoft.Common.targets 导入 Directory.Build.targets。 因此，可使用它替代在大部分生成逻辑中定义的属性和目标，但有时可能必须在最终导入后在项目文件内进行自定义。

## <a name="see-also"></a>另请参阅  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)   

