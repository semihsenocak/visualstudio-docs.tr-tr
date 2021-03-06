---
title: '&lt;Assembly &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d619b8b3cd81e5b00fc689077a95ade08f4d7eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183475"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Assembly &gt; öğesi (ClickOnce uygulaması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama bildirimi için en üst düzey öğe.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `assembly`Öğesi kök öğesidir ve gereklidir. İlk kapsanan öğesi bir `assemblyIdentity` öğesi olmalıdır. Bildirim öğeleri şu ad alanlarından birinde olmalıdır:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Derlemenin alt öğeleri de bu ad alanlarında, devralmayla veya etiketlemeyle olmalıdır.  
  
 `assembly`Öğesi aşağıdaki özniteliğe sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`manifestVersion`|Gereklidir. `manifestVersion`Özniteliğin olarak ayarlanması gerekir `1.0` .|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `assembly` bir uygulama için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu kod örneği, [ClickOnce uygulama bildiriminde](../deployment/clickonce-application-manifest.md)sağlanmış daha büyük bir örneğin bir parçasıdır.  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)   
 [\<assembly> Dosyalarında](../deployment/assembly-element-clickonce-deployment.md)
