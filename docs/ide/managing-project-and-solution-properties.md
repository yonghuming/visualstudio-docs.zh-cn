---
title: "管理项目和解决方案属性 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 481153e7f3d609c56f313ff5ee9f3f1b511dc5ef
ms.contentlocale: zh-cn
ms.lasthandoff: 07/11/2017

---
# <a name="managing-project-and-solution-properties"></a>管理项目和解决方案属性
项目具有一些控制编译、调试、测试和部署的很多方面的属性。 有些属性在所有项目类型中是通用的，而有些则只用于特定语言或平台。 右键单击解决方案资源管理器中的项目节点并选择属性，或者将属性键入菜单栏中的“快速启动”搜索框，可访问项目属性。  
  
 ![项目上下文菜单](~/ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")  
  
 在项目树本身，.NET 项目也可能具有一个属性节点。  
  
 ![解决方案资源管理器树中的属性节点](~/ide/media/vs2015_props_se.png "VS2015_Props_SE")  
  
> [!TIP]
>  解决方案和项目项都具有一些属性；这些属性可在[属性窗口](../ide/reference/properties-window.md)中访问，而不是在**项目设计器**中访问。  
  
## <a name="project-properties"></a>项目属性  
 项目属性分到各个组且每组具有自己的属性页，而这些页面可能因语言和项目类型不同而有所不同。  
  
### <a name="c-visual-basic-and-f-projects"></a>C#、Visual Basic 和 F# 项目  
 在 C#、Visual Basic 和 F# 项目中，属性在“项目设计器”中公开。 下图显示了 C# 中的 WPF 项目的生成属性页：  
  
 ![Visual Studio 项目设计器](~/ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")  
  
 有关“项目设计器”中每个属性页的信息，请参阅[项目属性引用](../ide/reference/project-properties-reference.md)。  
  
### <a name="c-and-javascript-projects"></a>C++ 和 JavaScript 项目  
 C++ 和 JavaScript 项目对于管理项目属性有不同的用户界面。 此图显示了 C++ 项目属性页（JavaScript 页面与此类似）：  
  
 ![Visual C++ 项目属性](~/ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")  
  
 有关 C++ 项目属性的信息，请参阅[使用项目属性](/cpp/ide/working-with-project-properties)。 有关 JavaScript 属性的详细信息，请参阅[属性页，JavaScript](../ide/reference/property-pages-javascript.md)。  
  
## <a name="solution-properties"></a>解决方案属性  
 若要访问解决方案上的属性，请右键单击“解决方案资源管理器”中的解决方案节点，然后选择“属性”。 在对话框中，可以设置用于“调试”或“发布”版本的项目配置，选择按下 F5 时应启动的项目，然后设置代码分析选项。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 中的解决方案和项目](../ide/solutions-and-projects-in-visual-studio.md)

