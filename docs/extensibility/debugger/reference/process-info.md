---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713879"
---
# <a name="process_info"></a>PROCESS_INFO
Bir işlem hakkındaki bilgileri içerir.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Üyeler
 `Fields`\
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi.

 `bstrFileName`\
 İşlemin tam yol adı. Parametresiyle [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metodunu çağırmaya eşdeğerdir `GN_FILENAME` .

 `bstrBaseName`\
 İşlemin dosya adı ve uzantısı. `IDebugProcess2::Getname`Yöntemi parametresiyle çağırma ile eşdeğerdir `GN_BASENAME` .

 `bstrTitle`\
 Bir varsa, işlemin başlığı. `IDebugProcess2::Getname`Yöntemi parametresiyle çağırma ile eşdeğerdir `GN_TITLE` .

 `ProcessId`\
 İşlemi tanımlayan [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısı. [Getphysicalprocessıd](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) yöntemini çağırmaya eşdeğerdir.

 `dwSessionId`\
 Bu işlemin üzerinde çalıştığı hata ayıklama oturumunun tanımlayıcısı.

 `bstrAttachedSessionName`\
 Eklenen oturum adı. [Getattachedoturumadı](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) yöntemini çağırmaya eşdeğerdir.

 `CreationTime`\
 İşlemin oluşturulduğu zaman.

 `Flags`\
 İşlemin özelliklerini belirten [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) Numaralandırmadaki bayrakların birleşimi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, doldurulduğu [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
