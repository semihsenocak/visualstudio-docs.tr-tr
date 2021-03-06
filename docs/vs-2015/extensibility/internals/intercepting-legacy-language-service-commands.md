---
title: Eski dil hizmeti komutlarını kesintiye uğratan | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6510df2cc9cc1e504f09af033548e0d1c9b4ae74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195005"
---
# <a name="intercepting-legacy-language-service-commands"></a>Eski Dil Hizmeti Komutlarını Kesme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , metin görünümünün daha sonra işleyememesi için dil hizmeti kesme komutlarının de olmasını sağlayabilirsiniz. Bu, metin görünümünün yönetmediğinden dile özgü davranış için yararlıdır. Dil hizmetinizdeki metin görünümüne bir veya daha fazla komut filtresi ekleyerek bu komutları ele alabilirsiniz.  
  
## <a name="getting-and-routing-the-command"></a>Komutu alma ve yönlendirme  
 Komut filtresi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> belirli karakter dizilerini veya anahtar komutları izleyen bir nesnedir. Birden fazla komut filtresini tek bir metin görünümüyle ilişkilendirebilirsiniz. Her metin görünümü bir komut filtreleri zinciri saklar. Yeni bir komut filtresi oluşturduktan sonra, uygun metin görünümü için filtreyi zincire eklersiniz.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Komut filtrenizi zincire eklemek için üzerinde yöntemini çağırın. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>' İ çağırdığınızda, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komut filtreniz tarafından işlemeyen komutları geçirebilmeniz için başka bir komut filtresi döndürür.  
  
 Komut işleme için aşağıdaki seçenekleriniz vardır:  
  
- Komutu işleyin ve ardından zincirindeki sonraki komut filtresine komutunu geçirin.  
  
- Komutu işleyin ve komutu bir sonraki komut filtresine iletmeyin.  
  
- Komutu işlemez, ancak komutunu bir sonraki komut filtresine geçirin.  
  
- Komutu yoksayın. Geçerli filtrede işlemeyin ve sonraki filtreye geçirmeyin.  
  
  Dil hizmetinizin hangi komutları işlemesi gerektiği hakkında daha fazla bilgi için bkz. [dil hizmeti filtreleri Için önemli komutlar](../../extensibility/internals/important-commands-for-language-service-filters.md).
