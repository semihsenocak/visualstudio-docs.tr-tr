---
title: Başlatma tabanlı ek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09a6b39bef9ba6af098bf92d779a490e22492209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203155"
---
# <a name="launch-based-attachment"></a>Başlatma Tabanlı Ek
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir programa başlatma tabanlı ek otomatik. Programı barındıran işlem SDM tarafından başlatıldığında, başlatma tabanlı ek el ile ek yöntemine benzer bir yol izler. Bilgi için bkz. [programa ekleme](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Iliştirme Işlemi  
 Ana fark, aşağıdaki gibi, **iliştirme** çağrısını izleyen olayların sırasıdır:  
  
1. SDM 'ye bir **IDebugEngineCreateEvent2** Event nesnesi gönderin. Ayrıntılar için bkz. [olayları gönderme](../../extensibility/debugger/sending-events.md).  
  
2. `IDebugProgram2::GetProgramId` **Attach** yöntemine geçirilen **IDebugProgram2** arabirimindeki yöntemi çağırın.  
  
3. Yerel **IDebugProgram2** nesnesinin program tarafından da temsil etmek IÇIN oluşturulduğunu SDM 'ye bildirmek Için bir **IDebugProgramCreateEvent2** olay nesnesi gönderin.  
  
4. SDM 'yi Başlatan işlem için yeni bir iş parçacığının oluşturulduğunu bildirmek için bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gerekli olaylar gönderiliyor](../../extensibility/debugger/sending-the-required-events.md)   
 [Bir Programı Hataları Ayıklanacak Şekilde Etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
