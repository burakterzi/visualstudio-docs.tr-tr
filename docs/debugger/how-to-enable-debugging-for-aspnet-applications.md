---
title: ASP.NET uygulamaları için hata ayıklamayı etkinleştirme | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911347"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio 'da ASP.NET veya ASP.NET Core uygulamalarında hata ayıklama

Visual Studio 'da ASP.NET ve ASP.NET Core uygulamalarında hata ayıklaması yapabilirsiniz. İşlem, ASP.NET ve ASP.NET Core arasında ve IIS Express ya da yerel bir IIS sunucusunda çalıştırıp çalıştırıetmeksizin farklılık gösterir.

>[!NOTE]
>Aşağıdaki adımlar ve ayarlar yalnızca yerel bir sunucudaki uygulamalarda hata ayıklama için geçerlidir. Uzak IIS sunucusundaki uygulamalarda hata ayıklama Işlemi, **işlemek Için İliştir**kullanır ve bu ayarları yoksayar. IIS üzerinde uzaktan hata ayıklama ASP.NET uygulamaları hakkında daha fazla bilgi ve yönergeler için, uzak bir IIS bilgisayarında [BIR IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) veya [uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)bakın.

Yerleşik IIS Express sunucusu, Visual Studio 'Ya dahildir. IIS Express, ASP.NET ve ASP.NET Core projelerine yönelik varsayılan hata ayıklama sunucusudur ve önceden yapılandırılmıştır. Hata ayıklamanın en kolay yolu, ilk hata ayıklama ve test için idealdir.

Ayrıca, uygulamayı çalıştıracak şekilde yapılandırılmış yerel bir IIS sunucusunda (sürüm 8,0 veya üzeri) bir ASP.NET veya ASP.NET Core uygulamasında hata ayıklaması yapabilirsiniz. Yerel IIS 'de hata ayıklamak için aşağıdaki gereksinimleri karşılamanız gerekir:

<a name="iis"></a>
- Visual Studio 'Yu yüklerken **geliştirme zamanı IIS desteği** ' ni seçin. (Gerekirse, Visual Studio Yükleyicisi yeniden çalıştırın, **Değiştir**' i seçin ve bu bileşeni ekleyin.)
- Visual Studio 'Yu yönetici olarak çalıştırıyor olun.
- ASP.NET ve/veya ASP.NET Core uygun sürümleri ile IIS 'yi yükleyip doğru şekilde yapılandırın. Daha fazla bilgi ve yönergeler için bkz. IIS [Ile Windows üzerinde](/aspnet/core/host-and-deploy/iis/index) [ASP.NET 3,5 ve ASP.NET 4,5 veya Host ASP.NET Core kullanarak IIS 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) .
- Uygulamanın IIS 'de hata olmadan çalıştığından emin olun.

## <a name="debug-aspnet-apps"></a>ASP.NET uygulamalarında hata ayıklama

IIS Express varsayılandır ve önceden yapılandırılmıştır. Yerel IIS 'de hata ayıklaması yapıyorsanız, [yerel IIS hata ayıklama gereksinimlerini](#iis)karşıladığınızdan emin olun.

1. Visual Studio 'da ASP.NET projesini seçin **Çözüm Gezgini** ve **Özellikler** simgesine tıklayın, **alt**+**ENTER**tuşuna basın veya sağ tıklayıp **Özellikler**' i seçin.

1. **Web** sekmesini seçin.

1. **Özellikler** bölmesinde, **sunucular**altında,
   - IIS Express için, açılan listeden **IIS Express** seçin.
   - Yerel IIS için
     1. Açılan listeden **yerel IIS** ' yi seçin.
     1. Uygulamayı henüz IIS 'de ayarlamadıysanız, **proje URL 'si** alanının yanında, **sanal dizin oluştur**' u seçin.

1. **Hata ayıklayıcılar**altında **ASP.net**' yi seçin.

   ![ASP.NET hata ayıklayıcısı ayarları](media/dbg-aspnet-enable-debugging2.png "ASP.NET hata ayıklayıcısı ayarları")

1. Değişiklikleri kaydetmek için **Seçili öğeleri** veya **Ctrl**+**S** > **dosyayı** kullanın.

1. Uygulamada hata ayıklamak için, projenizde, bazı koddaki kesme noktaları ayarlayın. Visual Studio araç çubuğunda, yapılandırmanın **hata ayıklama**olarak ayarlandığından ve istediğiniz tarayıcının **IIS Express (\<tarayıcı adı >)** ya da öykünücü alanında **Yerel ııs (\<tarayıcı adı >)** göründüğünden emin olun.

1. Hata ayıklamayı başlatmak için, araç çubuğunda **IIS Express (\<tarayıcı adı >)** veya **yerel IIS (\<tarayıcı adı >)** seçeneğini belirleyin, **Hata Ayıkla** menüsünden **hata ayıklamayı Başlat** ' ı seçin veya **F5**tuşuna basın. Hata ayıklayıcı kesme noktalarında duraklatılır. Hata ayıklayıcı kesme noktalarına ulaşamıyorum, bkz. [hata ayıklama sorun giderme](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>ASP.NET Core uygulamalarda hata ayıkla

IIS Express varsayılandır ve önceden yapılandırılmıştır. Yerel IIS 'de hata ayıklaması yapıyorsanız, [yerel IIS hata ayıklama gereksinimlerini](#iis)karşıladığınızdan emin olun.

1. Visual Studio **Çözüm Gezgini** ASP.NET Core projesi seçin ve **Özellikler** simgesine tıklayın, **alt**+**ENTER**tuşlarına basın veya sağ tıklayıp **Özellikler**' i seçin.

1. **Hata Ayıkla** sekmesini seçin.

1. **Özellikler** bölmesinde, **profil**' ın yanında,
   - IIS Express için, açılan listeden **IIS Express** seçin.
   - Yerel IIS için, açılan listeden uygulama adını seçin veya **Yeni**' yi seçin, yeni bir profil adı oluşturun ve **Tamam**' ı seçin.

1. **Başlat**' ın yanındaki açılan listeden **IIS Express** veya **IIS** ' yi seçin.

1. **Başlatma tarayıcısının** seçili olduğundan emin olun.

1. **Ortam değişkenleri**altında, **ASPNETCORE_ENVIRONMENT** ' nin bir **geliştirme**değeriyle bulunduğundan emin olun. Aksi takdirde **Ekle** ' yi seçin ve ekleyin.

   ![ASP.NET Core hata ayıklayıcı ayarları](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core hata ayıklayıcı ayarları")

1. Değişiklikleri kaydetmek için **Seçili öğeleri** veya **Ctrl**+**S** > **dosyayı** kullanın.

1. Uygulamada hata ayıklamak için, projenizde, bazı koddaki kesme noktaları ayarlayın. Visual Studio araç çubuğunda, yapılandırmanın **hata ayıklama**olarak ayarlandığından ve **IIS Express**ya da yeni IIS profili adının öykünücü alanında göründüğünden emin olun.

1. Hata ayıklamayı başlatmak için **IIS Express** veya **\<IIS profili adı** ' nı seçin > araç çubuğunda Hata **Ayıkla** menüsünden **hata ayıklamayı Başlat** ' ı seçin veya **F5**tuşuna basın. Hata ayıklayıcı kesme noktalarında duraklatılır. Hata ayıklayıcı kesme noktalarına ulaşamıyorum, bkz. [hata ayıklama sorun giderme](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Hata ayıklama sorunlarını giderme

Yerel IIS hata ayıklaması kesme noktasına ilerleyememesi durumunda sorun gidermek için aşağıdaki adımları izleyin.

1. Web uygulamasını IIS 'den başlatın ve düzgün çalıştığından emin olun. Web uygulamasını çalışır durumda bırakın.

2. Visual Studio 'da **Işleme eklemek > hata ayıkla** ' yı seçin veya **Ctrl**+**alt**+**P**tuşlarına basın ve ASP.net ya da ASP.NET Core işlemine (genellikle **W3wp. exe** veya **DotNet. exe**) bağlanın. Daha fazla bilgi için bkz. [Işleme iliştirme](attach-to-running-processes-with-the-visual-studio-debugger.md) ve [ASP.NET işleminin adını bulma](how-to-find-the-name-of-the-aspnet-process.md).

**Işleme İliştir** **' > i** kullanarak bağlantı noktasına bağlanabilir ve bu kesme noktasına ulaşırsanız, hata **ayıklamayı Başlat** veya **F5**' i kullanarak bir ayar proje özelliklerinde yanlış olur. Bir HOSTS dosyası kullanıyorsanız, bunun da doğru yapılandırıldığından emin olun.

## <a name="configure-debugging-in-the-webconfig-file"></a>Web. config dosyasında hata ayıklamayı yapılandırma

ASP.NET projelerinde, hata ayıklama ayarları dahil olmak üzere uygulama yapılandırma ve başlatma bilgilerini içeren *Web. config* dosyaları varsayılan olarak bulunur. *Web. config* dosyalarının hata ayıklama için doğru şekilde yapılandırılması gerekir. Önceki bölümlerdeki **Özellikler** ayarları *Web. config* dosyalarını güncelleştirir, ancak bunları el ile de yapılandırabilirsiniz.

> [!NOTE]
> ASP.NET Core projelerin başlangıçta *Web. config* dosyaları yoktur, ancak uygulama yapılandırması ve başlatma bilgileri için *appSettings. JSON* ve *launchsettings. JSON* dosyalarını kullanın. Uygulamanın dağıtımı, projede bir *Web. config* dosyası veya dosyaları oluşturur, ancak genellikle hata ayıklama bilgilerini içermez.

> [!TIP]
> Dağıtım işleminiz *Web. config* ayarlarını güncelleştirebilir, bu nedenle hata ayıklamayı denemeden önce *Web. config* dosyasının hata ayıklama için yapılandırıldığından emin olun.

**Bir *Web. config* dosyasını hata ayıklama için el ile yapılandırmak için:**

1. Visual Studio 'da ASP.NET projesinin *Web. config* dosyasını açın.

2. *Web. config* bir XML dosyasıdır, bu nedenle Etiketler tarafından işaretlenen iç içe yerleştirilmiş bölümler içerir. `configuration/system.web/compilation` bölümünü bulun. (`compilation` öğesi yoksa, oluşturun.)

3. `compilation` öğesindeki `debug` özniteliğinin `true`olarak ayarlandığından emin olun. (`compilation` öğesi bir `debug` özniteliği içermiyorsa, ekleyin ve `true`olarak ayarlayın.)

   Varsayılan IIS Express sunucusu yerine yerel IIS kullanıyorsanız, `compilation` öğesindeki `targetFramework` öznitelik değerinin IIS sunucusundaki çerçevesiyle eşleştiğinden emin olun.

   *Web. config* dosyasının `compilation` öğesi aşağıdaki örnekteki gibi görünmelidir:

   > [!NOTE]
   > Bu örnek, kısmi bir *Web. config* dosyasıdır. `configuration` ve `system.web` öğelerinde genellikle ek XML bölümleri vardır ve `compilation` öğesi de diğer öznitelikleri ve öğeleri içerebilir.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], *Web. config* dosyalarında yapılan değişiklikleri otomatik olarak algılar ve yeni yapılandırma ayarlarını uygular. Değişikliklerin etkili olması için bilgisayarı veya IIS sunucusunu yeniden başlatmanız gerekmez.

Bir Web sitesi, her birinde *Web. config* dosyaları ile çeşitli sanal dizinler ve alt dizinler içerebilir. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamalar, *Web. config* dosyalarından yapılandırma ayarlarını URL yolundaki daha yüksek düzeylerde devralınır. Hiyerarşik *Web. config* dosyası ayarları, hiyerarşideki tüm [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamalar için geçerlidir. Hiyerarşide daha düşük bir *Web. config* dosyasında farklı bir yapılandırmanın ayarlanması, daha yüksek dosyadaki ayarları geçersiz kılar.

Örneğin, <em>www.Microsoft.com/aaa/Web.config</em>içinde `debug="true"` belirtirseniz, *aaa* klasöründeki veya *aaa* 'ın herhangi bir alt klasöründeki tüm uygulamalar bu ayarı devralır, bu uygulamalardan biri ayarı kendi *Web. config* ile geçersiz kılar. dosyasýný.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Dosya sistemini kullanarak hata ayıklama modunda yayımlayın

Uygulamaları IIS 'de yayımlamanın farklı yolları vardır. Bu adımlarda, dosya sistemini kullanarak bir hata ayıklama yayımlama profili oluşturma ve dağıtma gösterilmektedir. Bunu yapmak için, Visual Studio 'Yu yönetici olarak çalıştırıyor olmanız gerekir.

> [!IMPORTANT]
> Kodunuzu değiştirirseniz veya yeniden oluşturursanız, yeniden yayımlamak için bu adımları yinelemeniz gerekir.

1. Visual Studio 'da projeye sağ tıklayın ve **Yayımla**' yı seçin.

3. **IIS, FTP, vb.** seçeneklerini belirleyip **Yayımla**' ya tıklayın.

    ![IIS 'de Yayımla](media/dbg-aspnet-local-iis.png "IIS 'de Yayımla")

4. **Customprofile** iletişim kutusunda, **Yayımla yöntemi**için **dosya sistemi**' ni seçin.

5. **Hedef konum**için, ( **...** ) **düğmesini** seçin.

   - ASP.NET için **yerel IIS**' yi seçin, uygulama için oluşturduğunuz Web sitesini seçin ve sonra **Aç**' ı seçin.

     ![ASP.NET 'de IIS 'ye yayımlama](media/dbg-aspnet-local-iis1.png "ASP.NET 'i IIS 'ye yayımlama")

   - ASP.NET Core için **dosya sistemi**' ni seçin, uygulama için ayarladığınız klasörü seçin ve **Aç**' ı seçin.

1. **İleri ' yi**seçin.

1. **Yapılandırma**altında, açılan listeden **Hata Ayıkla** ' yı seçin.

1. **Kaydet**' i seçin.

1. **Yayımla** Iletişim kutusunda **customprofile** (veya yeni oluşturduğunuz profilin adı) göründüğünden emin olun ve **Lastusedbuildconfiguration** **hata ayıklama**olarak ayarlanmıştır.

1. **Yayımla**' yı seçin.

    ![IIS 'de Yayımla](media/dbg-aspnet-local-iis-select-site.png "IIS 'de Yayımla")

> [!IMPORTANT]
> Hata ayıklama modu uygulamanızın performansını önemli ölçüde azaltır. En iyi performansı elde etmek için, *Web. config* 'de `debug="false"` ayarlayın ve bir üretim uygulaması dağıtırken veya performans ölçümleri yaparken bir yayın derlemesi belirleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET hata ayıklama: sistem gereksinimleri](aspnet-debugging-system-requirements.md)
- [Nasıl yapılır: Bir kullanıcı hesabı altında çalışan işlemini çalıştırma](how-to-run-the-worker-process-under-a-user-account.md)
- [Nasıl yapılır: ASP.NET işleminin adını bulma](how-to-find-the-name-of-the-aspnet-process.md)
- [Dağıtılmış Web uygulamalarında hata ayıklama](debugging-deployed-web-applications.md)
- [İzlenecek yol: Web formunda hata ayıklama](walkthrough-debugging-a-web-form.md)
- [Nasıl yapılır: ASP.NET özel durumlarında hata ayıklama](how-to-debug-aspnet-exceptions.md)
- [Web uygulamalarında hata ayıklama: hatalar ve sorun giderme](debugging-web-applications-errors-and-troubleshooting.md)
