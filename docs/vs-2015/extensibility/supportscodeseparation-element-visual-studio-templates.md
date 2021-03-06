---
title: Supportscodeayrım öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd454873fb6a81e66efa99ed68007408f87ff824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160498"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Yeni öğe Ekle** iletişim kutusunda **farklı dosya yerleştir** onay kutusunun etkin olup olmadığını belirtir.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SupportsCodeSeparation>  
  
## <a name="syntax"></a>Syntax  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** ya da **Yeni öğe** iletişim kutusunda nasıl görüntülediğini tanımlar.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Metin `true` , ya da `false` **Yeni öğe Ekle** Iletişim kutusunda **farklı dosya yerleştir** onay kutusunun etkin olup olmadığını belirten bir değer olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `SupportsCodeSeparation` isteğe bağlı bir öğedir. Varsayılan değer: `false`.  
  
 `SupportsCodeSeparation`Öğesi yalnızca Web öğesi şablonları için kullanılabilir.  
  
 Kod ayrımı veya arka plan kod modeli, biçimlendirmeyi bir dosyada ve diğer bir dosyadaki programlama kodunda tutmanıza olanak sağlar. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ve diğer .NET dilleri bu modeli kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, **yer kodunu ayrı dosya** seçeneğinde göstermek için belirtir.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
