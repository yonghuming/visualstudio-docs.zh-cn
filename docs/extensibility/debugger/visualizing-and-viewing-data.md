---
title: "可视化和查看数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 3f2317abd4bfaf6ebf8151812cf15541a1c94ecf
ms.lasthandoff: 04/05/2017

---
# <a name="visualizing-and-viewing-data"></a>可视化和查看数据
类型可视化工具和自定义查看器存在数据，以快速开发人员有意义的方式。 表达式计算器 (EE) 可以支持第三方类型可视化工具，以及提供其自己的自定义查看器。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]确定多少类型可视化工具和自定义查看器是与对象的类型相关联的调用[GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)方法。 如果没有至少一个类型的可视化工具或自定义查看器可用，Visual Studio 会调用[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法来检索那些可视化工具和查看者列表 (实际上，列表`CLSID`实现可视化工具和查看器的 s)，提供给用户。  
  
## <a name="supporting-type-visualizers"></a>支持的类型可视化工具  
 有大量的 EE 必须实现以支持类型可视化工具的接口。 这些接口可以分为两大类︰ 那些列表在类型可视化工具和访问属性数据。  
  
### <a name="listing-type-visualizers"></a>列表类型可视化工具  
 EE 支持列出在类型可视化工具在其实现`IDebugProperty3::GetCustomViewerCount`和`IDebugProperty3::GetCustomViewerList`。 这些方法将传递到相应方法的调用[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)通过调用获取[CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)。 此方法要求[IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)接口，可从获得[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)接口传递到[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 `IEEVisualizerServiceProvider::CreateVisualizerService`此外需要[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)和[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)接口传递到了这些接口`IDebugParsedExpression::EvaluateSync`。 创建所需的最终接口`IEEVisualizerService`接口是[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) EE 实现的接口。 此接口允许必须对要可视化的属性所做的更改。 所有属性数据都封装在[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)接口，还由 EE 实现该接口。  
  
### <a name="accessing-property-data"></a>访问属性数据  
 访问属性数据通过[IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)接口。 若要获取此接口，Visual Studio 会调用[QueryInterface](/cpp/atl/queryinterface)上要获取的属性对象[IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)接口 (在实现的相同对象上实现[IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)接口)，然后调用[GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)方法来获取`IPropertyProxyEESide`接口。  
  
 所有数据都传递到和移出`IPropertyProxyEESide`接口封装在[IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)接口。 此接口表示一个字节数组，由 Visual Studio 和 EE 实现。 如果要更改属性的数据，Visual Studio 将创建`IEEDataStorage`对象持有的新数据和调用[CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)与该数据对象以获取新`IEEDataStorage`对象，反过来，传递给[InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)更新属性的数据。 `IPropertyProxyEESide::CreateReplacementObject`允许实例化实现其自己类 EE`IEEDataStorage`接口。  
  
## <a name="supporting-custom-viewers"></a>支持自定义查看器  
 标志`DBG_ATTRIB_VALUE_CUSTOM_VIEWER`中设置`dwAttrib`字段[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)结构 (通过调用返回[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) 以指示该对象具有与之关联的自定义查看器。 当设置此标志时，Visual Studio 将获取[IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)接口从[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)接口使用[QueryInterface](/cpp/atl/queryinterface)。  
  
 如果用户选择自定义查看器，Visual Studio 实例化自定义查看器查看器的`CLSID`提供`IDebugProperty3::GetCustomViewerList`方法。 然后调用 visual Studio [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)来向用户显示的值。  
  
 通常情况下，`IDebugCustomViewer::DisplayValue`提供数据的只读视图。 若要允许对数据的更改，EE 必须实现一个自定义接口，在属性对象上支持不断变化的数据。 `IDebugCustomViewer::DisplayValue`方法使用此自定义接口来支持更改数据。 方法查找自定义接口`IDebugProperty2`接口作为传入`pDebugProperty`自变量。  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>同时支持键入可视化工具和自定义查看器  
 类型可视化工具和自定义查看器中的，可以支持 EE [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法。 首先，EE 在返回的值中添加了自定义查看器，它提供大量[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)方法。 其次，EE 追加`CLSID`返回的列表到其自己自定义查看器 s [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)   
 [类型可视化工具和自定义查看器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
