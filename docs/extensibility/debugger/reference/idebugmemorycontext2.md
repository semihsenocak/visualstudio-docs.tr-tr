---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727432"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Bu arabirim, hata ayıklanan programı çalıştıran makinenin adres alanındaki konumu temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), belleğin bir adresini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) veya [getmemorycontext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) çağrısı bu arabirimi döndürür. Ayrıca, ilgili aritmetik işlem uygulandıktan sonra [Ekle](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) ve [çıkar](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) çağrıları bu arabirimin yeni kopyalarını döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugMemoryContext2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Bu bağlam için Kullanıcı tarafından görüntülenebilen adı alır.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Bu bağlamı açıklayan bilgileri alır.|
|[Ekle](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Yeni bir bağlam oluşturmak için geçerli bağlamın adresine belirtilen bir değer ekler.|
|[Çıkar](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Yeni bir bağlam oluşturmak için, geçerli bağlamın adresinden belirtilen değeri çıkartır.|
|[Karşılaştır](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|İki bağlamı karşılaştırma bayrakları tarafından belirtilen şekilde karşılaştırır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio 'nun **bellek** penceresi, bellek adresi için kullanılan değerlendirilen ifadeyi içeren arabirimi almak Için [getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ' i çağırır `IDebugMemoryContext2` . Bu bağlam daha sonra, okunacak veya yazılacak adresi belirtmek için [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) ve [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) 'a geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
