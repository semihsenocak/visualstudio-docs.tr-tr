---
title: İç içe projeleri kaldırma ve yeniden yükleme
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 154eb51014d9719b601cf87d53383f57941403a8
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036827"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>İç içe projeleri kaldırma ve yeniden yükleme konuları

İç içe geçmiş proje türleri uyguladığınızda, projeleri kaldırıp yeniden yüklediğinizde ek adımlar gerçekleştirmeniz gerekir. Dinleyicileri çözüm olaylarına doğru şekilde bildirmek için ve olaylarını doğru şekilde yükseltmeniz gerekir `OnBeforeUnloadProject` `OnAfterLoadProject` .

Bu olayları yükseltmek için bir neden kaynak kodu denetimine (SCC) yöneliktir. SCC 'in öğeleri sunucudan silmesini ve SCC 'ten bir işlem varsa bunları *Yeni* olarak geri eklemesini istemezsiniz `Get` . Bu durumda, SCC 'den yeni bir dosya yüklenir. Farklı olmaları durumunda tüm dosyaları kaldırmanız ve yeniden yüklemeniz gerekir.

Kaynak kodu denetim çağrıları `ReloadItem` . Öğesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> çağırmak `OnBeforeUnloadProject` ve `OnAfterLoadProject` projeyi silmek ve yeniden oluşturmak için arabirimini uygulayın. Arabirimi bu şekilde uyguladığınızda, SCC, projenin geçici olarak silindiğini ve yeniden eklendiğini bilgilendirilir. Bu nedenle, proje *gerçekten* silinip yeniden EKLENDIYSE, scc proje üzerinde çalışmaz.

## <a name="reload-projects"></a>Projeleri yeniden yükle

İç içe projelerin yeniden yüklenmesini desteklemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemini uygulayın. Uygulamanızda `ReloadItem` , iç içe geçmiş projeleri kapatıp yeniden oluşturursunuz.

Genellikle bir proje yeniden yüklendiğinde, IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> olaylarını oluşturur. Ancak, silinen ve yeniden yüklenen iç içe projeler için üst proje, IDE değil, işlemi başlatır. Üst proje çözüm olayları yükseltmediğinden ve IDE 'nin işlemin başlatılması hakkında hiçbir bilgisi olmadığından, olaylar oluşturulmaz.

Bu işlemi işlemek için, üst proje arabirimini çağırır `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> . `IVsFireSolutionEvents` , IDE 'ye `OnBeforeUnloadProject` iç içe geçmiş projeyi kaldırmak için olayı kullanmasını söyleyen ve sonra `OnAfterLoadProject` aynı projeyi yeniden yüklemek için olayı oluşturan işlevlere sahiptir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [İç içe projeler](../../extensibility/internals/nesting-projects.md)
