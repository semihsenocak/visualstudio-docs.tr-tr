---
title: Proje modelinin öğeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3b07068939e34b5c9e9487761177c0e12f5654
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700134"
---
# <a name="elements-of-a-project-model"></a>Proje Modeli Öğeleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Temel yapıyı paylaşan tüm projelerin arabirimleri ve uygulamaları [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] : proje türü için proje modeli. Geliştirmekte olduğunuz VSPackage olan proje modelinizde, tasarım kararlarınızla uyumlu olan ve IDE tarafından sunulan genel işlevlerle birlikte çalışan nesneler oluşturursunuz. Bir proje öğesinin nasıl kalıcı olduğunu denetlemenize karşın, örneğin, bir dosyanın kalıcı olması gerektiğini kontrol edersiniz. Bir Kullanıcı, odağı açık bir proje öğesine yerleştiriyor ve menü çubuğundaki **Dosya** menüsünde **Kaydet** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ' i SEÇTIĞINDE, proje türü kodunuz IDE 'den komutu ele almalıdır, dosyayı kalıcı hale getirin ve dosyanın artık değiştirilmediğini daha sonra geri bildirim gönderir.  
  
 VSPackage, IDE arabirimlerine erişim sağlayan hizmetler aracılığıyla IDE ile etkileşime girer. Örneğin, belirli hizmetler aracılığıyla komutları izleyip yönlendirebilir ve projede yapılan seçimlere yönelik bağlam bilgilerini sağlarsınız. VSPackage için gereken tüm Global IDE işlevleri hizmetler tarafından sağlanmaktadır. Hizmetler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet alma](../../extensibility/how-to-get-a-service.md).  
  
 Diğer uygulama konuları:  
  
- Tek bir proje modelinde birden fazla proje türü bulunabilir.  
  
- Proje türleri ve ilgili proje fabrikaları, GUID 'lerle bağımsız olarak kaydedilir.  
  
- Kullanıcı Kullanıcı arabirimi aracılığıyla yeni bir proje oluşturduğunda, her projenin yeni proje dosyasını başlatması için bir şablon dosyası veya Sihirbazı olması gerekir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Örneğin, şablonlar, son olarak [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] . vcproj dosyaları olmaya başlatırlar.  
  
  Aşağıdaki çizimde, tipik bir proje uygulamasını oluşturan birincil arabirimler, hizmetler ve nesneler gösterilmektedir. Temel nesneleri ve diğer programlama ortak nesnelerini oluşturmak için HierUtil7 uygulama yardımcısını kullanabilirsiniz. HierUtil7 uygulama Yardımcısı hakkında daha fazla bilgi için bkz. [derlemede değil: proje türü uygulamak Için HierUtil7 proje sınıflarını kullanma (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Visual Studio proje modeli grafiği](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  Proje modeli  
  
  Önceki diyagramda listelenen arabirimler ve hizmetler ve diyagramda bulunmayan diğer isteğe bağlı arabirimler hakkında daha fazla bilgi için bkz. [proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md).  
  
  Projeler komutları destekleyebilir ve bu nedenle komut <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> yönlendirme GUID 'leri aracılığıyla komut yönlendirmesine katılmak için arabirimi uygulamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim listesi: yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Yapıda değil: proje türü uygulamak için HierUtil7 proje sınıflarını kullanma (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)   
 [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Nasıl yapılır: hizmet alma](../../extensibility/how-to-get-a-service.md)   
 [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)
