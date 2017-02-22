---
title: "DBG_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DBG_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_ATTRIB_FLAGS 枚举"
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 或 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 接口的各个属性。  [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 结构的成员。  
  
## 语法  
  
```cpp#  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```c#  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## 成员  
 DBG\_ATTRIB\_NONE  
 不指示属性。  
  
 DBG\_ATTRIB\_ALL  
 指示所有属性。  
  
 DBG\_ATTRIB\_OBJ\_IS\_EXPANDABLE  
 指示该引用或属性具有子级。  
  
 DBG\_ATTRIB\_OBJ\_HAS\_ID  
 指示此对象的 ID 时创建的。  
  
 DBG\_ATTRIB\_OBJ\_CAN\_HAVE\_ID  
 指示此对象的 ID 可以创建。  
  
 DBG\_ATTRIB\_VALUE\_READONLY  
 指示该值是只读的。  
  
 DBG\_ATTRIB\_VALUE\_ERROR  
 指示该值是错误。  
  
 DBG\_ATTRIB\_VALUE\_SIDE\_EFFECT  
 指示计算具有副作用。  
  
 DBG\_ATTRIB\_OVERLOADED\_CONTAINER  
 指示此属性实际上是一个容器重载。  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN  
 指示在 `DEBUG_PROPERTY_INFO::bstrValue` 的值布尔值。  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN\_TRUE  
 指示在 `DEBUG_PROPERTY_INFO::bstrValue` 的值是布尔值和 `TRUE`。  
  
 DBG\_ATTRIB\_VALUE\_INVALID  
 指示在 `DEBUG_PROPERTY_INFO::bstrValue` 的值无效。  
  
 DBG\_ATTRIB\_VALUE\_NAT  
 指示在 `DEBUG_PROPERTY_INFO::bstrValue` 的值为 “*不是内容*” \(NAT\)。  NAT 在 Intel 64 位处理器描述指示延迟投机异常的一个注册标志。  
  
 DBG\_ATTRIB\_VALUE\_AUTOEXPANDED  
 指示在 `DEBUG_PROPERTY_INFO::bstrValue` 的值可能已自动扩展。  
  
 DBG\_ATTRIB\_VALUE\_TIMEOUT  
 指示计算与计时。  
  
 DBG\_ATTRIB\_VALUE\_RAW\_STRING  
 指示在 `DEBUG_PROPERTY_INFO::bstrValue` 的值可由基元的字符串表示形式。  
  
 DBG\_ATTRIB\_VALUE\_CUSTOM\_VIEWER  
 指示该特性至少有一个自定义浏览器与它。  
  
 DBG\_ATTRIB\_ACCESS\_NONE  
 指示没有 `public`、 `private`，并 `protected` 类型访问的对象。  
  
 DBG\_ATTRIB\_ACCESS\_PUBLIC  
 指示具有公共可访问性的对象。  
  
 DBG\_ATTRIB\_ACCESS\_PRIVATE  
 指示访问私有的对象。  
  
 DBG\_ATTRIB\_ACCESS\_PROTECTED  
 指示保护访问的对象。  
  
 DBG\_ATTRIB\_ACCESS\_FINAL  
 指示访问最终的对象。  
  
 DBG\_ATTRIB\_ACCESS\_ALL  
 提取访问属性的掩码从 `DBG_ATTRIB_FLAGS`。  
  
 DBG\_ATTRIB\_STORAGE\_NONE  
 指示未指定存储的类型。  
  
 DBG\_ATTRIB\_STORAGE\_GLOBAL  
 指示全局存储区。  
  
 DBG\_ATTRIB\_STORAGE\_STATIC  
 指示静态存储。  
  
 DBG\_ATTRIB\_STORAGE\_REGISTER  
 指示在注册的存储。  
  
 DBG\_ATTRIB\_STORAGE\_ALL  
 提取存储属性的掩码从 `DBG_ATTRIB_FLAGS`。  
  
 DBG\_ATTRIB\_TYPE\_NONE  
 指示没有类型修饰符。  
  
 DBG\_ATTRIB\_TYPE\_VIRTUAL  
 指示对象的类型是虚拟的。  
  
 DBG\_ATTRIB\_TYPE\_CONSTANT  
 指示对象的类型是常数。  
  
 DBG\_ATTRIB\_TYPE\_SYNCHRONIZED  
 指示对象的类型同步。  
  
 DBG\_ATTRIB\_TYPE\_VOLATILE  
 指示对象的类型是可变的。  
  
 DBG\_ATTRIB\_TYPE\_ALL  
 提取的掩码类型属性从 `DBG_ATTRIB_FLAGS`。  
  
 DBG\_ATTRIB\_DATA  
 指示此对象是数据字段。  
  
 DBG\_ATTRIB\_METHOD  
 指示此对象是方法。  
  
 DBG\_ATTRIB\_PROPERTY  
 指示此对象是属性。  
  
 DBG\_ATTRIB\_CLASS  
 指示此对象是类。  
  
 DBG\_ATTRIB\_BASECLASS  
 指示此对象是基类。  
  
 DBG\_ATTRIB\_INTERFACE  
 指示此对象是接口。  
  
 DBG\_ATTRIB\_INNERCLASS  
 指示此对象是内部类。  
  
 DBG\_ATTRIB\_MOSTDERIVED  
 指示该对象是 “most\-derived。  术语 “*首选派生的*”表示对象的实际类型，而不是类型的类型引用。  
  
 DBG\_ATTRIB\_CHILD\_ALL  
 通过 `DBG_ATTRIB_MOSTDERIVED`指示 `DBG_ATTRIB_DATA` 掩码。  
  
 DBG\_ATTRIB\_MULTI\_CUSTOM\_VIEWERS  
 指示对象有多个自定义浏览器与它。  
  
## 备注  
  
> [!NOTE]
>  此枚举的值在 C\# 的程序集实际未定义。  相反，必须定义复制到源文件。  
  
 ，例如，这些标志也用于筛选对象的子级，当将作为参数传递 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)。  值可以按位组合使用 `OR`。  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` 标志是表示该 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 从 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 接口的 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口并调用自定义浏览器中列出的 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)