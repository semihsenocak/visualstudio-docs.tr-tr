---
title: 'IDebugProperty3:: GetCustomViewerList | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 212f8d251232d35ee7d9cc46074a21239eea29f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721164"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Bu özellikle ilişkili özel görüntüleyicilerin bir listesini alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celtSkip`\
'ndaki Atlanacak görüntüleyiciler sayısı.

`celtRequested`\
'ndaki Alınacak görüntüleyiciler sayısı (Ayrıca dizinin boyutunu belirtir `rgViewers` ).

`rgViewers`\
[in, out] Doldurulacak [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapıları dizisi.

`pceltFetched`\
dışı Döndürülen gerçek izleyici sayısı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Tür görselleştiricileri desteklemek için, bu yöntem çağrıyı [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemine iletir. İfade değerlendirici bu özelliğin türü için özel görüntüleyiciler de destekliyorsa, bu yöntem ilgili özel görüntüleyicilerin listeye eklenmesini sağlayabilir.

Tür Görselleştiriciler ve özel görüntüleyiciler arasındaki farklılıklar hakkındaki ayrıntılar için bkz. [tür görselleştiricisi ve özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini kullanıma sunan bir **cproperty** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)
{
    if (NULL == prgViewers)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
