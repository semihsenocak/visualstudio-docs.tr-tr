---
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720658"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) hata ayıklama altyapısını (DE) temsil eden bir arabirim almasına izin verir.

## <a name="syntax"></a>Syntax

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Ayrıca, bu arabirimi en yaygın olarak kullanılan ( [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)ve [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)gibi) nesnelerin kendi [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabirimine erişime izin vermek için uygulayan nesneler üzerinde de uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi edinmek için tipik bir DE arabirimi üzerinde [QueryInterface](/cpp/atl/queryinterface) 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugQueryEngine2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Özel bir hata ayıklama altyapısı (DE) arabirimini alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim tipik olarak işlevler aracılığıyla sıralı adımlamayı desteklemek için [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimini uygulayan nesnede uygulanır; diğer bir deyişle, hata ayıklayıcı bir işlevden dışarı adımla, yürütülecek sonraki işlev yığında önceki işlev olmayabilir, ancak başka bir iş parçacığında bir işlev değildir. "Causitesi" tanımı için bkz. [Visual Studio hata ayıklayıcısı sözlüğü](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
