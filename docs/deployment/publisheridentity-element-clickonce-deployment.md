---
title: "&lt;publisherIdentity&gt;元素 （ClickOnce 部署） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 9a59b97b3260beaf39ae20b62a44903add13e622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt;元素 （ClickOnce 部署）
包含有关为此部署清单签名的发布者的信息。  
  
## <a name="syntax"></a>语法  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `publisherIdentity`元素是必需的签名的清单。 下表显示的特性`publisherIdentity`元素支持。  
  
|特性|说明|  
|---------------|-----------------|  
|`name`|必需。 描述此应用程序发布一方的标识。|  
|`issuerKeyHash`|必需。 包含证书颁发者的公钥的 sha-1 哈希。|  
  
#### <a name="parameters"></a>参数  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
  
## <a name="exceptions"></a>异常  
  
## <a name="remarks"></a>备注  
  
## <a name="requirements"></a>要求  
  
## <a name="subhead"></a>副标题