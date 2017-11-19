---
title: "&lt;文件&gt;元素 （ClickOnce 应用程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: "24"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f448b7455bcbe13b7257a58a0eafbadd1165b197
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;文件&gt;元素 （ClickOnce 应用程序）
标识下载和应用程序使用的所有非程序集文件。  
  
## <a name="syntax"></a>语法  
  
```  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `file` 元素是可选的。 元素具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`name`|必需。 标识文件的名称。|  
|`size`|必需。 指定的大小，以字节的文件。|  
|`group`|可选的如果`optional`属性未指定或设置为`false`; 如果存在`optional`是`true`。 此文件所属的组的名称。 名称可以是由开发人员，选择任何 Unicode 字符串值，用于下载文件使用按需<xref:System.Deployment.Application.ApplicationDeployment>类。|  
|`optional`|可选。 指定此文件必须下载第一个应用程序时运行，还是是否文件之前应用程序请求它按需应驻留在服务器上仅。 如果`false`或未定义，该文件将下载时首次运行或安装应用程序。 如果`true`、`group`必须为有效的应用程序清单中指定。 `optional`不能为 true 如果`writeableType`值指定`applicationData`。|  
|`writeableType`|可选。 指定此文件是一个数据文件。 目前，唯一有效的值是`applicationData`。|  
  
## <a name="typelib"></a>类型库  
 `typelib`元素是可选元素子级的文件。 元素描述 COM 组件所属的类型库。 元素具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`tlbid`|必需。 分配给类型库的 GUID。|  
|`version`|必需。 类型库的版本号。|  
|`helpdir`|必需。 包含该组件的帮助文件的目录。 可能是长度为零。|  
|`resourceid`|可选。 十六进制字符串表示形式的区域设置标识符 (LCID)。 它为一至四个十六进制数字不带 0x 前缀和不带前导零。 LCID 可能具有特定的次语言标识符。|  
|`flags`|可选。 此类型库的类型库标志的字符串表示形式。 具体而言，它应为"受限"、"控件"、"隐藏"和"HASDISKIMAGE"之一。|  
  
## <a name="comclass"></a>comClass  
 `comClass`元素是可选的子`file`，但如果元素是必需[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序包含它想要使用免注册 com。 部署的 COM 组件 元素具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`clsid`|必需。 表示作为 GUID 的 COM 组件的类 ID。|  
|`description`|可选。 类名。|  
|`threadingModel`|可选。 使用进程内 COM 类的线程处理模型。 如果此属性为 null，则不使用任何线程处理模型。 在客户端的主线程上创建该组件和来自其他线程的调用封送到此线程。 以下列表显示有效的值：<br /><br /> `Apartment`、`Free`、`Both` 和 `Neutral`。|  
|`tlbid`|可选。 用于此 COM 组件的类型库的 GUID。|  
|`progid`|可选。 与 COM 组件的版本依赖型编程标识符。 格式`ProgID`是`<vendor>.<component>.<version>`。|  
|`miscStatus`|可选。 在程序集中的重复项清单提供的信息`MiscStatus`注册表项。 如果值为`miscStatusIcon`， `miscStatusContent`， `miscStatusDocprint`，或`miscStatusThumbnail`找不到属性、 中列出的相应默认值`miscStatus`用于缺少的特性。 值可以是以下表格中的属性值的以逗号分隔列表。 你可以使用此属性的 COM 类是否需要为 OCX 类`MiscStatus`注册表项值。|  
|`miscStatusIcon`|可选。 在程序集中的重复项清单 DVASPECT_ICON 提供的信息。 它可以提供一个对象的图标。 值可以是以下表格中的属性值的以逗号分隔列表。 你可以使用此属性的 COM 类是否需要为 OCX 类`Miscstatus`注册表项值。|  
|`miscStatusContent`|可选。 在程序集中的重复项清单 DVASPECT_CONTENT 提供的信息。 它可以提供屏幕或打印机可显示的复合文档。 值可以是以下表格中的属性值的以逗号分隔列表。 你可以使用此属性的 COM 类是否需要为 OCX 类`MiscStatus`注册表项值。|  
|`miscStatusDocPrint`|可选。 在程序集中的重复项清单 DVASPECT_DOCPRINT 提供的信息。 它可以提供可显示的对象表示在屏幕上，就像打印到打印机。 值可以是以下表格中的属性值的以逗号分隔列表。 你可以使用此属性的 COM 类是否需要为 OCX 类`MiscStatus`注册表项值。|  
|`miscStatusThumbnail`|可选。 程序集内的重复清单 DVASPECT_THUMBNAIL 提供的信息。 它可以提供的对象中浏览工具可显示的缩略图。 值可以是以下表格中的属性值的以逗号分隔列表。 你可以使用此属性的 COM 类是否需要为 OCX 类`MiscStatus`注册表项值。|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 `comInterfaceExternalProxyStub`元素是可选的子`file`元素，但如果可能需要[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序包含它想要使用免注册 com。 部署的 COM 组件 元素包含以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`iid`|必需。 接口 ID (IID) 由此代理。 该 IID 必须有语法错误。 的大括号。|  
|`baseInterface`|可选。 从其接口引用的接口的 IID`iid`派生。|  
|`numMethods`|可选。 实现由接口的方法数。|  
|`name`|可选。 因为该接口的名称将出现在代码中。|  
|`tlbid`|可选。 包含指定的接口的说明的类型库`iid`属性。|  
|`proxyStubClass32`|可选。 将 IID 映射到 32 位代理 Dll 中 CLSID。|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 `comInterfaceProxyStub`元素是可选的子`file`元素，但如果可能需要[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序包含它想要使用免注册 com。 部署的 COM 组件 元素包含以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`iid`|必需。 接口 ID (IID) 由此代理。 该 IID 必须有语法错误。 的大括号。|  
|`baseInterface`|可选。 从其接口引用的接口的 IID`iid`派生。|  
|`numMethods`|可选。 实现由接口的方法数。|  
|`Name`|可选。 因为该接口的名称将出现在代码中。|  
|`Tlbid`|可选。 包含指定的接口的说明的类型库`iid`属性。|  
|`proxyStubClass32`|可选。 将 IID 映射到 32 位代理 Dll 中 CLSID。|  
|`threadingModel`|可选。 可选。 使用进程内 COM 类的线程处理模型。 如果此属性为 null，则不使用任何线程处理模型。 在客户端的主线程上创建该组件和来自其他线程的调用封送到此线程。 以下列表显示有效的值：<br /><br /> `Apartment`、`Free`、`Both` 和 `Neutral`。|  
  
## <a name="windowclass"></a>windowClass  
 `windowClass`元素是可选的子`file`元素，但如果可能需要[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序包含它想要使用免注册 com。 部署的 COM 组件 元素是指由 COM 组件，必须具有应用于它的版本中定义的窗口类。 元素包含以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`versioned`|可选。 控件的内部窗口类注册中使用的名称是否包含含有窗口类的程序集的版本。 此属性的值可以是`yes`或`no`。 默认值为 `yes`。 值`no`只用于如果相同的窗口类定义的并排显示组件和等效的非并行组件，并且你想要将它们视为相同的窗口类。 请注意，关于窗口类注册的常用规则应用 — 只有注册窗口类的第一个组件将能够注册它，因为它不具有应用于它的版本。|  
  
## <a name="hash"></a>hash  
 `hash`元素是可选的子`file`元素。 `hash`元素没有任何特性。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用应用程序中的所有文件的哈希算法作为一种安全检查，以确保部署之后的任何文件发生更改。 如果`hash`元素不包含，则不会执行此检查。 因此，省略`hash`元素不建议。  
  
 如果清单包含不进行哈希处理的文件，无法对该清单进行数字签名，因为用户无法验证未经哈希的文件的内容。  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 `dsig:Transforms`元素是必需的子`hash`元素。 `dsig:Transforms`元素没有任何特性。  
  
## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform`元素是必需的子`dsig:Transforms`元素。 `dsig:Transform`元素具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`Algorithm`|用来计算此文件的摘要的算法。 当前使用的唯一值[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]是`urn:schemas-microsoft-com:HashTransforms.Identity`。|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`元素是必需的子`hash`元素。 `dsig:DigestMethod`元素具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`Algorithm`|用来计算此文件的摘要的算法。 当前使用的唯一值[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]是`http://www.w3.org/2000/09/xmldsig#sha1`。|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 `dsig:DigestValue`元素是必需的子`hash`元素。 `dsig:DigestValue`元素没有任何特性。 其文本值是指定的文件的计算哈希。  
  
## <a name="remarks"></a>备注  
 此元素标识组成应用程序的所有非程序集文件和具体而言，文件验证有关的哈希值。 此元素还可以包括与文件关联的组件对象模型 (COM) 隔离数据。 如果文件发生更改，应用程序清单文件还必须更新以反映更改。  
  
## <a name="example"></a>示例  
 下面的代码示例阐释了`file`应用程序中的元素的部署使用的应用程序清单[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。  
  
```  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)