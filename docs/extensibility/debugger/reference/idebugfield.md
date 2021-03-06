---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728759"
---
# <a name="idebugfield"></a>IDebugField
Bu arabirim bir alanı, diğer bir deyişle, bir simgenin veya türün açıklamasını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir sembol sağlayıcısı, bu arabirimi tüm alanları için temel sınıf olarak uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, tüm alanlar için temel sınıftır. Bu arabirim, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md)'nin dönüş değerine bağlı olarak, [QueryInterface](/cpp/atl/queryinterface)kullanarak daha özelleştirilmiş arabirimler döndürebilir. Ayrıca, birçok arabirim `IDebugField` çeşitli metotlardan nesne döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugField` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Sembol veya tür hakkında görüntülenebilen bilgileri alır.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Alan türünü alır.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Alan türünü alır.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Alanın kapsayıcısını alır.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Alanın adresini alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Bir alanın boyutunu bayt cinsinden alır.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Bir alanla ilgili genişletilmiş bilgileri alır.|
|[Eşittir](../../../extensibility/debugger/reference/idebugfield-equal.md)|İki alanı karşılaştırır.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Sembol veya tür hakkındaki tür bağımsız bilgileri alır.|

## <a name="remarks"></a>Açıklamalar
 Bir tür C diline eşdeğerdir `typedef` .

 Aşağıdaki C++ dili örneğinde, `weather` bir sınıf türüdür ve `sunny` `stormy` simgeler şunlardır:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Bir alanın bir simgeyi veya türü temsil edip etmediği, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) çağırarak ve [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) sonucunu inceleyerek belirlenebilir. `FIELD_KIND_TYPE`Bit ayarlandıysa, alan bir türdür ve `FIELD_KIND_SYMBOL` bit ayarlandıysa, bir simgedir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
