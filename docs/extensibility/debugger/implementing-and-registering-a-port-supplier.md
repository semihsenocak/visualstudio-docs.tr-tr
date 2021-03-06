---
title: Bağlantı noktası sağlayıcısı uygulama ve kaydetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738527"
---
# <a name="implement-and-register-a-port-supplier"></a>Bir bağlantı noktası sağlayıcısı uygulama ve kaydetme
Bir bağlantı noktası tedarikçinin rolü, işlem yönetimini izleyen ve bu bağlantı noktalarını izlemek ve sağlamak için kullanılır. Bir bağlantı noktasının oluşturulması gerektiğinde, bağlantı noktası sağlayıcısının GUID 'SI ile CoCreate kullanılarak oluşturulur (oturum hata ayıklama Yöneticisi [SDM], kullanıcının seçtiği bağlantı noktası tedarikçisine veya proje sistemi tarafından belirtilen bağlantı noktası sağlayıcısına) sahip olur. SDM daha sonra herhangi bir bağlantı noktasının eklenip eklenediğine bakmak için [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) öğesini çağırır. Bir bağlantı noktası eklenediyse, [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) çağırarak ve bağlantı noktasını açıklayan bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) geçirerek yeni bir bağlantı noktası istenir. `AddPort` bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilen yeni bir bağlantı noktasını döndürür.

## <a name="discussion"></a>Tartışma
 Bir bağlantı noktası, bir makine ya da hata ayıklama sunucusu ile ilişkilendirilmiş bir bağlantı noktası sağlayıcısı tarafından oluşturulur. Sunucu, bağlantı noktası tedarikçilerini[Trksağlayıcılar](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) yöntemiyle numaralandırır ve bir bağlantı noktası tedarikçisi, [TRTs](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) yöntemiyle bağlantı noktalarını numaralandırır.

 Tipik COM kaydına ek olarak, bir bağlantı noktası tedarikçinin CLSID ve adı belirli kayıt defteri konumlarına yerleştirerek kendisini Visual Studio ile kaydetmesi gerekir. Bu adı işleyen bir hata ayıklama SDK Yardımcısı işlevi `SetMetric` : her öğe kaydedilecek şekilde çağrılır, bu nedenle:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Bir bağlantı noktası sağlayıcısı `RemoveMetric` , kayıtlı her öğe için bir kez çağırarak (başka bir hata ayıklama SDK Yardımcısı işlevi) kendisini siler, bu nedenle:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> [Hata ayıklama Için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` ve `RemoveMetric` *dbgmetric. h* içinde tanımlanan ve *ad2de. lib*içinde derlenen statik işlevlerdir. `metrictypePortSupplier`, `metricCLSID` Ve `metricName` yardımcıları *dbgmetric. h*içinde de tanımlanmıştır.

 Bir bağlantı noktası sağlayıcısı, sırasıyla [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) ve [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)YÖNTEMLERI aracılığıyla adını ve GUID 'sini sağlayabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Bağlantı noktası tedarikçileri](../../extensibility/debugger/port-suppliers.md)
