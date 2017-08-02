---
title: "公开 Visual Studio SDK 中的事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事件 [Visual Studio] 公开"
  - "自动化 [Visual Studio SDK]，公开事件"
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 公开 Visual Studio SDK 中的事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 允许通过使用自动化源事件。 我们建议源项目和项目项的事件。  
  
 从自动化者中检索事件 <xref:EnvDTE.DTEClass.Events%2A> 对象或 <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName")。 环境调用 `IDispatch::Invoke` 使用 `DISPATCH_METHOD` 或 `DISPATCH_PROPERTYGET` 标志返回事件。  
  
 以下过程说明如何返回 VSPackage 特定的事件。  
  
1.  启动该环境。  
  
2.  它从注册表中读取所有 Vspackage，自动化、 AutomationEvents 和 AutomationProperties 项下的所有值名称，并将这些名称存储在表中。  
  
3.  自动化使用者调用，在此示例中， `DTE.Events.AutomationProjectsEvents` 或 `DTE.Events.AutomationProjectItemsEvents`。  
  
4.  环境表中查找的字符串参数，并加载相应的 VSPackage。  
  
5.  环境调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法使用的名称传递的调用中; 在此示例中，AutomationProjectsEvents 或 AutomationProjectItemsEvents。  
  
6.  VSPackage 创建一个根对象，如具有方法 `get_AutomationProjectsEvents` 和 `get_AutomationProjectItemEvents` 然后 IDispatch 指针返回到对象。  
  
7.  环境调用相应方法基于传递给自动化调用的名称。  
  
8.   `get_` 方法创建同时实现的另一个基于 IDispatch 的事件对象 `IConnectionPointContainer` 接口和 `IConnectionPoint` 接口，并返回 IDispatchpointer 的对象。  
  
 若要通过使用自动化中公开事件，你必须响应 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 和向注册表添加的字符串的监视。 在基本项目示例中，字符串为"BscProjectsEvents"和"BscProjectItemsEvents"。  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>从基本项目示例的注册表项  
 本部分说明如何向注册表添加自动化事件值。  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 "AutomationProjectEvents"="返回 AutomationProjectEvents 对象"  
  
 "AutomationProjectItemEvents"="返回 AutomationProjectItemsEvents 对象"  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|默认值 (@)|REG_SZ|未使用|未使用。 数据字段可用于文档。|  
|AutomationProjectsEvents|REG_SZ|事件对象的名称。|仅密钥的名称为相关。 数据字段可用于文档。<br /><br /> 此示例来自于基本项目示例。|  
|AutomationProjectItemEvents|REG_SZ|事件对象的名称|仅密钥的名称为相关。 数据字段可用于文档。<br /><br /> 此示例来自于基本项目示例。|  
  
 当自动化使用者所请求的任何事件对象时，创建具有为你的 VSPackage 支持任何事件的方法的根对象。 环境调用相应 `get_` 对此对象的方法。 例如，如果 `DTE.Events.AutomationProjectsEvents` 调用时， `get_AutomationProjectsEvents` 调用上的根对象的方法。  
  
 ![Visual Studio 项目事件](~/docs/extensibility/internals/media/projectevents.gif "ProjectEvents")  
事件的自动化模型  
  
 类 `CProjectEventsContainer` BscProjectsEvents，表示源对象时 `CProjectItemsEventsContainer` BscProjectItemsEvents 表示源对象。  
  
 在大多数情况下，您必须返回每个事件请求的新对象，因为大多数事件对象需要的筛选器对象。 当在激发事件时，检查此筛选器以验证正在调用事件处理程序。  
  
 AutomationEvents.h 和 AutomationEvents.cpp 包含声明和下表中的类的实现。  
  
|类|描述|  
|-----------|-----------------|  
|`CAutomationEvents`|实现从检索到的事件根对象 `DTE.Events` 对象。|  
|`CProjectsEventsContainer` 和 `CProjectItemsEventsContainer`|实现激发相应的事件的事件源对象。|  
  
 下面的代码示例演示如何对一个事件对象的请求作出响应。  
  
```cpp#  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 在上面的代码， `g_wszAutomationProjects` 是你的项目集合 ("FigProjects") 的名称 `g_wszAutomationProjectsEvents` ("FigProjectsEvents") 和 `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") 是项目事件的名称和项目项源自 VSPackage 实现的事件。  
  
 从相同的中心位置，检索事件对象 `DTE.Events` 对象。 这样一来，所有事件对象被都组合在一起，以便最终用户不必浏览整个对象模型以查找特定事件。 这还允许你提供特定的 VSPackage 对象，而不是要求你可以实现你自己的代码的系统级事件。 但是，最终用户，用户必须找到的事件你 `ProjectItem` 接口，它不是立即清除从中检索该事件对象。  
  
## <a name="see-also"></a>请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [VSSDK 示例](../../misc/vssdk-samples.md)