---
title: ProjectTemplateLink öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6ee9f5d4a162f994cfea4fb3fe620599c1627b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681324"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden fazla projeli bir şablonda, tek bir projenin .vstemplate dosyasının yolunu belirtir.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<ProjectTemplateLink>  
-veya-  
\<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<SolutionFolder>  
 \<ProjectTemplateLink>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectTemplateLink ProjectName="Name">  
    PathToTemplateFile  
</ProjectTemplateLink>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`ProjectName`|İsteğe bağlı öznitelik.<br /><br /> Birden fazla projeli bir şablonda, her bir proje için adı belirtir. **Yeni proje** iletişim kutusu ayrı projelere ad atayamaz.|  
|`CopyParameters`|Ana grup şablonundaki tüm değişkenlerin bağlı şablonların her birine kopyalanmasını sağlar.<br /><br /> Bağlantılı şablonlardaki parametrelerin öneki vardır `"$ext_*$"` . Örneğin, üst grup şablonunda parametresinin `$projectname$` bir **ExampleProject1**değeri varsa, bağlantılı şablon, yürütülmesi için bir değer aldığında, `$ext_projectname$` `$projectname$` üst grup şablonundan parametresinin bir kopyası olan bir parametre alır.<br /><br /> Bu durum, bağlı şablonların, yalnızca üst grup şablonunda rahatlıkla oluşturulabilecek bazı ortak parametreleri paylaşmasına olanak sağlar.<br /><br /> Bu öznitelik isteğe bağlıdır ve dahil olmadığında otomatik olarak varsayılan olarak ayarlanır `false` .<br /><br /> Visual Studio 2013 güncelleştirme 2 ' de kullanıma sunulmuştur. Doğru ürün sürümüne başvurmak için, bkz. [VISUAL STUDIO 2013 SDK güncelleştirme 2 ' de sunulan derlemelere başvuru](https://msdn.microsoft.com/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Birden fazla projeli şablonların içeriğini ve düzenini belirtir.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Birden fazla projeli şablonlardaki projeleri gruplandırır.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Bu metin, şablonun .vstemplate dosyasının yolunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. `ProjectTemplateLink`Öğesi, şablondaki projelerden biri için. vstemplate dosyasının konumunu belirtmek için kullanılır. Çoklu proje şablonunun. vstemplate dosyası `ProjectTemplateLink` şablondaki her proje için bir öğe içeriyor. Çoklu proje şablonları hakkında daha fazla bilgi için bkz. [nasıl yapılır: çoklu proje şablonları oluşturma](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, basit bir çoklu proje kök .vstemplate dosyası gösterilmektedir. Bu örnekte, şablon iki proje içerir `My Windows Application` ve `My Class Library` . `ProjectName`Öğesi üzerindeki özniteliği, `ProjectTemplateLink` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu projeyi atamak için adını ayarlar. `ProjectName`Özniteliği yoksa,. vstemplate dosyasının adı proje adı olarak kullanılır.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Nasıl Yapılır: Birden Çok Proje Şablonu Oluşturma](../ide/how-to-create-multi-project-templates.md)
