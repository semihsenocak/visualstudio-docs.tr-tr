---
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192910"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, ağdaki bir makinedeki bir sunucudan bilgi göstermek ve almak için kullanılır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Visual Studio, bir sunucuyu temsil etmek için bu arabirimi uygular. Visual Studio 'nun her örneği, bu arabirimin bir örneğini oluşturur.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Özel bir bağlantı noktası sağlayıcısı bu arabirimi bir [olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)çağrısıyla alır.  
  
 Bir hata ayıklama altyapısı, bu arabirimi bir [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) çağrısıyla dolaylı olarak alabilir ( [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), öğesinden türetilmiş bir arabirim `IDebugCoreServer2` ).  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugCoreServer2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Bir makinenin adını ve özniteliklerini alır.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Makinenin adını alır.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Bir makinede bulunan bir bağlantı noktası sağlayıcısı alır.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Bir makinede zaten bulunan bir bağlantı noktasını alır.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Bir makinedeki tüm bağlantı noktaları için bir Numaralandırıcı oluşturur.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Bir makinedeki tüm bağlantı noktası tedarikçileri için bir Numaralandırıcı oluşturur.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Makine için makine yardımcı programlarını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, ağdaki makinelerde çalışan işlemlere gitmek için Visual Studio tarafından da kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
