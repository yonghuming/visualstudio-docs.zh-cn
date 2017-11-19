---
title: "IDispatchEx 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a100a193f5e3abcb076fb8aaf3d64a0d0c38833
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchex-interface"></a>IDispatchEx 接口
`IDispatchEx`的扩展`IDispatch`接口，支持的功能不适用于动态语言，如脚本语言。 本部分介绍`IDispatchEx`接口本身，之间的差异`IDispatch`和`IDispatchEx`，和扩展的基本原理。 应读者已经熟悉`IDispatch`并有权访问`IDispatch`文档。  
  
## <a name="remarks"></a>备注  
 `IDispatch`是实质上被开发的 Microsoft Visual Basic。 主要限制`IDispatch`是它假定对象是静态。 换而言之，因为未在运行时更改对象，类型信息可以完全描述它们在编译时。 在 Visual Basic Scripting Edition (VBScript) 等的脚本语言中找到的动态运行时模型和[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]和对象模型，如动态 HTML 需要更灵活的界面。  
  
 `IDispatchEx`开发是为了提供的所有服务`IDispatch`以及适用于等脚本语言的更多动态后期绑定语言某些扩展插件。 其他功能`IDispatchEx`之外提供`IDispatch`是：  
  
-   将新成员添加到对象 ("expando")-使用`GetDispID`与`fdexNameEnsure`标志。  
  
-   删除对象的成员-使用`DeleteMemberByName`或`DeleteMemberByDispID`。  
  
-   区分大小写的调度操作 — 使用`fdexNameCaseSensitive`或`fdexNameCaseInsensitive`。  
  
-   搜索具有隐式名称的成员-使用`fdexNameImplicit`。  
  
-   枚举的对象的 Dispid-使用`GetNextDispID`。  
  
-   从 DISPID 到元素名称的映射 — 使用`GetMemberName`。  
  
-   获取属性的对象成员-使用`GetMemberProperties`。  
  
-   方法调用与`this`指针-使用`InvokeEx`与 DISPATCH_METHOD。  
  
-   允许的浏览器支持的命名空间，以获取父对象的名称空间概念-使用`GetNameSpaceParent`。  
  
 对象支持`IDispatchEx`可能还支持`IDispatch`为了向后兼容。 支持的对象具有动态性`IDispatchEx`几暗示了`IDispatch`这些对象的接口。 例如，`IDispatch`进行以下假设：  
  
-   成员和参数 Dispid 必须保持不变的对象的生存期内。 这允许客户端在获得 Dispid 后，其缓存供以后使用。  
  
 由于`IDispatchEx`允许的添加和删除的成员的一套有效的 Dispid 不保持不变。 但是，`IDispatchEx`需要 DISPID 和成员名称之间的映射保持不变。 这意味着，如果删除成员：  
  
-   不能重复使用 DISPID，直至创建具有相同名称的成员。  
  
-   DISPID 必须保持有效`GetNextDispID`。  
  
-   必须按任何正常接受 DISPID`IDispatch`或`IDispatchEx`方法-它们必须识别为已删除的成员，并返回相应的错误代码 （通常 DISP_E_MEMBERNOTFOUND 或 S_FALSE）。  
  
## <a name="examples"></a>示例  
 这[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]函数 test （） 中的代码执行下列任务：  
  
-   通过调用创建一个新对象`Object`构造函数并将指针赋给变量 obj。 新的对象  
  
-   创建一个新元素名 Elem 为对象中并将指向函数 cat 的指针分配给此元素。  
  
-   调用此函数。 由于它作为一种方法，正在调用`this`指针引用的对象 obj。该函数添加一个新的元素，栏中的，到对象。  
  
 完整的 HTML 代码是：  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 在此相同的网页上施加的控制，可从浏览器到脚本引擎获得调度指针。 然后，该控件可以实现函数 test （）：  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 从控件的代码、 测试、 执行同样的操作作为[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]函数`test()`。 请注意，这些调度调用到运行[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引擎并更改引擎的状态：  
  
-   获取指向 cat 函数使用的调度指针`GetDispID()`。  
  
-   获取指向对象的函数使用的调度指针`GetDispID()`。  
  
-   通过调用对象函数将构造一个对象`InvokeEx()`，并获取指向新构造的对象的调度。  
  
-   在对象中使用创建一个新元素，Elem，`GetDispID()`与`fdexNameEnsure`标志。  
  
-   将调度指针放置在元素中使用 cat `InvokeEx()`。  
  
-   通过调用作为一种方法调用调度指向 cat`InvokeEx()`并在调度指针将传递给构造的对象作为`this`指针。  
  
-   Cat 方法创建一个新的元素，栏中的，对当前`this`对象。  
  
-   验证新的元素中，菜单栏上，在中创建构造的对象通过枚举通过使用的元素`GetNextDispID()`。  
  
 测试控件的代码：  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>方法  
 [IDispatchEx 方法](../../winscript/reference/idispatchex-methods.md)