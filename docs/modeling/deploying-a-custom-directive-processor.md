---
title: "Özel yönerge işlemcisi dağıtma | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, custom directive processors
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7c7881c20412ab5ffc3f1c4486958f4b5ca68a1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-a-custom-directive-processor"></a>Özel Yönerge İşlemcisi Dağıtma
Özel yönerge işlemcisi içinde kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] herhangi bir bilgisayarda, onu bu konuda açıklanan yöntemlerden biri tarafından kaydetmeniz gerekir.  
  
 Diğer yöntemler şunlardır:  
  
-   [Visual Studio Uzantısı (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832). Bu, yönerge işlemcisini hem kendi bilgisayar hem de diğer bilgisayarlara yüklemek/kaldırmak için bir yol sağlar. Genellikle, diğer özellikleri aynı VSIX'te paketleyebilirsiniz.  
  
-   [VSPackage](../extensibility/internals/vspackages.md). Yönerge işlemcisinin yanı sıra diğer özellikleri de içeren bir VSPackage tanımlıyorsanız, yönerge işlemcisi kaydetmeye uygun bir yöntem yoktur.  
  
-   Bir kayıt defteri anahtarı ayarlayın. Bu yöntemde, yönerge işlemcisi için bir kayıt defteri girdisini ekleyin.  
  
 Yalnızca metin şablonunuzda dönüştürmek istiyorsanız aşağıdaki yöntemlerden birini kullanmanız gerekir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Kendi uygulamanızda özel bir ana bilgisayar kullanıyorsanız, her yönerge için yönerge işlemcisi bulmak özel ana bilgisayarınızın sorumluluğundadır.  
  
## <a name="deploying-a-directive-processor-in-a-vsix"></a>VSIX'te Yönerge İşlemcisini Dağıtma  
 Özel yönerge işlemcisi için ekleyebileceğiniz bir [Visual Studio Uzantısı (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832).  
  
 Aşağıdaki iki öğenin .vsix dosyasında bulunduğundan emin olmanız gerekir:  
  
-   Özel yönerge işlemcisi sınıfını içeren derleme (.dll).  
  
-   Yönerge işlemcisini kaydeden .pkgdef dosyası. Dosyanın kök adı derleme ile aynı olmalıdır. Örneğin, dosyalarınız CDP.dll ve CDP.pkgdef olarak adlandırılabilir.  
  
 Bir .vsix dosyasının içeriğini denetlemek veya değiştirmek için, dosya adı uzantısını .zip olarak değiştirin ve açın. İçerikleri düzenledikten sonra, dosya adını .vsix olarak eski haline döndürün.  
  
 Bir .vsix dosyası oluşturmanın birkaç yolu vardır. Aşağıdaki yordam bir yöntemi açıklamaktadır.  
  
#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Bir VSIX projesinde özel bir yönerge işlemcisi geliştirmek için  
  
1.  VSIX projesi oluşturma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   İçinde **yeni proje** iletişim kutusunda, genişletin **Visual Basic** veya **Visual C#**, ardından **genişletilebilirlik**. Tıklatın **VSIX proje**.  
  
2.  İçinde **source.extension.vsixmanifest**, içerik türü ayarlayın ve desteklenen sürümleri.  
  
    1.  İçinde VSIX içine üzerinde Düzenleyicisi, bildirim **varlıklar** sekmesinde, seçin **yeni** ve yeni öğenin özelliklerini ayarlayın:  
  
         **İçerik türü** = **VSPackage**  
  
         **Kaynak proje** = \<*geçerli proje*>  
  
    2.  Tıklatın **seçili sürümleri** ve kullanılabilmesi için yönerge işlemcisi istediğiniz yükleme türleri kontrol edin.  
  
3.  .pkgdef dosyası ekleyin ve özelliklerini VSIX'e dahil edecek şekilde ayarlayın.  
  
    1.  Bir metin dosyası oluşturun ve adlandırın \< *assemblyName*> .pkgdef.  
  
         \<*assemblyName*> projesinin adı genellikle aynıdır.  
  
    2.  Çözüm Gezgini'nde seçin ve özelliklerini aşağıdaki gibi ayarlayın:  
  
         **Derleme eylemi** = **içeriği**  
  
         **Çıktı Dizinine Kopyala** = **her zaman Kopyala**  
  
         **İçinde VSIX içine dahil** = **True**  
  
    3.  VSIX'in adını ayarlayın ve kimliğin benzersiz olmasını sağlayın.  
  
4.  Aşağıdaki metni .pkgdef dosyasına ekleyin.  
  
    ```  
    [$RootKey$\TextTemplating]  
    [$RootKey$\TextTemplating\DirectiveProcessors]  
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]  
    @="Custom Directive Processor description"  
    "Class"="NamespaceName.ClassName"  
    "CodeBase"="$PackageFolder$\AssemblyName.dll"  
    ```  
  
     Aşağıdaki adları kendi adlarıyla değiştirin: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.  
  
5.  Aşağıdaki başvuruları projeye ekleyin:  
  
    -   **Microsoft.VisualStudio.TextTemplating. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.VSHost. \*.0**  
  
6.  Projeye özel yönerge işlemcisi sınıfınızı ekleyin.  
  
     Bu, uygulamanız gerekir, ortak bir sınıftır <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> veya <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
#### <a name="to-install-the-custom-directive-processor"></a>Özel Yönerge İşlemcisini yüklemek için  
  
1.  Windows Gezgini'nde (Windows 8'de Dosya Gezgini) yapı dizinini (genellikle bin\Debug veya bin\Release) açın.  
  
2.  Yönerge işlemcisini başka bir bilgisayara yüklemek isterseniz .vsix dosyasını başka bir bilgisayara kopyalayın.  
  
3.  .vsix dosyasına çift tıklatın. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Uzantısı yükleyicisi görüntülenir.  
  
4.  Yeniden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Artık, özel yönerge işlemcisine başvuran yönergeleri içeren metin şablonlarını çalıştırmak mümkün olacaktır. Her yönerge bu şekildedir:  
  
     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`  
  
#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Özel yönerge işlemcisini kaldırmak veya kalıcı olarak devre dışı bırakmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.  
  
2.  Yönerge işlemcisi içeren VSIX seçin ve ardından **kaldırma** veya **devre dışı**.  
  
### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>VSIX'te bir Yönerge İşlemcisine Sorun Giderme İşlemi Yapma  
 Yönerge işlemcisi çalışmazsa şu öneriler yardımcı olabilir:  
  
-   Özel yönergesinde belirttiğiniz işlemci adı eşleşmelidir `CustomDirectiveProcessorName` .pkgdef dosyasında belirtilen.  
  
-   `IsDirectiveSupported` Yöntemi döndürmelidir `true` zaman, geçirilen adını, `CustomDirective`.  
  
-   Uzantı Yöneticisi'nde uzantısı göremez, ancak sistem yüklemeye izin vermez, uzantı silme **%localappdata%\Microsoft\VisualStudio\\\*. 0\Extensions\\** .  
  
-   .Vsix dosyasını açın ve içeriğini inceleyin. Açmak için, dosya adı uzantısını .zip olarak değiştirin. .dll, .pkgdef ve extension.vsixmanifest dosyalarını içerdiğini doğrulayın. .vsixmanifest uzantı dosyası SupportedProducts düğümü için uygun listeyi içermelidir ve buna ek olarak İçerik düğümü altında bir VsPackage düğümü içermelidir:  
  
     `<Content>`  
  
     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`  
  
     `</Content>`  
  
## <a name="deploying-a-directive-processor-in-a-vspackage"></a>VSPackage'ta Yönerge İşlemcisini Dağıtma  
 Yönerge işlemciniz GAC'ye yüklenecek VSPackage'ın parçasıysa sistemin sizin için .pkgdef dosyası oluşturmasını sağlayın.  
  
 Paket sınıfınıza şu öznitelikleri yerleştirin:  
  
```  
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]  
```  
  
> [!NOTE]
>  Bu öznitelik, yönerge işlemcisi sınıfına değil, paket sınıfına yerleştirilir.  
  
 .pkgdef dosyası projeyi oluşturduğunuzda oluşturulur. VSPackage'i yüklediğinizde, .pkgdef dosyası yönerge işlemcisini kaydeder.  
  
 .pkgdef dosyasının, genellikle bin\Debug veya bin\Release olan yapı klasöründe göründüğünü doğrulayın. Görünmüyorsa, .csproj dosyasını bir metin düzenleyicisinde açın ve aşağıdaki düğüm kaldırın: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.  
  
 Daha fazla bilgi için bkz: [VSPackages](../extensibility/internals/vspackages.md).  
  
## <a name="setting-a-registry-key"></a>Bir Kayıt Defteri Anahtarını Ayarlama  
 Bu, özel bir yönerge işlemcisi yükleme yöntemi en az tercih edilir. Yönerge işlemcisini etkinleştirmek veya devre dışı bırakmak için uygun bir yol sağlamaz; yönerge işlemcisinin başka kullanıcılara dağıtılması yöntemini de sağlamaz.  
  
> [!CAUTION]
>  Kayıt defterinin hatalı şekilde düzenlenmesi sisteminizde ciddi arızalara yol açabilir. Kayıt defterinde değişiklikler yapmadan önce, bilgisayarınızdaki tüm değerli verileri yedeklediğinizden emin olun.  
  
#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Bir kayıt defteri anahtarı ayarlayarak bir yönerge işlemcisi kaydetmek için  
  
1.  Çalıştırma `regedit`.  
  
2.  Regedit içinde şuraya gidin:  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
     Yönerge işlemcisi Deneysel sürümü yüklemek istiyorsanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], "11.0" sonra "Exp" ekleyin.  
  
3.  Yönerge işlemcisi sınıfıyla aynı ada sahip bir kayıt defteri anahtarı ekleyin.  
  
    -   Kayıt defteri ağacında sağ **DirectiveProcessors** düğümünü sağ **yeni**ve ardından **anahtar**.  
  
4.  Yeni düğümünde, Sınıf ve CodeBase veya Derleme için dize değerlerini aşağıdaki tablolara göre ekleyin.  
  
    1.  Oluşturduğunuz düğüme sağ tıklayın, fareyle **yeni**ve ardından **dize değeri**.  
  
    2.  Değerin adını düzenleyin.  
  
    3.  Adı çift tıklatın ve verileri düzenleyin.  
  
 Özel yönerge işlemcisi GAC'de değilse, kayıt defteri alt anahtarları aşağıdaki tabloda gibi görünmelidir:  
  
|Ad|Tür|Veri|  
|----------|----------|----------|  
|(Varsayılan)|REG_SZ|(değer ayarlı değil)|  
|örneği|REG_SZ|**\<Namespace adı >. \<Sınıf adı >**|  
|CodeBase|REG_SZ|**\<Yolunuzu >\\< derleme adı\>**|  
  
 Derleme GAC'deyse, kayıt defteri alt anahtarları aşağıdaki tabloda gibi görünmelidir:  
  
|Ad|Tür|Veri|  
|----------|----------|----------|  
|(Varsayılan)|REG_SZ|(değer ayarlı değil)|  
|örneği|REG_SZ|\<**Tam sınıf adı**>|  
|Derleme|REG_SZ|\<**GAC, derleme adı**>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md)