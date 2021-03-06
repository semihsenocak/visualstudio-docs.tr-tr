---
title: 'Yeni proje oluşturma: devlet, Ikinci bölüm | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6643c52ff8e5801c562524e99c4e3f03c00f74b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687499"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Yeni Proje Oluşturma: Arka Plan, 2. Bölüm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[Yeni proje oluşturma bölümünde: birinci bölüm bölümünde](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) **Yeni proje** iletişim kutusunun nasıl doldurulduğu gördünüz. Bir **Visual C# Windows uygulaması**seçtiğinizi, **ad** ve **konum** metin kutularını doldurduktan ve Tamam ' a tıkladığınızı varsayalım.  
  
## <a name="generating-the-solution-files"></a>Çözüm dosyalarını oluşturma  
 Uygulama şablonu seçme [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , unzip ve ilgili. vstemplate dosyasını açmak ve bu DOSYADAKI xml komutlarını yorumlamak için bir şablon başlatmak üzere yönlendirir. Bu komutlar yeni veya mevcut çözümde projeler ve proje öğeleri oluşturur.  
  
 Şablon,. vstemplate dosyasını tutan aynı. zip klasöründen öğe şablonları olarak adlandırılan kaynak dosyalarını kaldırır. Şablon bu dosyaları yeni projeye kopyalar ve bunları uygun şekilde özelleştiriliyor. Proje ve öğe şablonlarına genel bir bakış için bkz. [nib: Visual Studio şablonları](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Şablon parametresi değiştirme  
 Şablon bir öğe şablonunu yeni bir projeye kopyaladığında, dosyayı özelleştirmek için tüm şablon parametrelerini dizeler ile değiştirir. Şablon parametresi, önce ve ardından dolar işareti (örneğin, $date $) gelen özel bir belirteçtir.  
  
 Tipik bir proje öğesi şablonuna göz atalım. Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründe Program.cs ayıklayın ve inceleyin.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Basit adlı yeni bir Windows uygulaması projesi oluşturursanız, şablon `$safeprojectname$` parametresini projenin adıyla değiştirir.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Şablon parametrelerinin tüm listesi için bkz. [şablon parametreleri](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Içindeki bir görünüm. VSTemplate dosyası  
 Temel bir. vstemplate dosyası bu biçime sahiptir  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 \<TemplateData>Yeni proje oluşturma bölümündeki bölümüne baktık [: birinci bölüm, birinci](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)bölüm. Bu bölümdeki Etiketler **Yeni proje** iletişim kutusunun görünümünü denetlemek için kullanılır.  
  
 \<TemplateContent>Bölümdeki Etiketler yeni projelerin ve proje öğelerinin oluşturulmasını denetler. \<TemplateContent>\Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründeki cswindowsapplication. vstemplate dosyasının bölümü aşağıda verilmiştir.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 \<Project>Etiketi bir projenin neslini denetler ve \<ProjectItem> etiketi bir proje öğesinin oluşturulmasını denetler. ReplaceParameters parametresi true ise, şablon proje dosyasındaki veya öğedeki tüm şablon parametrelerini özelleştirecek. Bu durumda, ayarlar. ayarlar dışında tüm proje öğeleri özelleştirilir.  
  
 TargetFileName parametresi, sonuçta elde edilen proje dosyasının veya öğesinin adını ve göreli yolunu belirtir. Bu, projeniz için bir klasör yapısı oluşturmanızı sağlar. Bu bağımsız değişkeni belirtmezseniz, proje öğesi proje öğesi şablonuyla aynı ada sahip olacaktır.  
  
 Ortaya çıkan Windows uygulama klasörü yapısı şöyle görünür:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Şablondaki ilk ve tek \<Project> etiket şunu okur:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Bu, yeni proje şablonuna, WindowsApplication. csproj şablon öğesini kopyalayarak ve özelleştirerek basit. csproj proje dosyası oluşturmasını söyler.  
  
### <a name="designers-and-references"></a>Tasarımcılar ve başvurular  
 Çözüm Gezgini Özellikler klasörünün mevcut olduğunu ve beklenen dosyaları içerdiğini görebilirsiniz. Ancak Resources.Designer.cs to resources. resx ve Form1.Designer.cs to Form1.cs gibi proje başvuruları ve tasarımcı dosya bağımlılıkları hakkında ne olacak?  Bunlar, oluşturulduğu sırada basit. csproj dosyasında ayarlanır.  
  
 İşte \<ItemGroup> proje başvurularını oluşturan Simple. csproj.  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Bunların Çözüm Gezgini görüntülenen altı proje başvurusu olduğunu görebilirsiniz. Diğer bir bölümü aşağıda verilmiştir \<ItemGroup> . Birçok kod satırı açıklık için silindi. Bu bölüm, Settings.Designer.cs ayarlarına bağımlı hale getirir. Ayarlar:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeni Proje Oluşturma: Arka Plan, 1. Bölüm](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBUILD](../../msbuild/msbuild.md)
