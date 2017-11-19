---
title: "公开项目对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f29ca84669f563da5733c8c07b219d498ccf6ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-project-objects"></a>公开项目对象
自定义项目类型可以提供自动化对象，以便允许访问项目使用自动化接口。 每个项目类型需要提供标准<xref:EnvDTE.Project>从访问的自动化对象<xref:EnvDTE.Solution>，其中包含在 IDE 中打开的所有项目的集合。 应在项目中的每个项，可以公开的<xref:EnvDTE.ProjectItem>通过访问的对象`Project.ProjectItems`。 除了这些标准的自动化对象，项目可以选择提供特定于项目的自动化对象。  
  
 您可以创建自定义的根级别自动化对象，您可以访问从根 DTE 对象使用的后期绑定`DTE.<customeObjectName>`或`DTE.GetObject("<customObjectName>")`。 例如，Visual c + + 创建名为"VCProjects"可使用 DTE 访问 c + + 项目特有的项目集合。VCProjects 或 DTE。GetObject("VCProjects")。 你还可以创建 Project.Object，对于项目类型，Project.CodeModel，可为其派生程度最高的对象，ProjectItem，公开 ProjectItem.Object 和 ProjectItem.FileCodeModel 查询是唯一的。  
  
 它是用于公开的自定义的、 特定于项目的项目集合的项目的通用约定。 例如，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]创建一个 c + + 特定的项目集合，然后就可以访问使用`DTE.VCProjects`或`DTE.GetObject("VCProjects")`。 你还可以创建`Project.Object`，即对于项目类型中，唯一`Project.CodeModel`，为其派生程度最高的对象，该查询`ProjectItem`，这会公开`ProjectItem.Object`，和一个`ProjectItem.FileCodeModel`。  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>提供一个项目的特定于 VSPackage 的对象  
  
1.  将相应的键添加到你的 VSPackage 的.pkgdef 文件。  
  
     例如，以下是 c + + 语言项目的.pkgdef 设置：  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  实现中的代码<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法，如下面的示例所示。  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     在代码中，`g_wszAutomationProjects`是你的项目集合的名称。 `GetAutomationProjects`方法创建实现的对象`Projects`接口并返回`IDispatch`指向所调用的对象，如下面的代码示例中所示。  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     你应选择您的自动化对象的唯一名称。 名称冲突是不可预知，并且冲突导致冲突的对象名称任意引发如果多个项目类型使用相同的名称。 你应包括你公司的名称或某个唯一方面的自动化对象的名称及其产品名称。  
  
     自定义`Projects`集合对象是您项目的自动化模型的其余部分的方便入口点。 你的项目对象也是可从访问<xref:EnvDTE.Solution>项目集合。 创建适当的代码和注册表条目，它们提供使用者后`Projects`对象集合，您的实现必须提供剩余项目模型的标准对象。 有关详细信息，请参阅[项目建模](../../extensibility/internals/project-modeling.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>