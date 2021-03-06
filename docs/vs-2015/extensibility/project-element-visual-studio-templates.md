---
title: Project öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c9708bb8c35e66199aaf3665883307e48a63c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193972"
---
# <a name="project-element-visual-studio-templates"></a>Project Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projeye eklenecek dosyaları veya dizinleri belirtir.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Project>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`File`|Gerekli öznitelik.<br /><br /> Şablon. zip dosyasındaki proje dosyasının adını belirtir.|  
|`ReplaceParameters`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda proje dosyasında değiştirilmesini gerektiren parametre değerleri olup olmadığını belirten bir Boolean değer. Varsayılan değer `false` .|  
|`TargetFileName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda proje dosyasının adını belirtir.|  
|`IgnoreProjectParameter`|İsteğe bağlı öznitelik.<br /><br /> Projenin geçerli çözüme eklenip eklenmeyeceğini belirtir. "$*MyCustomParameter*$" özel parametresinin değeri parametre değiştirme dosyasında mevcutsa, proje oluşturulur ancak şu anda açık olan çözümün parçası olarak eklenmez.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Klasör](../extensibility/folder-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeye eklenecek klasörü belirtir.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeye eklenecek bir dosya belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Project` , öğesinin isteğe bağlı bir alt öğesidir `TemplateContent` .  
  
 `Project`Öğesi bir proje belirtmek için kullanılır ve bu nedenle yalnızca proje şablonlarında geçerlidir.  
  
 `Project` öğeler [klasör](../extensibility/folder-element-visual-studio-project-templates.md) alt öğeleri veya [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) alt öğeleri olabilir, ancak hem hem de `Folder` alt öğelerinin bir karışımını içermez `ProjectItem` .  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Yeni proje** iletişim kutusunda Kullanıcı tarafından girilen ada göre proje dosya adını otomatik olarak yeniden adlandırır. `TargetFileName`Şablonuyla oluşturulan proje dosyaları için alternatif bir dosya adı sağlamak istiyorsanız özniteliğini kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama için bir proje şablonu meta verilerini gösterir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [ProjectItem öğesi (Visual Studio proje şablonları)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder Öğesi (Visual Studio Proje Şablonları)](../extensibility/folder-element-visual-studio-project-templates.md)
