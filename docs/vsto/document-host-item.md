---
title: Belge konak öğesi
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ebea0c3a09d08741523deddce94def170d844202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253704"
---
# <a name="document-host-item"></a>Belge konak öğesi
  <xref:Microsoft.Office.Tools.Word.Document>Konak öğesi, <xref:Microsoft.Office.Interop.Word.Document> Word için birincil birlikte çalışma derlemesinden türü genişleten bir türdür. <xref:Microsoft.Office.Tools.Word.Document>Konak öğesi, aynı özellikleri, yöntemleri ve olayları bir nesne olarak sağlar <xref:Microsoft.Office.Interop.Word.Document> , ancak ayrıca ek olaylar sunar ve konak denetimleri ve Windows Forms denetimleri için bir kapsayıcı görevi görür.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Belge düzeyi projelerinde, <xref:Microsoft.Office.Tools.Word.Document> projenizdeki belgeyi temsil eden bir varsayılan konak öğesi vardır. VSTO eklenti projelerinde, <xref:Microsoft.Office.Tools.Word.Document> çalışma zamanında konak öğeleri oluşturabilirsiniz.

## <a name="understand-the-document-host-item-in-document-level-projects"></a>Belge düzeyi projelerdeki belge konak öğesini anlayın
 Projenizdeki belgeye erişmek için `ThisDocument` sınıfını kullanın. Belge düzeyinde bir proje oluşturduğunuzda, Visual Studio `ThisDocument` Word ile özelleştirme kodunuz arasında iletişim bağlantısı olarak kullanılacak sınıfı oluşturur. `ThisDocument`Sınıfı, <xref:Microsoft.Office.Tools.Word.Document> özelleştirme sırasında kod çalıştırma veya kapatma gibi temel görevleri gerçekleştirmek için konak öğesinin üyelerine erişmenizi sağlar. Belgeye denetim eklemek için sınıfını da kullanabilirsiniz. Farklı denetim kümelerini birleştirerek ve kod yazarken, denetimleri verilere bağlayabilir, kullanıcıdan bilgi toplayabilir ve kullanıcı eylemlerine yanıt verebilirsiniz. Daha fazla bilgi için bkz. [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

 `ThisDocument`Sınıfı, projenizde kod yazmaya başlayabilmeniz için bir konum sağlar. Sınıfı, Word için birincil birlikte çalışma derlemesindeki nesne olarak aynı özellikleri, yöntemleri ve olayları sağladığından, <xref:Microsoft.Office.Interop.Word.Document> `ThisDocument` Word nesne modeline erişmek için de kullanabilirsiniz. Daha fazla bilgi için bkz. [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Belge düzeyi projelerdeki belge konak öğesinin sınırlamaları
 Belge düzeyindeki bir proje yalnızca bir <xref:Microsoft.Office.Tools.Word.Document> konak öğesi (yani, `ThisDocument` sınıfı) içerebilir. <xref:Microsoft.Office.Tools.Word.Document>Tasarım zamanında projenize yeni konak öğeleri ekleyemez ve <xref:Microsoft.Office.Tools.Word.Document> çalışma zamanında belge düzeyi özelleştirmesindeki yeni konak öğeleri oluşturamazsınız.

 Çalışma zamanında yeni bir Word belgesi oluşturursanız, bu, türü olacaktır <xref:Microsoft.Office.Interop.Word.Document> . Konak öğesi olmadığından, hiçbir konak denetimi veya Windows Forms denetimi içeremez. Çalışma zamanında belge oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md).

## <a name="understand-document-host-items-in-application-level-projects"></a>Uygulama düzeyi projelerindeki belge konak öğelerini anlama
 VSTO eklenti projelerinde, <xref:Microsoft.Office.Tools.Word.Document> Word 'de açık olan herhangi bir belge için çalışma zamanında bir konak öğesi oluşturabilirsiniz. <xref:Microsoft.Office.Tools.Word.Document>İlişkili belgeye denetim eklemek veya nesnelerde kullanılamayan olayları işlemek için konak öğesini kullanabilirsiniz <xref:Microsoft.Office.Interop.Word.Document> .

 Bir <xref:Microsoft.Office.Tools.Word.Document> konak öğesi oluşturmak için `GetVstoObject` yöntemini kullanın. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
