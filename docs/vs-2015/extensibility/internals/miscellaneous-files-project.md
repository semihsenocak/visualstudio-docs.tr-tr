---
title: Çeşitli dosyalar projesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c128475ad9f5cb71b98325bbece4e524507a08b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179782"
---
# <a name="miscellaneous-files-project"></a>Çeşitli Dosyalar Projesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir kullanıcı proje öğelerini açtığında, IDE çeşitli dosyalar projesine bir çözümdeki projelerin üyesi olmayan tüm öğeleri atar.  
  
 Projeler, bir Kullanıcı bir proje öğesi açtığında hangi düzenleyicinin kullanıldığını belirlemek için önemli bir rol oynar. Bir proje, belirli dosyaları projeye özgü bir düzenleyici veya standart bir düzenleyici kullanılarak açılacak şekilde tasarlanabilir.  
  
 Projeye özgü bir düzenleyici, genellikle kullanıcının özel bilgiye sahip olmasını veya projeden özel arabirimler kullanmasını gerektirir. Daha fazla bilgi için bkz. [nasıl yapılır: projeye özgü düzenleyicilerin açık](../../extensibility/how-to-open-project-specific-editors.md)olması.  
  
 Standart bir düzenleyici, herhangi bir projede belirli bir uzantının herhangi bir dosyasını açabilir. Kullanıcı, projeler için metin Düzenleyicisi gibi bazı standart düzenleyicileri özelleştirebilir, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ancak yine de ortak karakterlerini koruyabilir. Standart düzenleyiciler yöntemi kullanılarak oluşturulur <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
 Çözümdeki hiçbir proje bir proje öğesi açabildiğinden yanıt verirse, IDE, herhangi bir dosyayı açan çeşitli dosyalar projesi adlı özel bir proje sağlar.  
  
 Bu özel proje, bir dosyanın bir proje bağlamı dışında açılmasını sağlar. Yöntemin işlenmesi sırasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> , Miscellaneous Files projesi her zaman çok düşük bir önceliğe sahip olarak yanıt verir. Bu nedenle, çeşitli dosyalar projesi her zaman dosyaları açan daha yüksek öncelikli bir projeye üretir.  
  
 Çeşitli dosyalar projesi, kullanıcının bunu **Yeni proje** iletişim kutusuyla açıkça oluşturmasını gerektirmez. Ayrıca, Miscellaneous Files projesi Proje üyelerinin bir listesini kalıcı olarak yönetmez. Her Kullanıcı için en son kullanılan dosyaların listesini kaydetmek için isteğe bağlı bir özellik kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Nasıl yapılır: projeye özgü düzenleyiciler açma](../../extensibility/how-to-open-project-specific-editors.md)   
 [Nasıl yapılır: standart düzenleyiciler açma](../../extensibility/how-to-open-standard-editors.md)   
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
