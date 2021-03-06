---
title: Komut satırından ClickOnce uygulamaları oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2625a8d4caa7dd53e9ce86395a98622f91d686b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155706"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Komut Satırından ClickOnce Uygulamalarını Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

' De [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , tümleşik geliştirme ortamında (IDE) oluşturulmuş olsalar dahi, komut satırından projeler oluşturabilirsiniz. Aslında, ile oluşturulmuş bir projeyi, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yalnızca yüklü olan başka bir bilgisayarda yeniden oluşturabilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu, bir derlemeyi otomatik bir işlem kullanarak yeniden oluşturmanızı sağlar (örneğin, merkezi bir yapı laboratuvarında veya projenin kendisini oluşturma kapsamının ötesinde gelişmiş betik oluşturma tekniklerini kullanarak).  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>ClickOnce uygulama dağıtımlarını yeniden oluşturmak için MSBuild kullanma  
 MSBuild/target: Publish komutunu komut satırında çağırdığınızda, MSBuild sistemine projeyi oluşturmasını ve [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Publish klasöründe bir uygulama oluşturmasını söyler. Bu, IDE 'de **Publish** komutunu seçmeye eşdeğerdir.  
  
 Bu komut, Visual Studio komut istemi ortamındaki yolda olan msbuild.exe yürütür.  
  
 "Target", komutun nasıl işlenmesi üzerine MSBuild için bir göstergedir. Anahtar hedefleri "derleme" hedefi ve "Yayımla" hedefidir. Yapı hedefi, IDE 'de Yapı komutunu seçmeye (veya F5 tuşuna basarak) eşdeğerdir. Yalnızca projenizi derlemek istiyorsanız yazarak bunu yapabilirsiniz `msbuild` . Bu komut, derleme hedefi tarafından oluşturulan tüm projeler için varsayılan hedef olduğu için geçerlidir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Bu, açıkça derleme hedefini belirtmeniz gerekmediği anlamına gelir. Bu nedenle, yazma `msbuild` işlemi ile aynı işlem aynıdır `msbuild /target:build` .  
  
 `/target:publish`Komutu MSBuild 'in yayımlama hedefini çağırmasını söyler. Yayımla hedefi derleme hedefine bağlıdır. Bu, yayımlama işleminin derleme işleminin bir üst kümesi olduğu anlamına gelir. Örneğin, Visual Basic veya C# kaynak dosyalarından birine bir değişiklik yaptıysanız, ilgili derleme Yayımla işlemi tarafından otomatik olarak yeniden oluşturulur.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Bildiriminizi oluşturmak için Mage.exe komut satırı aracını kullanarak tam dağıtım oluşturma hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bkz. [Izlenecek yol: El Ile ClickOnce uygulaması dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>MSBuild kullanarak temel ClickOnce uygulaması oluşturma ve oluşturma  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>ClickOnce projesi oluşturmak ve yayımlamak için  
  
1. **Dosya** menüsünden **Yeni proje** ' ye tıklayın. **Yeni Proje** iletişim kutusu görünür.  
  
2. **Windows uygulaması** ' nı seçin ve adlandırın `CmdLineDemo` .  
  
3. **Build** menüsünden **Publish** komutuna tıklayın.  
  
    Bu adım, projenin bir uygulama dağıtımı oluşturmak için düzgün şekilde yapılandırılmasını sağlar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
    Yayımla Sihirbazı görüntülenir.  
  
4. Yayımla sihirbazında **son**' a tıklayın.  
  
    Visual Studio, Publish.htm adlı varsayılan Web sayfasını oluşturur ve görüntüler.  
  
5. Projenizi kaydedin ve depolandığı klasör konumunu aklınızda olun.  
  
   Yukarıdaki adımlar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ilk kez yayımlanmış bir proje oluşturur. Artık derlemeyi IDE dışında yeniden oluşturabilirsiniz.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Derlemeyi komut satırından yeniden oluşturmak için  
  
1. Çıkış yapın [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .  
  
2. Windows **Başlat** menüsünde **tüm programlar**' a ve ardından **Microsoft Visual Studio** **Visual Studio Araçları**, sonra da **Visual Studio komut istemi**' ne tıklayın. Bu, geçerli kullanıcının kök klasöründe bir komut istemi açması gerekir.  
  
3. **Visual Studio komut isteminde**, geçerli dizini yukarıda oluşturduğunuz projenin konumuyla değiştirin. Örneğin, `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. "Bir proje oluşturmak ve yayımlamak Için" içinde oluşturulan mevcut dosyaları kaldırmak için [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , yazın `rmdir /s publish` .  
  
    Bu adım isteğe bağlıdır, ancak yeni dosyaların tümünün komut satırı derlemesi tarafından üretilmiş olmasını sağlar.  
  
5. `msbuild /target:publish` yazın.  
  
   Yukarıdaki adımlar, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projenizin **Publish**adlı bir alt klasöründe tam uygulama dağıtımı oluşturacak. CmdLineDemo. Application, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bildirimidir. CmdLineDemo_1.0.0.0 klasörü, uygulama bildirimi CmdLineDemo.exe ve CmdLineDemo.exe. manifest dosyalarını içerir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Setup.exe, varsayılan olarak, yüklemek için yapılandırılmış olan önyükleyici olur [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . DotNetFX klasörü, için yeniden dağıtılabilir içerir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu, uygulamanızı Web üzerinden veya UNC veya CD/DVD aracılığıyla dağıtmanız için gereken tüm dosya kümesidir.  
  
## <a name="publishing-properties"></a>Yayımlama özellikleri  
 Uygulamayı yukarıdaki yordamlarda yayımladığınızda, Yayımlama Sihirbazı tarafından proje dosyanıza aşağıdaki özellikler eklenir. Bu özellikler, uygulamanın nasıl üretildiğini doğrudan etkiler [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
 CmdLineDemo. vbproj/CmdLineDemo. csproj içinde:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Bu özelliklerden herhangi birini, proje dosyasının kendisini değiştirmeden, komut satırında geçersiz kılabilirsiniz. Örneğin, aşağıdakiler [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] önyükleyici olmadan uygulama dağıtımını oluşturur:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Yayımlama özellikleri, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Proje Tasarımcısı**'nın **Yayımlama**, **güvenlik**ve **imzalama** Özellik sayfalarından denetlenir. Aşağıda, yayımlama özelliklerinin açıklaması ve bunların her birinin Uygulama Tasarımcısı 'nın çeşitli özellik sayfalarında nasıl ayarlandığı hakkında bir gösterge verilmiştir:  
  
- `AssemblyOriginatorKeyFile` Uygulama bildirimlerinizi imzalamak için kullanılan anahtar dosyasını belirler [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu aynı anahtar, derlemelerinize güçlü bir ad atamak için de kullanılabilir. Bu özellik, **Proje Tasarımcısı**' nın **imzalama** sayfasında ayarlanır.  
  
  Aşağıdaki özellikler **güvenlik** sayfasında ayarlanır:  
  
- **ClickOnce güvenlik ayarlarını etkinleştirme** [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , bildirimlerin oluşturulup oluşturulmayacağını belirler. Bir proje ilk oluşturulduğunda, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirim oluşturma varsayılan olarak kapalıdır. İlk kez yayımladığınızda sihirbaz otomatik olarak bu bayrağı kullanacaktır.  
  
- **TargetZone** , uygulama bildiriminiz için kullanılacak güven düzeyini belirler [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Olası değerler şunlardır. "Internet", "LocalIntranet" ve "özel". Internet ve LocalIntranet, varsayılan bir izin kümesinin uygulama bildiriminize yayılmasına neden olur [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . LocalIntranet varsayılandır ve temel olarak tam güven anlamına gelir. Custom, yalnızca temel app. manifest dosyasında açıkça belirtilen izinlerin uygulama bildirimine yayınlandığını belirtir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . App. manifest dosyası, yalnızca güven bilgileri tanımlarını içeren kısmi bir bildirim dosyasıdır. **Güvenlik** sayfasında izinleri yapılandırdığınızda otomatik olarak projenize eklenen gizli bir dosyadır.  
  
  **Yayımla** sayfasında aşağıdaki özellikler ayarlanır:  
  
- `PublishUrl` , uygulamanın IDE 'de Yayınlanma konumu olur. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `InstallUrl` Ya da özelliği belirtilmemişse uygulama bildirimine eklenir `UpdateUrl` .  
  
- `ApplicationVersion` uygulamanın sürümünü belirtir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu, dört basamaklı bir sürüm numarasıdır. Son basamak bir "*" ise, `ApplicationRevision` derleme zamanında bildirime yerleştirilen değerin yerine kullanılır.  
  
- `ApplicationRevision` düzeltmeyi belirtir. Bu, IDE 'de yayımladığınız her seferinde artan bir tamsayıdır. Komut satırında gerçekleştirilen derlemeler için otomatik olarak arttırılmadığından emin olun.  
  
- `Install` uygulamanın yüklü bir uygulama mı yoksa bir Web 'den Çalıştırma uygulaması mı olduğunu belirler.  
  
- `InstallUrl` (gösterilmez), kullanıcıların uygulamayı yükleneceği konumdur. Belirtilmişse, özellik etkinse bu değer setup.exe önyükleyici içine yazılır `IsWebBootstrapper` . Belirtilmemişse, uygulama bildirimine de eklenir `UpdateUrl` .  
  
- `SupportUrl` (gösterilmez), yüklü bir uygulama için **Program Ekle/Kaldır** iletişim kutusunda bağlanan konumdur.  
  
  Aşağıdaki özellikler **Yayımla** sayfasından erişilen **uygulama güncelleştirmeleri** iletişim kutusunda ayarlanır.  
  
- `UpdateEnabled` uygulamanın güncelleştirmeleri denetleyip denetmeyeceğini belirtir.  
  
- `UpdateMode` Ön plan güncelleştirmelerini veya arka plan güncelleştirmelerini belirtir.  
  
- `UpdateInterval` uygulamanın hangi sıklıkta güncelleştirmeleri denetlemesi gerektiğini belirtir.  
  
- `UpdateIntervalUnits``UpdateInterval`değerin saat, gün veya hafta cinsinden olup olmadığını belirtir.  
  
- `UpdateUrl` (gösterilmez), uygulamanın güncelleştirmeleri alacağı konumdur. Belirtilmişse, bu değer uygulama bildirimine eklenir.  
  
- Aşağıdaki özellikler **Yayımla sayfasından erişilen** **Yayımla Seçenekleri** iletişim kutusunda ayarlanır.  
  
- `PublisherName` uygulamayı yüklerken veya çalıştırırken gösterilen istem içinde gösterilen yayımcının adını belirtir. Yüklü bir uygulama söz konusu olduğunda, **Başlangıç** menüsünde Klasör adını belirtmek için de kullanılır.  
  
- `ProductName` uygulamayı yüklerken veya çalıştırırken gösterilen istem içinde gösterilen ürünün adını belirtir. Yüklü bir uygulama söz konusu olduğunda, **Başlangıç** menüsünde kısayol adını belirtmek için de kullanılır.  
  
- Aşağıdaki özellikler, **Yayımla** sayfasından erişilen **Önkoşullar** iletişim kutusunda ayarlanır.  
  
- `BootstrapperEnabled` setup.exe önyükleyici oluşturulup oluşturulmayacağını belirler.  
  
- `IsWebBootstrapper` setup.exe önyükleyicinin Web üzerinde veya disk tabanlı modda çalışıp çalışmadığını belirler.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallUrl, SupportUrl, PublishURL ve UpdateURL  
 Aşağıdaki tabloda ClickOnce dağıtımı için dört URL seçeneği gösterilmektedir.  
  
|URL seçeneği|Açıklama|  
|----------------|-----------------|  
|`PublishURL`|ClickOnce uygulamanızı bir Web sitesinde yayımlıyorsanız gereklidir.|  
|`InstallURL`|İsteğe bağlı. Yükleme sitesi öğesinden farklıysa bu URL seçeneğini ayarlayın `PublishURL` . Örneğin, öğesini bir `PublishURL` FTP yolu olarak ayarlayabilir ve ' ı `InstallURL` BIR Web URL 'si olarak ayarlayabilirsiniz.|  
|`SupportURL`|İsteğe bağlı. Destek sitesi öğesinden farklıysa bu URL seçeneğini ayarlayın `PublishURL` . Örneğin, seçeneğini `SupportURL` şirketinizin müşteri desteği web sitesine ayarlayabilirsiniz.|  
|`UpdateURL`|İsteğe bağlı. Güncelleştirme konumu öğesinden farklıysa bu URL seçeneğini ayarlayın `InstallURL` . Örneğin, öğesini bir `PublishURL` FTP yolu olarak ayarlayabilir ve ' ı `UpdateURL` BIR Web URL 'si olarak ayarlayabilirsiniz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
