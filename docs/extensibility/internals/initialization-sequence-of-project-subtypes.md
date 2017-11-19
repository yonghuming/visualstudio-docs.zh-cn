---
title: "项目子类型的初始化序列 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd80a8571a9c6167dab3be355365754a9e1fb7f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="initialization-sequence-of-project-subtypes"></a>项目子类型的初始化顺序
环境构造一个项目，通过调用的基本项目工厂实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>。 当环境确定项目文件的扩展名的项目类型 GUID 列表不为空时，将开始项目子类型的构造。 项目文件扩展名和项目 GUID 指定的项目是否[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]项目类型。 例如，.vbproj 扩展和 {F184B08F-C81C-45F6-A57F-5ABD9991F28F} 标识[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]项目。  
  
## <a name="environments-initialization-of-project-subtypes"></a>项目子类型的环境的初始化  
 以下过程详细描述项目系统按多个项目子类型聚合初始化序列。  
  
1.  环境调用基项目<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>，项目分析其项目文件时发现不是聚合项目类型 Guid 列表`null`。 项目终止直接创建其项目。  
  
2.  项目调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>服务以创建项目子类型使用的环境实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法。 在此方法内环境使你的实现的递归函数调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>，`M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>方法时它遍历的项目列表键入开头的外面项目子类型的 Guid。  
  
     下面详细介绍的初始化步骤。  
  
    1.  环境的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法调用 HrCreateInnerProj '' 与以下函数声明的方法：  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         当调用此函数是第一次，即外面项目子类型，参数`pOuter`和`pOwner`作为传递`null`和函数设置最外层项目子类型`IUnknown`到`pOuter`。  
  
    2.  接下来环境将调用`HrCreateInnerProj`与第二个项目类型 GUID 列表中的函数。 此 GUID 对应于将关心基项目聚合序列中的单步执行的第二个内部项目子类型。  
  
    3.  `pOuter`现在指向`IUnknown`外面项目子类型，和`HrCreateInnerProj`调用的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>跟的实现调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>。 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>方法传入控制`IUnknown`外面项目子类型， `pOuter`。 需要创建其的聚合项目对象拥有的项目 （内部项目子类型）。 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>方法实现中指向的指针传递`IUnknown`正在聚合的内部项目。 这两种方法创建的聚合对象，并且您的实现需要遵循 COM 聚合规则，以确保项目子类型不结尾向上保存到其自身的引用计数。  
  
    4.  `HrCreateInnerProj`调用的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>。 在此方法中，项目子类型完成其初始化工作。 例如，可以注册中的解决方案事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>。  
  
    5.  `HrCreateInnerProj`被调用以递归方式，直到到达列表中的最后一个 GUID （基本项目）。 对于每个这些调用，重复执行步骤，c d，到。 `pOuter`指向外面项目子类型`IUnknown`针对每个聚合级别。  
  
 以下示例将详细介绍的近似表示形式中的编程过程<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>由的环境实现为它的方法。 代码只是一个示例;它并非要编译，并且所有错误检查为清楚起见已都删除。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
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
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [项目子类型](../../extensibility/internals/project-subtypes.md)