---
title: 'IDebugStackFrame3:: Yakatcurrentexception | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719484"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Geçerli özel durumu ele almak istediğinde geçerli yığın çerçevesinde hata ayıklayıcı tarafından çağırılır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Parametreler
`dwFlags`\
'ndaki Farklı eylemleri belirtir. Şu anda yalnızca [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) değeri `IEA_INTERCEPT` desteklenir ve belirtilmelidir.

`pqwCookie`\
dışı Belirli bir özel durumu tanımlayan benzersiz değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

 En yaygın hata döndürme aşağıda verilmiştir.

|Hata|Açıklama|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Geçerli özel durum yakalanamıyor.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Geçerli yürütme çerçevesi henüz bir işleyici için aranmadı.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Bu yöntem bu çerçeve için desteklenmiyor.|

## <a name="remarks"></a>Açıklamalar
 Bir özel durum oluştuğunda, hata ayıklayıcı özel durum işleme işlemi sırasında anahtar noktalarında çalışma zamanından denetim kazanır. Bu önemli süre boyunca, çerçeve özel durumu ele almak isterse, hata ayıklayıcı geçerli yığın çerçevesini sorabilir. Bu şekilde, bir yığın çerçevesinin bir özel durum işleyicisi (örneğin, program kodunda bir try/catch bloğu) olmasa bile, ele geçirilebilecek bir özel durum aslında bir yığın çerçevesi için hareket halindeyken özel durum işleyicisidir.

 Hata ayıklayıcı, özel durumun yakalanmak gerekip gerekmediğini bilmek istediğinde, geçerli yığın çerçeve nesnesi üzerinde bu yöntemi çağırır. Bu yöntem, özel durumun tüm ayrıntılarını işlemekten sorumludur. [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) arabirimi uygulanmayabilir veya `InterceptStackException` Yöntem herhangi bir hata döndürürse, hata ayıklayıcı normal olarak özel durumu işlemeye devam eder.

> [!NOTE]
> Özel durumlar yalnızca yönetilen kodda yakalanabilir, diğer bir deyişle, hata Ayıklanan program .NET çalışma zamanı altında çalışmaktadır. Tabii ki, üçüncü taraf dil uygulayıcıları, `InterceptStackException` seçseler kendi hata ayıklama altyapılarında uygulanabilir.

 Yakalaşmayı tamamladıktan sonra bir [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) sinyali verilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
