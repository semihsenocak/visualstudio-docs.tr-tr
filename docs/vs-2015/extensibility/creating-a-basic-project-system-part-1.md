---
title: Temel proje sistemi oluşturma, Bölüm 1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20637fb47d85b7cb8341df22d056ffe44534835f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295487"
---
# <a name="creating-a-basic-project-system-part-1"></a>Temel Proje Sistemi Oluşturma, Bölüm 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, projeler, geliştiricilerin kaynak kodu dosyalarını ve diğer varlıkları düzenlemek için kullandığı kapsayıcılardır. Projeler **Çözüm Gezgini**çözümlerin alt öğeleri olarak görünür. Projeler, kaynak kodu düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza, Web Hizmetleri, veritabanları ve diğer kaynaklara başvurular oluşturmanıza imkan tanır.  
  
 Projeler proje dosyalarında tanımlanır, örneğin bir Visual C# projesi için. csproj dosyası. Kendi proje dosya adı uzantınıza sahip olan kendi proje türünü de oluşturabilirsiniz. Proje türleri hakkında daha fazla bilgi için bkz. [Proje türleri](../extensibility/internals/project-types.md).  
  
> [!NOTE]
> Visual Studio 'Yu özel bir proje türüyle genişletmenize gerek duyuyorsanız, sıfırdan bir proje sistemi oluşturma konusunda birçok avantaj içeren [Visual Studio proje sisteminin](https://github.com/Microsoft/VSProjectSystem) kullanılmasını önemle öneririz:  
> 
> - Daha kolay ekleme.  Temel bir proje sistemi bile on binlerce satır kod gerektirir.  CPS 'yi kullanmak, ekleme maliyetini gereksinimlerinize göre özelleştirmeye başlamadan önce birkaç tıklamayla azaltır.  
>   - Daha kolay bakım.  CPS 'den yararlanarak yalnızca kendi senaryolarınızı korumanız gerekir.  Tüm proje sistemi altyapısının sürekli tutulmasını yaptık.  
> 
>   Visual Studio 'nun Visual Studio 2013 'den eski sürümlerini hedefliyorsanız, Visual Studio uzantısında CPS 'den yararlanabilemeyeceksiniz.  Böyle bir durum söz konusu olduğunda bu izlenecek yol, başlamak için iyi bir yerdir.  
  
 Bu izlenecek yol, proje dosya adı uzantısına sahip bir proje türünün nasıl oluşturulacağını gösterir. myproj. Bu, var olan Visual C# Proje sisteminden boratır izlenecek yolu.  
  
> [!NOTE]
> Tam dil projesi sisteminin uçtan uca bir örneği için bkz. [VSSDK örnekleri](../misc/vssdk-samples.md)Içindeki IronPython örnek derin açıklaması.  
  
 Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:  
  
- Temel proje türü oluşturun.  
  
- Temel bir proje şablonu oluşturun.  
  
- Proje şablonunu Visual Studio ile kaydedin.  
  
- **Yeni proje** iletişim kutusunu açıp şablonunuzu kullanarak bir proje örneği oluşturun.  
  
- Proje sisteminiz için bir proje fabrikası oluşturun.  
  
- Proje sisteminiz için bir proje düğümü oluşturun.  
  
- Proje sistemi için özel simgeler ekleyin.  
  
- Temel şablon parametre değişimini uygulayın.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Ayrıca, [Projeler Için yönetilen paket çerçevesi](https://archive.codeplex.com/?p=mpfproj12)için kaynak kodunu da indirmeniz gerekir. Dosyayı oluşturacağınız çözümün erişebileceği bir konuma ayıklayın.  
  
## <a name="creating-a-basic-project-type"></a>Temel proje türü oluşturma  
 **SimpleProject**ADLı BIR C# VSIX projesi oluşturun. (**Dosya, yeni, proje** ve ardından **C#, genişletilebilirlik, Visual Studio paketi**). Visual Studio Package proje öğesi şablonu ekleyin (Çözüm Gezgini, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin, ardından **genişletilebilirlik/Visual Studio paketine**gidin). Dosyayı **Simpleprojectpackage**olarak adlandırın.  
  
## <a name="creating-a-basic-project-template"></a>Temel proje şablonu oluşturma  
 Şimdi, yeni. myproj proje türünü uygulamak için bu temel VSPackage 'ı değiştirebilirsiniz. . Myproj proje türünü temel alan bir proje oluşturmak için, Visual Studio 'nun hangi dosyaları, kaynakları ve başvuruları yeni projeye ekleneceğini bilmeleri gerekir. Bu bilgileri sağlamak için proje dosyalarını bir proje şablonu klasörüne koyun. Bir Kullanıcı bir proje oluşturmak için. myproj projesini kullandığında, dosyalar yeni projeye kopyalanır.  
  
#### <a name="to-create-a-basic-project-template"></a>Temel proje şablonu oluşturmak için  
  
1. Projeye bir tane olmak üzere üç klasör ekleyin: **Templates\projeler** ( **Çözüm Gezgini**, **SimpleProject** proje düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni klasör**' e tıklayın. Klasörü adlandırın `Templates` . **Şablonlar** klasöründe adlı bir klasör ekleyin `Projects` . **Projeler** klasöründe adlı bir klasör ekleyin `SimpleProject` .)  
  
2. **Projeler\simpleproject** klasöründe adlı bir simge dosyası ekleyin `SimpleProject.ico` . **Ekle**' ye tıkladığınızda, simge Düzenleyicisi açılır.  
  
3. Simgeyi farklı yapın. Bu simge, izlenecek yolun ilerleyen kısımlarında yer alacak **Yeni proje** iletişim kutusunda görünür.  
  
    ![Basit proje simgesi](../extensibility/media/simpleprojicon.png "Simpleprojıcon")  
  
4. Simgeyi kaydedin ve simge düzenleyicisini kapatın.  
  
5. **Projeler\simpleproject** klasöründe adlı bir **sınıf** öğesi ekleyin `Program.cs` .  
  
6. Mevcut kodu aşağıdaki satırlarla değiştirin.  
  
   ```csharp  
   using System;  
   using System.Collections.Generic;  
   using System.Text;  
  
   namespace $nameSpace$  
   {  
       public class $className$  
       {  
           static void Main(string[] args)  
           {  
               Console.WriteLine("Hello VSX!!!");  
               Console.ReadKey();  
           }  
       }  
   }  
   ```  
  
   > [!IMPORTANT]
   > Bu, Program.cs kodunun son formu değildir; değiştirme parametreleri sonraki bir adımda ele alınacaktır. Derleme hataları görebilirsiniz, ancak dosyanın **Builkaction** **içeriği**olduğu sürece projeyi her zamanki gibi derleyip çalıştırabilirsiniz.  
  
7. Dosyayı kaydedin.  
  
8. AssemblyInfo.cs dosyasını **Özellikler** klasöründen, **projelerprojem proje** klasörüne kopyalayın.  
  
9. **Projeler\simpleproject** klasöründe ADLı bir XML dosyası ekleyin `SimpleProject.myproj` .  
  
   > [!NOTE]
   > Bu türden tüm projeler için dosya adı uzantısı. myproj ' dir. Bunu değiştirmek istiyorsanız, izlenecek yolda bahsedilen her yerde değiştirmeniz gerekir.  
  
10. Mevcut içeriği aşağıdaki satırlarla değiştirin.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
11. Dosyayı kaydedin.  
  
12. **Özellikler** penceresinde, AssemblyInfo.cs, program.cs, SimpleProject. ICO ve SimpleProject. myproj öğesinin **Build eylemini** **Content**olarak ayarlayın ve **VSIX özellikleri içindeki Include** değerlerini **true**olarak ayarlayın.  
  
    Bu proje şablonu, hem hata ayıklama yapılandırması hem de sürüm yapılandırması olan temel bir Visual C# projesi tanımlar. Proje iki kaynak dosyası, AssemblyInfo.cs ve Program.cs ve çeşitli derleme başvuruları içerir. Şablondan bir proje oluşturulduğunda, Projectguıd değeri otomatik olarak yeni bir GUID ile değiştirilmiştir.  
  
    **Çözüm Gezgini**, genişletilmiş **Şablonlar** klasörü aşağıdaki gibi görünmelidir:  
  
    Şablonlar  
  
    Projeler  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject. ico  
  
    SimpleProject. myproj  
  
## <a name="creating-a-basic-project-factory"></a>Temel proje fabrikası oluşturma  
 Visual Studio 'nun proje şablonu klasörünüzün konumunu söylemeniz gerekir. Bunu yapmak için, VSPackage oluşturulduğunda şablon konumunun sistem kayıt defterine yazılması için, VSPackage sınıfına proje fabrikası uygulayan bir öznitelik ekleyin. Bir proje fabrikası GUID 'ı tarafından tanımlanan temel bir proje fabrikası oluşturarak başlayın. <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>Proje fabrikasını SimpleProjectPackage sınıfına bağlamak için özniteliğini kullanın.  
  
#### <a name="to-create-a-basic-project-factory"></a>Temel bir proje fabrikası oluşturmak için  
  
1. Kod düzenleyicisinde SimpleProjectPackageGuids.cs öğesini açın.  
  
2. Proje fabrikanızın GUID 'Leri oluşturun ( **Araçlar** menüsünde **GUID oluştur**' a tıklayın) veya aşağıdaki örnekteki birini kullanın. GUID 'Leri Simpleprojectpackageguıd sınıfına ekleyin. GUID 'Ler hem GUID biçiminde hem de dize biçiminde olmalıdır. Elde edilen kod aşağıdaki örneğe benzemelidir.  
  
   ```  
   static class SimpleProjectPackageGuids  
   {  
       public const string guidSimpleProjectPkgString =   
           "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
       public const string guidSimpleProjectCmdSetString =   
           "72c23e1d-f389-410a-b5f1-c938303f1391";  
       public const string guidSimpleProjectFactoryString =   
           "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
       public static readonly Guid guidSimpleProjectCmdSet =   
           new Guid(guidSimpleProjectCmdSetString);  
       public static readonly Guid guidSimpleProjectFactory =   
           new Guid(guidSimpleProjectFactoryString);  
   }  
   ```  
  
3. Adlı üst **SimpleProject** klasörüne bir sınıf ekleyin `SimpleProjectFactory.cs` .  
  
4. Deyimleri kullanarak aşağıdakileri ekleyin:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. SimpleProjectFactory sınıfına bir Guid özniteliği ekleyin. Özniteliğin değeri, yeni proje fabrikası GUID 'sidir.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   Artık proje şablonunuzu kaydedebilirsiniz.  
  
#### <a name="to-register-the-project-template"></a>Proje şablonunu kaydetmek için  
  
1. SimpleProjectPackage.cs içinde, <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> SimpleProjectPackage sınıfına aşağıdaki gibi bir öznitelik ekleyin.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.  
  
    Yeniden derleme proje şablonunu kaydeder.  
  
   Parametreler `defaultProjectExtension` ve `possibleProjectExtensions` Proje dosya adı uzantısına ayarlanır (. Myproj). `projectTemplatesDirectory`Parametresi, Şablonlar klasörünün göreli yoluna ayarlanır. Derleme sırasında, bu yol tam bir yapıya dönüştürülür ve proje sistemini kaydetmek için kayıt defterine eklenir.  
  
## <a name="testing-the-template-registration"></a>Şablon kaydını test etme  
 Şablon kaydı, Visual Studio 'Ya proje şablonu klasörünüzün konumunu söyler, böylece Visual Studio **Yeni proje** iletişim kutusunda şablon adı ve simgesini görüntüleyebilir.  
  
#### <a name="to-test-the-template-registration"></a>Şablon kaydını test etmek için  
  
1. Visual Studio 'nun deneysel örneğinde hata ayıklamaya başlamak için F5 'e basın.  
  
2. Deneysel örnekte, yeni oluşturulan proje türünden yeni bir proje oluşturun. **Yeni proje** iletişim kutusunda, **yüklü şablonlar**altında **SimpleProject** ' i görmeniz gerekir.  
  
   Artık kayıtlı bir proje fabrikasına sahipsiniz. Ancak, henüz bir proje oluşturamaz. Proje paketi ve proje fabrikası bir proje oluşturmak ve başlatmak için birlikte çalışır.  
  
## <a name="add-the-managed-package-framework-code"></a>Yönetilen paket çerçevesi kodunu ekleyin  
 Proje paketiyle proje fabrikası arasındaki bağlantıyı uygulayın.  
  
- Yönetilen paket çerçevesi için kaynak kodu dosyalarını içeri aktarın.  
  
    1. SimpleProject projesini kaldırın ( **Çözüm Gezgini**, proje düğümünü seçin ve bağlam menüsünde **Projeyi Kaldır**' a tıklayın.) ve proje dosyasını XML düzenleyicisinde açın.  
  
    2. Aşağıdaki blokları proje dosyasına ekleyin (blokların hemen üzerinde \<Import> ). ProjectBasePath öğesini, indirdiğiniz yönetilen paket çerçeve kodundaki ProjectBase. Files dosyasının konumuna ayarlayın. Yol adına bir ters eğik çizgi eklemeniz gerekebilir. Bunu yapmazsanız, proje yönetilen paket çerçevesi kodunu bulamamasına neden olabilir.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        > Yolun sonundaki ters eğik çizgiyi unutmayın.  
  
    3. Projeyi yeniden yükleyin.  
  
    4. Aşağıdaki derlemelere başvurular ekleyin:  
  
        - Microsoft. VisualStudio. Designer. Interfaces ( \<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        - WindowsBase  
  
        - Microsoft. Build. Tasks. v 4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Proje fabrikasını başlatmak için  
  
1. SimpleProjectPackage.cs dosyasında aşağıdaki `using` ifadeyi ekleyin.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. Sınıfından türet `SimpleProjectPackage` `Microsoft.VisualStudio.Package.ProjectPackage` .  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. Proje fabrikasını kaydedin. Yöntemine hemen sonra aşağıdaki satırı ekleyin `SimpleProjectPackage.Initialize` `base.Initialize` .  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4. Soyut özelliği uygulayın `ProductUserContext` :  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5. SimpleProjectFactory.cs ' de, `using` mevcut deyimlerden sonra aşağıdaki deyimi ekleyin `using` .  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. Sınıfından türet `SimpleProjectFactory` `ProjectFactory` .  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. Aşağıdaki kukla yöntemi `SimpleProjectFactory` sınıfına ekleyin. Bu yöntemi sonraki bir bölümde uygulayacaksınız.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. Sınıfına aşağıdaki alanı ve oluşturucuyu ekleyin `SimpleProjectFactory` . Bu `SimpleProjectPackage` başvuru, bir hizmet sağlayıcı sitesi ayarlamakta kullanılabilmesi için özel bir alanda önbelleğe alınır.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.  
  
## <a name="testing-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etme  
 Proje fabrikası uygulamanızın oluşturucusunun adlandırılıp çağrılmadığını test edin.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etmek için  
  
1. SimpleProjectFactory.cs dosyasında, oluşturucunun aşağıdaki satırında bir kesme noktası ayarlayın `SimpleProjectFactory` .  
  
    ```  
    this.package = package;  
    ```  
  
2. Visual Studio 'nun deneysel bir örneğini başlatmak için F5 tuşuna basın.  
  
3. Deneysel örnekte, yeni bir proje oluşturmaya başlayın. **Yeni proje** iletişim kutusunda, SimpleProject proje türünü seçin ve ardından **Tamam**' a tıklayın. Yürütme kesme noktasında durmaktadır.  
  
4. Kesme noktasını temizle ve hata ayıklamayı Durdur. Henüz bir proje düğümü oluşturmadınız, proje oluşturma kodu hala özel durumlar oluşturuyor.  
  
## <a name="extending-the-project-node-class"></a>Proje düğümü sınıfını genişletme  
 Artık `SimpleProjectNode` sınıfından türeten sınıfını uygulayabilirsiniz `ProjectNode` . `ProjectNode`Temel sınıf, proje oluşturma için aşağıdaki görevleri işler:  
  
- SimpleProject. myproj proje şablon dosyasını yeni proje klasörüne kopyalar. Kopya, **Yeni proje** iletişim kutusuna girilen ada göre yeniden adlandırılır. `ProjectGuid`Özellik değeri yeni BIR GUID ile değiştirilmiştir.  
  
- , SimpleProject. myproj proje şablon dosyasının MSBuild öğelerine erişir ve `Compile` öğeleri arar. Her `Compile` hedef dosya için dosyayı yeni proje klasörüne kopyalar.  
  
  Türetilmiş `SimpleProjectNode` sınıf şu görevleri gerçekleştirir:  
  
- **Çözüm Gezgini** veya seçilmesi için proje ve dosya düğümlerinin simgelerini sağlar.  
  
- Ek proje şablonu parametre değişimlerin belirtilmesini sağlar.  
  
#### <a name="to-extend-the-project-node-class"></a>Proje düğümü sınıfını genişletmek için  
  
1. 
  
2. Adlı bir sınıf ekleyin `SimpleProjectNode.cs` .  
  
3. Mevcut kodu aşağıdaki kodla değiştirin.  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Project;  
  
   namespace SimpleProject  
   {  
       public class SimpleProjectNode : ProjectNode  
       {  
           private SimpleProjectPackage package;  
  
           public SimpleProjectNode(SimpleProjectPackage package)  
           {  
               this.package = package;  
           }  
           public override Guid ProjectGuid  
           {  
               get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
           }  
           public override string ProjectType  
           {  
               get { return "SimpleProjectType"; }  
           }  
  
           public override void AddFileFromTemplate(  
               string source, string target)  
           {  
               this.FileTemplateProcessor.UntokenFile(source, target);  
               this.FileTemplateProcessor.Reset();  
           }  
       }  
   }  
   ```  
  
   Bu `SimpleProjectNode` sınıf uygulamasında bu geçersiz kılınan yöntemler vardır:  
  
- `ProjectGuid`, proje fabrikası GUID 'sini döndürür.  
  
- `ProjectType`, proje türünün yerelleştirilmiş adını döndürür.  
  
- `AddFileFromTemplate`Seçili dosyaları şablon klasöründen hedef projeye kopyalayan. Bu yöntem daha sonraki bir bölümde daha da uygulanabilir.  
  
  Oluşturucu `SimpleProjectNode` gibi Oluşturucu, `SimpleProjectFactory` `SimpleProjectPackage` daha sonra kullanılmak üzere bir özel alanda bir başvuruyu önbelleğe alır.  
  
  `SimpleProjectFactory`Sınıfı sınıfa bağlamak için `SimpleProjectNode` , yönteminde yeni bir örneği oluşturmanız `SimpleProjectNode` `SimpleProjectFactory.CreateProject` ve daha sonra kullanmak üzere özel bir alanda önbelleğe almanız gerekir.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Project Factory sınıfını ve Node sınıfını bağlamak için  
  
1. SimpleProjectFactory.cs dosyasında aşağıdaki `using` ifadeyi ekleyin:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. `SimpleProjectFactory.CreateProject`Aşağıdaki kodu kullanarak yöntemini değiştirin.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.  
  
## <a name="testing-the-project-node-class"></a>Proje düğümü sınıfını test etme  
 Proje fabrikasını bir proje hiyerarşisi oluşturup oluşturmadığını görmek için test edin.  
  
#### <a name="to-test-the-project-node-class"></a>Proje düğümü sınıfını test etmek için  
  
1. Hata ayıklamaya başlamak için F5'e basın. Deneysel örnekte, yeni bir SimpleProject oluşturun.  
  
2. Visual Studio proje oluşturmak için proje fabrikasını çağırmalıdır.  
  
3. Visual Studio 'nun Deneysel örneğini kapatın.  
  
## <a name="adding-a-custom-project-node-icon"></a>Özel proje düğümü simgesi ekleme  
 Önceki bölümdeki proje düğümü simgesi varsayılan simgedir. Bunu özel bir simge olarak değiştirebilirsiniz.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Özel bir proje düğümü simgesi eklemek için  
  
1. **Kaynaklar** klasöründe SimpleProjectNode.bmp adlı bir bit eşlem dosyası ekleyin.  
  
2. **Özellikler** penceresinde bit eşlemi 16 ile 16 piksel azaltın. Bit eşlemi farklı hale getirin.  
  
    ![Basit proje Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. **Özellikler** penceresinde, bit eşlemin **derleme eylemini** **katıştırılmış kaynak**olarak değiştirin.  
  
4. SimpleProjectNode.cs içinde aşağıdaki `using` deyimleri ekleyin:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Sınıfına aşağıdaki static alanı ve oluşturucuyu ekleyin `SimpleProjectNode` .  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Aşağıdaki özelliği sınıfının başına ekleyin `SimpleProjectNode` .  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Örnek oluşturucusunu aşağıdaki kodla değiştirin.  
  
   ```  
   public SimpleProjectNode(SimpleProjectPackage package)  
   {  
       this.package = package;  
  
       imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
       foreach (Image img in imageList.Images)  
       {  
           this.ImageHandler.AddImage(img);  
       }  
   }  
   ```  
  
   Statik oluşturma sırasında, `SimpleProjectNode` derleme bildirim kaynaklarından proje düğümü bit eşlemini alır ve daha sonra kullanmak üzere özel bir alanda önbelleğe alır. Görüntü yolunun söz dizimine dikkat edin <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> . Bir derlemeye gömülü olan bildirim kaynaklarının adlarını görmek için <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> yöntemini kullanın. Bu yöntem `SimpleProject` derlemeye uygulandığında, sonuçlar aşağıdaki gibi olmalıdır:  
  
- SimpleProject. resources. resources  
  
- VisualStudio. Project. resources  
  
- SimpleProject. VSPackage. resources  
  
- Resources.imagelis.bmp  
  
- Microsoft. VisualStudio. Project. DontShowAgainDialog. resources  
  
- Microsoft. VisualStudio. Project. SecurityWarningDialog. resources  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  Örnek oluşturma sırasında, `ProjectNode` temel sınıf, Resources\imagelis.bmp, yaygın olarak kullanılan 16 x 16 bit eşlem olan Resources.imagelis.bmp yükler. Bu bit eşlem listesi `SimpleProjectNode` ImageHandler. ImageList olarak kullanılabilir hale getirilir. `SimpleProjectNode` proje düğümü bit eşlemini listeye ekler. Görüntü listesindeki proje düğümü bit eşleminin boşluğu daha sonra public özelliğinin değeri olarak kullanılmak üzere önbelleğe alınır `ImageIndex` . Visual Studio, proje düğümü simgesi olarak hangi bit eşlemin gösterileceğini öğrenmek için bu özelliği kullanır.  
  
## <a name="testing-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etme  
 Özel proje düğümünüz simgenizi içeren bir proje hiyerarşisi oluşturup oluşturmadığını görmek için proje fabrikasını test edin.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etmek için  
  
1. Hata ayıklamayı başlatın ve deneysel örnekte yeni bir SimpleProject oluşturun.  
  
2. Yeni oluşturulan projede SimpleProjectNode.bmp proje düğümü simgesi olarak kullanıldığına dikkat edin.  
  
     ![Basit proje yeni proje düğümü](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3. Kod düzenleyicisinde Program.cs dosyasını açın. Aşağıdaki koda benzer kaynak kodu görmeniz gerekir.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     $NameSpace $ ve $className $ şablon parametrelerinin yeni değerlere sahip olmadığına dikkat edin. Bir sonraki bölümde şablon parametre değişimini nasıl uygulayacağınızı öğreneceksiniz.  
  
## <a name="substituting-template-parameters"></a>Şablon parametrelerini değiştirme  
 Önceki bir bölümde, özniteliğini kullanarak proje şablonunu Visual Studio ile kaydettiniz `ProvideProjectFactory` . Bir şablon klasörünün yolunu bu şekilde kaydetme, sınıfı geçersiz kılarak ve genişleterek temel şablon parametre değişimini etkinleştirmenizi sağlar `ProjectNode.AddFileFromTemplate` . Daha fazla bilgi için bkz. [Yeni proje oluşturma: Ikinci bölüm altında](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Şimdi sınıfa değiştirme kodu ekleyin `AddFileFromTemplate` .  
  
#### <a name="to-substitute-template-parameters"></a>Şablon parametrelerini koymak için  
  
1. SimpleProjectNode.cs dosyasında aşağıdaki `using` ifadeyi ekleyin.  
  
   ```  
   using System.IO;  
   ```  
  
2. `AddFileFromTemplate`Aşağıdaki kodu kullanarak yöntemini değiştirin.  
  
   ```  
   public override void AddFileFromTemplate(  
       string source, string target)  
   {  
       string nameSpace =   
           this.FileTemplateProcessor.GetFileNamespace(target, this);  
       string className = Path.GetFileNameWithoutExtension(target);  
  
       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
       this.FileTemplateProcessor.AddReplace("$className$", className);  
  
       this.FileTemplateProcessor.UntokenFile(source, target);  
       this.FileTemplateProcessor.Reset();  
   }  
   ```  
  
3. Yöntem içinde, atama ifadesinden hemen sonra bir kesme noktası ayarlayın `className` .  
  
   Atama deyimleri, bir ad alanı ve yeni bir sınıf adı için makul değerler belirlenir. Bu iki `ProjectNode.FileTemplateProcessor.AddReplace` Yöntem çağrısı, ilgili şablon parametre değerlerini bu yeni değerleri kullanarak değiştirir.  
  
## <a name="testing-the-template-parameter-substitution"></a>Şablon parametre değişimini test etme  
 Artık şablon parametre değişimini test edebilirsiniz.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Şablon parametre değişimini test etmek için  
  
1. Hata ayıklamayı başlatın ve deneysel örnekte yeni bir SimpleProject oluşturun.  
  
2. Yürütme, yöntemindeki kesme noktasında durmaktadır `AddFileFromTemplate` .  
  
3. `nameSpace`Ve parametrelerinin değerlerini inceleyin `className` .  
  
   - `nameSpace` , \<RootNamespace> \Templates\projelerisimpleproject\simpleproject.exe. myproj proje şablonu dosyasındaki öğesinin değeri olarak verilir. Bu durumda, değer "MyRootNamespace" olur.  
  
   - `className` , dosya adı uzantısı olmadan sınıf kaynak dosya adının değeri olarak verilir. Bu durumda, hedef klasöre kopyalanacak ilk dosya AssemblyInfo.cs; Bu nedenle, className değeri "AssemblyInfo" olur.  
  
4. Kesme noktasını kaldırın ve yürütmeye devam etmek için F5 'e basın.  
  
    Visual Studio 'Nun bir proje oluşturmayı tamamlaması gerekir.  
  
5. Kod düzenleyicisinde Program.cs dosyasını açın. Aşağıdaki koda benzer kaynak kodu görmeniz gerekir.  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Linq;  
   using System.Text;  
  
   namespace MyRootNamespace  
   {  
       public class Program  
       {  
           static void Main(string[] args)  
           {  
               Console.WriteLine("Hello VSX!!!");  
               Console.ReadKey();  
           }  
       }  
   }  
   ```  
  
    Ad alanının artık "MyRootNamespace" olduğuna ve sınıf adının artık "program" olduğuna dikkat edin.  
  
6. Projede hata ayıklamayı başlatın. Yeni projenin derlenmesi, çalıştırması ve "Hello VSX!!!" görüntülemesi gerekir Konsol penceresinde.  
  
    ![Basit proje komutu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   Tebrikler! Temel yönetilen bir proje sistemi uyguladık.
