---
title: IntelliTrace tek başına toplayıcıyı kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
caps.latest.revision: 111
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81eedeeb9a1b2470e87f0d865996ad3e456723fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520555"
---
# <a name="using-the-intellitrace-stand-alone-collector"></a>IntelliTrace tek başına toplayıcıyı kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**IntelliTrace tek başına toplayıcısı** , Visual Studio 'yu hedef makineye yüklemeden ve hedef sistemin ortamını değiştirmeden, üretim sunucularında veya diğer ortamlarda uygulamalarınız için IntelliTrace Tanılama verileri toplamanıza olanak tanır. IntelliTrace tek başına toplayıcısı Web, SharePoint, WPF ve Windows Forms uygulamalarda kullanılabilir. Veri toplamayı tamamladıktan sonra kaldırmak için toplayıcıyı silmeniz yeterlidir.

 IntelliTrace 'i çalışırken izleyin: [hata ayıklama için üretimde IntelliTrace verilerini toplama ve analiz etme (Channel 9 Videosu)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)

> [!NOTE]
> Ayrıca, **izleme** modundaki **Microsoft Monitoring Agent** kullanarak uzak makinelerde çalışan Web ve SharePoint uygulamaları için aynı IntelliTrace verilerini toplayabilirsiniz.
>
> Aracıyı **izleyici** modunda çalıştırarak, IntelliTrace verilerinde performansla ilgili olayları toplayabilirsiniz. **İzleyici** modunun, **Izleme** modundan veya **IntelliTrace tek başına toplayıcısından**daha az performans etkisi vardır. Microsoft Monitoring Agent, yüklendiğinde hedef sistemin ortamını değiştirir. Bkz. [Microsoft Monitoring Agent kullanımı](../debugger/using-the-microsoft-monitoring-agent.md).

 **Gereksinimler**

- .NET Framework 3,5, 4 veya 4,5

- Geliştirme bilgisayarındaki veya başka bir bilgisayardaki. iTrace dosyalarını açmak için Visual Studio Enterprise (profesyonel veya Community Edition değil)

  > [!NOTE]
  > Sembol (. pdb) dosyalarınızı kaydettiğinizden emin olun. IntelliTrace ile hata ayıklamak ve kodda adım adım ilerlemek için, eşleşen kaynak dosyaları ve sembol dosyalarınız olmalıdır. Bkz. [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

  **SSS**

- [Toplayıcıyla hangi uygulamalar çalışıyor?](#WhatApps)

- [Nasıl kullanmaya başlayabilirim?](#GetStarted)

- [Uygulamamı yavaşlatmadan en çok veriyi nasıl alabilirim?](#Minimizing)

- [IntelliTrace verilerini başka bir şekilde alabilirim?](#WhereElse)

## <a name="what-apps-work-with-the-collector"></a><a name="WhatApps"></a> Toplayıcıyla hangi uygulamalar çalışıyor?

- Internet Information Services (IIS) sürüm 7,0, 7,5 ve 8,0 üzerinde barındırılan Web Apps ASP.NET

- SharePoint 2010 ve SharePoint 2013 uygulamaları

- Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar.

## <a name="how-do-i-get-started"></a><a name="GetStarted"></a> Nasıl yaparım? başlamak istiyor musunuz?

1. [Toplayıcıyı yükler](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [Toplayıcı dizini için izinleri ayarlama](#ConfigurePermissionsRunningCollector)

3. [Web uygulamaları veya SharePoint uygulamaları için veri toplamak üzere IntelliTrace PowerShell cmdlet 'lerini yükler](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [. İTrace dosya dizini için izinleri ayarlama](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [Bir Web uygulamasından veya SharePoint uygulamasından veri topla](#BKMK_Collect_Data_from_IIS_Application_Pools)

     -veya-

     [Yönetilen bir uygulamadan veri toplama](#BKMK_Collect_Data_from_Executables)

6. [. İTrace dosyasını Visual Studio Enterprise açın](#BKMK_View_IntelliTrace_Log_Files)

## <a name="install-the-collector"></a><a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Toplayıcıyı yükler

1. Uygulamanızın sunucusunda, toplayıcı dizinini oluşturun, örneğin: **C:\IntelliTraceCollector**

2. Microsoft Indirme merkezi 'nden veya Visual Studio 2103 güncelleştirme 3 yükleme klasöründen toplayıcıya ulaşın. [Visual Studio için IntelliTrace Collector 2013 güncelleştirme 4](https://www.microsoft.com/download/details.aspx?id=44909)::

   - **Microsoft Indirme merkezi**:

     1. **IntelliTraceCollector.exe**' nın yanındaki **İndir**' i seçin.

     2. IntelliTraceCollector.exe, toplayıcı dizinine kaydedin, örneğin: **C:\IntelliTraceCollector**

     3. IntelliTraceCollector.exe çalıştırın. Bu, IntelliTraceCollection.cab dosyasını ayıklar.

        \- veya

   - **Visual Studio yükleme klasörü**:

     1. Aşağıdaki klasörden IntelliTraceCollection.cab Kopyala:

          **.. \Microsoft Visual Studio 12.0 \ Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. IntelliTraceCollection.cab toplayıcı dizinine yerleştirin, örneğin: **C:\IntelliTraceCollector**

3. IntelliTraceCollection.cab Genişlet:

   1. Uygulamanızın sunucusunda, yönetici olarak bir komut istemi penceresi açın.

   2. Toplayıcı dizinine gidin, örneğin: **C:\IntelliTraceCollector**

   3. IntelliTraceCollection.cab genişletmek için sonundaki nokta (**.**) da dahil olmak üzere **Expand** komutunu kullanın:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > Nokta (**.**), yerelleştirilmiş koleksiyon planları içeren alt klasörleri korur.

## <a name="set-up-permissions-for-the-collector-directory"></a><a name="ConfigurePermissionsRunningCollector"></a> Toplayıcı dizini için izinleri ayarlama

1. Uygulamanızın sunucusunda, yönetici olarak bir komut istemi penceresi açın.

2. Sunucu yöneticisine toplayıcı dizinine tam izinler vermek için Windows **ıccacls** komutunu kullanın. Örneğin:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID>* `":F`

3. Bir Web uygulaması veya SharePoint uygulaması için veri toplamak için:

    1. IntelliTrace PowerShell cmdlet 'lerini çalıştıracak kişiye Toplayıcı dizini için tam izinleri verin.

         Örneğin:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2. Web uygulaması veya SharePoint uygulaması için uygulama havuzuna Toplayıcı dizini için okuma ve yürütme izinleri verin.

         Örneğin:

        - **DefaultAppPool** uygulama havuzundaki bir Web uygulaması için:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - **SharePoint-80** uygulama havuzundaki bir SharePoint uygulaması için:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="install-intellitrace-powershell-cmdlets-to-collect-data-for-web-apps-or-sharepoint-applications"></a><a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> Web uygulamaları veya SharePoint uygulamaları için veri toplamak üzere IntelliTrace PowerShell cmdlet 'lerini yükler

1. Uygulamanızın sunucusunda, PowerShell 'in etkinleştirildiğinden emin olun. Windows Server 'ın çoğu sürümünde, bu özelliği **Sunucu Yöneticisi** yönetim aracına ekleyebilirsiniz.

     ![Sunucu Yöneticisi kullanarak PowerShell ekleme](../debugger/media/intellitrace-servermanager-addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. IntelliTrace PowerShell cmdlet 'lerini yükler.

    1. Yönetici olarak bir PowerShell komut penceresi açın.

        1. **Başlat**, **tüm programlar**, **Donatılar**, **Windows PowerShell**seçeneklerini belirleyin.

        2. Aşağıdaki adımlardan birini seçin:

            - 64 bit işletim sistemlerinde, **Windows PowerShell**için kısayol menüsünü açın. **Yönetici olarak çalıştır**' ı seçin.

            - 32 bit işletim sistemlerinde, **Windows PowerShell (x86)** için kısayol menüsünü açın. **Yönetici olarak çalıştır**' ı seçin.

    2. PowerShell komut penceresinde, **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**içeri aktarmak için **Import-Module** komutunu kullanın.

         Örneğin:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="set-up-permissions-for-the-itrace-file-directory"></a><a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> . İTrace dosya dizini için izinleri ayarlama

1. Uygulamanızın sunucusunda,. iTrace dosya dizinini oluşturun, örneğin: **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Uygulamanızı yavaşlatmayı önlemek için, yerel bir yüksek hızlı diskte çok etkin olmayan bir konum seçin.
   >   - . İTrace dosyalarını ve toplayıcı dosyalarını aynı yere koyabilirsiniz. Ancak, bir Web uygulamanız veya SharePoint uygulamanız varsa, bu yerde uygulamayı barındıran dizinin dışında olduğundan emin olun.
   >
   > [!IMPORTANT]
   > - . İTrace dosya dizinini yalnızca toplayıcıyla çalışması gereken kimliklerle sınırlayın. Bir. iTrace dosyası, kullanıcılar, veritabanları, diğer kaynak konumları ve bağlantı dizeleri gibi gizli bilgiler içerebilir, çünkü IntelliTrace Yöntem parametrelerine veya dönüş değeri olarak herhangi bir veriyi kaydedebilir.
   >   - . İTrace dosyalarını açabilen kişilerin hassas verileri görüntüleme yetkisine sahip olduğundan emin olun. . İTrace dosyalarını paylaşırken dikkatli olun. Diğer kişilerin erişimi olması gerekiyorsa, dosyaları güvenli bir paylaşılan konuma kopyalayın.

2. Bir Web uygulaması veya SharePoint uygulaması için, uygulama havuzuna. iTrace dosya dizinine tam izinleri verin. Windows **ıccacls** komutunu veya Windows Gezgini 'ni (veya dosya Gezgini) kullanabilirsiniz.

    Örneğin:

   - Windows **ıccacls** komutuyla izinleri ayarlamak için:

     - **DefaultAppPool** uygulama havuzundaki bir Web uygulaması için:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - **SharePoint-80** uygulama havuzundaki bir SharePoint uygulaması için:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       -veya-

   - Windows Gezgini (veya dosya Gezgini) ile izinleri ayarlamak için:

     1. . İTrace dosya dizini için **özellikleri** açın.

     2. **Güvenlik** sekmesinde **Düzenle**, **Ekle**' yi seçin.

     3. **Bu nesne türünü seç** kutusunda **yerleşik güvenlik sorumlularının** göründüğünden emin olun. Bu yoksa eklemek için **nesne türleri** ' ni seçin.

     4. **Bu konumdan** yerel bilgisayarınızın göründüğünden emin olun. Orada yoksa, değiştirmek için **konumlar** ' ı seçin.

     5. **Seçilecek nesne adlarını girin** kutusunda, Web uygulaması veya SharePoint uygulaması için uygulama havuzunu ekleyin.

     6. Adı çözümlemek için **adları denetle** ' yi seçin. **Tamam ' ı**seçin.

     7. Uygulama havuzunun **tam denetime**sahip olduğundan emin olun.

## <a name="collect-data-from-a-web-app-or-sharepoint-application"></a><a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> Bir Web uygulamasından veya SharePoint uygulamasından veri topla

1. Veri toplamaya başlamak için yönetici olarak bir PowerShell komut penceresi açın ve ardından şu komutu çalıştırın:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    > Bu komutu çalıştırdıktan sonra, veri toplamaya başlamak istediğinizi onaylamak için **Y** yazın.

     Örneğin, **SharePoint-80** uygulama havuzundaki bir SharePoint uygulamasından veri toplamak için:

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |Öğe|Açıklama|
    |-|-|
    |*ApplicationPool*|Uygulamanızın çalıştırıldığı uygulama havuzunun adı|
    |*PathToCollectionPlan*|Toplayıcı için ayarları yapılandıran bir. xml dosyası olan bir koleksiyon planının yolu.<br /><br /> Toplayıcıyla birlikte gelen bir plan belirtebilirsiniz. Aşağıdaki planlar Web uygulamaları ve SharePoint uygulamaları için çalışır:<br /><br /> -collection_plan.ASP.NET.default.xml<br />     Özel durumlar, veritabanı çağrıları ve Web sunucusu istekleri dahil olmak üzere yalnızca IntelliTrace olaylarını ve SharePoint olaylarını toplar.<br />-collection_plan.ASP.NET.trace.xml<br />     İşlev çağrılarını ve collection_plan.ASP.NET.default.xml tüm verileri toplar. Bu plan, ayrıntılı analiz için uygundur, ancak uygulamanızın collection_plan.ASP.NET.default.xml daha fazla yavaşlamasına neden olabilir.<br /><br /> Uygulamanızı yavaşlatmayı önlemek için, bu planları özelleştirin veya kendi planınızı oluşturun. Güvenlik için, tüm özel planları toplayıcı dosyalarıyla aynı güvenli konuma yerleştirin. Bkz. [IntelliTrace koleksiyon planları oluşturma ve özelleştirme](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) ve [uygulamamı yavaşlatmadan en çok veriyi edinme nasıl yaparım?.](#Minimizing) **Note:**  Varsayılan olarak,. iTrace dosyasının en büyük boyutu 100 MB 'tır. . İTrace dosyası bu sınıra ulaştığında, toplayıcı yeni girişler için alan oluşturmak üzere dosyanın en eski girdilerini siler. Bu sınırı değiştirmek için koleksiyon planının `MaximumLogFileSize` özniteliğini düzenleyin. <br /><br /> *Bu koleksiyon planlarının yerelleştirilmiş sürümlerini nereden bulabilirim?*<br /><br /> Yerelleştirilmiş planları toplayıcı alt klasörlerinde bulabilirsiniz.|
    |*Fullpathtoitkcefiledirectory*|. İTrace dosya dizininin tam yolu. **Güvenlik notno:**  Tam yolu belirtin, göreli bir yol değil.|

     Toplayıcı uygulama havuzuna iliştirir ve veri toplamaya başlar.

     *. İTrace dosyasını şu anda açabilir miyim?* Hayır, veri toplama sırasında dosya kilitlenir.

2. Sorunu yeniden oluşturun.

3. . İTrace dosyasının anlık görüntüsünü almak için şu sözdizimini kullanın:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4. Koleksiyon durumunu denetlemek için şu sözdizimini kullanın:

     `Get-IntelliTraceCollectionStatus`

5. Veri toplamayı durdurmak için şu sözdizimini kullanın:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    > Bu komutu çalıştırdıktan sonra, veri toplamayı durdurmak istediğinizi onaylamak için **Y** yazın. Aksi takdirde Toplayıcı veri toplamaya devam edebilir, iTrace dosyası kilitli kalır veya dosya yararlı bir veri içermeyebilir.

6. [. İTrace dosyasını Visual Studio Enterprise açın](#BKMK_View_IntelliTrace_Log_Files)

## <a name="collect-data-from-a-managed-app"></a><a name="BKMK_Collect_Data_from_Executables"></a> Yönetilen bir uygulamadan veri toplama

1. Uygulamanızı başlatmak ve verileri aynı anda toplamak için şu sözdizimini kullanın:

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Örneğin, **MyApp**adlı bir uygulamadan veri toplamak için:

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |Öğe|Açıklama|
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Toplayıcı yürütülebilir dosyasının tam yolu, IntelliTraceSC.exe|
    |*PathToCollectionPlan*|Toplayıcı için ayarları yapılandıran bir. xml dosyası olan bir koleksiyon planının yolu.<br /><br /> Toplayıcıyla birlikte gelen bir plan belirtebilirsiniz. Aşağıdaki planlar yönetilen uygulamalar için çalışır:<br /><br /> -collection_plan.ASP.NET.default.xml<br />     Yalnızca özel durumlar, veritabanı çağrıları ve Web sunucusu istekleri dahil olmak üzere IntelliTrace olaylarını toplar.<br />-collection_plan.ASP.NET.trace.xml<br />     İşlev çağrılarını ve collection_plan.ASP.NET.default.xml tüm verileri toplar. Bu plan, ayrıntılı analiz için uygundur, ancak uygulamanızın collection_plan.ASP.NET.default.xml daha fazla yavaşlamasına neden olabilir.<br /><br /> Uygulamanızı yavaşlatmayı önlemek için, bu planları özelleştirin veya kendi planınızı oluşturun. Güvenlik için, tüm özel planları toplayıcı dosyalarıyla aynı güvenli konuma yerleştirin. Bkz. [IntelliTrace koleksiyon planları oluşturma ve özelleştirme](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) ve [uygulamamı yavaşlatmadan en çok veriyi edinme nasıl yaparım?.](#Minimizing) **Note:**  Varsayılan olarak,. iTrace dosyasının en büyük boyutu 100 MB 'tır. . İTrace dosyası bu sınıra ulaştığında, toplayıcı yeni girişler için alan oluşturmak üzere dosyanın en eski girdilerini siler. Bu sınırı değiştirmek için koleksiyon planının `MaximumLogFileSize` özniteliğini düzenleyin. <br /><br /> *Bu koleksiyon planlarının yerelleştirilmiş sürümlerini nereden bulabilirim?*<br /><br /> Yerelleştirilmiş planları toplayıcı alt klasörlerinde bulabilirsiniz.|
    |*Fullpathtoitkcefiledirectoryanddosya adı*|. İTrace dosya dizininin tam yolu ve. iTrace dosya adı. **iTrace** uzantısı. **Güvenlik notno:**  Tam yolu belirtin, göreli bir yol değil.|
    |*PathToAppExecutableFileAndFileName*|Yönetilen uygulamanızın yolu ve dosya adı|

2. Uygulamadan çıkmadan veri toplamayı durdurun.

3. [. İTrace dosyasını Visual Studio Enterprise açın](#BKMK_View_IntelliTrace_Log_Files)

## <a name="open-the-itrace-file-in-visual-studio-enterprise"></a><a name="BKMK_View_IntelliTrace_Log_Files"></a> . İTrace dosyasını Visual Studio Enterprise açın

> [!NOTE]
> IntelliTrace ile hata ayıklamak ve kodda adım adım ilerlemek için, eşleşen kaynak dosyaları ve sembol dosyalarınız olmalıdır. Bkz. [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

1. . İTrace dosyasını taşıyın veya Visual Studio Enterprise (Professional veya Community Edition değil) olan bir bilgisayara kopyalayın.

2. Visual Studio dışında. iTrace dosyasına çift tıklayın veya dosyayı Visual Studio içinde açın.

     Visual Studio, **IntelliTrace Özet** sayfasını gösterir. Çoğu bölümde, olayları veya diğer öğeleri gözden geçirebilir, bir öğe seçebilir ve bir olayın gerçekleştiği noktada ve IntelliTrace ile hata ayıklamaya başlayabilirsiniz. Bkz. [kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md).

    > [!NOTE]
    > IntelliTrace ile hata ayıklamak ve kodda adım adım ilerlemek için, geliştirme makinenizde eşleşen kaynak dosyaları ve sembol dosyaları olmalıdır. Bkz. [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

## <a name="how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> Uygulamamı yavaşlatmadan en çok veriyi almak Nasıl yaparım??
 IntelliTrace pek çok veri toplayabilir, bu nedenle uygulamanızın performansı üzerindeki etki, IntelliTrace 'in topladığı verilere ve analiz yaptığı kodun türüne bağlıdır. Bkz. [Üretim sunucularında IntelliTrace toplamasını iyileştirme](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/).

 Uygulamanızı yavaşlatmadan en çok veriyi almanın bazı yolları aşağıda verilmiştir:

- Toplayıcı 'yı yalnızca bir sorun olduğunu düşündüğünüzde veya sorunu yeniden oluşturmak için çalıştırın.

   Koleksiyonu başlatın, sorunu yeniden oluşturun ve ardından toplamayı durdurun. Visual Studio Enterprise. iTrace dosyasını açın ve verileri inceleyin. Bkz [. Visual Studio Enterprise içindeki. iTrace dosyasını açma](#BKMK_View_IntelliTrace_Log_Files).

- Web uygulamaları ve SharePoint uygulamaları için toplayıcı, belirtilen uygulama havuzunu paylaşan her uygulama için verileri kaydeder. Bu, aynı uygulama havuzunu paylaşan herhangi bir uygulamayı yavaşlatabilir, ancak yalnızca bir koleksiyon planında tek bir uygulama için modüller belirleyebilseniz de olabilir.

   Toplayıcının diğer uygulamaları yavaşlatmasını engellemek için, her uygulamayı kendi uygulama havuzunda barındırın.

- IntelliTrace 'in veri topladığı toplama planındaki olayları gözden geçirin. İlgili olmayan veya ilgilendiğiniz olayları devre dışı bırakmak için koleksiyon planını düzenleyin.

   Bir olayı devre dışı bırakmak için `enabled` öğesi için özniteliğini şu `<DiagnosticEventSpecification>` şekilde ayarlayın `false` :

   `<DiagnosticEventSpecification enabled="false">`

   `enabled`Öznitelik yoksa, olay etkinleştirilir.

   *Bu, performansı nasıl geliştirir?*

  - Uygulamayla ilgili olmayan olayları devre dışı bırakarak, başlangıç süresini azaltabilirsiniz. Örneğin, Windows Iş akışı kullanmayan uygulamalar için Windows Workflow olaylarını devre dışı bırakın.

  - Kayıt defterine erişen ancak kayıt defteri ayarlarıyla ilgili sorunları göstermemekte olan uygulamalar için kayıt defteri olaylarını devre dışı bırakarak, başlatma ve çalışma zamanı performansını geliştirebilirsiniz.

- IntelliTrace 'in veri topladığı toplama planındaki modülleri gözden geçirin. Koleksiyon planını yalnızca ilgilendiğiniz modülleri içerecek şekilde düzenleyin:

  1. Toplama planını açın. Öğesini bulun `<ModuleList>` .

  2. İçinde `<ModuleList>` , `isExclusionList` özniteliğini olarak ayarlayın `false` .

  3. `<Name>`Her modülü aşağıdakilerden biriyle belirtmek için öğesini kullanın: dosya adı, adı bu dizeyi içeren herhangi bir modül dahil olmak üzere dize değeri veya ortak anahtar.

     Örneğin, Fabrikam Fiber Web uygulamasının yalnızca ana Web modülünden veri toplamak için şöyle bir liste oluşturun:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>

  ```

   Adı "Fabrikam" içeren tüm modüllerden veri toplamak için, şöyle bir liste oluşturun:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>

  ```

   Ortak anahtar belirteçlerini belirterek modüllerden veri toplamak için şöyle bir liste oluşturun:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>

  ```

   *Bu, performansı nasıl geliştirir?*

   Bu, uygulama başlatıldığında ve çalıştırıldığında IntelliTrace 'in topladığı Yöntem çağrısı bilgilerini ve diğer izleme verilerini azaltır. Bu veriler şunları yapmanızı sağlar:

  - Verileri topladıktan sonra kod adım adım.

  - İşlev çağrılarından geçirilen ve döndürülen değerleri inceleyin.

    *Bunun yerine modülleri dışlamayız?*

    Varsayılan olarak, koleksiyon planları özniteliğini olarak ayarlayarak modülleri hariç tutar `isExclusionList` `true` . Ancak, modüllerin dışlanması hala, listenin ölçütlerine uymayan ve üçüncü taraf veya açık kaynaklı modüller gibi sizi ilgilendiremeyen modüllerden veri toplamaya neden olabilir.

- *IntelliTrace 'in toplamayacak herhangi bir veri var mı?*

   Evet, performans etkisini azaltmak için, IntelliTrace veri toplamayı, metotlara geçirilen ve metotlardan döndürülen temel veri türleri değerleriyle kısıtlar ve metotlara geçirilen ve metotlardan döndürülen üst düzey nesnelerdeki alanlarda ilkel veri türleri değerleri ile kısıtlar.

   Örneğin, bir `AlterEmployee` tamsayı ve bir nesne kabul eden bir yöntem imzasına sahip olduğunuzu varsayalım `id` `Employee` `oldemployee` :

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   `Employee`Tür şu özniteliklere sahiptir: `Id` , `Name` ve `HomeAddress` . Ve türü arasında bir ilişki ilişkisi var `Employee` `Address` .

   ![Çalışan ve adres arasındaki ilişki](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   Toplayıcı `id` ,, `Employee.Id` `Employee.Name` ve `Employee` yönteminden döndürülen nesnenin `AlterEmployee` değerlerini kaydeder. Ancak toplayıcı, nesne hakkında, null olup olmadığı dışında bir bilgi kaydetmez `Address` . Toplayıcı aynı zamanda yöntemdeki yerel değişkenlerle ilgili verileri, `AlterEmployee` diğer yöntemler ise Yöntem olarak bu yerel değişkenleri parametre olarak kullanmadığı sürece de kaydetmez.

## <a name="where-else-can-i-get-intellitrace-data"></a><a name="WhereElse"></a> IntelliTrace verilerini başka bir şekilde alabilirim?

- Visual Studio Enterprise bir IntelliTrace hata ayıklama oturumundan, bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).

- Microsoft Test Yöneticisi bir test oturumundan, bkz. [nasıl yapılır: IntelliTrace verilerini toplama, zor sorunları ayıklamaya yardımcı olma](/visualstudio/test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues?view=vs-2015).

## <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?
 [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Bloglar
 [IntelliTrace tek başına toplayıcıyı uzaktan kullanma](https://devblogs.microsoft.com/devops/using-the-intellitrace-standalone-collector-remotely/)

 [IntelliTrace koleksiyon planları oluşturma ve özelleştirme](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/)

 [Üretim sunucularında IntelliTrace toplamasını iyileştirme](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 [Visual Studio ALM + TFS blogu](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)

### <a name="forums"></a>Forumlar
 [Visual Studio Hata Ayıklayıcısı](https://social.msdn.microsoft.com/Forums/vsdebug)

### <a name="videos"></a>Videolar
 [Channel 9 videosu: IntelliTrace verilerini toplama ve analiz etme](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)
