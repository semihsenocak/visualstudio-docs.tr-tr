---
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 66af4d95707be99865df3df32751215cf5eb10b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181182"
---
# <a name="exception_info"></a>EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklamakta olan program tarafından oluşturulan bir özel durumu veya çalışma zamanı hatasını açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Üyeler  
 pProgram  
 Özel durumun gerçekleştiği programı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.  
  
 bstrProgramName  
 Özel durumun gerçekleştiği programın adı.  
  
 bstrExceptionName  
 Özel durumun adı.  
  
 dwCode  
 Özel durum veya çalışma zamanı hatası için kimlik kodu.  
  
 dwState  
 Özel durumun durumunu tanımlayan [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Numaralandırmadaki bir değer.  
  
 guidType  
 GUID dil tanımlayıcısı, ya da `guidLang` `guidEng` .  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) ve [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) yöntemlerine bir parametre olarak geçirilir. Bu yapı ayrıca doldurulacak [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) yöntemine geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
