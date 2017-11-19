---
title: "IDispatchEx::InvokeEx |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
提供对属性和方法公开的访问权限`IDispatchEx`对象。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `id`  
 标识成员。 使用`GetDispID`或`GetNextDispID`若要获取调度标识符。  
  
 `lcid`  
 要在其中解释自变量的区域设置上下文。 `lcid`传递给`InvokeEx`以允许要解释特定于区域设置其自变量的对象。  
  
 `wFlags`  
 的合法值为`wFlags`是：  
  
 DISPATCH_PROPERTYGET &#124;DISPATCH_METHOD &#124;DISPATCH_PROPERTYPUT &#124;DISPATCH_PROPERTYPUTREF &#124;DISPATCH_CONSTRUCT  
  
 描述上下文的标志`InvokeEx`调用：  
  
|值|含义|  
|-----------|-------------|  
|DISPATCH_METHOD|作为一种方法调用成员。 如果属性具有相同的名称，可能会设置此和 DISPATCH_PROPERTYGET 标志 (由定义`IDispatch`)。|  
|DISPATCH_PROPERTYGET|属性或数据成员的形式检索成员 (定义`IDispatch`)。|  
|DISPATCH_PROPERTYPUT|成员更改为属性或数据成员 (定义`IDispatch`)。|  
|DISPATCH_PROPERTYPUTREF|该成员会被分配引用而不是值分配更改。 此标志无效，仅当属性接受对对象的引用时 (通过定义`IDispatch`)。|  
|DISPATCH_CONSTRUCT|作为构造函数是正在使用的成员。 (这是由定义的新值`IDispatchEx`)。 的合法值为`wFlags`是：<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 指向一个结构的指针，该结构包含一个自变量数组、一个命名自变量的 DISPID 自变量数组和数组中元素数的计数。 请参阅`IDispatch`有关 DISPPARAMS 结构的完整说明的文档。  
  
 `pVarRes`  
 到其中的结果是要存储或调用方期望任何结果的情况下为 Null 的位置的指针。 如果指定 DISPATCH_PROPERTYPUT 或 DISPATCH_PROPERTYPUTREF，将忽略此参数。  
  
 `pei`  
 指向一个包含异常信息的结构的指针。 此结构应该填写如果`DISP_E_EXCEPTION`返回。 可以为 Null。 请参阅`IDispatch`文档的完整说明`EXCEPINFO`结构。  
  
 `pspCaller`  
 指向由调用方，使该对象可以从调用方获取服务提供的服务提供程序对象的指针。 可以为 Null。  
  
 `IDispatchEx::InvokeEx`提供与相同的功能的所有`IDispatch::Invoke`并添加有几个扩展：  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|指示正在作为构造函数使用项。|  
|`pspCaller`|`pspCaller`允许对由调用方提供的服务对象的访问。 可能由调用方本身或委派给调用方进一步调用链中向上特定服务。 例如，如果在脚本引擎浏览器将使`InvokeEx`调用外部对象，该对象可以按照`pspCaller`链，以获取从脚本引擎或浏览器的服务。 (请注意，调用链不创建链相同-也称为容器链或站点链。 创建链就能通过某种其他机制提供如`IObjectWithSite`。)|  
|`this` 指针|当 DISPATCH_METHOD 设置中进行`wFlags`，可能有一个"命名的参数"的"this"值。 DISPID 将 DISPID_THIS 并且它必须是第一个命名的参数。|  
  
 未使用`riid`中的参数`IDispatch::Invoke`已删除。  
  
 `puArgArr`中的参数`IDispatch::Invoke`已删除。  
  
 请参阅`IDispatch::Invoke`对于以下示例中的文档：  
  
 "调用不带任何参数的方法"  
  
 "获取和设置属性"  
  
 "传递参数"  
  
 "索引的属性"  
  
 "过程调用中的引发异常"  
  
 "返回错误"  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|DISP_E_BADPARAMCOUNT|提供给 DISPPARAMS 的元素的数目是不同的接受方法或属性的参数的数目。|  
|DISP_E_BADVARTYPE|中的自变量之一`rgvarg`不是有效的变体类型。|  
|DISP_E_EXCEPTION|应用程序需要引发异常。 在这种情况下，该结构传递`pei`应该填写。|  
|DISP_E_MEMBERNOTFOUND|请求的成员不存在，或者对调用`InvokeEx`试图设置只读属性的值。|  
|DISP_E_NONAMEDARGS|此实现的`IDispatch`不支持命名自变量。|  
|DISP_E_OVERFLOW|中的自变量之一`rgvarg`不能强制为指定的类型。|  
|DISP_E_PARAMNOTFOUND|一个参数的 Dispid 不对应上方法的参数。|  
|DISP_E_TYPEMISMATCH|一个或多个参数不能强制。|  
|DISP_E_UNKNOWNLCID|被调用的成员将解释 LCID，根据字符串自变量，并且无法识别的 LCID。 如果不需要 LCID 解释自变量，不应返回此错误。|  
|DISP_E_PARAMNOTOPTIONAL|所需的参数被省略。|  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>另请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)