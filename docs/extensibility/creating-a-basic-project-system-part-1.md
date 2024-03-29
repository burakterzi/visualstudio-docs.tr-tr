---
title: Temel proje sistemi oluşturma, Bölüm 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73bacf2c5d1650da91093c92c67e6b67bbbc73a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633511"
---
# <a name="create-a-basic-project-system-part-1"></a>Temel proje sistemi oluşturma, Bölüm 1
Visual Studio 'da, projeler, geliştiricilerin kaynak kodu dosyalarını ve diğer varlıkları düzenlemek için kullandığı kapsayıcılardır. Projeler **Çözüm Gezgini**çözümlerin alt öğeleri olarak görünür. Projeler, kaynak kodu düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza, Web Hizmetleri, veritabanları ve diğer kaynaklara başvurular oluşturmanıza imkan tanır.

 Projeler proje dosyalarında tanımlanır, örneğin bir görsel C# proje için *. csproj* dosyası. Kendi proje dosya adı uzantınıza sahip olan kendi proje türünü de oluşturabilirsiniz. Proje türleri hakkında daha fazla bilgi için bkz. [Proje türleri](../extensibility/internals/project-types.md).

> [!NOTE]
> Visual Studio 'Yu özel bir proje türüyle genişletmenize gerek duyuyorsanız, sıfırdan bir proje sistemi oluşturma konusunda birçok avantaj içeren [Visual Studio proje sistemi](https://github.com/Microsoft/VSProjectSystem) 'nin (vsps) kullanılmasını önemle öneririz:
>
> - Daha kolay ekleme.  Temel bir proje sistemi bile on binlerce satır kod gerektirir.  VSPS 'yi kullanmak, gereksinimlerinize göre özelleştirmeye başlamadan önce ekleme maliyetini birkaç tıklamayla azaltır.
> - Daha kolay bakım.  VSPS 'den yararlanarak yalnızca kendi senaryolarınızı korumanız gerekir.  Tüm proje sistemi altyapısının sürekli tutulmasını yaptık.
>
>   Visual Studio 'nun Visual Studio 2013 'den daha eski sürümlerini hedefliyorsanız, Visual Studio uzantısında VSPS 'den yararlanabilemeyeceksiniz.  Böyle bir durum söz konusu olduğunda bu izlenecek yol, başlamak için iyi bir yerdir.

 Bu izlenecek yol, proje dosya adı uzantısına sahip bir proje türünün nasıl oluşturulacağını gösterir *. myproj*. Bu, varolan görsel C# Proje sisteminden boratır izlenecek yolu.

> [!NOTE]
> Uzantı projelerine ilişkin daha fazla örnek için bkz. [VSSDK örnekleri](https://aka.ms/vs2015sdksamples).

 Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:

- Temel proje türü oluşturun.

- Temel bir proje şablonu oluşturun.

- Proje şablonunu Visual Studio ile kaydedin.

- **Yeni proje** iletişim kutusunu açıp şablonunuzu kullanarak bir proje örneği oluşturun.

- Proje sisteminiz için bir proje fabrikası oluşturun.

- Proje sisteminiz için bir proje düğümü oluşturun.

- Proje sistemi için özel simgeler ekleyin.

- Temel şablon parametre değişimini uygulayın.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

 Ayrıca, [Projeler Için yönetilen paket çerçevesi](https://github.com/tunnelvisionlabs/MPFProj10)için kaynak kodunu da indirmeniz gerekir. Dosyayı oluşturacağınız çözümün erişebileceği bir konuma ayıklayın.

## <a name="create-a-basic-project-type"></a>Temel proje türü oluşturma
 C# **SimpleProject**adlı bir VSIX projesi oluşturun. (**Dosya**  > **Yeni**  > **projesi** ve **Visual C#**   > **genişletilebilirlik**  > **VSIX projesi**). Visual Studio Package proje öğesi şablonu ekleyin ( **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve  > **Yeni öğe** **Ekle** ' yi seçin ve ardından **genişletilebilirlik**  > **Visual Studio paketi**) ' ne gidin. Dosyayı *Simpleprojectpackage*olarak adlandırın.

## <a name="creating-a-basic-project-template"></a>Temel proje şablonu oluşturma
 Şimdi, yeni *. myproj* proje türünü uygulamak için bu temel VSPackage 'ı değiştirebilirsiniz. *. Myproj* proje türünü temel alan bir proje oluşturmak Için, Visual Studio 'nun hangi dosyaları, kaynakları ve başvuruları yeni projeye ekleneceğini bilmeleri gerekir. Bu bilgileri sağlamak için proje dosyalarını bir proje şablonu klasörüne koyun. Bir Kullanıcı bir proje oluşturmak için *. myproj* projesini kullandığında, dosyalar yeni projeye kopyalanır.

### <a name="to-create-a-basic-project-template"></a>Temel proje şablonu oluşturmak için

1. Projeye bir tane olmak üzere üç klasör ekleyin: *Templates\projeler* ( **Çözüm Gezgini**, **SimpleProject** proje düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni klasör**' e tıklayın. Klasör *şablonlarını*adlandırın. *Şablonlar* klasöründe, *Projeler*adlı bir klasör ekleyin. *Projeler* klasöründe, *SimpleProject*adlı bir klasör ekleyin.)

2. *Templates\projeler\simpleproject* klasöründe, *SimpleProject. ico*adlı simge olarak kullanılacak bir bit eşlem resim dosyası ekleyin. **Ekle**' ye tıkladığınızda, simge Düzenleyicisi açılır.

3. Simgeyi farklı yapın. Bu simge, izlenecek yolun ilerleyen kısımlarında yer alacak **Yeni proje** iletişim kutusunda görünür.

    ![Basit proje simgesi](../extensibility/media/simpleprojicon.png "Simpleprojıcon")

4. Simgeyi kaydedin ve simge düzenleyicisini kapatın.

5. *Templates\projeler\simpleproject* klasöründe, *program.cs*adlı bir **sınıf** öğesi ekleyin.

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
   > Bu, *program.cs* kodunun son formu değildir; değiştirme parametreleri sonraki bir adımda ele alınacaktır. Derleme hataları görebilirsiniz, ancak dosyanın **Builkaction** **içeriği**olduğu sürece projeyi her zamanki gibi derleyip çalıştırabilirsiniz.

7. Dosyayı kaydedin.

8. *AssemblyInfo.cs* dosyasını *Özellikler* klasöründen, *projelerprojem proje* klasörüne kopyalayın.

9. *Projeler\simpleproject* klasöründe, *SimpleProject. myproj*adlı bir XML dosyası ekleyin.

   > [!NOTE]
   > Bu türden tüm projeler için dosya adı uzantısı *. myproj*' dir. Bunu değiştirmek istiyorsanız, izlenecek yolda bahsedilen her yerde değiştirmeniz gerekir.

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

12. **Özellikler** penceresinde, *AssemblyInfo.cs*, *program.cs*, *SimpleProject. ico*ve *SimpleProject. myproj* öğesinin **derleme eylemini** **içerik**olarak ayarlayın ve **VSIX özelliklerine dahil** edin **true**olarak.

    Bu proje şablonu, hem hata ayıklama C# Yapılandırması hem de sürüm yapılandırması olan temel bir görsel proje tanımlar. Proje iki kaynak dosyası, *AssemblyInfo.cs* ve *program.cs*ve çeşitli derleme başvuruları içerir. Şablondan bir proje oluşturulduğunda, Projectguıd değeri otomatik olarak yeni bir GUID ile değiştirilmiştir.

    **Çözüm Gezgini**, genişletilmiş **Şablonlar** klasörü aşağıdaki gibi görünmelidir:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Temel proje fabrikası oluşturma
 Visual Studio 'nun proje şablonu klasörünüzün konumunu söylemeniz gerekir. Bunu yapmak için, VSPackage oluşturulduğunda şablon konumunun sistem kayıt defterine yazılması için, VSPackage sınıfına proje fabrikası uygulayan bir öznitelik ekleyin. Bir proje fabrikası GUID 'ı tarafından tanımlanan temel bir proje fabrikası oluşturarak başlayın. Proje fabrikasını `SimpleProjectPackage` sınıfına bağlamak için <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> özniteliğini kullanın.

### <a name="to-create-a-basic-project-factory"></a>Temel bir proje fabrikası oluşturmak için

1. Proje fabrikanızın GUID 'Leri oluşturun ( **Araçlar** menüsünde **GUID oluştur**' a tıklayın) veya aşağıdaki örnekteki birini kullanın. GUID 'Leri, önceden tanımlanmış `PackageGuidString` bölümünün yakınında `SimpleProjectPackage` sınıfına ekleyin. GUID 'Ler hem GUID biçiminde hem de dize biçiminde olmalıdır. Elde edilen kod aşağıdaki örneğe benzemelidir.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. *SimpleProjectFactory.cs*adlı üst *SimpleProject* klasörüne bir sınıf ekleyin.

3. Aşağıdaki using yönergelerini ekleyin:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. @No__t_0 sınıfına bir GUID özniteliği ekleyin. Özniteliğin değeri, yeni proje fabrikası GUID 'sidir.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Artık proje şablonunuzu kaydedebilirsiniz.

### <a name="to-register-the-project-template"></a>Proje şablonunu kaydetmek için

1. *SimpleProjectPackage.cs*' de, aşağıdaki şekilde `SimpleProjectPackage` sınıfına bir <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> özniteliği ekleyin.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.

    Yeniden derleme proje şablonunu kaydeder.

   @No__t_0 ve `possibleProjectExtensions` parametreleri proje dosya adı uzantısına ayarlanır ( *. myproj*). @No__t_0 parametresi, *Şablonlar* klasörünün göreli yoluna ayarlanır. Derleme sırasında, bu yol tam bir yapıya dönüştürülür ve proje sistemini kaydetmek için kayıt defterine eklenir.

## <a name="test-the-template-registration"></a>Şablon kaydını test etme
 Şablon kaydı, Visual Studio 'Ya proje şablonu klasörünüzün konumunu söyler, böylece Visual Studio **Yeni proje** iletişim kutusunda şablon adı ve simgesini görüntüleyebilir.

### <a name="to-test-the-template-registration"></a>Şablon kaydını test etmek için

1. Visual Studio 'nun deneysel örneğinde hata ayıklamaya başlamak için **F5** 'e basın.

2. Deneysel örnekte, yeni oluşturulan proje türünden yeni bir proje oluşturun. **Yeni proje** iletişim kutusunda, **yüklü şablonlar**altında **SimpleProject** ' i görmeniz gerekir.

   Artık kayıtlı bir proje fabrikasına sahipsiniz. Ancak, henüz bir proje oluşturamaz. Proje paketi ve proje fabrikası bir proje oluşturmak ve başlatmak için birlikte çalışır.

## <a name="add-the-managed-package-framework-code"></a>Yönetilen paket çerçevesi kodunu ekleyin
 Proje paketiyle proje fabrikası arasındaki bağlantıyı uygulayın.

- Yönetilen paket çerçevesi için kaynak kodu dosyalarını içeri aktarın.

    1. SimpleProject projesini kaldırın ( **Çözüm Gezgini**, proje düğümünü seçin ve bağlam menüsünde **Projeyi Kaldır**' a tıklayın.) ve proje dosyasını XML düzenleyicisinde açın.

    2. Aşağıdaki blokları proje dosyasına ekleyin (\<Import > bloklarının hemen üzerinde). @No__t_0, az önce indirdiğiniz yönetilen paket çerçeve kodundaki *ProjectBase. Files* dosyasının konumuna ayarlayın. Yol adına bir ters eğik çizgi eklemeniz gerekebilir. Bunu yapmazsanız, proje yönetilen paket çerçevesi kaynak kodunu bulamamasına neden olabilir.

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

        - `Microsoft.VisualStudio.Designer.Interfaces` ( *\<VSSDK ınstall > \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Proje fabrikasını başlatmak için

1. *SimpleProjectPackage.cs* dosyasında aşağıdaki `using` yönergesini ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. @No__t_0 sınıfını `Microsoft.VisualStudio.Package.ProjectPackage` türet.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Proje fabrikasını kaydedin. Aşağıdaki satırı, `base.Initialize` hemen sonra `SimpleProjectPackage.Initialize` yöntemine ekleyin.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Soyut özelliği `ProductUserContext` uygulayın:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. *SimpleProjectFactory.cs*' de, mevcut `using` yönergelerinden sonra aşağıdaki `using` yönergesini ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. @No__t_0 sınıfını `ProjectFactory` türet.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Aşağıdaki kukla yöntemi `SimpleProjectFactory` sınıfına ekleyin. Bu yöntemi sonraki bir bölümde uygulayacaksınız.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Aşağıdaki alanı ve oluşturucuyu `SimpleProjectFactory` sınıfına ekleyin. Bu `SimpleProjectPackage` başvurusu bir özel alanda önbelleğe alınır, böylece bir hizmet sağlayıcı sitesi ayarlamada kullanılabilir.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.

## <a name="test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etme
 Proje fabrikası uygulamanızın oluşturucusunun adlandırılıp çağrılmadığını test edin.

### <a name="to-test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etmek için

1. *SimpleProjectFactory.cs* dosyasında, `SimpleProjectFactory` oluşturucusunun aşağıdaki satırında bir kesme noktası ayarlayın.

    ```csharp
    this.package = package;
    ```

2. Visual Studio 'nun deneysel bir örneğini başlatmak için **F5** tuşuna basın.

3. Deneysel örnekte, yeni bir proje oluşturmaya başlayın. **Yeni proje** iletişim kutusunda, **SimpleProject** proje türünü seçin ve ardından **Tamam**' a tıklayın. Yürütme kesme noktasında durmaktadır.

4. Kesme noktasını temizle ve hata ayıklamayı Durdur. Henüz bir proje düğümü oluşturmadınız, proje oluşturma kodu hala özel durumlar oluşturuyor.

## <a name="extend-the-projectnode-class"></a>ProjectNode sınıfını genişletme
 Artık `ProjectNode` sınıfından türeten `SimpleProjectNode` sınıfını uygulayabilirsiniz. @No__t_0 temel sınıfı, proje oluşturma için aşağıdaki görevleri işler:

- *SimpleProject. myproj*proje şablon dosyasını yeni proje klasörüne kopyalar. Kopya, **Yeni proje** iletişim kutusuna girilen ada göre yeniden adlandırılır. @No__t_0 özelliği değeri yeni bir GUID ile değiştirilmiştir.

- , *SimpleProject. myproj*proje şablon dosyasının MSBuild öğelerine erişir ve `Compile` öğeleri arar. Her bir `Compile` hedef dosya için dosyayı yeni proje klasörüne kopyalar.

  Türetilmiş `SimpleProjectNode` sınıfı şu görevleri gerçekleştirir:

- **Çözüm Gezgini** veya seçilmesi için proje ve dosya düğümlerinin simgelerini sağlar.

- Ek proje şablonu parametre değişimlerin belirtilmesini sağlar.

### <a name="to-extend-the-projectnode-class"></a>ProjectNode sınıfını genişletmek için

1. @No__t_0 adlı bir sınıf ekleyin.

2. Mevcut kodu aşağıdaki kodla değiştirin.

   ```csharp
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
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
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

   Bu `SimpleProjectNode` sınıfı uygulamasının bu geçersiz kılınan yöntemleri vardır:

- proje fabrikası GUID 'sini döndüren `ProjectGuid`.

- Proje türünün yerelleştirilmiş adını döndüren `ProjectType`.

- Seçili dosyaları şablon klasöründen hedef projeye kopyalayan `AddFileFromTemplate`. Bu yöntem daha sonraki bir bölümde daha da uygulanabilir.

  @No__t_1 Oluşturucusu gibi `SimpleProjectNode` Oluşturucu, daha sonra kullanmak üzere bir özel alanda `SimpleProjectPackage` başvurusunu önbelleğe alır.

  @No__t_0 sınıfını `SimpleProjectNode` sınıfına bağlamak için, `SimpleProjectFactory.CreateProject` yönteminde yeni bir `SimpleProjectNode` örneği oluşturmanız ve daha sonra kullanmak üzere özel bir alanda önbelleğe almanız gerekir.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Project Factory sınıfını ve Node sınıfını bağlamak için

1. *SimpleProjectFactory.cs* dosyasında aşağıdaki `using` yönergesini ekleyin:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Aşağıdaki kodu kullanarak `SimpleProjectFactory.CreateProject` yöntemini değiştirin.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.

## <a name="test-the-projectnode-class"></a>ProjectNode sınıfını test etme
 Proje fabrikasını bir proje hiyerarşisi oluşturup oluşturmadığını görmek için test edin.

### <a name="to-test-the-projectnode-class"></a>ProjectNode sınıfını test etmek için

1. Hata ayıklamayı başlatmak için **F5** 'e basın. Deneysel örnekte, yeni bir SimpleProject oluşturun.

2. Visual Studio proje oluşturmak için proje fabrikasını çağırmalıdır.

3. Visual Studio 'nun Deneysel örneğini kapatın.

## <a name="add-a-custom-project-node-icon"></a>Özel bir proje düğümü simgesi ekleyin
 Önceki bölümdeki proje düğümü simgesi varsayılan simgedir. Bunu özel bir simge olarak değiştirebilirsiniz.

### <a name="to-add-a-custom-project-node-icon"></a>Özel bir proje düğümü simgesi eklemek için

1. **Kaynaklar** klasöründe, *SimpleProjectNode. bmp*adlı bir bit eşlem dosyası ekleyin.

2. **Özellikler** penceresinde bit eşlemi 16 ile 16 piksel azaltın. Bit eşlemi farklı hale getirin.

    ![Basit proje Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. **Özellikler** penceresinde, bit eşlemin **derleme eylemini** **katıştırılmış kaynak**olarak değiştirin.

4. *SimpleProjectNode.cs*' de aşağıdaki `using` yönergeleri ekleyin:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Aşağıdaki statik alanı ve oluşturucuyu `SimpleProjectNode` sınıfına ekleyin.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Aşağıdaki özelliği `SimpleProjectNode` sınıfının başına ekleyin.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Örnek oluşturucusunu aşağıdaki kodla değiştirin.

   ```csharp
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

   Statik oluşturma sırasında `SimpleProjectNode`, derleme bildirim kaynaklarından proje düğümü bit eşlemini alır ve daha sonra kullanmak üzere özel bir alanda önbelleğe alır. @No__t_0 resim yolunun söz dizimini görürsünüz. Bir derlemeye gömülü olan bildirim kaynaklarının adlarını görmek için <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> yöntemini kullanın. Bu yöntem `SimpleProject` derlemesine uygulandığında, sonuçlar aşağıdaki gibi olmalıdır:

- *SimpleProject. resources. resources*

- *VisualStudio. Project. resources*

- *SimpleProject. VSPackage. resources*

- *Resources. imagelis. bmp*

- *Microsoft. VisualStudio. Project. DontShowAgainDialog. resources*

- *Microsoft. VisualStudio. Project. SecurityWarningDialog. resources*

- *SimpleProject. resources. SimpleProjectNode. bmp*

  Örnek oluşturma sırasında `ProjectNode` temel sınıfı, *Resources\imagelis.bmp*'den yaygın olarak kullanılan 16 x 16 bit eşlem olan *Resources. imagelis. bmp*yükler. Bu bit eşlem listesi, `ImageHandler.ImageList` olarak `SimpleProjectNode` kullanılabilir hale getirilir. `SimpleProjectNode`, proje düğümü bit eşlemini listeye ekler. Görüntü listesindeki proje düğümü bit eşleminin, daha sonra public `ImageIndex` özelliğinin değeri olarak kullanılmak üzere önbelleğe alınır. Visual Studio, proje düğümü simgesi olarak hangi bit eşlemin gösterileceğini öğrenmek için bu özelliği kullanır.

## <a name="test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etme
 Özel proje düğümünüz simgenizi içeren bir proje hiyerarşisi oluşturup oluşturmadığını görmek için proje fabrikasını test edin.

### <a name="to-test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etmek için

1. Hata ayıklamayı başlatın ve deneysel örnekte yeni bir SimpleProject oluşturun.

2. Yeni oluşturulan projede, *SimpleProjectNode. bmp* ' nin proje düğümü simgesi olarak kullanıldığını görürsünüz.

     ![Basit proje yeni proje düğümü](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Kod düzenleyicisinde *program.cs* öğesini açın. Aşağıdaki koda benzer kaynak kodu görmeniz gerekir.

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

     $NameSpace $ ve $className $ şablon parametrelerinin yeni değerlere sahip olmadığına dikkat edin. Bir sonraki bölümde şablon parametre değişimini nasıl uygulayacağınızı öğreneceksiniz.

## <a name="substitute-template-parameters"></a>Şablon değiştirme parametreleri
 Daha önceki bir bölümde, `ProvideProjectFactory` özniteliğini kullanarak proje şablonunu Visual Studio ile kaydettiniz. Bir şablon klasörünün yolunu bu şekilde kaydetme, `ProjectNode.AddFileFromTemplate` sınıfını geçersiz kılarak ve genişleterek temel şablon parametre değişimini etkinleştirmenizi sağlar. Daha fazla bilgi için bkz. [Yeni proje oluşturma: ikinci bölüm altında](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Şimdi `AddFileFromTemplate` sınıfına değiştirme kodu ekleyin.

### <a name="to-substitute-template-parameters"></a>Şablon parametrelerini koymak için

1. *SimpleProjectNode.cs* dosyasında aşağıdaki `using` yönergesini ekleyin.

   ```csharp
   using System.IO;
   ```

2. Aşağıdaki kodu kullanarak `AddFileFromTemplate` yöntemini değiştirin.

   ```csharp
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

3. Yönteminde, `className` atama ifadesinden hemen sonra bir kesme noktası ayarlayın.

   Atama deyimleri, bir ad alanı ve yeni bir sınıf adı için makul değerler belirlenir. İki `ProjectNode.FileTemplateProcessor.AddReplace` yöntemi çağrısı, bu yeni değerleri kullanarak karşılık gelen şablon parametre değerlerini değiştirir.

## <a name="test-the-template-parameter-substitution"></a>Şablon parametre değişimini test etme
 Artık şablon parametre değişimini test edebilirsiniz.

### <a name="to-test-the-template-parameter-substitution"></a>Şablon parametre değişimini test etmek için

1. Hata ayıklamayı başlatın ve deneysel örnekte yeni bir SimpleProject oluşturun.

2. Yürütme `AddFileFromTemplate` yönteminde kesme noktasında durmaktadır.

3. @No__t_0 ve `className` parametrelerinin değerlerini inceleyin.

   - `nameSpace`, *\Templates\ıtssimpleproject\simpleproject.exe* klasöründeki \<RootNamespace > öğesinin değeri verilir. Bu durumda, değer `MyRootNamespace`.

   - `className`, dosya adı uzantısı olmadan sınıf kaynak dosya adının değeri olarak verilir. Bu durumda, hedef klasöre kopyalanacak ilk dosya *AssemblyInfo.cs*; Bu nedenle, className değeri `AssemblyInfo`.

4. Kesme noktasını kaldırın ve yürütmeye devam etmek için **F5** 'e basın.

    Visual Studio 'Nun bir proje oluşturmayı tamamlaması gerekir.

5. Kod düzenleyicisinde *program.cs* öğesini açın. Aşağıdaki koda benzer kaynak kodu görmeniz gerekir.

   ```csharp
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

    Ad alanının artık `MyRootNamespace` olduğunu ve sınıf adının artık `Program` olduğunu unutmayın.

6. Projede hata ayıklamayı başlatın. Yeni projenin derlenmesi, çalıştırması ve "Hello VSX!!!" görüntülemesi gerekir Konsol penceresinde.

    ![Basit proje komutu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Mühendisi! Temel yönetilen bir proje sistemi uyguladık.
