---
title: Projeler ve düzenleyicilerle ilgili ek kaynak denetimi yönergeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 376b297e94cc8e5f429254bdc981aea994b27130
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203838"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Projeler ve Düzenleyiciler için Ek Kaynak Denetimi Yönergeleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projeler ve düzenleyicilerin kaynak denetimini desteklemek için uyması gereken birçok yönerge vardır.  
  
## <a name="guidelines"></a>Yönergeler  
 Kaynak denetimini desteklemek için projeniz veya düzenleyiciniz aşağıdakileri de yapmanız gerekir:  
  
|Alan|Project|Düzenleyici|Ayrıntılar|  
|----------|-------------|------------|-------------|  
|Dosyaların özel kopyaları|X||Ortam, dosyaların özel kopyalarını destekler. Diğer bir deyişle, projeye kayıtlı her kişi, bu projedeki dosyaların özel bir kopyasına sahiptir.|  
|ANSI/UNICODE kalıcılığı|X|X|Kalıcılık kodu yazarsanız, kaynak denetim programlarının çoğu şu anda Unicode desteklemediği için dosyaları ANSI biçiminde kalıcı hale getirin.|  
|Dosyaları listeleme|X||Proje, içindeki tüm dosyaların belirli bir listesini içermeli ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling) kullanarak dosya listesini numaralandırabilmelidir. Proje ayrıca, uygulama aracılığıyla öğe adlarını da kullanıma sunmalı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> ve uygulama aracılığıyla ad aramasını (özel dosyalar dahil) desteklemelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> .|  
|Metin biçimi|X|X|Mümkün olduğunda, farklı sürümlerin birleştirilmesini desteklemek için dosyaların metin biçiminde olması gerekir. Metin biçiminde olmayan dosyalar daha sonra dosyanın diğer sürümleriyle birleştirilemez. Tercih edilen metin biçimi XML 'dir.|  
|Başvuru tabanlı|X||Başvuru tabanlı projeler kaynak denetiminde kolayca desteklenir. Ancak, bu dosyaların diskte bulunup bulunmaması fark edildiğinde, proje, kaynak denetimi tarafından isteğe bağlı olarak bir liste oluşturabildiği sürece kaynak denetimi tarafından da desteklenir. Kaynak denetiminden bir proje açılırken, proje dosyası öncelikle dosyalarından herhangi birinin önüne getirilir.|  
|Nesneleri ve özellikleri öngörülebilir sırada kalıcı yap|X|X|Birleştirmeyi kolaylaştırmak için dosyalarınızı alfabetik sıralama gibi öngörülebilir bir düzende kalıcı hale getirin.|  
|Yeniden yükle|X|X|Diskteki bir dosya değiştiğinde, Düzenleyicinizde yeniden yükleyebilmelidir. Kaynak denetimine katıldığınızda, ortam, uygulamanızı çağırarak verileri sizin için yeniden yükler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> . En zor yeniden yükleme durumu, IVsQueryEditQuerySave:: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ' i çağırdığınızda ve bilgileri işlerken bir kullanıma alma işlemi meydana gelir. Ancak, yeniden yükleme kodunuzun bu durumda çalışması gerekir.<br /><br /> Ortam, proje dosyalarını otomatik olarak yeniden yükler. Ancak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> iç içe geçmiş proje dosyalarını yeniden yüklemeyi desteklemek için bir proje iç içe hiyerarşiler içeriyorsa uygulaması gerekir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
