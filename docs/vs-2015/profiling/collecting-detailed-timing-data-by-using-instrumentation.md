---
title: Izleme kullanarak ayrıntılı zamanlama verileri toplama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c129ddf016e02fe6c29d5cf63fe57ba07fbd4e95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176652"
---
# <a name="collecting-detailed-timing-data-by-using-instrumentation"></a>İzleme Kullanarak Ayrıntılı Zamanlama Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Profil oluşturma araçları izleme yöntemi, profil oluşturma kodunu bir modülün kopyasına çıkarır. Kod, bir profil oluşturma çalışması sırasında modüldeki işlevlerin her bir girdisini, çıkış ve işlev çağrısını kaydeder. İzleme yöntemi, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerinde etkisini anlamak için yararlıdır.  
  
 Aşağıdaki yordamlardan birini kullanarak izleme yöntemini belirtebilirsiniz:  
  
- Profil oluşturma sihirbazının ilk sayfasında, **izleme**' yi seçin.  
  
- **Performans Gezgini** araç çubuğunda, **Yöntem** listesinde, **izleme**' yi tıklatın.  
  
- Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında, **izleme**' yi seçin.  
  
## <a name="common-tasks"></a>Ortak Görevler  
 Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:  
  
- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
  Aşağıdaki tabloda yer alan görevler, izleme yöntemini kullanarak profil oluştururken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Genel** sayfasında, .net bellek ayırma ve ömür verileri ekleyin ve oluşturulan profil oluşturma verileri (. vsp) dosyası için adlandırma ayrıntılarını belirtin.|-   [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Başlatma** sayfasında, çözümünüzde birden çok. exe projeniz varsa, başlatılacak uygulamayı ve başlangıç sıralarını belirtin.|-   [Nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)|  
|**Ikili dosyalar** sayfasında, modüllerin belgelenmiş kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikililer bir yedekleme klasörüne taşınır.|-   [Nasıl yapılır: Işaretlenmiş Ikililerin konumunu değiştirme](../profiling/how-to-relocate-instrumented-binaries.md)|  
|**Katman etkileşimi** sayfasında, profil oluşturma çalıştırmasına ADO.NET çağrı verileri ekleyin.|-   [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md)|  
|**İzleme** sayfasında, profil oluşturma ek yükünü azaltmak, ASP.NET Web sayfalarındaki JavaScript kodu profilini oluşturmak ve izleme işleminden önce ve sonra bir komut isteminde çalışacak komutları belirtmek için, yönetim sayfası ' ndan küçük işlevleri hariç tutun.|-   [Nasıl yapılır: Izleme 'den kısa Işlevler hariç tutma veya dahil etme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Nasıl yapılır: ön ve araç sonrası komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|**CPU sayaçları** sayfasında, profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|-   [Nasıl yapılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)|  
|**Windows olayları** sayfasında, örnekleme verileriyle toplanacak bir veya daha fazla Windows Için olay Izleme (ETW) olayları seçin.|-   [Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|-   [Nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)|  
|**Gelişmiş** sayfasında, belirli işlevleri dahil etme veya hariç tutma seçenekleri gibi VSInstr araçları programına geçirmek istediğiniz ek seçenekleri belirtin.|-   [Nasıl yapılır: ek Izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Nasıl yapılır: belirli Işlevlerle Izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
