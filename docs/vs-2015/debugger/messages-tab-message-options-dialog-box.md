---
title: İletiler sekmesi, Ileti seçenekleri Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9eb1c88d935fa307e8b86a9a75da423bc08111c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149441"
---
# <a name="messages-tab-message-options-dialog-box"></a>İletiler Sekmesi, İleti Seçenekleri İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İleti [görünümünde](../debugger/messages-view.md)listelemek istediğiniz ileti türlerini seçmek ve ileti arama ölçütlerini belirtmek için **iletiler** sekmesini kullanın. [Ileti seçenekleri Iletişim kutusunu](../debugger/message-options-dialog-box.md)göstermek için **Spy** menüsünde **günlük iletileri** ' ni seçin.  
  
 Genellikle, önce **Ileti grupları**' nı seçin ve ardından **görüntülenecek iletileri**tek tek seçerek seçimi hassas şekilde ayarlayabilirsiniz. All **düğmesi tüm** ileti türlerini seçer ve **hiçbiri** düğmesi tüm türleri temizler.  
  
 **İletiler** sekmesinde aşağıdaki ayarlar kullanılabilir:  
  
 **Görüntülenecek iletiler**  
 Görüntülenecek belirli iletileri seçin. Yeni bir Iletiler penceresi oluşturduğunuzda, tüm iletiler görüntülenebilir. İletileri **iletiler** sekmesinden filtreleyerek, bu filtre yalnızca yeni iletiler için geçerlidir, Windows görünümünde zaten görüntülenmiş iletiler değildir.  
  
 **İleti grupları**  
 Görüntülenecek ileti gruplarını seçin. Kullanılabilir gruplar şunlardır:  
  
- WM_USER: WM_USER büyük veya eşit bir kodla  
  
- Kaydedildi: **RegisterWindowMessage** çağrısıyla kaydedilir  
  
- Bilinmiyor: 0 ile arasında bilinmeyen iletiler (WM_USER – 1)  
  
  Bu **Ileti gruplarının** , **görüntülenecek iletiler**altındaki belirli girdilerle eşlemediğine unutmayın. Bir grup seçtiğinizde, seçim doğrudan ileti akışına uygulanır.  
  
  **Ileti grupları** içindeki gri onay kutusu, görüntülenecek **iletiler** liste kutusunda o gruptaki iletiler için değiştirildiğini belirtir; Bu gruptaki ileti türlerinin hepsi seçili değil.  
  
  **Ayarları varsayılan olarak kaydet**  
  Geçerli ayarları daha sonra ileti arama seçenekleri olarak kullanmak üzere kaydedin. Bu ayarlar, Spy + + ' dan çıkıldığında da kaydedilir.
