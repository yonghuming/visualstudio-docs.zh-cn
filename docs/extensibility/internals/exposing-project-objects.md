---
title: "公开项目对象 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "显示的项目对象"
  - "可扩展性，项目对象"
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 公开项目对象
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

自定义项目类型可以以允许访问使用自动化接口的项目中提供的自动化对象。 每种项目类型需要提供标准 <xref:EnvDTE.Project> 从访问的自动化对象 <xref:EnvDTE.Solution>, ，其中包含已在 IDE 中打开的所有项目的集合。 在项目中的每一项需要公开的 <xref:EnvDTE.ProjectItem> 对象使用的访问 <xref:Project.ProjectItems>。 除了这些标准的自动化对象，可以选择项目中提供特定于项目的自动化对象。  
  
 您可以创建自定义根级别的自动化对象可以访问从根 DTE 对象使用后期绑定 `DTE.<customeObjectName>` 或 `DTE.GetObject(“<customObjectName>”)`。 例如，Visual c \+ \+ 创建名为"VCProjects"，您可以访问使用 DTE 的 c \+ \+ 项目特定的项目集合。VCProjects 或 DTE。GetObject\("VCProjects"\)。 此外可以创建 Project.Object，这是唯一的项目类型，Project.CodeModel，可为其派生程度最高的对象，项目项，它公开 ProjectItem.Object 和 ProjectItem.FileCodeModel 查询。  
  
 它是要公开的自定义的、 特定于项目的项目集合的项目的通用约定。 例如， [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 创建一个 c \+ \+ 特定项目集合，然后您可以访问使用 `DTE.VCProjects` 或 `DTE.GetObject("VCProjects")`。 您还可以创建 `Project.Object`, ，这是唯一的项目类型， `Project.CodeModel`, ，其派生程度最高的对象，可从中查询其 `ProjectItem`, ，这会公开 `ProjectItem.Object`, ，和一个 `ProjectItem.FileCodeModel`。  
  
### 若要参与一个项目的 VSPackage 特定对象  
  
1.  将相应的键添加到你的 VSPackage 的.pkgdef 文件。  
  
     例如，下面是 c \+ \+ 语言项目的.pkgdef 设置:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation] "VCProjects"="" [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents] "VCProjectEngineEventsObject"=""  
    ```  
  
2.  实现中的代码 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法，如下面的示例所示。  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject( /* [in]  */ LPCOLESTR       pszPropName, /* [out] */ IDispatch **    ppIDispatch) { ExpectedPtrRet(pszPropName); ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (m_fZombie) return E_UNEXPECTED; if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0) { return GetAutomationProjects(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } return E_INVALIDARG; }   
    ```  
  
     在代码中， `g_wszAutomationProjects` 是您的项目集合的名称。`GetAutomationProjects` 方法创建一个实现对象 `Projects` 接口，并返回 `IDispatch` 对调用对象，如下面的代码示例中所示的指针。  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch) { ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (!m_srpAutomationProjects) { HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects); IfFailRet(hr); ExpectedExprRet(m_srpAutomationProjects != NULL); } return m_srpAutomationProjects.CopyTo(ppIDispatch); }  
    ```  
  
     您应选择您的自动化对象的唯一名称。 名称冲突是不可预知，并且冲突导致冲突的对象名称以被任意抛弃如果多个项目类型使用相同的名称。 应包括您的公司名称或自动化对象的名称及其产品名称的一些独特之处。  
  
     自定义 `Projects` 集合对象是您项目的自动化模型的其余部分的便利入口点。 项目对象也是从进行访问 <xref:EnvDTE.Solution> 项目集合。 创建相应的代码和注册表条目，它们提供使用者后 `Projects` 对象集合，您的实现必须提供剩余标准项目模型对象。 有关详细信息，请参阅[项目建模](../../extensibility/internals/project-modeling.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>