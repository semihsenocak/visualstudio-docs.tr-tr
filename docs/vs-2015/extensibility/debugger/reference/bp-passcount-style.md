---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: deb4ce7c464e8518faff55957e1873ef1cd92c39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153366"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kesme noktasının tetiklenmesine neden olan kesme noktası geçiş sayısıyla ilişkili koşulu belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Üyeler  
 BP_PASSCOUNT_NONE  
 Kesme noktası geçiş sayısı stilini belirtir.  
  
 BP_PASSCOUNT_EQUAL  
 Kesme noktası geçiş sayısı stilini eşit olarak ayarlar. Kesme noktası, kesme noktası isabet sayısına eşit olduğunda harekete geçirilir.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Kesme noktası geçiş sayısı stilini eşit veya daha büyük olarak ayarlar. Kesme noktası, kesme noktası isabet sayısı, geçiş sayısına eşit veya ondan daha büyük olduğunda ateşlenir.  
  
 BP_PASSCOUNT_MOD  
 Modül geçiş sayısını belirtir. Örneğin, geçiş sayısı tür ise `BP_PASSCOUNT_MOD` ve pass Count değeri 4 ise, her isabet sayısı 4 ' ün katı olduğunda kesme noktası ateşlenir.  
  
## <a name="remarks"></a>Açıklamalar  
 `stylePassCount` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapılarının bir üyesini sırayla [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) yapısının üyesi için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
