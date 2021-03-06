---
title: İleti numaralandırıcısı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702503"
---
# <a name="message-enumerator"></a>İleti numaralandırıcısı
Aşağıdaki bayraklar, `TEXTOUTPROC` IDE 'Nin [SccOpenProject](../extensibility/sccopenproject-function.md) çağırdığında sağladığı bir geri çağırma işlevi olan işlevi için kullanılır (geri çağırma işlevi hakkında ayrıntılar Için bkz. [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) ).

 IDE 'nin işlemi iptal etmek isteniyorsa, iptal iletilerinden birini alabilir. Bu durumda, kaynak denetimi eklentisi `SCC_MSG_STARTCANCEL` IDE 'Nin **iptal** düğmesini görüntülemesini istemek için kullanır. Bundan sonra, herhangi bir normal ileti kümesi gönderilebilir. Bunlardan herhangi biri dönerse `SCC_MSG_RTN_CANCEL` , eklenti işlemden çıkar ve döndürür. Eklenti Ayrıca, `SCC_MSG_DOCANCEL` kullanıcının işlemi iptal etmiş olup olmadığını belirlemede düzenli aralıklarla yoklar. Tüm işlemler tamamlandığında veya Kullanıcı iptal edildiyse, eklenti gönderilir `SCC_MSG_STOPCANCEL` . `SCC_MSG_INFO`, SCC_MSG_WARNING ve SCC_MSG_ERROR türleri, iletilerin kaydırılan listesinde görüntülenen iletiler için kullanılır. `SCC_MSG_STATUS` , metnin bir durum çubuğunda veya geçici görüntüleme alanında gösterilmesi gerektiğini belirten özel bir türdür. Listede kalıcı olarak kalmaz.

## <a name="syntax"></a>Syntax

```
enum { 
   SCC_MSG_RTN_CANCEL = -1, 
   SCC_MSG_RTN_OK = 0, 
   SCC_MSG_INFO = 1 
   SCC_MSG_WARNING, 
   SCC_MSG_ERROR, 
   SCC_MSG_STATUS, 
   SCC_MSG_DOCANCEL, 
   SCC_MSG_STARTCANCEL, 
   SCC_MSG_STOPCANCEL 
};
```

## <a name="members"></a>Üyeler
 SCC_MSG_RTN_CANCEL iptali göstermek için geri aramadan geri dönün.

 SCC_MSG_RTN_OK devam etmek için geri aramadan geri dönün.

 SCC_MSG_INFO Ileti bilgilendirme amaçlıdır.

 SCC_MSG_WARNING Ileti bir uyarıdır.

 SCC_MSG_ERROR Ileti bir hatadır.

 SCC_MSG_STATUS Ileti durum çubuğuna yöneliktir.

 SCC_MSG_DOCANCEL metin yok; IDE, `SCC_MSG_RTN_OK` veya döndürür `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL bir iptal döngüsü başlatır.

 SCC_MSG_STOPCANCEL iptal döngüsünü durduruyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
