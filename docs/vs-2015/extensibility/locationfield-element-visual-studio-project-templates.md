---
title: LocationField öğesi (Visual Studio proje şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b28fe0e696b23724758bd877b6031287290f879e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194468"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField Öğesi (Visual Studio Proje Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Yeni proje** Iletişim kutusundaki **konum** metin kutusunun etkin, devre dışı veya proje şablonu için gizli olup olmadığını belirtir.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<LocationField>  
  
## <a name="syntax"></a>Syntax  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni projede**nasıl görüntüleneceğini tanımlar.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Geçerli metin değerleri şunlardır:  
  
- `Enabled`**Yeni proje** Iletişim kutusunun **konum** kutusunun etkin olduğunu belirtir.  
  
- `Disabled`**Yeni proje** Iletişim kutusunun **konum** kutusunun devre dışı olduğunu belirtir.  
  
- `Hidden`**Yeni proje** Iletişim kutusunun **konum** kutusunun gizlendiğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan değer: `Enabled`.  
  
 **Yeni proje** Iletişim kutusundaki **konum** metin kutusu, kullanıcıların, yeni projelerin kaydedildiği varsayılan dizini değiştirmesine olanak sağlar.  
  
 Öğesinde belirtilen değer `Location` yalnızca temel alınan proje sistemi destekliyorsa iletişim kutusu tarafından kabul edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir şablon için meta verileri gösterir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
