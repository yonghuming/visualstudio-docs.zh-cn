---
title: "项目子类型的初始化序列 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目子类型，初始化序列"
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 项目子类型的初始化序列
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

该环境通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>的基本项目工厂实现构造项目。  项目子类型的构造开始，当环境确定项类型 GUID 为项目文件的扩展列表不为空。  项目文件扩展名和项目 GUID 指定项目是否 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 项类型。  例如， .vbproj 扩展名和 {F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F} 标识一个 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 项目。  
  
## 项目子类型的环境的初始化  
 以下过程详细说明了多个项目子类型聚合的项目系统的初始化顺序。  
  
1.  该环境调用基项目的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>，，所以，当该项分析其项目文件时它发现复合项目类型 GUID 列表不是 `null`。  该项目停止直接创建它的项。  
  
2.  使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 方法的环境的实现，该项对 <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> 服务的 `QueryService` 创建项目子类型。  在环境进行递归函数的方法中调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>、 `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> 方法的实现，当它来浏览项类型 GUID 列表时，从最外面的项目子类型开始。  
  
     下面详细介绍初始化步骤。  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 方法环境的实现调用具有以下特点声明的 `HrCreateInnerProj```方法:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         虽然此功能最外面的项目子类型时第一次调用，也就是说，参数， `pOuter` 和 `pOwner` 通过，当 `null` 和函数用于设置最外面的项目子类型 `IUnknown` 到 `pOuter`。  
  
    2.  接下来该环境调用与第二个项目类型的 GUID 的 `HrCreateInnerProj` 功能在列表中。  此 GUID 对应于遍历从拖向摘要序列的基项目的第二个内部项的子类型。  
  
    3.  `pOuter` 现在指向最外面的项目子类型的 `IUnknown` ，并且， `HrCreateInnerProj` 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 的实现中调用遵循为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>的实现。  在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 方法在最外层的项目子类型的控件 `IUnknown` ， `pOuter`通过。  拥有的项目 \(内部项子类型\) 需要创建其复合项目对象示。  在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 方法实现在指针传递给聚合内部项的 `IUnknown` 。  这两种方法创建摘要对象，并且，实现所需遵循 COM 摘要规则确保项目子类型不会导致持有引用计数到自身。  
  
    4.  `HrCreateInnerProj` 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>的实现。  在此方法中，项目子类型完成其初始化工作。  可以，例如，注册在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>的解决方案事件。  
  
    5.  `HrCreateInnerProj` 递归调用，直到最后一个 GUID \(基项目\) 在列表中为止。  对于每一个调用，步骤， c 到 d，重复。  `pOuter` 指向每最外面的项目子类型 `IUnknown` 聚合级别。  
  
 ，在该环境，实现下面的示例在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 方法的一个大致表示详细编程方式处理。  是示例代码;不应被编译，并且所有错误检查为清楚起见移除。  
  
## 示例  
  
### 代码  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [项目子类型](../../extensibility/internals/project-subtypes.md)