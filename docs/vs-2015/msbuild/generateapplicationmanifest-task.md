---
title: GenerateApplicationManifest görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3493c487c446bb66e99bf98a7c3f5599599801fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816208"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi veya yerel bildirim oluşturur. Yerel bildirim bileşeni, bileşen için benzersiz bir kimlik tanımlayarak ve bileşeni oluşturan tüm derlemeleri ve dosyaları tanımlayarak bir bileşeni tanımlar. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulama bildirimi, uygulamanın giriş noktasını belirterek ve uygulama güvenlik düzeyini belirterek yerel bir bildirimi genişletir.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda, görevi için parametreler açıklanmaktadır `GenerateApplicationManifest` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AssemblyName`|İsteğe bağlı `String` parametre.<br /><br /> `Name`Oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmemişse, ad `EntryPoint` veya `InputManifest` parametrelerinden algılanır. Ad oluşturuoluşturulamadığı takdirde, görev bir hata oluşturur.|  
|`AssemblyVersion`|İsteğe bağlı `String` parametre.<br /><br /> `Version`Oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmemişse, varsayılan "1.0.0.0" değeri kullanılır.|  
|`ClrVersion`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın gerektirdiği ortak dil çalışma zamanının (CLR) en düşük sürümünü belirtir. Varsayılan değer, yapı sistemi tarafından kullanılan CLR sürümüdür. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır.|  
|`ConfigFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Hangi öğenin uygulama yapılandırma dosyasını içerdiğini belirtir. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır.|  
|`Dependencies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim için bağımlı derlemelerin kümesini tanımlayan bir öğe listesini belirtir. Her öğe, ek dağıtım durumu ve bağımlılık türü belirtmek için öğe meta verileri tarafından daha ayrıntılı bir şekilde açıklanabilir. Daha fazla bilgi için aşağıdaki "öğe meta verileri" bölümüne bakın.|  
|`Description`|İsteğe bağlı `String` parametre.<br /><br /> Uygulama veya bileşen için açıklama belirtir.|  
|`EntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim derlemesi için giriş noktasını gösteren tek bir öğeyi belirtir.<br /><br /> [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulama bildirimi için, bu parametre uygulama çalıştırıldığında başlayan derlemeyi belirtir.|  
|`ErrorReportUrl`|İsteğe bağlı [dize] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->parametresinin.<br /><br /> ClickOnce yüklemelerinde hata raporları sırasında iletişim kutularında görüntülenen Web sayfasının URL 'sini belirtir.|  
|`FileAssociations`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> ClickOnce dağıtım bildirimiyle ilişkili bir veya daha fazla dosya türünün listesini belirtir.<br /><br /> Dosya ilişkilendirmeleri yalnızca .NET Framework 3,5 veya üzeri hedeflenirse geçerlidir.|  
|`Files`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bildirime dahil edilecek dosyalar. Her dosyanın tam yolunu belirtin.|  
|`HostInBrowser`|İsteğe bağlı [Boole] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->parametresinin.<br /><br /> Varsa `true` , uygulama bir tarayıcıda barındırılır (WPF Web tarayıcısı uygulamaları gibi).|  
|`IconFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Uygulama simge dosyasını gösterir. Uygulama simgesi oluşturulan uygulama bildiriminde ifade edilir ve Başlat menüsü ve Program Ekle/Kaldır iletişim kutusu için kullanılır. Bu giriş belirtilmemişse, varsayılan bir simge kullanılır. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır.|  
|`InputManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Bildirim Oluşturucu için temel olarak hizmet veren bir giriş XML belgesi gösterir. Bu, uygulama güvenliği veya özel bildirim tanımları gibi yapılandırılmış verilerin çıktı bildiriminde yansıtılmasına olanak tanır. XML belgesindeki kök öğesi asmv1 ad alanında bir derleme düğümü olmalıdır.|  
|`IsolatedComReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirimde yalıtmak için COM bileşenlerini belirtir. Bu parametre, "kayıt ücretsiz COM" dağıtımı için COM bileşenlerini yalıtma yeteneğini destekler. Standart COM kayıt tanımlarına sahip bir bildirimi otomatik olarak oluşturarak işe yarar. Ancak, bunun düzgün çalışması için COM bileşenlerinin derleme makinesinde kayıtlı olması gerekir.|  
|`ManifestType`|İsteğe bağlı `String` parametre.<br /><br /> Oluşturulacak bildirim türünü belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Bu parametre belirtilmezse, görev varsayılan olarak olur `ClickOnce` .|  
|`MaxTargetPath`|İsteğe bağlı `String` parametre.<br /><br /> Uygulama dağıtımında bir dosya yolunun izin verilen en fazla uzunluğunu belirtir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu değer belirtilmişse, uygulamadaki her dosya yolunun uzunluğu bu sınıra karşı denetlenir. Sınırı aşan öğeler bir yapı uyarısında oluşturulur. Bu giriş belirtilmezse veya sıfırsa hiçbir denetim yapılmaz. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır.|  
|`OSVersion`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın gerektirdiği en düşük işletim sistemi (OS) sürümünü belirtir. Örneğin, "5.1.2600.0" değeri işletim sisteminin Windows XP olduğunu gösterir. Bu parametre belirtilmezse, en düşük desteklenen işletim .NET Framework sistemi olan Windows 98 Second Edition 'ı gösteren "4.10.0.0" değeri kullanılır. Görev yerel bir bildirim oluşturuyorsa bu giriş yok sayılır.|  
|`OutputManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Oluşturulan çıkış bildirimi dosyasının adını belirtir. Bu parametre belirtilmemişse, çıkış dosyasının adı oluşturulan bildirimin kimliğinden algılanır.|  
|`Platform`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın hedef platformunu belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Bu parametre belirtilmezse, görev varsayılan olarak olur `AnyCPU` .|  
|`Product`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirimin kimliğinden algılanır. Bu ad, başlangıç menüsündeki kısayol adı için kullanılır ve Program Ekle veya Kaldır iletişim kutusunda görünen adın bir parçasıdır.|  
|`Publisher`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğiyle algılanır. Bu ad, başlangıç menüsündeki klasör adı için kullanılır ve Program Ekle veya Kaldır iletişim kutusunda görünen adın bir parçasıdır.|  
|`RequiresMinimumFramework35SP1`|İsteğe bağlı `Boolean` parametre.<br /><br /> Doğru ise, uygulama .NET Framework 3,5 SP1 veya daha yeni bir sürümü gerektirir.|  
|`TargetCulture`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın kültürünü tanımlar ve `Language` oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmezse, uygulamanın kültür sabiti olduğu varsayılır.|  
|`TargetFrameworkMoniker`|İsteğe Bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresinin.<br /><br /> Hedef çerçevenin bilinen adını belirtir.|  
|`TargetFrameworkProfile`|İsteğe Bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresinin.<br /><br /> Hedef çerçeve profilini belirtir.|  
|`TargetFrameworkSubset`|İsteğe Bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresinin.<br /><br /> Hedeflenecek .NET Framework alt kümesinin adını belirtir.|  
|`TargetFrameworkVersion`|İsteğe Bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresinin.<br /><br /> Projenin hedef .NET Framework belirtir.|  
|`TrustInfoFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulama güvenliğini belirten bir XML belgesi gösterir. XML belgesindeki kök öğesi asmv2 ad alanında TrustInfo düğümü olmalıdır. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır.|  
|`UseApplicationTrust`|İsteğe Bağlı <!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  --> parametresinin.<br /><br /> True ise,, `Product` `Publisher` ve `SupportUrl` özellikleri uygulama bildirimine yazılır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.GenerateManifestBase> <xref:Microsoft.Build.Utilities.Task> . Görev sınıfının parametrelerinin listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).  
  
 Görevi kullanma hakkında daha fazla bilgi için `GenerateDeploymentManifest` bkz. [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md).  
  
 Bağımlılıklar ve dosyalar için girişler, her öğe için ek dağıtım durumu belirtmek üzere öğe meta verileri ile birlikte daha da oluşturulabilir.  
  
## <a name="item-metadata"></a>Öğe meta verileri  
  
|Meta veri adı|Description|  
|-------------------|-----------------|  
|`DependencyType`|Bağımlılığın uygulama veya ön koşul ile yayımlanıp yayımlanmadığını ve yüklenip yüklenmediğini belirtir. Bu meta veriler tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılmaz. Bu meta veriler için kullanılabilir değerler şunlardır:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Varsayılan değer Install değeridir.|  
|`AssemblyType`|Bağımlılığın yönetilen mi yoksa yerel derleme mi olduğunu gösterir. Bu meta veriler tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılmaz. Bu meta veriler için kullanılabilir değerler şunlardır:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` , bildirim oluşturucunun derleme türünü otomatik olarak belirlemesini belirten varsayılan değerdir.|  
|`Group`|İsteğe bağlı ek dosyaları indirme grubunu gösterir. Grup adı uygulama tarafından tanımlanır ve herhangi bir dize olabilir. Boş bir dize, dosyanın varsayılan olan bir indirme grubunun parçası olmadığını gösterir. Bir grupta olmayan dosyalar ilk uygulama indirmenin bir parçasıdır. Bir gruptaki dosyalar yalnızca kullanılarak uygulama tarafından açıkça istendiğinde indirilir <xref:System.Deployment.Application> .<br /><br /> Bu meta veriler, olduğu tüm dosyalar `IsDataFile` ve olduğu `false` tüm bağımlılıklar için geçerlidir `DependencyType` `Install` .|  
|`TargetPath`|Yolun oluşturulan bildirimde nasıl tanımlanması gerektiğini belirtir. Bu öznitelik tüm dosyalar için geçerlidir. Bu öznitelik belirtilmemişse, öğe belirtimi kullanılır. Bu öznitelik, değerine sahip tüm dosyalar ve Bağımlılıklar için geçerlidir `DependencyType` `Install` .|  
|`IsDataFile`|`Boolean`Dosyanın bir veri dosyası olup olmadığını belirten bir meta veri değeri. Bir veri dosyası, uygulama güncelleştirmeleri arasında geçirilme için özeldir. Bu meta veriler yalnızca dosyalar için geçerlidir. `False` varsayılan değerdir.|  
  
## <a name="example"></a>Örnek  
 Bu örnek, `GenerateApplicationManifest` bir uygulama bildirimi oluşturmak için görevini [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ve tek bir `GenerateDeploymentManifest` bütünleştirilmiş koda sahip bir uygulama için dağıtım bildirimi oluşturmak için görevini kullanır. Daha sonra bu `SignFile` görevi bildirimleri imzalamak için kullanır.  
  
 Bu, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tek bir program için bildirimlerin oluşturulduğu en basit olası bildirim oluşturma senaryosunu gösterir. Bildirim için derlemeden varsayılan bir ad ve kimlik algılanır.  
  
> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri bildirim oluşturma yönlerine odaklanmak için önceden oluşturulmuştur. Bu örnek, tam olarak çalışan bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım üretir.  
  
> [!NOTE]
> `Thumbprint`Bu örnekteki görevde kullanılan özelliği hakkında daha fazla bilgi için `SignFile` bkz. [SignFile görevi](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, `GenerateApplicationManifest` ve `GenerateDeploymentManifest` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirimlerinin ad ve kimliğini belirterek tek bir bütünleştirilmiş koda sahip bir uygulama için uygulama ve dağıtım bildirimleri oluşturmak için ve görevlerini kullanır.  
  
 Bu örnek, bildirimlerin adı ve kimliği açıkça belirtildiğinde, önceki örneğe benzerdir. Ayrıca, bu örnek yüklü bir uygulama yerine çevrimiçi bir uygulama olarak yapılandırılır.  
  
> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri bildirim oluşturma yönlerine odaklanmak için önceden oluşturulmuştur. Bu örnek, tam olarak çalışan bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım üretir.  
  
> [!NOTE]
> `Thumbprint`Bu örnekteki görevde kullanılan özelliği hakkında daha fazla bilgi için `SignFile` bkz. [SignFile görevi](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, `GenerateApplicationManifest` `GenerateDeploymentManifest` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] birden çok dosya ve derlemeye sahip bir uygulama için uygulama ve dağıtım bildirimleri oluşturmak üzere ve görevlerini kullanır.  
  
> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri bildirim oluşturma yönlerine odaklanmak için önceden oluşturulmuştur. Bu örnek, tam olarak çalışan bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım üretir.  
  
> [!NOTE]
> `Thumbprint`Bu örnekteki görevde kullanılan özelliği hakkında daha fazla bilgi için `SignFile` bkz. [SignFile görevi](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, `GenerateApplicationManifest` uygulama Test.exe için yerel bileşen Alpha.dll ve yalıtılmış BIR com bileşeni Bravo.dll başvuruda bulunan bir yerel bildirim oluşturmak için görevini kullanır.  
  
 Bu örnek Test.exe. manifest dosyasını üretir, böylece uygulama XCOPY, kayıt ücretsiz COM avantajlarından yararlanabilir.  
  
> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri bildirim oluşturma yönlerine odaklanmak için önceden oluşturulmuştur. Bu örnek, tam olarak çalışan bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım üretir.  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)   
 [SignFile görevi](../msbuild/signfile-task.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
