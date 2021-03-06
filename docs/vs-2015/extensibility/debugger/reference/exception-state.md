---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e30d9cc9df592cc6feb97c14449dbc6a122ec63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149364"
---
# <a name="exception_state"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Özel durum durumunu belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Üyeler  
 EXCEPTION_NONE  
 Özel durumunda durmayın.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 İlk özel durum tetikde durdur. Özel durum olayını açıkladığınızda, bu bayrak özel durum olayının ilk şans özel durum olayı olduğunu gösterir.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Özel durumun ikinci olarak TETİKİ durdur. Bir özel durum olayını açıkladığınızda, özel durum olayının ikinci şans özel durum olayı olduğunu gösterir.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Kullanıcı modu özel durumunun ilk aşamasında durun. Bir özel durum olayını açıkladığınızda, özel durum olayının bir birinci şans Kullanıcı özel durum olayı olduğunu gösterir.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Bir Kullanıcı modu özel durumu yakalanmadığında durdur. Bir özel durum olayını açıkladığınızda, özel durum olayının yakalanamayan bir Kullanıcı modu özel durum olayı olduğunu gösterir.  
  
 EXCEPTION_STOP_ALL  
 Herhangi bir özel durum üzerinde durun. Bir özel durum olayı açıklanırken kullanılmaz.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 Bir özel durum olayını açıkladığınızda, özel durumun devam ettirilemez olduğunu gösterir.  
  
 EXCEPTION_CODE_SUPPORTED  
 Özel durumun onu destekleyen kodu olduğunu gösterir. Özel durum görüntülemek için kullanılır  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Özel durum kodunun onaltılı olarak görüntülenmesi gerektiğini gösterir. Özel durum görüntülemek için kullanılır.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Özel durum kodunun, Barkodmkodu desteklediğini gösterir. Özel durum görüntülemek için kullanılır.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Yönetilen kod hata ayıklayıcının özel durumları işlemesinin gerektiği anlamına gelir. Ayarlanmamışsa, varsayılan hata ayıklayıcı özel durumları işler. Bu, [Setallexceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) yöntemine geçirilir ve [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısında kullanılmaz.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 ARTıK KULLANıLMıYOR, KULLANMAYıN.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 ARTıK KULLANıLMıYOR, KULLANMAYıN.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 ARTıK KULLANıLMıYOR, KULLANMAYıN.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 ARTıK KULLANıLMıYOR, KULLANMAYıN.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwState`Özel durumun durumunu ve bunun için neler yapılabileceğini göstermek için [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısının üyesi olarak kullanılır.  
  
 Bu değerler, tüm özel durumların durumunu ayarlamak için [Setallexceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) yöntemine de geçirilir.  
  
 Bu bayraklar bit düzeyinde OR ile birleştirilebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
