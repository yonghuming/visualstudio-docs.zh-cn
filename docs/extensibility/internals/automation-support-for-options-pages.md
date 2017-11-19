---
title: "自动化选项页的支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ca9031e623ec7009d4f489931871f093f4c05d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="automation-support-for-options-pages"></a>选项页的自动化支持
Vspackage 可以提供自定义**选项**到对话框**工具**菜单 （工具选项页） 中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以使它们可用于自动化模型。  
  
## <a name="tools-options-pages"></a>工具选项页  
 若要创建**工具选项**页，VSPackage 必须提供返回到通过 VSPackage 的实现的环境的用户控件实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法 (或适用于托管代码<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法）。  
  
 它是可选的但强烈建议，以允许访问通过自动化模型此新页面。 可以通过以下步骤来执行此操作：  
  
1.  扩展<xref:EnvDTE._DTE.Properties%2A>对象，通过 IDispatch 派生对象的实现。  
  
2.  返回的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法 (或托管代码的<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>方法) 到 IDispatch 派生对象。  
  
3.  当自动化使用者调用<xref:EnvDTE._DTE.Properties%2A>方法的自定义**选项**属性页中，该环境使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法来获取自定义**工具选项**页面的自动化实现。  
  
4.  VSPackage 的自动化对象然后用于为每项<xref:EnvDTE.Property>返回<xref:EnvDTE._DTE.Properties%2A>。  
  
 实现自定义工具选项页的示例，请参阅[VSSDK 示例](http://aka.ms/vs2015sdksamples)。  
  
## <a name="see-also"></a>另请参阅  
 [公开项目对象](../../extensibility/internals/exposing-project-objects.md)