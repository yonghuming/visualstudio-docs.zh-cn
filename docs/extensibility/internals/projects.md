---
title: "项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 842bef303d7a3211b8711920ef6cec357a876f8a
ms.lasthandoff: 02/22/2017

---
# <a name="projects"></a>项目
在 Visual Studio 中，项目是开发人员使用源代码文件和其他资源显示在组织的容器**解决方案资源管理器**。 通常情况下，项目是存储对源代码文件和资源，如位图文件的引用的文件 （例如，对于 C# 项目的.csproj 文件）。 项目的让组织、 生成、 调试和部署的源代码，请对 Web 服务和数据库，以及其他资源的引用。 Vspackage 可以扩展 Visual Studio 项目系统以三种主要方式︰*项目类型*，*项目子类型*，和*自定义工具*。  
  
## <a name="in-this-section"></a>本节内容  
 [项目类型](../../extensibility/internals/project-types.md)  
 *项目类型*添加对新类型的项目，如编程语言的支持。 例如，Visual Studio 支持每种语言有其自己的项目类型，并且 IronPython 集成示例包括 IronPython 语言的项目类型。 您必须创建一个项目类型为非 C# 或 Visual Basic 自定义如何项将生成、 调试、 部署，并显示在语言**解决方案资源管理器**。 有关详细信息，请参阅[项目类型](../../extensibility/internals/project-types.md)。  
  
 [项目子类型](../../extensibility/internals/project-subtypes.md)  
 *项目的子类型*基于项目类型和可用于自定义生成、 调试和部署项目的方式。 Visual Studio 将使用用于智能设备项目; 项目子类型它们通过将新生成的程序从开发计算机复制到目标设备自定义部署。 C# 和 Visual Basic 项目类型可用于根据项目的子类型;C + + 项目类型不能。 您自己的项目类型还可为基础的项目子类型。 有关详细信息，请参阅[项目子类型](../../extensibility/internals/project-subtypes.md)。  
  
 [Web 项目](../../extensibility/internals/web-projects.md)  
 解释又会创建 Web 应用程序的 Web 项目。  
  
 [生成新的项目︰ 实质上，第&1; 部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)和[生成新的项目︰ 实质上，第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 介绍什么实际发生的情况时创建一个新项目。  
  
 [VSSDK 示例](../../misc/vssdk-samples.md)  
 说明 VSSDK 处理项目和解决方案的示例。  
  
## <a name="related-sections"></a>相关章节  
 [在 Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 介绍了 Visual Studio 可扩展性的不同方面。
