---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82caf285d73ab1b9b49b9546012bbb45f25c3320
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153428"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kullanıcının tümleşik geliştirme ortamından (IDE) girebileceği bir dizeyi temel alan veri kesme noktaları ayarlamak için kullanılır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>Üyeler  
 `pThread`  
 Kesme noktasının gerçekleştiği iş parçacığını temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.  
  
 `bstrContext`  
 Bir çağrı yığınında görülen, genellikle bir yöntem veya işlev adı içindeki kesme noktasının bağlamı.  
  
 `bstrDataExpr`  
 Kullanıcının kesme noktasını ayarlamak için girdiği veri dizesi.  
  
 `dwNumElements`  
 Kesme noktasının gerçekleştiği veri dizesindeki öğe sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, bir birleşimin parçası olarak [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapısının bir üyesidir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
