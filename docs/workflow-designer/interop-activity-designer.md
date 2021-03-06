---
title: İş Akışı Tasarımcısı-Interop etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650205"
---
# <a name="interop-activity-designer"></a>Interop Etkinlik Tasarımcısı

**Birlikte çalışma** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Interop> .

## <a name="the-interop-activity"></a>Birlikte çalışma etkinliği

<xref:System.Activities.Statements.Interop>Etkinlik, <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> bir iş akışı içinden türetilen türlerin yürütülmesini yönetir.

### <a name="use-the-interop-activity-designer"></a>Birlikte çalışabilirlik etkinlik tasarımcısını kullanma

**Birlikte çalışabilirlik** etkinlik Tasarımcısı, araç **kutusu** sekmesine tıklanarak erişilen **araç kutusu** **geçiş** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X**tuşlarına basın.

Etkinlik içeren [geçiş](../workflow-designer/migration-activity-designers.md) kategorisi yalnızca, <xref:System.Activities.Statements.Interop> projeniz .NET Framework 4 (tam) veya daha sonraki bir sürümü hedefliyorsa **araç kutusu** 'nda görüntülenir. Gerekirse, projenizin hedeflediği Framework sürümünü değiştirebilirsiniz.

**Birlikte çalışabilirlik** etkinlik Tasarımcısı, **araç kutusu** 'ndan sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyi üzerinde bırakılabilir <xref:System.Activities.Statements.Sequence> . **Birlikte çalışma** etkinlik Tasarımcısı 'nın atılması, <xref:System.Activities.Statements.Interop> birlikte çalışma için varsayılan **DisplayName** olan bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>Öğesini **birlikte çalışma** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenleyebilirsiniz.

**Bir .NET türü görüntüle ve Seç** iletişim kutusunu açmak Için, **birlikte çalışma** Etkinlik tasarımcısında veya özellik kılavuzunda, **ActivityType** kutusunda bulunan metne gitmek **için tıklayın** . Yalnızca iş akışı 3,0 veya iş akışı 3,5 etkinlikleri için türler gösterilir. Diğer bir deyişle, yalnızca öğesinden türetilmiş türler <xref:System.Workflow.ComponentModel.Activity> gösterilir. Bir tür belirtmek için bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [bir .NET türü Için tarama ve seçme Iletişim kutusu](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Birlikte çalışma özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Interop> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.Interop> . Varsayılan değer **birlikte çalışabilirlik**' dir. Görünen ad gerekli olmasa da, bir tane sağlamanız önerilir.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Doğru|Etkinliğin içerdiği etkinliğin türünü belirtir <xref:System.Activities.Statements.Interop> . Belirtilen bu tür öğesinden türetilmelidir <xref:System.Workflow.ComponentModel.Activity> .|

## <a name="see-also"></a>Ayrıca bkz.

- [Geçiş](../workflow-designer/migration-activity-designers.md)