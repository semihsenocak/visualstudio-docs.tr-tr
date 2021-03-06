---
title: Komut satırından performans verileri toplamak için profil oluşturma yöntemlerini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fe9e8d3dbd1e7395287cd7241f1e6145dffca7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145394"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Komut Satırından Performans Verileri Toplamak için Profil Oluşturma Yöntemlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Komut satırı araçları ve seçenekleri profil oluşturma araçları seçiminiz, profil oluşturduğunuz uygulamanın türü, kullanmak istediğiniz profil oluşturma yöntemi ve hedef uygulamanın yerel veya kod içinde yazılıp yazılmayacağı gibi faktörlere bağlıdır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Bu konu, komut satırı yordamsal konuları seçtiğiniz profil oluşturma yöntemine göre düzenler.  
  
## <a name="in-this-topic"></a>Bu konuda  
 [Performans istatistikleri toplamak için örnekleme yöntemini kullanma](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Ayrıntılı zamanlama verilerini toplamak için izleme yöntemini kullanma](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Bellek ayırma ve nesne yaşam süresi verilerini toplamak için .NET bellek yöntemlerini kullanma](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Kaynak çekişmesini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanma](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Bir profil oluşturma çalıştırmasına katman etkileşim verileri ekleme](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
## <a name="using-the-sampling-method-to-collect-performance-statistics"></a><a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Performans istatistikleri toplamak için örnekleme yöntemini kullanma  
 Profil Oluşturma Araçları örnekleme yöntemi, bir profil oluşturma çalıştırmasında belirtilen aralıklarda performans verilerini toplar. Örnekleme verileri, CPU 'ya dayalı performans sorunlarına yönelik öngörüler sağlayabilir ve bir uygulamanın performansını keşfetmeye başlamak için iyi bir yoldur.  
  
 Profil oluşturucuyu ve uygulamayı aynı anda başlatabilir veya profil oluşturucuyu uygulamanın çalışan bir örneğine iliştirebilirsiniz.  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Uygulama başlatma**|-   [Tek başına uygulamalar](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Çalışan bir işleme iliştirme**|-   [Tek başına uygulamalar .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Yerel tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [ASP.NET Web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Yerel hizmetler](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="using-the-instrumentation-method-to-collect-detailed-timing-data"></a><a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Ayrıntılı zamanlama verilerini toplamak için izleme yöntemini kullanma  
 Profil Oluşturma Araçları izleme yöntemi, performans bilgilerini kaydetmek için yazılım araştırmalarını içeren uygulama ikili dosyalarının kopyalarından performans verilerini toplar. İzleme verileri, her bir belgelenmiş işlevin başlangıcında ve sonunda ve belgelenmiş işlevden gelen diğer işlevlere yapılan her çağrıda toplanır. İzleme yöntemi, disk kullanımı gibi g/ç sorunları ile ilgili performans sorunlarını bulmak için yararlıdır.  
  
 İşaretlenmiş ikiliyi [VInstr.exe](../profiling/vsinstr.md) aracı ile oluşturursunuz. Profil oluşturucuyu başlattıktan sonra, hedef uygulamayı çalıştırdığınızda veriler otomatik olarak belgelenmiş ikili dosyalar üzerinden toplanır.  
  
 **Hedef uygulama türü**  
  
- [Tek başına bileşenleri .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [Yerel tek başına bileşenler](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [Statik olarak derlenen ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [Dinamik olarak derlenen ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [.NET Hizmetleri](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
- [Yerel hizmetler](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="using-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a><a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Bellek ayırma ve nesne yaşam süresi verilerini toplamak için .NET bellek yöntemlerini kullanma  
 Profil Oluşturma Araçları .NET bellek yöntemi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , bellek ayırma verilerini ve içindeki nesnelerin ömrü hakkında bilgileri toplamanıza olanak sağlar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Profil oluşturucuyu kullanarak hedef uygulamayı başlatabilirsiniz; profil oluşturucuyu uygulamanın çalışan bir örneğine ekleyebilirsiniz; ve ayrıntılı zamanlama bilgilerini bellek verileriyle birlikte toplamak için uygulamanın belgelenmiş sürümlerini oluşturabilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Uygulama başlatma**|-   [Tek başına .NET Framework uygulamalar](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Çalışan bir işleme iliştirme**|-   [Tek başına uygulamalar .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [ASP.NET Web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Araç modülleri**|-   [Tek başına bileşenleri .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Statik olarak derlenen ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Dinamik olarak derlenen ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="using-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a><a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Kaynak çekişmesini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanma  
 Profil Oluşturma Araçları eşzamanlılık yöntemi, çok iş parçacıklı uygulamalardan kaynak çekişmesini ve iş parçacığını toplamanıza ve etkinlik verilerini işlemenize olanak sağlar.  
  
 Profil oluşturucuyu kullanarak uygulamayı başlatabilir veya profil oluşturucuyu bir uygulamanın çalışan örneğine iliştirebilirsiniz.  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Uygulama başlatma**|-   [Tek başına .NET Framework uygulaması](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Tek başına yerel uygulama](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Çalışan bir işleme iliştirme**|-   [Tek başına uygulama .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Yerel tek başına uygulama](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)<br />-   [ASP.NET Web uygulaması](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET hizmeti](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Yerel hizmet](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="adding-tier-interaction-data-to-a-profiling-run"></a><a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Bir profil oluşturma çalıştırmasına katman etkileşim verileri ekleme  
 Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
