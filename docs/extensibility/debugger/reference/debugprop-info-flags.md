---
title: "DEBUGPROP_INFO_FLAGS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 11
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5b749cffbc05fcc3fa6c533dc4bb3bdcd1ad1c0
ms.lasthandoff: 02/22/2017

---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
指定要检索的调试属性对象有关的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>成员  
 DEBUGPROP_INFO_FULLNAME  
 初始化或使用`bstrFullName`字段。  
  
 DEBUGPROP_INFO_NAME  
 初始化或使用`bstrName`字段。  
  
 DEBUGPROP_INFO_TYPE  
 初始化或使用`bstrType`字段。  
  
 DEBUGPROP_INFO_VALUE  
 初始化或使用`bstrValue`字段。  
  
 DEBUGPROP_INFO_ATTRIB  
 初始化或使用`dwAttrib`字段。  
  
 DEBUGPROP_INFO_PROP，  
 初始化或使用`pProperty`包含字段[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)接口。  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 指定值字段应包含自动扩展的值，是否可用，此类型的对象。  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 已否决。  
  
 DEBUGPROP_INFO_VALUE_RAW  
 不返回任何美化值或成员 （即，不进行格式化值）。  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 不返回任何特殊的合成的值 (例如，不要调用`ToString()`某个对象以生成值)。  
  
 DEBUGPROP_INFO_NONE  
 指定不设置任何标志。  
  
 DEBUGPROP_INFO_STANDARD  
 初始化或使用`dwAttrib`， `bstrName`， `bstrType`，和`bstrValue`字段。  
  
 DEBUGPROP_INFO_All  
 指示所有标志的掩码。  
  
## <a name="remarks"></a>备注  
 这些值传递给[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)， [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)，和[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)方法，以指示哪些字段是要初始化[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)结构。  
  
 这些值还用于`dwFields`的成员`DEBUG_PROPERTY_INFO`以表明该结构的哪些字段是用和有效时返回结构的结构。  
  
 这些值可能与按位结合起来`OR`。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
