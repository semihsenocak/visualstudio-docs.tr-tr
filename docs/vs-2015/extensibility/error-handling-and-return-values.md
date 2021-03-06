---
title: Hata Işleme ve dönüş değerleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74e61e60384b3e98bf26eb8208696ecb9223efa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696341"
---
# <a name="error-handling-and-return-values"></a>Hata İşleme ve Dönüş Değerleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages ve COM, hatalar için aynı mimariyi kullanır. `SetErrorInfo`Ve `GetErrorInfo` Işlevleri, Win32 uygulama programlama ARABIRIMININ (API) bir parçasıdır. Tümleşik geliştirme ortamındaki (IDE) herhangi bir VSPackage, hata bildirimi alırken zengin hata bilgilerini kaydetmek için bu genel Win32 API 'Lerini çağırabilir. , [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Hata bilgilerini yönetmek için birlikte çalışma derlemeleri sağlar.  
  
## <a name="interop-methods"></a>Birlikte çalışma yöntemleri  
 Bir kolaylık olması halinde, IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Win32 API 'lerini çağırmak yerine kullanmak için bir yöntem sağlar. Yönetilen kod kullanımı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . `HRESULT`Hata iletisinin gösterilmesi gereken düzeye bir hata ulaştığında (Bu genellikle bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komut işleyicisini uygulayan nesnedir), IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> uygun ileti kutusunu göstermek için başka bir yöntem kullanır. Yönetilen kodda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> yöntemini kullanın.  
  
 VSPackage uygulayıcısı olarak COM nesneleriniz normalde uygular `ISupportErrorInfo` . `ISupportErrorInfo`Arabirim, zengin hata bilgilerinin, çağrı zincirinde dikey olarak taşınmasını sağlar. İşlem genelinde veya iş parçacıkları genelinde kullanılabilecek nesneler, `ISupportErrorInfo` zengin hata bilgilerinin çağırana doğru şekilde geri sıralandığından emin olmak için desteklemelidir.  
  
 VSPackages ile ilgili olan ve düzenleyici fabrikası, düzenleyiciler, hiyerarşiler ve sunulan hizmetler de dahil olmak üzere IDE 'yi genişletmeye dahil olan tüm nesneler, zengin hata bilgilerini desteklemelidir. IDE, bu VSPackage nesnelerinin uygulanmasını gerektirse de `ISupportErrorInfo` her zaman önerilir.  
  
 IDE, hata bilgilerini bildirmekten ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 'ye her yayıldıktan sonra bir kullanıcıya görüntülüyor `HRESULT` . IDE, nesne oluşturmaya yönelik mekanizmaya de sahiptir `ErrorInfo` .  
  
## <a name="general-guidelines"></a>Genel Yönergeler  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>Ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> yöntemlerini, VSPackage uygulamanızda iç hataları ayarlamak ve raporlamak için de kullanabilirsiniz. Bununla birlikte, genel bir kural olarak, VSPackage 'daki hata iletilerini işlemek için aşağıdaki yönergeleri izleyin:  
  
- `ISupportErrorInfo`VSPackage com nesnelerinizi uygulayın.  
  
- Uygulayan nesnelerde yöntemini çağıran bir hata raporlama mekanizması oluşturun <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
- IDE 'nin yöntemi aracılığıyla kullanıcılara hata görüntülemesine izin verin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> .  
  
## <a name="error-information-in-the-ide"></a>IDE 'de hata bilgileri  
 Aşağıdaki kurallar IDE 'de hata bilgilerinin nasıl işleneceğini gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- Eski hata bilgilerinin kullanıcılara bildirilmediğinden emin olmak için savunma stratejisi olarak, yöntemi çağıran işlevler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> öncelikle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemi çağırmalıdır. `null`Yeni hata bilgileri ayarlayabilen herhangi bir şeyi çağırmadan önce önbelleğe alınmış hata iletilerini temizlemek için geçirin.  
  
- Doğrudan hata iletilerini bildirmeyen işlevlerin yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> bir hata döndürmeleri durumunda yöntemi çağırması için izin verilir `HRESULT` . `ErrorInfo`Girişi bir işleve veya döndürme sırasında temizlemek için izin verilir <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Bu kuralın tek istisnası, bir çağrının, `HRESULT` alıcı tarafın açıkça kurtarabileceği veya güvenli bir şekilde yoksaydığı bir hata döndürdüğü durumdur.  
  
- Açıkça bir hatayı yok sayan herhangi bir tarafın `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> ile yöntemini çağırması gerekir <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Aksi takdirde, `ErrorInfo` nesne yanlışlıkla başka bir taraf kendi kendine sağlamadan bir hata oluşturduğunda kullanılıyor olabilir `ErrorInfo` .  
  
- Bir hata oluşturan tüm yöntemlerin `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> zengin hata bilgileri sağlamak için yöntemini çağırması önerilir. Döndürülen `HRESULT` özel bir `FACILITY_ITF` hata ise, uygun bir nesne sağlamak için yöntemi gerekir `ErrorInfo` . Döndürülen hata standart sistem hatası ise (örneğin,,,, vb <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> .), yöntemi açıkça çağrılmadan hata kodunu döndürmek kabul edilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Bir hata oluştuğunda (sistem hataları dahil) Savunma kod oluşturma stratejisi olarak, hatayı `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> `ErrorInfo` daha ayrıntılı olarak açıklayan veya ya da yöntemini her zaman çağırın `null` .  
  
- Başka bir çağrının kaynaklandığı bir hatayı döndüren tüm işlevler, nesne üzerinde değişiklik yapmadan, içindeki başarısız çağrıdan alınan bilgileri iletmelidir `HRESULT` `ErrorInfo` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (Bileşen Otomasyonu)](https://msdn.microsoft.com/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](https://msdn.microsoft.com/03317526-8c4f-4173-bc10-110c8112676a)   
 [Iupporterrorınfo arabirimi](https://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32)
