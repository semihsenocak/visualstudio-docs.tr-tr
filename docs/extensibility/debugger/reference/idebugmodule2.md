---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726914"
---
# <a name="idebugmodule2"></a>IDebugModule2
Bu arabirim, DLL gibi bir programın yürütülebilir bir birimi olan bir modülü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi bir modülü göstermek ve bu modülle ilgili bilgilere erişim sağlamak için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) çağrısı bu arabirimi döndürür. DE, [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) arabirimini [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metodunu kullanarak oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir.

 Bu arabirim Ayrıca bir [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapısında ( [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)çağrısıyla döndürülen) döndürülür.

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) Ayrıca bu arabirimi döndürür ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) arabirimini döndürür).

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugModule2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Bu modülü açıklayan [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) alır.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|Dışı. KULLANMAYıN. Bu modülün sembollerini yeniden yükler.|

## <a name="remarks"></a>Açıklamalar
 Modül bilgileri IDE 'nin **modüller** penceresinde görüntülenebilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
