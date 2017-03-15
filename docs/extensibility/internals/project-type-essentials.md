---
title: "项目类型 Essentials |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 11
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
ms.openlocfilehash: 77ac7852a4fe42e69602edcd7e75354b404e315e
ms.lasthandoff: 02/22/2017

---
# <a name="project-type-essentials"></a>项目类型 Essentials
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包括多种项目类型语言，如[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]此外可以创建您自己的项目类型。  
  
 如果只是想要添加自定义命令、 编辑器或为工具窗口[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以完成，而不必创建新的项目类型。 有关详细信息，请参阅下列主题：  
  
-   [命令、 菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [扩展和自定义工具窗口](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 同样，如果想要自定义所提供的行为[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]可以执行的项目类型，因此，使用项目子类型。 有关详细信息，请参阅[项目子类型](../../extensibility/internals/project-subtypes.md)。  
  
 您必须创建基于一种语言之外的项目的新项目类型[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]如果您想要支持的一个或多项操作︰  
  
-   生成  
  
-   部署  
  
-   多个配置  
  
-   源代码管理  
  
-   调试  
  
-   在解决方案资源管理器中的项目项  
  
-   **打开项目**或**新项目**对话框  
  
-   项目的嵌套  
  
-   项目类型的功能的详细信息，请参阅︰  
  
-   项目类型是在 VSPackage 中实现的接口集的对象[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]期望。 如果您使用 C# 开发一种项目类型，管理包框架项目类为您实现必要的接口，让您继承该实现。 有关详细信息，请参阅[使用管理包框架来实现一种项目类型 (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)。  
  
-   对于 c + + 开发人员，HierUtil 库中的类以类似的方式工作。 有关详细信息，请参阅[不在生成︰ 使用 HierUtil7 项目类以实现项目类型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
-   项目类型都可以支持为.exe 或.dll 程序集生成的典型的源代码文件之外的其他数据。 例如，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]数据库项目包含对脚本和查询存储在磁盘上的文件的引用，并将命令添加到**解决方案资源管理器**要执行的脚本和针对数据库中，但这些项目的查询不支持生成行为。 有关详细信息，请参阅[打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
-   一种项目类型没有用于在所有文件。 例如，项目类型可以存储在数据库中的所有数据。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]为项目类型提供完全控制如何将项目和项目项的数据的保存。 有关详细信息，请参阅[项目类型的设计决策](../../extensibility/internals/project-type-design-decisions.md)。  
  
-   项目的类型必须提供*项目工厂*，这是一个对象创建项目的一个实例，只要键入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]告知要打开或创建基于该项目类型的项目。 有关详细信息，请参阅[创建项目实例通过使用项目工厂](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。  
  
-   项目类型必须提供用于项目和项目项模板。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]当用户创建新的项目并向现有项目添加新项目将使用模板。 有关详细信息，请参阅[添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
-   项目类型可支持多个配置，如调试和发布。 用户可以通过使用您提供的属性页更改项目的不同的配置。 有关详细信息，请参阅[管理配置选项](../../extensibility/internals/managing-configuration-options.md)。  
  
## <a name="see-also"></a>另请参阅  
 [部署项目类型](../../extensibility/internals/deploying-project-types.md)
