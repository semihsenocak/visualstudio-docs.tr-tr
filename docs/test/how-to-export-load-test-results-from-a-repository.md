---
title: Yük Test Sonuçları dışarı aktar
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9b20915d5c320ff8db4da849d20267355c26590
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287759"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Nasıl yapılır: bir depodan yük testi sonuçlarını dışarı aktarma

Bir yük testi çalıştırdığınızda, çalıştırma sırasında toplanan bilgiler Load Test Sonuçları deposunda depolanır. Load Test Sonuçları Deposu, performans sayacı verilerini ve hatalar hakkındaki bilgileri içerir. Daha fazla bilgi için bkz. [yük test sonuçları deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Yük testi sonuçlarını, **yük test sonuçları aç ve Yönet** iletişim kutusunu kullanarak Yük Testi Düzenleyicisi yönetebilirsiniz. Yük testi sonuçlarını açabilir, içeri aktarabilir, dışarı aktarabilir ve kaldırabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Bir depodan sonuçları dışarı aktarmak için

1. Bir Web performans ve yük testi projesinden bir yük testi açın.

2. Katıştırılmış araç çubuğunda, **sonuçları aç ve Yönet**' i seçin.

     **Yük test sonuçları aç ve Yönet** iletişim kutusu görüntülenir.

3. **Yük testi sonuçlarını bulmak için bir denetleyici adı girin**' de bir denetleyici seçin. **\<Local - No controller>** Yerel olarak depolanan sonuçlara erişmek için seçin.

4. **Aşağıdaki yük testi için sonuçları göster**bölümünde, sonuçlarını görüntülemek istediğiniz yük testini seçin. **\<Show results for all tests>** Tüm testlerin tüm sonuçlarını görmek için seçin.

     Yük testi sonuçları kullanılabiliyorsa, bunlar **Yük testi sonuçları** listesinde görünürler. Sütunlar **saat**, **süre**, **Kullanıcı**, **sonuç**, **Test**ve **Açıklama**. **Test, testin adını içerir ve** **Açıklama** , test çalıştırılmadan önce eklenen isteğe bağlı açıklamayı içerir. **Açıklama** sütunu, bu test sonucu Için **analiz açıklamalarında** girilen kısa açıklamaları görüntüler.

5. **Yük testi sonuçları** listesinde bir sonuç seçin. Birden fazla sonuç seçmek ve bunları tek bir dosyaya dışarı aktarmak için **SHIFT** tuşunu, **CTRL** tuşunu veya her ikisini de kullanabilirsiniz.

6. **Dışarı aktar**' ı seçin.

     **Yük test sonuçları dışarı aktar** iletişim kutusu görünür.

7. **Dosya adı** kutusuna bir ad yazın ve ardından **Kaydet**' i seçin.

     Sonuçlar bir arşiv dosyasına aktarılmalıdır.

    > [!NOTE]
    > **Yük test sonuçları aç ve Yönet** iletişim kutusu, Sonuçlar görüntülendikten sonra açık kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük Test Sonuçları deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Nasıl yapılır: bir depodan yük testi sonuçlarını silme](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: yük testi sonuçlarını depoya aktarma](../test/how-to-import-load-test-results-into-a-repository.md)
