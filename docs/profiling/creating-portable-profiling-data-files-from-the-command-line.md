---
title: Profil oluşturma komut satırı-taşınabilir veri dosyaları oluşturma
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0584cd2a476a7552beec483dd72ad1e957800ec
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808844"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Komut satırından taşınabilir profil oluşturma veri dosyaları oluşturma
Profil oluşturma verilerinin paylaşılmasını daha kolay hale getirmek için, [VSPerfReport](../profiling/vsperfreport.md) komut satırı aracını kullanarak bir profil oluşturma çalıştırmasının sembollerini öğesine ekleyebilirsiniz. *VSP* dosyası.

 Ayrıca, önceden çözümlenmiş bir profil oluşturma verileri (.* vsps*), daha küçük olan ve IDE 'de daha hızlı yüklenmeye yönelik bir dosyadır.

> [!NOTE]
> Simgenin (.* pdb*) dosyaları **VSPerfReport**için kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: sembol dosyası konumlarını komut satırından belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> **VSReport**yolu hakkında daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> İçindeki profil oluşturma verileri. *vsps* dosyası filtrelenemez.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Profil oluşturma için sembolleri profil oluşturma verilerine eklemek için (.* VSP*) dosyası

- Komut istemi penceresinde aşağıdaki komutu yazın:

   \<Path><strong>VSPerfReport \<</strong> VSP dosyası> **/packsymbols**

   Varsayılan olarak,. *vsps* dosyası, öğesinin temel adıyla adlandırılır. *VSP* dosyası. **Output** seçeneğini kullanarak alternatif bir ad belirtebilirsiniz.

### <a name="to-create-a-summary-profiling-data-file"></a>Özet profil oluşturma veri dosyası oluşturmak için

- Komut istemi penceresinde aşağıdaki komutu yazın:

   \<Path><strong>VSPerfReport \<</strong> VSP dosyası> **/summaryfile** [**/output:** \<File Name> ]

   Varsayılan olarak,. *vsps* dosyası, öğesinin temel adıyla adlandırılır. *VSP* dosyası. **Output** seçeneğini kullanarak alternatif bir ad belirtebilirsiniz.
