---
title: Seçim bağlamı nesneleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705506"
---
# <a name="selection-context-objects"></a>Seçim Bağlamı Nesneleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamı (IDE), IDE 'de neyin gösterilmesi gerektiğini belirlemek için bir genel seçim bağlam nesnesi kullanır. IDE içindeki her bir pencere, genel seçim bağlamına gönderilen kendi seçim bağlamı nesnesine sahip olabilir. IDE, bir pencere odağa sahip olduğunda bir penceredeki değerlerle genel seçim bağlamını günceller. Daha fazla bilgi için bkz. [kullanıcıya geri bildirim](../../extensibility/internals/feedback-to-the-user.md).

 IDE 'deki her pencere çerçevesinin veya sitesinin adlı bir hizmeti vardır <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . VSPackage tarafından oluşturulan ve pencere çerçevesinde yer alan nesne, `QueryService` arabirime yönelik bir işaretçi almak için yöntemini çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

 Çerçeve pencereleri, seçim bağlamı bilgilerinin bölümlerinin, başlatıldıklarında genel seçim bağlamına yayılmasına devam edebilir. Bu özellik, boş bir seçimle başlamak zorunda olabilecek araç pencereleri için yararlıdır.

 Genel seçim bağlamını değiştirmek, VSPackages 'in izleyebileceği olayları tetikler. VSPackages, ve arabirimlerini uygulayarak aşağıdaki görevleri gerçekleştirebilir `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> :

- Hiyerarşide etkin olan dosyayı güncelleştirin.

- Belirli öğe türlerinde yapılan değişiklikleri izleyin. Örneğin, VSPackage özel bir **Özellikler** penceresi kullanıyorsa, etkin **Özellikler** penceresinde değişiklikleri izleyebilir ve gerektiğinde kendiniz yeniden başlatabilirsiniz.

  Aşağıdaki sırada, seçim izlemenin tipik bir kursu gösterilmektedir.

1. IDE, yeni açılan pencereden seçim bağlamını alır ve onu genel seçim bağlamına koyar. Seçim bağlamı HIERARCHY_DONTPROPAGATE veya SELCONTAINER_DONTPROPAGATE kullanıyorsa, bu bilgiler genel içeriğe yayılmaz. Daha fazla bilgi için bkz. [kullanıcıya geri bildirim](../../extensibility/internals/feedback-to-the-user.md).

2. Bildirim olayları, isteyen herhangi bir VSPackage 'a yayınlanır.

3. VSPackage, bir hiyerarşiyi güncelleştirme, bir aracı veya benzer görevleri yeniden etkinleştirme gibi etkinlikleri gerçekleştirerek aldığı olaylara göre davranır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE’de Seçim ve Para Birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Proje Türleri](../../extensibility/internals/project-types.md)
