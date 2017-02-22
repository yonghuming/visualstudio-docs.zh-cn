---
title: "Bitflags 由特定的命令使用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件、 bitflags 由特定的命令使用"
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Bitflags 由特定的命令使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以通过在单个值中设置一个或多个位修改多个源控制插件 API 中的函数的行为。 这些值称为 bitflags。 使用源控制插件 API 各种 bitflags 详细介绍了在这里，使用这些函数进行分组。  
  
## 签出标志  
 可以为任何一个设置此标志 [SccAdd](../extensibility/sccadd-function.md) 或 [SccCheckin](../extensibility/scccheckin-function.md)。  
  
|Flag|值|描述|  
|----------|-------|--------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|保持签出该文件。|  
  
## 添加标记  
 通过使用这些标志 [SccAdd](../extensibility/sccadd-function.md)。  
  
|Flag|值|描述|  
|----------|-------|--------|  
|`SCC_FILETYPE_AUTO`|0x00|源代码管理插件需要自动检测文件是否是文本或二进制文件。|  
|`SCC_FILETYPE_TEXT`|0x01|文件类型为文本。|  
|`SCC_FILETYPE_BINARY`|0x04，则|文件类型为二进制。 **Note:**  `SCC_FILETYPE_TEXT` 和 `SCC_FILETYPE_BINARY` 标志是互相排斥。 设置恰好一个还是两者皆否。|  
|`SCC_ADD_STORELATEST`|0x02|存储仅最新版本 \(没有增量\)。|  
  
## 比较标志  
 [SccDiff](../extensibility/sccdiff-function.md) 使用这些标志来定义 diff 运算的作用域。`SCC_DIFF_QD_xxx` 标志是互相排斥。 如果指定了其中任何一个，则没有可视反馈是得到。 在"快速比较"\(QD\)，该插件不能确定该文件的不同，仅当它是不同的方式。 如果不指定这些标志，实现"可视化差异";计算和显示详细的文件之间的差异。 如果不支持请求的 QD，插件将移到下一步最好的一个。 例如，如果 IDE 请求校验和，并且该插件不支持它时，插件会完整内容检查 \(仍速度快于以可视方式显示\)。  
  
|Flag|值|说明|  
|----------|-------|--------|  
|`SCC_DIFF_IGNORECASE`|0x0002|忽略大小写差异。|  
|`SCC_DIFF_IGNORESPACE`|0x0004|忽略空白差异。 **Note:**  `SCC_DIFF_IGNORECASE` 和 `SCC_DIFF_IGNORESPACE` 标志为可选 bitflags。|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|通过将整个文件内容进行比较的 QD。|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|通过校验和 QD。|  
|`SCC_DIFF_QD_TIME`|0x0040|通过文件日期\/时间戳 QD。|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|这是用于检查所有 QD bitflags 掩码。 它不应传递到函数;三个 QD bitflags 是互相排斥的。 QD 始终表示不显示 UI。|  
  
## PopulateList 标志  
 通过使用此标志 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 中 `fOptions` 参数。  
  
|Flag|值|描述|  
|----------|-------|--------|  
|`SCC_PL_DIR`|0x00000001L|IDE 传递目录，不是文件。|  
  
## PopulateDirList 标志  
 通过使用这些标志 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 中 `fOptions` 参数。  
  
|选项值|值|描述|  
|---------|-------|--------|  
|SCC\_PDL\_ONELEVEL|0x0000|检查的目录 \(这是默认值\) 的目录的仅一个级别。|  
|SCC\_PDL\_RECURSIVE|它需要 0x0001|以递归方式检查每个给定目录下的所有目录。|  
|SCC\_PDL\_INCLUDEFILES|0x0002|检查过程中包括文件的名称。|  
  
## 打开项目标志  
 通过使用这些标志 [SccOpenProject](../extensibility/sccopenproject-function.md) 中 `dwFlags` 参数。  
  
|选项值|值|说明|  
|---------|-------|--------|  
|SCC\_OP\_CREATEIFNEW|0x00000001L|如果项目在源代码管理中不存在，则创建它。 如果未设置此标志，提示用户输入项目以创建 \(除非 `SCC_OP_SILENTOPEN` 指定标志\)。|  
|SCC\_OP\_SILENTOPEN|0x00000002L|不提示用户创建一个项目;仅返回 `SCC_E_UNKNOWNPROJECT`。|  
  
## 获取标志  
 通过使用这些标志 [SccGet](../extensibility/sccget-function.md) 和 [SccCheckout](../extensibility/scccheckout-function.md)。  
  
|Flag|值|描述|  
|----------|-------|--------|  
|`SCC_GET_ALL`|0x00000001L|IDE 谁在传递目录，而不是文件: 获取这些目录中的所有文件。|  
|`SCC_GET_RECURSIVE`|0x00000002L|IDE 谁在传递目录: 获取这些目录和其所有子目录。|  
  
## nOption 值  
 通过使用这些标志 [SccSetOption](../extensibility/sccsetoption-function.md) 中 `nOption` 参数。  
  
|Flag|值|说明|  
|----------|-------|--------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|设置事件队列的状态。|  
|`SCC_OPT_USERDATA`|0x00000002L|指定的用户数据 `SCC_OPT_NAMECHANGEPFN`。|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE 可以处理取消|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|设置名称更改为回调。|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|禁用源控制插件 UI 签出并不设置工作目录。|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|添加从源代码管理系统，以指定工作目录。 请尝试进行的直接后代是否共享到关联的项目。|  
  
## Bitflags dwVal  
 通过使用这些标志 [SccSetOption](../extensibility/sccsetoption-function.md) 中 `dwVal` 参数。  
  
|Flag|值|描述|使用 `nOption` 值|  
|----------|-------|--------|--------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|事件队列活动挂起。|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|启用事件队列日志记录。|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|\(默认值\)进入任何取消模式;如果需要，必须提供插件。|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE 处理取消。|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|\(默认值\)确定以从插件 UI，则签出设置工作目录。|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|没有插件的 UI 签出，没有工作目录。|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)