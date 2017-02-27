---
title: "SccAddFromScc 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFromScc"
helpviewer_keywords: 
  - "SccAddFromScc 函数"
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAddFromScc 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数允许用户浏览源代码管理系统中已存在的文件，并随后使这些文件属于当前项目。 例如，此函数可以获取的常见头文件到当前项目而不复制该文件。 返回数组的文件， `lplpFileNames`, ，包含的用户想要将添加到 IDE 项目的文件列表。  
  
## 语法  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpnFiles  
 \[in、 out\]缓冲区中添加的文件数。 \(这是 `NULL` 如果指向的内存 `lplpFileNames` 是被释放。 请参阅备注详细信息\)。  
  
 lplpFileNames  
 \[in、 out\]指向不目录路径的情况下的所有文件名称的指针的数组。 此数组是分配和释放由源代码管理插件。 如果 `lpnFiles` \= 1 和 `lplpFileNames` 不是 `NULL`, ，指向该数组中的第一个名称 `lplpFileNames` 包含目标文件夹。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|文件已成功位于并添加到项目中。|  
|SCC\_I\_OPERATIONCANCELED|操作被取消而不影响。|  
|SCC\_I\_RELOADFILE|需要重新加载文件或项目。|  
  
## 备注  
 IDE 将调用此函数。 如果源代码管理插件支持指定的本地目标文件夹，IDE 将传递 `lpnFiles` \= 1，并将传递到本地文件夹名称 `lplpFileNames`。  
  
 当调用 `SccAddFromScc` 函数返回时，该插件已将值分配到 `lpnFiles` 和 `lplpFileNames`, ，如有必要的文件名称数组分配内存 \(请注意，此分配替代中的指针 `lplpFileNames`\)。 源代码管理插件负责将所有文件都放到用户的目录或指定的指定文件夹中。 然后，IDE 将文件添加到 IDE 项目。  
  
 最后，IDE 将调用此函数的第二次，并传入 `NULL` 为 `lpnFiles`。 这被解释为特殊的信号由源代码管理插件用于释放为的文件名称数组中分配的内存 `lplpFileNames``.`  
  
 `lplpFileNames` 是 `char ***` 指针。 源代码管理插件将放置到的文件的名称，因此将以标准方式的列表传递此 api 的指针的数组的指针。  
  
> [!NOTE]
>  初始版本的 VSSCI API 未提供一种方法，以指示添加的文件的目标项目。 为此的语义 `lplpFIleNames` 参数已得到增强，以使其输入\/输出参数，而不是一个 output 参数。 如果仅指定一个文件，即指向的值由 `lpnFiles` \= 1，则第一个元素的 `lplpFileNames` 包含目标文件夹。 若要使用这些新的语义，IDE 调用 `SccSetOption` 起作用 `nOption`参数设置为 `SCC_OPT_SHARESUBPROJ`。 如果源代码管理插件不支持语义，它将返回 `SCC_E_OPTNOTSUPPORTED`。 执行使用的是禁用 **从源代码管理添加** 功能。 如果插件支持 **从源代码管理添加** 功能 \(`SCC_CAP_ADDFROMSCC`\)，则它必须支持新的语义，并返回 `SCC_I_SHARESUBPROJOK`。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)