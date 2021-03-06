---
title: Eski dil hizmetinde hızlı bilgi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc8bfff0903d2ed1554cfd8b3d5b1dcf5cf0fa8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64781970"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Hızlı Bilgiler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**IntelliSense hızlı** bilgi, Kullanıcı giriş işaretini tanımlayıcıya **yerleştirdikçe veya** fare imlecini tanımlayıcı üzerinde tuttuğunda, kaynaktaki bir tanımlayıcı hakkındaki bilgileri gösterir. Bu, bir araç ipucunun tanımlayıcı hakkında bilgi ile görünmesine neden olur. Bu bilgiler genellikle tanımlayıcı türünden oluşur. Hata ayıklama altyapısı etkin olduğunda, bu bilgiler geçerli değeri içerebilir. Hata ayıklama altyapısı, yalnızca tanımlayıcıları işlerken, ifade değerleri sağlar.  
  
 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [Izlenecek yol: hızlı bilgi araç Ipuçlarını görüntüleme](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.  
  
 Yönetilen paket çerçevesi (MPF) dil hizmeti sınıfları, IntelliSense hızlı bilgi araç ipucunu görüntülemek için tam destek sağlar. Tüm yapmanız gerekir, görüntülenecek metni sağlamak ve hızlı bilgi özelliğini etkinleştirmek için gereklidir.  
  
 Görüntülenecek metin, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayrıştırma nedeni değeri olan yöntem ayrıştırıcısı çağırarak elde edilir <xref:Microsoft.VisualStudio.Package.ParseReason> . Bu nedenle, ayrıştırıcının nesne içinde belirtilen konumdaki tanımlayıcı için tür bilgilerini (veya hızlı bilgi araç ipucunda görüntülenmek üzere uygun olanını) almasını söyler <xref:Microsoft.VisualStudio.Package.ParseRequest> . <xref:Microsoft.VisualStudio.Package.ParseRequest>Nesnesi yöntemine geçirilen şeydir <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> .  
  
 Ayrıştırıcı, <xref:Microsoft.VisualStudio.Package.ParseRequest> Tüm tanımlayıcıların türlerini belirleyebilmek için nesnedeki konuma kadar her şeyi ayrıştıramalıdır. Sonra ayrıştırıcı, ayrıştırma isteği konumundaki tanımlayıcıyı almalıdır. Son olarak, ayrıştırıcının bu tanımlayıcıyla ilişkili araç ipucu verisini nesnesine geçirmesi gerekir, <xref:Microsoft.VisualStudio.Package.AuthoringScope> böylece nesne yönteminden metin döndürebilir <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> .  
  
## <a name="enabling-the-quick-info-feature"></a>Hızlı bilgi özelliğini etkinleştirme  
 Hızlı bilgi özelliğini etkinleştirmek için, `CodeSense` ve `QuickInfo` adlandırılmış parametrelerini ayarlamanız gerekir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Bu öznitelikler <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> ve özelliklerini ayarlar <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> .  
  
## <a name="implementing-the-quick-info-feature"></a>Hızlı bilgi özelliğini uygulama  
 <xref:Microsoft.VisualStudio.Package.ViewFilter>Sınıfı, IntelliSense hızlı bilgi işlemini işler. <xref:Microsoft.VisualStudio.Package.ViewFilter>Sınıf <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> komutu aldığında, sınıfı <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemini ayrıştırma nedenine <xref:Microsoft.VisualStudio.Package.ParseReason> ve komutun gönderildiği sırada giriş işaretinin konumunu çağırır <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> . <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Yöntem ayrıştırıcısı daha sonra kaynağı verilen konuma ayrıştırır ve sonra hızlı bilgi araç ipucunda nelerin görüntüleneceğini belirlemek için verilen konumdaki tanımlayıcıyı ayrıştırmalıdır.  
  
 Çoğu ayrıştırıcıları kaynak dosyanın tamamını bir kez ayrıştırarak sonuçları bir ayrıştırma ağacına depolar. Yönteme geçirildiğinde, tüm ayrıştırma yürütülür <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Diğer ayrıştırma türleri, istenen bilgileri elde etmek için ayrıştırma ağacını kullanabilir.  
  
 Örneğin, ayrıştırma nedeni değeri <xref:Microsoft.VisualStudio.Package.ParseReason> kaynak konumda tanımlayıcıyı bulabilir ve tür bilgilerini almak için ayrıştırma ağacında arama yapabilir. Bu tür bilgileri daha sonra <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfına geçirilir ve yöntemi tarafından döndürülür <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> .
