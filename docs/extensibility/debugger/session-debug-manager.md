---
title: Oturum hata ayıklama Yöneticisi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712881"
---
# <a name="session-debug-manager"></a>Oturum hata ayıklama Yöneticisi
Oturum hata ayıklama Yöneticisi (SDM), herhangi bir sayıda makinede birden çok işlemde bulunan her sayıda programda hata ayıklamış herhangi bir hata ayıklama altyapısını (DE) yönetir. Bir hata ayıklama altyapısı Çoğullayıcı olmanın yanı sıra, SDM, IDE 'ye hata ayıklama oturumunun Birleşik bir görünümünü sağlar.

## <a name="session-debug-manager-operation"></a>Oturum hata ayıklama Yöneticisi işlemi
 Oturum hata ayıklama Yöneticisi (SDM), DE yönetir. Aynı anda bir makinede çalışan birden fazla hata ayıklama altyapısı olabilir. DEs çoğullanır olması için, SDM DEs 'ten bir dizi arabirimi sarmalamalı ve bunları tek bir arabirim olarak IDE 'ye gösterir.

 Performansı artırmak için bazı arabirimler çoğullanmamış. Bunun yerine, doğrudan DE ile kullanılırlar ve bu arabirimlerin çağrıları SDM 'ye gitmez. Örneğin, bellek, kod ve belge bağlamlarında kullanılan arabirimler, belirli bir aynı hata ayıkladığı belirli bir programdaki belirli bir yönerge, bellek veya belgeye başvurduğundan çoğullanmamış. Bu iletişim düzeyine dahil olması gereken başka bir DE yok.

 Bu, tüm bağlamlarda doğru değildir. İfade değerlendirme bağlamı arabirimine yapılan çağrılar SDM aracılığıyla gider. İfade değerlendirmesi sırasında, SDM, bu ifade değerlendirildiği zaman, aynı iş parçacığında çalışmakta olabilecek programlarda hata ayıklama [yapan, aynı](../../extensibility/debugger/reference/idebugexpression2.md) işlemde çalışan birden fazla des içerebilir.

 SDM genellikle bir yetkilendirme mekanizması işlevi görür, ancak bir yayın mekanizması işlevi görebilir. Örneğin, ifade değerlendirmesi sırasında, SDM, belirli bir iş parçacığında kod çalıştırabilecekleri tüm DEs 'e bildirimde bulunan bir yayın mekanizması olarak görev yapar. Benzer şekilde, SDM bir durdurma olayı aldığında, çalışmayı durdurması gereken programlara yayınlar. Bir adım çağrıldığında, SDM çalışmaya devam edebilecekleri programlara yayınlar. Kesme noktaları aynı zamanda her da ' a yayınlanır.

 SDM geçerli program, iş parçacığı veya yığın çerçevesini izlemez. İşlem, program ve iş parçacığı bilgileri, belirli hata ayıklama olaylarıyla birlikte SDM 'ye gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)
- [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)
