---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715348"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Bu arabirim [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılarını numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), belirli bir özellik için bilgileri göstermek üzere bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Belirli bir özelliğin alt öğelerini temsil eden bu arabirimi edinmek için [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) öğesini çağırın. Belirli bir yığın çerçevesinin özelliklerini temsil eden bu arabirimi edinmek için [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugPropertyInfo2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Sabit Listesi dizisinde belirtilen sayıda [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısını alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Bir Numaralandırıcı içindeki [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Genel olarak, bir özellik ad, değer, adres ve tür, ilişkili özellik nesnesine veya yığın çerçevesine uygun diğer bilgileri içerebilen bir bilgi hiyerarşisidir. Daha fazla bilgi için bkz. [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
