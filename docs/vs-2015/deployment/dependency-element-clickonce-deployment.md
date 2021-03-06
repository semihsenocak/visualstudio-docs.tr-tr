---
title: '&lt;Dependency &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f191b11dfce5b3877d0a31e260e092000a556a5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187777"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;Dependency &gt; öğesi (ClickOnce dağıtımı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yüklenecek uygulamanın sürümünü ve uygulama bildiriminin konumunu tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
      <hash>  
         <dsig:Transforms>  
            <dsig:Transform  
                Algorithm  
            />  
         </dsig:Transforms>  
         <dsig:DigestMethod />  
         <dsig:DigestValue>  
         </dsig:DigestValue>  
      </hash>  
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `dependency`Öğe gereklidir. Hiç özniteliği yok. Dağıtım bildiriminde birden fazla öğe olabilir `dependency` .  
  
 `dependency`Öğesi genellikle bir uygulama içinde yer alan derlemelerdeki ana uygulamanın bağımlılıklarını ifade eder [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Main.exe uygulamanız DotNetAssembly.dll adlı bir derlemeyi kullanıyorsa, bu derlemenin bir bağımlılık bölümünde listelenmesi gerekir. Ancak bağımlılık, ortak dil çalışma zamanının belirli bir sürümünde, genel derleme önbelleğindeki (GAC) bir derlemede veya bir COM nesnesinde bağımlılıklar gibi diğer bağımlılıklar türlerini de ifade edebilir. Dokunma gerektirmeyen bir dağıtım teknolojisi olduğundan, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bu tür bağımlılıkların indirilmesini ve yüklenmesini başlatamaz, ancak belirtilen bağımlılıklardan biri veya daha fazlası yoksa uygulamanın çalışmasını önler.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Gereklidir. Bu öğe öğesi içerir `assemblyIdentity` . Aşağıdaki tabloda, desteklediği öznitelikler gösterilmektedir `dependentAssembly` .  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`preRequisite`|İsteğe bağlı. Bu derlemenin GAC 'de zaten var olması gerektiğini belirtir. Geçerli değerler `true` ve ' dir `false` . `true`Ve belirtilen derleme GAC 'de yoksa, uygulama çalıştırılamaz.|  
|`visible`|İsteğe bağlı. Bağımlılıkları da dahil olmak üzere en üst düzey uygulama kimliğini tanımlar. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulama depolamayı ve etkinleştirmeyi yönetmek için tarafından dahili olarak kullanılır.|  
|`dependencyType`|Gereklidir. Bu bağımlılık ve uygulama arasındaki ilişki. Geçerli değerler:<br /><br /> -   `install`. Bileşen geçerli uygulamadan ayrı bir yüklemeyi temsil eder.<br />-   `preRequisite`. Bileşen geçerli uygulama için gereklidir.|  
|`codebase`|İsteğe bağlı. Uygulama bildiriminin tam yolu.|  
|`size`|İsteğe bağlı. Uygulama bildiriminin bayt cinsinden boyutu.|  
  
## <a name="assemblyidentity"></a>AssemblyIdentity  
 Gereklidir. Bu öğe, öğesinin bir alt öğesidir `dependentAssembly` . İçeriği, `assemblyIdentity` uygulama bildiriminde açıklananla aynı olmalıdır [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Aşağıdaki tablo, öğesinin özniteliklerini gösterir `assemblyIdentity` .  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gereklidir. Uygulamanın adını tanımlar.|  
|`Version`|Gereklidir. Uygulamanın sürüm numarasını aşağıdaki biçimde belirtir: `major.minor.build.revision`|  
|`publicKeyToken`|Gereklidir. Uygulamanın veya derlemenin imzalandığı ortak anahtarın SHA-1 karmasının son 8 baytını temsil eden 16 karakterlik bir onaltılık dize belirtir. İmzalamak için kullanılan ortak anahtar 2048 bit veya daha büyük olmalıdır.|  
|`processorArchitecture`|Gereklidir. Mikroişlemciyi belirtir. Geçerli değerler `x86` 32 bitlik Windows ve `IA64` 64 bit Windows içindir.|  
|`Language`|İsteğe bağlı. Derlemenin iki bölüm dil kodunu tanımlar. Örneğin, EN-US, Ingilizce (ABD) anlamına gelir. Varsayılan değer: `neutral`. Bu öğe `asmv2` ad alanıdır.|  
|`type`|İsteğe bağlı. Windows yan yana yüklemesi teknolojisi ile geriye dönük uyumluluk için. İzin verilen tek değer `win32` .|  
  
## <a name="hash"></a>hash  
 `hash`Öğesi, öğesinin isteğe bağlı bir alt öğesidir `file` . `hash`Öğesinde hiç öznitelik yok.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] herhangi bir dosyanın dağıtımdan sonra değişmediğinden emin olmak için bir uygulamadaki tüm dosyaların algoritmik karmasını güvenlik denetimi olarak kullanır. `hash`Öğe dahil değilse, bu denetim gerçekleştirilmez. Bu nedenle, `hash` öğesinin atlanması önerilmez.  
  
## <a name="dsigtransforms"></a>dsig: dönüşümler  
 `dsig:Transforms`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . `dsig:Transforms`Öğesinde hiç öznitelik yok.  
  
## <a name="dsigtransform"></a>dsig: dönüştürme  
 `dsig:Transform`Öğesi, öğesinin gerekli bir alt öğesidir `dsig:Transforms` . Aşağıdaki tablo, öğesinin özniteliklerini gösterir `dsig:Transform` .  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Algorithm`|Bu dosya için Özeti hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
## <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 `dsig:DigestMethod`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . Aşağıdaki tablo, öğesinin özniteliklerini gösterir `dsig:DigestMethod` .  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Algorithm`|Bu dosya için Özeti hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 `dsig:DigestValue`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . `dsig:DigestValue`Öğesinde hiç öznitelik yok. Metin değeri, belirtilen dosya için hesaplanan karmadır.  
  
## <a name="remarks"></a>Açıklamalar  
 Dağıtım bildirimlerinin genellikle `assemblyIdentity` uygulama bildiriminin adını ve sürümünü tanımlayan tek bir öğesi vardır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir `dependency` dağıtım bildiriminde bir öğe gösterilmektedir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği GAC 'de zaten yüklü olan bir derlemeye bağımlılığı belirtir.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ortak dil çalışma zamanının belirli bir sürümü için bir bağımlılık belirtir.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir işletim sistemi bağımlılığını belirtir.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency> Dosyalarında](../deployment/dependency-element-clickonce-application.md)
