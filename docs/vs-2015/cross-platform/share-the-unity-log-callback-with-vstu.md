---
title: VSTU ile Unity günlük geri aramasını paylaşma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: b58d693980ffc55ccfe613d52e868bccca9908b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145730"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>VSTU ile Unity Günlük Geri Çağırması paylaşma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Unity için Visual Studio Araçları, kendi konsolunu Visual Studio 'ya akıkabilmek için Unity ile bir günlük geri çağırma kaydeder. Düzenleyici betikleriniz Ayrıca Unity ile bir günlük geri çağırma işlemini kaydettiğinin, VSTU geri çağırması geri çağırmanızı etkileyebilir. Bu olasılığa engel olmak için, bir `VisualStudioIntegration.LogCallback` olayı, VSTU ile birlikte çalışmak üzere kullanın.  
  
## <a name="demonstrates"></a>Gösteriler  
 Unity için Visual Studio Araçları tarafından oluşturulan Unity günlük geri aramasını paylaşma.  
  
## <a name="example"></a>Örnek  
  
```csharp  
using System;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örnek: Proje Dosyası Oluşturma](../cross-platform/customize-project-files-created-by-vstu.md)
