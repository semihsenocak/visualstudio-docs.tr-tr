---
title: Özel parametreler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a595861be835ec1aaa7079b3e3fe1962d5055e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154993"
---
# <a name="custom-parameters"></a>Özel Parametreler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Özel parametreler sihirbaz başladıktan sonra sihirbazın işlemini denetler. İlgili bir. vsz dosyası, tümleşik geliştirme ortamı (IDE) tarafından paketlenmiş ve sihirbaz başlatıldığında dize dizisi olarak sihirbaza geçilen Kullanıcı tanımlı parametrelerin dizisini sağlar. Sihirbaz daha sonra dizeler dizisini ayrıştırır ve sihirbazın gerçek işlemini denetlemek için bu bilgileri kullanır. Bu şekilde, bir sihirbaz. vsz dosyasının içeriğine bağlı olarak işlevselliği özelleştirebilir.  
  
 Bağlam parametreleri, diğer yandan, sihirbaz başlatıldığında projenin durumunu tanımlar. Daha fazla bilgi için bkz. [Bağlam parametreleri](../../extensibility/internals/context-parameters.md).  
  
 Özel parametrelere sahip bir. vsz dosyasının örneği aşağıda verilmiştir:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 . Vsz dosyasının yazarı parametre değerlerini ekler. Bir Kullanıcı **Yeni proje** **seçtiğinde veya dosya** menüsünde bir projeye sağ TıKLANARAK **Çözüm Gezgini**, IDE bu değerleri bir dizeler dizisine toplar. Daha sonra IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> bayrak kümesiyle projenin yöntemini çağırır <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> ve proje, <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> Sihirbazı çalıştırmaktan ve sonucu döndürmekten sorumlu yöntemi çağırır.  
  
 Sihirbaz, dizelerin dizisini ayrıştırmaktan ve dizilerin uygun şekilde davranmasından sorumludur. Bu şekilde, özel parametreler uygulayarak çeşitli işlevler gerçekleştiren bir sihirbaz oluşturabilirsiniz. Diğer bir deyişle, bir sihirbaz üç farklı. vsz dosyasına sahip olabilir. Her dosya, sihirbazın çeşitli durumlarda davranışını denetlemek için farklı özel parametre kümeleri geçirir.  
  
 Daha fazla bilgi için bkz [. sihirbaz (. Vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)   
 ['Nı](../../extensibility/internals/wizards.md)   
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
