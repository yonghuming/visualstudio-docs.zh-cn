---
title: "IDispatchEx 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispatchEx 接口"
  - "IDispatchEx 接口, 关于 IDispatchEx"
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDispatchEx 接口
`IDispatchEx`，`IDispatch` 接口的扩展，支持功能适用于动态语言\(如脚本语言。  本节描述 `IDispatchEx` 接口，该接口在 `IDispatch` 和 `IDispatchEx`之间的差异以及扩展的理论基础。  应读取器熟悉 `IDispatch` 和访问 `IDispatch` 文档的。  
  
## 备注  
 `IDispatch` 对于Microsoft Visual Basic基本已经开发了。  `IDispatch` 的主要限制是假定，对象是静态的。  换言之，因为，在运行时，对象不更改，类型信息可详细描述它们在编译时。  在脚本语言中找到例如脚本编辑器的动态运行时设计\(vbscript\)和 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 和对象模型\(例如动态HTML的Visual Basic需要更灵活的接口。  
  
 `IDispatchEx` 中开发提供更具动态后语言适用于例如脚本语言 `IDispatch` 以及某些扩展的所有服务。  `IDispatchEx` 附加功能在 `IDispatch` 提供的参数以外的是：  
  
-   将新成员添加到对象\(“expando”\) —用于 `fdexNameEnsure` 标志的 `GetDispID`。  
  
-   删除对象使用 `DeleteMemberByName` 或 `DeleteMemberByDispID`的成员。  
  
-   区分大小写的计划操作使用 `fdexNameCaseSensitive` 或 `fdexNameCaseInsensitive`。  
  
-   搜索具有隐式名称使用的 `fdexNameImplicit`成员。  
  
-   枚举对象使用 `GetNextDispID`的Dispid。  
  
-   从DISPID映射到元素名称使用 `GetMemberName`。  
  
-   获取对象成员使用 `GetMemberProperties`属性。  
  
-   与 `this` 使用指针 `InvokeEx` 的方法调用与DISPATCH\_METHOD。  
  
-   允许支持命名空间的概念获取对象使用 `GetNameSpaceParent`的命名空间父的浏览器。  
  
 支持 `IDispatchEx` 的对象可能还支持向后兼容的 `IDispatch`。  支持 `IDispatchEx` 对象的动态谓词有一些对象 `IDispatch` 接口的几种含义。  例如，`IDispatch` 进行以下操作：  
  
-   该成员和参数Dispid必须保持不变为对象的生存期。  这允许客户端一次获取Dispid和缓存它们供以后使用。  
  
 因为 `IDispatchEx` 允许成员的添加和删除，将活动Dispid不保持不变。  但是，`IDispatchEx` 需要映射在DISPID和成员名称之间保持不变。  如果成员删除，这意味着：  
  
-   不能重新使用DISPID，直到具有相同名称的成员创建。  
  
-   DISPID必须保持有效。`GetNextDispID`。  
  
-   必须由方法它们必须识别该成员标记为已删除并返回相应的错误代码的正常接受DISPID任何 `IDispatch` 或 `IDispatchEx` \(通常DISP\_E\_MEMBERNOTFOUND或S\_FALSE\)。  
  
## 示例  
 在的此 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码函数可测试\(\) 执行以下操作：  
  
-   通过调用 `Object` 构造函数创建新的对象并将指针发送至变量的Obj的新对象。  
  
-   创建对象名为的Elem一个新的组件并分配给此元素指向功能猫。  
  
-   调用此函数。  因为它调用作为方法，`this` 指针引用对象Obj。  该函数添加一个新元素，条，为对象。  
  
 完整的HTML代码为：  
  
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
  
 此相同网页上的控件中获取计划指向从浏览器的脚本引擎。  控件可以实现函数可测试\(\)：  
  
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
  
 从控件的代码，测试，执行操作和 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 功能 `test()`相同。  注意这些计划调用为运行的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎并更改引擎处理状态：  
  
-   使用 `GetDispID()`，获取计划指向猫功能。  
  
-   使用 `GetDispID()`，获取计划指向对象功能。  
  
-   通过调用与 `InvokeEx()` 的对象功能构造对象并获取计划指向新构造的对象。  
  
-   在对象中创建一个新元素，Elem，使用 `GetDispID()` 用 `fdexNameEnsure` 标志。  
  
-   使用 `InvokeEx()`，将计划指向猫在元素中。  
  
-   调用计划指向猫作为方法通过调用 `InvokeEx()` 并传入计划指向构造的对象作为 `this` 指针。  
  
-   猫方法创建一个新元素，条，在当前 `this` 对象。  
  
-   验证使用 `GetNextDispID()`，新元素，条，在构造对象时的枚举传递通过组件。  
  
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
  
## 方法  
 [IDispatchEx 方法](../../winscript/reference/idispatchex-methods.md)