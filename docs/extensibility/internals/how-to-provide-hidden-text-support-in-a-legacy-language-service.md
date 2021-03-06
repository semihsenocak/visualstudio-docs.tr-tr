---
title: Eski dil hizmetinde gizli metin desteği sağlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707924"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Nasıl yapılır: eski dil hizmetinde gizli metin desteği sağlama
Ana hat bölgelerine ek olarak gizli metin alanları da oluşturabilirsiniz. Gizli metin bölgeleri, istemci denetimli veya düzenleyiciden denetlenebilir ve bir metin bölgesini tamamen gizlemek için kullanılır. Düzenleyici, gizli bir bölgeyi yatay çizgiler olarak görüntüler. Bunun bir örneği, HTML düzenleyicisinde **yalnızca betik** görünümüdür.

## <a name="to-implement-a-hidden-text-region"></a>Gizli metin bölgesi uygulamak için

1. `QueryService`İçin çağrısı <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Bu, için bir işaretçi döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>Belirli bir metin arabelleği için bir işaretçiye geçerek çağrı yapın. Bu, bir gizli metin oturumunun arabellekte zaten mevcut olup olmadığını belirler.

3. Zaten varsa, bir tane oluşturmanız gerekmez ve var olan nesneye bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> döndürülür. Gizli metin bölgelerini numaralandırmak ve oluşturmak için bu işaretçiyi kullanın. Aksi takdirde, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> arabellek için gizli metin oturumu oluşturma çağrısı yapın.

     Nesneye yönelik bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> döndürülür.

    > [!NOTE]
    > `CreateHiddenTextSession`Öğesini çağırdığınızda gizli bir metin istemcisi (yani, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ) belirtebilirsiniz. Gizli metin istemcisi, gizli metin veya anahat oluşturma kullanıcı tarafından genişletildiğinde veya daraltıldığında size bildirir.

4. Tek seferde bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> veya daha fazla yeni ana hat bölgesi eklemek için çağırın ve `reHidReg` () parametresinde aşağıdaki bilgileri belirtin <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> :

    1. Bir `hrtConcealed` `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ana hat bölgesi yerine gizli bölge oluşturduğunuz belirten yapının üyesinde bir değer belirtin.

        > [!NOTE]
        > Gizli olmayan bölgeler gizliyse, düzenleyici, otomatik olarak gizli bölgelerin çevresindeki satırları gösterir.

    2. Bölgenin, yapının üyelerinde istemci denetimli veya düzenleyiciyle kontrol edilip edilmeyeceğini belirtin `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> . Akıllı anahat oluşturma uygulamanız, düzenleyici ve istemci denetimli ana hat ve gizli metin bölgelerinin bir karışımını içerebilir.
