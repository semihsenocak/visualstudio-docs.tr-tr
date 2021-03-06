---
title: Profil oluşturma komut satırı-rapor oluşturma
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5eb0f1fa0f9bbe760b1ea89074d02044cf26ab7d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808831"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Komut satırından profil Oluşturucu raporları oluşturma
**VSPerfReport** komut satırı aracı oluşturmanıza olanak sağlar. *XML* veya virgülle ayrılmış değer (.* CSV*) profil oluşturma verilerinden raporlar (.* VSP*) dosyaları. VSPerfReport rapor türleri, arabiriminin tablo tabanlı görünümlerini yakından eşleştirin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Raporu yalnızca kendi kodunuzu göstermek ve profil oluşturma veri dosyasının yalnızca bir kesimini göstermek için filtreleyebilirsiniz. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

 Ayrıca, içinde semboller ekleyerek profil oluşturma veri dosyalarınızı daha kolay bir şekilde paylaşabilirsiniz. *VSP* dosyaları ve önceden analiz edilmiş rapor oluşturma (.* vsps*) dosyaları daha küçük ve daha hızlı açılır.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Temel bir rapor oluşturun.** VSPerfReport rapor türlerinin tümünü veya bir alt kümesini oluşturun.|-   [Temel raporlar oluşturma](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**İki profil oluşturma veri dosyasını karşılaştırın.** Performans verilerini iki profil oluşturma veri dosyasında karşılaştıran bir "fark" raporu oluşturun.|-   [Nasıl yapılır: komut isteminden profil oluşturucu karşılaştırma raporu oluşturma](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Windows için çağrı izleme ve olay Izleme (ETW) verilerini görüntüleyin.** Her giriş için zamanlama bilgilerini ve uygulamanızın işlevlerine yönelik her bir çıkış noktasını ve işleviniz tarafından diğer işlevlere yapılan her çağrıyı listeleyen bir çağrı izleme raporu oluşturun. Veya profil oluşturma çalıştırmasında toplanan tüm ETW olaylarının ayrıntılı bir listesini oluşturun.|-   [Nasıl yapılır: çağrı izleme raporu oluşturma](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Bir raporu filtreleyin.** Bir raporu yalnızca kodunuzdaki işlevlerle veya profil oluşturma veri dosyasında belirli bir zamana sınırlayın.|-   [Nasıl yapılır: komut satırından raporları filtreleme](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Taşınabilir profil oluşturma veri dosyaları oluşturun.** Profil oluşturma verilerinin paylaşılmasını daha kolay hale getirmek için, bir profil oluşturma çalıştırmasının sembollerini öğesine ekleyebilirsiniz. *VSP* dosyası. Ayrıca, önceden çözümlenmiş bir profil oluşturma verileri (.* vsps*) dosyası daha küçük ve daha hızlı açılır.|-   [Taşınabilir profil oluşturma veri dosyaları oluşturma](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
