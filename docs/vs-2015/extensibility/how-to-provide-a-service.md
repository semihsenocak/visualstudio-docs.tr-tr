---
title: 'Nasıl yapılır: hizmet sağlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802751"
---
# <a name="how-to-provide-a-service"></a>Nasıl Yapılır: Hizmet Sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage, diğer VSPackages tarafından kullanılabilecek hizmetler sağlayabilir. Bir hizmet sağlamak için, bir VSPackage hizmeti Visual Studio ile kaydetmelidir ve hizmeti ekleyecek.  
  
 <xref:Microsoft.VisualStudio.Shell.Package>Sınıfı hem hem de <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> uygular <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> isteğe bağlı hizmetler sağlayan geri çağırma yöntemleri içerir.  
  
 Hizmetler hakkında daha fazla bilgi için bkz. [Service Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
> VSPackage boşaltılacak şekilde olduğunda Visual Studio, VSPackage 'ın sağladığı tüm hizmetlere yönelik tüm istekler teslim edilene kadar bekler. Bu hizmetler için yeni isteklere izin vermez. <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>Kaldırma sırasında bir hizmeti iptal etmek için yöntemini açıkça çağırmamalıdır.  
  
#### <a name="implementing-a-service"></a>Hizmet uygulama  
  
1. VSıX projesi oluşturun (**dosya/yeni/proje/Visual C#/Extensiblity/VSIX projesi**).  
  
2. Projeye VSPackage ekleyin. **Çözüm Gezgini** proje düğümünü seçin ve **Ekle/yeni öğe/Visual C# öğeleri/genişletilebilirlik/Visual Studio paketi**' ne tıklayın.  
  
3. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:  
  
   - Hizmeti tanımlayan bir arabirim. Bu arabirimlerin birçoğu boştur, yani bir yöntemi yoktur.  
  
   - Hizmet arabirimini tanımlayan bir arabirim. Bu arabirim uygulanacak yöntemleri içerir.  
  
   - Hem hizmeti hem de hizmet arabirimini uygulayan bir sınıf.  
  
     Aşağıdaki örnek, üç türün temel bir uygulamasını gösterir. Hizmet sınıfının Oluşturucusu, hizmet sağlayıcısını ayarlamış olmalıdır.  
  
   ```csharp  
   public class MyService : SMyService, IMyService  
   {  
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
       private string myString;  
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
       {  
           Trace.WriteLine(  
                  "Constructing a new instance of MyService");  
           serviceProvider = sp;  
       }  
       public void Hello()  
       {  
           myString = "hello";  
       }  
       public string Goodbye()  
       {  
          return "goodbye";  
       }  
   }  
   public interface SMyService  
   {  
   }  
   public interface IMyService  
   {  
       void Hello();  
       string Goodbye();  
   }  
  
   ```  
  
### <a name="registering-a-service"></a>Hizmet kaydetme  
  
1. Bir hizmeti kaydetmek için <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmeti sağlayan VSPackage öğesine ekleyin. Aşağıda bir örnek verilmiştir:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Bu öznitelik `SMyService` , Visual Studio ile kaydedilir.  
  
    > [!NOTE]
    > Aynı ada sahip başka bir hizmetin yerini alan bir hizmeti kaydetmek için öğesini kullanın <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Yalnızca bir hizmetin geçersiz kılınmasına izin verildiğini unutmayın.  
  
### <a name="adding-a-service"></a>Hizmet ekleme  
  
1. 1.  VSPackage başlatıcısında hizmeti ekleyin ve hizmetleri oluşturmak için bir geri arama yöntemi ekleyin. Bu yöntemde yapılacak değişiklik aşağıda verilmiştir <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> :  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. Hizmeti oluşturması ve döndürmesi gereken geri çağırma yöntemini veya oluşturuoluşturuoluşturulmadıysa null değerini uygulayın.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio, hizmet sağlama isteğini reddedebilir. Başka bir VSPackage hizmeti zaten sağlıyorsa bunu yapar.  
  
3. Artık hizmeti alabilir ve yöntemlerini kullanabilirsiniz. Bunu başlatıcıda göstereceğiz, ancak hizmeti, hizmeti kullanmak istediğiniz her yerde edinebilirsiniz.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     Değeri `helloString` "Merhaba" olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md)   
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)
