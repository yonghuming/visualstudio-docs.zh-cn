---
title: "IDispatchEx::InvokeEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "InvokeEx 方法"
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDispatchEx::InvokeEx
提供对 `IDispatchEx` 对象和方法显示的属性。  
  
## 语法  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### 参数  
 `id`  
 标识成员。  使用 `GetDispID` 或 `GetNextDispID` 获取调度标识符。  
  
 `lcid`  
 要在其中解释参数的区域设置上下文。  `lcid` 传递给 `InvokeEx` 允许对象解释其参数特定于区域设置。  
  
 `wFlags`  
 `wFlags` 的合法值为：  
  
 DISPATCH\_PROPERTYGET&#124;DISPATCH\_METHOD&#124;DISPATCH\_PROPERTYPUT&#124;DISPATCH\_PROPERTYPUTREF&#124;DISPATCH\_CONSTRUCT  
  
 描述 `InvokeEx` 上下文的标志调用：  
  
|值|含义|  
|-------|--------|  
|DISPATCH\_METHOD|该成员调用作为方法。  如果特性具有相同的名称，则，并DISPATCH\_PROPERTYGET标志可以设置为\(定义 `IDispatch`\)。|  
|DISPATCH\_PROPERTYGET|该成员检索作为属性或数据成员\(定义 `IDispatch`\)。|  
|DISPATCH\_PROPERTYPUT|该成员将更改作为属性或数据成员\(定义 `IDispatch`\)。|  
|DISPATCH\_PROPERTYPUTREF|引用分配更改成员\(而非值分配。  此标志有效，仅在属性接受对对象\(定义 `IDispatch`\)。|  
|DISPATCH\_CONSTRUCT|该成员用作构造函数。  \(这是 `IDispatchEx`定义的新值\)。  `wFlags` 的合法值为：<br /><br /> DISPATCH\_PROPERTYGET DISPATCH\_METHOD DISPATCH\_PROPERTYPUT DISPATCH\_PROPERTYPUTREF DISPATCH\_CONSTRUCT|  
  
 `pdp`  
 指向一个结构的指针，该结构包含一个参数数组、一个命名参数的 DISPID 参数数组和数组中元素数的计数。  为DISPPARAMS结构的完整说明参见 `IDispatch` 文档。  
  
 `pVarRes`  
 对结果将存储的位置或Null的指针，如果调用方不需要结果。  如果DISPATCH\_PROPERTYPUT或DISPATCH\_PROPERTYPUTREF指定，此参数将被忽略。  
  
 `pei`  
 指向一个包含异常信息的结构的指针。  如果 `DISP_E_EXCEPTION` 返回，应填充此结构。  可以为Null。  为 `EXCEPINFO` 结构的完整说明参见 `IDispatch` 文档。  
  
 `pspCaller`  
 向调用方提供的服务提供程序对象的指针，使对象从调用方的服务。  可以为Null。  
  
 `IDispatchEx::InvokeEx` 提供的所有功能和 `IDispatch::Invoke` 相同并添加几个扩展：  
  
|||  
|-|-|  
|DISPATCH\_CONSTRUCT|指示该项目用作构造函数。|  
|`pspCaller`|`pspCaller` 允许对该调用方提供的服务对象访问。  特定服务可以由调用方处理或将委托给调用方将来调用链。  例如，因此，如果在浏览器中的脚本引擎使 `InvokeEx` 调用外部对象，可以跟 `pspCaller` 链从脚本引擎或浏览器的服务。  \(调用链与称为容器链或站点链中创建链还说明。  创建链可能可用通过某些其他框架\(如 `IObjectWithSite`。\)|  
|`this` 指针|当DISPATCH\_METHOD在 `wFlags`设置时，可能有一个名为“参数”中的“this”值。  DISPID将是DISPID\_THIS，它必须是第一个命名参数。|  
  
 移除了 `IDispatch::Invoke` 中未使用的 `riid` 参数。  
  
 移除了 `IDispatch::Invoke` 的 `puArgArr` 参数。  
  
 为下面的示例参见 `IDispatch::Invoke` 文档：  
  
 “调用方法没有参数”  
  
 “获取和设置属性”  
  
 “传递参数”  
  
 “索引属性”  
  
 “引发异常期间调用”  
  
 “返回false”  
  
## 返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|DISP\_E\_BADPARAMCOUNT|元素数提供给DISPPARAMS与方法或属性接受的参数的数量不同。|  
|DISP\_E\_BADVARTYPE|某个 `rgvarg` 的参数不是有效的不同类型的。|  
|DISP\_E\_EXCEPTION|应用程序需要引发异常。  在这种情况下，应填充 `pei` 传递机制。|  
|DISP\_E\_MEMBERNOTFOUND|请求的成员不存在，则为 `InvokeEx` 的调用尝试设置只读属性的值。|  
|DISP\_E\_NONAMEDARGS|`IDispatch` 的此实现不支持命名参数。|  
|DISP\_E\_OVERFLOW|某个 `rgvarg` 的参数不能强制为指定的类型。|  
|DISP\_E\_PARAMNOTFOUND|一个参数Dispid不对应于方法的参数。|  
|DISP\_E\_TYPEMISMATCH|一个或多个参数不能强制。|  
|DISP\_E\_UNKNOWNLCID|成员调用基于LCID解释字符串参数，并且，LCID不识别。  如果 LCID 不需要解释参数，不应返回此错误。|  
|DISP\_E\_PARAMNOTOPTIONAL|缺少某个必需的参数。|  
  
## 示例  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## 请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)