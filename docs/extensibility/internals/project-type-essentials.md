---
title: "项目类型 Essentials |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33f31ec1d5adedb2fac6c2a37c050ee65d774894
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-type-essentials"></a>项目类型 Essentials
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包括几种语言的项目类型，如[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]此外可以创建您自己的项目类型。  
  
 如果你只想要添加自定义命令、 编辑器或到工具窗口[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以这样无需创建新的项目类型。 有关详细信息，请参阅下列主题：  
  
-   [命令、菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [扩展和自定义工具窗口](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 同样，如果你想要自定义所提供的行为[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]可以执行项目类型，因此使用项目子类型。 有关详细信息，请参阅[项目子类型](../../extensibility/internals/project-subtypes.md)。  
  
 你必须创建新项目类型的项目的以外的语言基于[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]如果你想要支持一个或多个以下：  
  
-   生成  
  
-   部署  
  
-   多个配置  
  
-   源代码管理  
  
-   调试  
  
-   在解决方案资源管理器中的项目项  
  
-   **打开项目**或**新项目**对话框  
  
-   项目嵌套  
  
-   项目类型的功能的详细信息，请参阅以下资源：  
  
-   项目类型是在 VSPackage 中实现的接口集的对象[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]要求。 如果你使用的 C# 来开发项目类型，托管包框架项目类将为你实现必要的接口，并可以继承该实现。 有关详细信息，请参阅[使用托管包框架来实现一种项目类型 (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)。  
  
-   对于 c + + 开发人员，HierUtil 库中的类以类似的方式工作。 有关详细信息，请参阅[不在生成中： 使用 HierUtil7 项目类以实现项目类型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
-   项目类型都可以支持将内置的.exe 或.dll 程序集的典型的源代码文件之外的数据。 例如，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]数据库项目包含对存储在磁盘上的脚本和查询文件的引用，并且将命令添加到**解决方案资源管理器**要执行的脚本和针对数据库中，但项目的查询不支持生成行为。 有关详细信息，请参阅[打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
-   项目类型没有用于在所有文件。 例如，项目类型可以存储在数据库中的所有数据。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]为项目类型提供完全控制如何将项目和项目项的数据的保存。 有关详细信息，请参阅[项目类型的设计决策](../../extensibility/internals/project-type-design-decisions.md)。  
  
-   项目类型必须提供*项目工厂*，这是创建项目的实例的对象键入每当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]所指示的打开或创建基于该项目类型的项目。 有关详细信息，请参阅[创建项目实例通过使用项目工厂](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。  
  
-   项目类型必须提供项目和项目项模板。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]当用户创建新项目，然后将新项添加到现有项目时，请使用模板。 有关详细信息，请参阅[添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
-   项目类型可支持多个配置，例如调试和发布。 用户可以通过使用你提供的属性页更改项目的不同配置。 有关详细信息，请参阅[管理配置选项](../../extensibility/internals/managing-configuration-options.md)。  
  
## <a name="see-also"></a>另请参阅  
 [部署项目类型](../../extensibility/internals/deploying-project-types.md)