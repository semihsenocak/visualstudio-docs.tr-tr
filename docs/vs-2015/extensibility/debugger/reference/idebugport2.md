---
title: IDebugPort2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9227e2e05499feac628a5b90fc6e3d2a4399992
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188571"
---
# <a name="idebugport2"></a>IDebugPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim bir makinedeki hata ayıklama bağlantı noktasını temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Özel bir bağlantı noktası sağlayıcısı, bu arabirimi bir makinedeki hata ayıklama bağlantı noktasını göstermek için uygular.  
  
 Bağlantı noktası bağlantı noktası olaylarının gönderilmesini destekliyorsa, ayrıca <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) arabirimini sağlayan bir arabirimi desteklemek için arabirimi de uygulamalıdır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [Getport](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) veya [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) çağrıları, istenen bağlantı noktasını temsil eden bu arabirimi döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugPort2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Bağlantı noktası adını döndürür.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Bağlantı noktası tanımlayıcısını döndürür.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Bağlantı noktası (varsa) oluşturmak için kullanılan isteği döndürür.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Bu bağlantı noktası için bağlantı noktası tedarikçiyi döndürür.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|İşlemin tanımlayıcısı verilen işleme bir arabirim döndürür.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Bir bağlantı noktası üzerinde çalışan tüm işlemi numaralandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yerel bağlantı noktası, yerel makinede çalışan tüm işlemlere ve programlara erişim sağlar. Diğer bağlantı noktaları Windows CE tabanlı bir cihaza seri kablo bağlantısını veya DCOM olmayan bir bilgisayara ağ bağlantısını temsil edebilir. `IDebugPort2`Arabirim, bir bağlantı noktasının adını ve tanımlayıcısını bulmak, bağlantı noktasında çalışan tüm işlemlerin sayısını listelemek ve bağlantı noktasında işlem başlatma ve sonlandırma olanakları sağlamak için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
