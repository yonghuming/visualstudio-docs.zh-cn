---
title: "DisassemblyData | Microsoft Docs"
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
  - "DisassemblyData"
helpviewer_keywords: 
  - "DisassemblyData 结构"
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# DisassemblyData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述集成开发环境 \(ide\) 的一个反汇编命令 \(IDE\)将显示。  
  
## 语法  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```c#  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## 成员  
 `dwFields`  
 指定的 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 常数哪些字段。完成。  
  
 `bstrAddress`  
 地址为从某些的偏移量起点 \(通常关联的函数的开头\)。  
  
 `bstrCodeBytes`  
 此命令的代码字节。  
  
 `bstrOpcode`  
 此命令的操作码。  
  
 `bstrOperands`  
 此命令的操作数。  
  
 `bstrSymbol`  
 符号名，如果有，与地址 \(公共符号，标签，等等\)。  
  
 `uCodeLocationId`  
 此被拆卸行的代码位置标识符。  如果一行代码上下文地址比另一个的代码上下文地址大，则将反汇编的代码位置标识符第一个也比代码位置标识符大第二个。  
  
 `posBeg`  
 对应于文档的位置反汇编数据开始的 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) 。  
  
 `posEnd`  
 对应于文档的位置反汇编数据结尾的 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) 。  
  
 `bstrDocumentUrl`  
 使用格式 `file://file 名称`，对于可表示为文件名的文本文档， `bstrDocumentUrl` 字段创建一个源可以找到的文件名，填充。  
  
 对于不能表示为文件名的文本文档， `bstrDocumentUrl` 是文档的唯一标识符，因此，调试引擎必须执行 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) 方法。  
  
 此字段也可以包含有关校验和的附加信息。  请参见 " 备注 " 了解详细信息。  
  
 `dwByteOffset`  
 字节数命令是从初始代码行。  
  
 `dwFlags`  
 指定的 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) 常数的标志处于活动状态。  
  
## 备注  
 每 `DisassemblyData` 结构描述反汇编的命令。  数组这些结构从 [读取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 方法返回。  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) framework 为文本只使用基本单据。  此命令的源代码大小为生成的第一个命令只能在从语句或行，例如，那么，当 `dwByteOffset == 0`。  
  
 对于文档是非文本的，文档上下文可以从代码获取，因此， `bstrDocumentUrl` 字段应为 null 值。  如果 `bstrDocumentUrl` 字段相同的与前面的 `DisassemblyData` 数组元素的 `bstrDocumentUrl` 字段，然后将 `bstrDocumentUrl` 为一个 null 值。  
  
 如果 `dwFlags` 字段都有 `DF_DOCUMENT_CHECKSUM` 设置了标志，则附加的检查和信息遵循该字符串指向由 `bstrDocumentUrl` 字段。  具体而言，对 null 字符串结束符后，其中遵循标识依次通过指示字节数在检查和的 4 个字节值执行，并通过检查和字节而执行的检查和算法的 GUID。  请参见本主题中的示例有关如何输入和解密。 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]的此字段。  
  
## 示例  
 ，如果 `DF_DOCUMENT_CHECKSUM` 设置了标志， `bstrDocumentUrl` 字段可以包含其他信息字符串以外的。  创建和读取此编码字符串处理非常简单在 [!INCLUDE[vcprvc](../../../debugger/includes/vcprvc_md.md)]。  但是，在 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]，它是另一个问题。  对于是好奇的人员，下面的示例演示一种创建从 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] 的编码字符串和一种解密。 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]的编码字符串。  
  
```c#  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [读取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)