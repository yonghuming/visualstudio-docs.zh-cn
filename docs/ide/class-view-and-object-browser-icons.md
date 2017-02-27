---
title: "“类视图”和“对象浏览器”图标 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "图标，在对象浏览器中"
  - "信号图标"
  - "“类视图”工具，符号"
  - "图形符号"
  - "IntelliSense，图标"
  - "图标，IntelliSense"
  - "符号，“对象浏览器”图标"
  - "对象浏览器，类视图中的图标"
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# “类视图”和“对象浏览器”图标
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**“类视图”**和**“对象浏览器”**显示一些图标，这些图标表示代码实体，例如命名空间、类、函数和变量。  下表以图文并茂的形式说明了这些图标。  
  
|图标|说明|图标|说明|  
|--------|--------|--------|--------|  
|![命名空间符号](../ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|命名空间|![声明符号](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|方法或函数|  
|![“类”图标](../ide/media/vxclass_icon.png "vxClass\_Icon")|类|![运算符符号](../ide/media/vxoperator_icon.png "vxOperator\_Icon")|运算符|  
|![棒棒糖形状的接口符号](../ide/media/vxinterface_icon.png "vxInterface\_Icon")|接口|![属性符号](../ide/media/vxproperty_icon.png "vxProperty\_Icon")|属性|  
|![结构符号](../ide/media/vxstruct_icon.png "vxStruct\_Icon")|结构|![“字段”图标](../ide/media/vxfield_icon.png "vxField\_Icon")|字段或变量|  
|![联合符号](../ide/media/vxunion_icon.png "vxUnion\_Icon")|Union|![事件符号](../ide/media/vxevent_icon.png "vxEvent\_Icon")|Event|  
|![枚举符号](../ide/media/vxenum_icon.png "vxEnum\_Icon")|Enum|![“常量”图标](../ide/media/vxconstant_icon.png "vxConstant\_Icon")|常量|  
|![类型定义符号](../ide/media/vxtypedef_icon.png "vxTypeDef\_Icon")|TypeDef|![枚举项符号](../ide/media/vxenumitem_icon.png "vxEnumItem\_Icon")|枚举项|  
|![Visual Studio 模块符号](../ide/media/vxmodule_icon.gif "vxModule\_Icon")|模块|![映射项符号](../ide/media/vxmapitem_icon.png "vxMapItem\_Icon")|映射项|  
|![扩展方法符号](../ide/media/extensionmethod.png "ExtensionMethod")|扩展方法|![声明符号](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|外部声明|  
|![委托符号](../ide/media/vxdelegate_icon.png "vxDelegate\_Icon")|委托|![类视图和对象浏览器的“错误”图标](../ide/media/erroricon.png "ErrorIcon")|错误|  
|![异常符号](../ide/media/vxexception_icon.png "vxException\_Icon")|异常|![模板符号](../ide/media/vxtemplate_icon.png "vxTemplate\_Icon")|模板|  
|![映射符号](../ide/media/vxmap_icon.png "vxMap\_Icon")|映射|![错误感叹号符号](../ide/media/vxerror_icon.png "vxError\_Icon")|未知|  
|![“类型转发”符号](../ide/media/ob_type_forward.png "ob\_type\_forward")|类型转发|||  
  
## 信号图标  
 以下信号图标适用于前面的所有图标，指示它们的可访问性。  
  
> [!NOTE]
>  如果项目包含在源代码管理数据库中，则可能会显示其他信号图标来指示源代码管理的状态，如签入或签出。  
  
|图标|说明|  
|--------|--------|  
|\<无信号图标\>|公共。  可从该组件内的任何地方访问或从任何引用它的组件访问。|  
|![信号 Protected 符号](../ide/media/vxsignal_icon_key.png "vxSignal\_Icon\_Key")|受保护。  可从包含类或类型内访问或从由包含类或类型派生的类或类型内访问。|  
|![信号 Private 符号](../ide/media/vxsignal_icon_lock.png "vxSignal\_Icon\_Lock")|私有。  仅可在包含类或类型内访问。|  
|![信号 Sealed 符号](../ide/media/vxsignal_icon_envelope.png "vxSignal\_Icon\_Envelope")|密封。|  
|![信号 Friend&#47;Internal 符号](../ide/media/vxsignal_icon_diamond.png "vxSignal\_Icon\_Diamond")|朋友\/内部。  仅可以从此项目内访问。|  
|![信号图标箭头](../ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|快捷方式。  对象的快捷方式。|  
  
## 请参阅  
 [查看代码的结构](../ide/viewing-the-structure-of-code.md)