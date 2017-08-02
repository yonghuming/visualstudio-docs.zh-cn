---
title: "在 VSIX v3 Ngen 支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 46b6f4d13b4c1938797dbe6cf6023e3c8c42d1ed
ms.lasthandoff: 03/07/2017

---
# <a name="ngen-support-in-vsix-v3"></a>在 VSIX v3 Ngen 支持

使用 Visual Studio 2017 和新的 VSIX v3 （版本 3） 扩展清单的格式，现在扩展开发人员可以"ngen"及其在安装时的程序集。

下面是什么"ngen"未解释的 MSDN 一段摘录︰

>本机映像生成器 (Ngen.exe) 是一种提高托管应用程序性能的工具。 Ngen.exe 创建本机映像（包含经编译的特定于处理器的机器代码的文件），并将它们安装到本地计算机上的本机映像缓存中。 运行时可从缓存中使用本机映像，而不必使用实时 (JIT) 编译器编译原始程序集。
>
>从[Ngen.exe （本机映像生成器）](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

到"ngen"的程序集，顺序 VSIX 必须安装"每个实例每台计算机"。 可以通过检查 extension.vsixmanifest 设计器中的"所有用户"复选框来启用该选项︰

![检查所有用户](~/extensibility/media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>如何启用 Ngen

若要启用程序集的 ngen，可以使用**属性**Visual Studio 窗口中的。

有 4 个属性可设置︰

1. **Ngen** （布尔值） – 如果为 true，Visual Studio 安装程序将"ngen"程序集。
2. **Ngen 应用程序**(string) – Ngen 提供机会来使用应用程序的 app.config 文件来解析程序集依赖项。 此值应设置为应用程序的 app.config 你想要使用 （相对于 Visual Studio 安装目录）。
3. **Ngen 体系结构**(enum) – 体系结构，以本机编译您的程序集。 选项为︰。 NotSpecified b。 X86 c。 X64 d。 全部
4. **Ngen 优先级**（介于 1 和 3 之间的整数） – 中所述的 Ngen 优先级别[Ngen.exe 优先级别](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3)。

下面我们来看**属性**中操作的窗口︰

![在属性中的 ngen](~/extensibility/media/ngen-in-properties.png)

这会将元数据添加到 VSIX 项目的.csproj 文件内的项目引用︰

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**注意︰**如果您愿意，您可以直接编辑.csproj 文件。

## <a name="extra-information"></a>附加信息

属性设计器更改应用于以外的其他项目的引用;您可以在您的项目以及内部设置项的 Ngen 元数据 （使用上面所述的相同方法） 长的项是.NET 程序集。
