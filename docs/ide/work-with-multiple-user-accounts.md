---
title: Birden çok kullanıcı hesabıyla çalışma
ms.date: 07/23/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5993d550d85cdc0bd1c9ce6b72553eda6fc280e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647072"
---
# <a name="work-with-multiple-user-accounts"></a>Birden çok kullanıcı hesabıyla çalışma

Birden çok Microsoft hesabınız ve/veya iş veya okul hesabınız varsa, bu kaynakları ayrı olarak oturum açmanıza gerek kalmadan herhangi bir hesaptan erişebilmek için, tümünü Visual Studio 'ya ekleyebilirsiniz. Azure, Application Insights, Azure DevOps ve Office 365 Hizmetleri, kolaylaştırılmış oturum açma deneyimini destekler.

Bir makineye birden çok hesap ekledikten sonra, başka bir makinede Visual Studio 'da oturum açarsanız, bu hesap kümesi sizinle gezinbir şekilde yapılır.

> [!NOTE]
> Hesap adları dolaşımda olsa da, kimlik bilgileri. Yeni bir makinede kaynaklarını ilk kez kullanmaya çalıştığınızda, bu hesapların kimlik bilgilerini girmeniz istenir.

Bu makalede, Visual Studio 'ya nasıl birden çok hesap ekleyeceğiniz gösterilmektedir. Ayrıca, **bağlı hizmet ekle** iletişim kutusu, **Sunucu Gezgini**ve **Takım Gezgini**gibi yerlerde bu hesaplardan erişilebilir kaynakları nasıl göregösterdiğini gösterir.

## <a name="sign-in-to-visual-studio"></a>Visual Studio’da oturum açma

Microsoft hesabı veya kurumsal hesapla Visual Studio 'da oturum açın. Kullanıcı adınızın pencerenin üst köşesinde göründüğünü, buna benzer şekilde görmeniz gerekir:

![Şu anda oturum açmış Kullanıcı](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Sunucu Gezgini Azure hesabınıza erişin

Sunucu Gezgini açmak için **görünüm**  > **Sunucu Gezgini** ' yı seçin (veya "genel" [ortam ayarlarını](../ide/environment-settings.md)kullanıyorsanız, **CTRL** +**alt** +**S**) tuşuna basın. **Azure** düğümünü genişletin ve Visual Studio 'da oturum açmak için kullandığınız hesapla ilişkili Azure hesabında kullanılabilir kaynakları içerdiğine dikkat edin. Aşağıdaki resme benzer şekilde görünür:

![Azure node genişletilmiş Sunucu Gezgini](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Belirli bir cihazda Visual Studio 'Yu ilk kez kullandığınızda, iletişim kutusu yalnızca ile oturum açtığınız hesap altına kaydedilen abonelikleri gösterir. **Azure** düğümüne sağ tıklayıp **abonelikleri Yönet ve filtrele**' yi seçip hesap Seçicisi denetiminden hesaplarınızı ekleyerek, diğer hesaplarınızdan herhangi birine ait kaynaklara doğrudan **Sunucu Gezgini** erişebilirsiniz. İsterseniz aşağı oka tıklayıp hesaplar listesinden seçerek başka bir hesap seçebilirsiniz. Hesabı seçtikten sonra, bu hesabın altındaki hangi aboneliklerin **Sunucu Gezgini**görüntüleneceğini özelleştirebilirsiniz.

![Azure aboneliklerini yönetme iletişim kutusu](../ide/media/vs2015_manage_subs.png)

**Sunucu Gezgini**bir sonraki açışınızda, bu aboneliğin kaynakları görüntülenir.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Bağlı hizmet Ekle iletişim kutusu aracılığıyla Azure hesabınıza erişin

1. Mevcut bir projeyi açın veya yeni bir proje oluşturun.

1. **Çözüm Gezgini**' de proje düğümünü seçin ve ardından sağ tıklayıp  > **bağlı hizmet** **Ekle** ' yi seçin.

   **Bağlı hizmet ekle** Sihirbazı görüntülenir ve Visual Studio kişiselleştirme hesabınızla ilişkili Azure hesabındaki hizmetlerin listesini gösterir. Azure 'da ayrı olarak oturum açmanıza gerek yoktur. Ancak, farklı bir makineden kaynaklarına ilk kez erişmeye çalıştığınızda diğer hesaplarda oturum açmanız gerekir.

### <a name="access-azure-active-directory-in-a-web-project"></a>Web projesindeki Azure Active Directory erişim

Azure Active Directory (AAD), Web API hizmetlerindeki ASP.NET MVC web uygulamalarında veya AD kimlik doğrulamasında Son Kullanıcı çoklu oturum açma desteği sunar. Etki alanı kimlik doğrulaması, bireysel kullanıcı hesabı kimlik doğrulamasından farklıdır. Active Directory etki alanına erişimi olan kullanıcılar, Web uygulamalarınıza bağlanmak için mevcut AAD hesaplarını kullanabilir. Office 365 uygulamaları, etki alanı kimlik doğrulaması da kullanabilir.

::: moniker range="vs-2017"

Bunu eylemde görmek için yeni bir **ASP.NET Core Web uygulaması** projesi oluşturun. **Yeni ASP.NET Core Web uygulaması** Iletişim kutusunda **Web uygulaması** şablonunu seçin ve ardından **kimlik doğrulamayı Değiştir**' i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

Bunu eylemde görmek için yeni bir **ASP.NET Core Web uygulaması** projesi oluşturun. **Yeni bir ASP.NET Core Web uygulaması oluştur** sayfasında, **Web uygulaması** şablonunu seçin ve ardından **kimlik doğrulaması**altında **Değiştir** ' i seçin.

::: moniker-end

Uygulamanızda kullanılacak kimlik doğrulaması türünü seçebileceğiniz **kimlik doğrulamayı Değiştir** iletişim kutusu görüntülenir.

![ASP.NET için kimlik doğrulama iletişim kutusunu değiştirme](../ide/media/vs2015_change_authentication.png)

ASP.NET ' de farklı kimlik doğrulama türleri hakkında daha fazla bilgi için bkz. [Visual Studio 'da ASP.NET Web projeleri oluşturma](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Azure DevOps kuruluşunuza erişin

Ana menüden **takım**  > **Bağlantıları Yönet** ' i seçerek **Takım Gezgini-Bağlan** penceresini açın. **Bir projeye bağlanmak** >  **Bağlantıları Yönet** ' i seçin. **Bir projeye Bağlan** iletişim kutusunda listeden bir proje seçin (veya **TFS sunucusu Ekle** ' yi seçin ve sunucunuza URL 'yi girin). Bir URL seçtiğinizde, kimlik bilgilerinizi yeniden girmeye gerek kalmadan oturum açarsınız.

Daha fazla bilgi için bkz. [Takım Gezgini projelere bağlanma](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Visual Studio 'ya ek hesap ekleme

Visual Studio 'ya ek bir hesap eklemek için:

1. **Dosya**  > **Hesap ayarları**' nı seçin.

1. **Tüm hesaplar**altında **Hesap Ekle**' yi seçin.

1. **Hesabınızda oturum açın** sayfasında hesabı seçin veya **başka bir hesap kullan**' ı seçin. Yeni hesap kimlik bilgilerini girmek için istemleri izleyin.

Seçim Artık **Sunucu Gezgini** giderek, yeni eklediğiniz hesapla ilişkili Azure hizmetlerini görebilirsiniz. **Sunucu Gezgini**' de, **Azure** düğümüne sağ tıklayın ve **abonelikleri Yönet ve filtrele**' yi seçin. Geçerli hesabın yanındaki aşağı açılan oka tıklayarak yeni hesabı seçin ve ardından **Sunucu Gezgini**hangi abonelikleri göstermek istediğinizi seçin. Belirtilen abonelikle ilişkili tüm hizmetleri görmeniz gerekir. Şu anda ikinci hesapla Visual Studio 'da oturum açmış olsanız da bu hesabın Hizmetleri ve kaynaklarında oturum açtınız. Aynı değer, **proje**  > **bağlı hizmet ekleme** ve **Takım**  >  Team Foundation Server 'e**bağlanması**için de geçerlidir.

### <a name="add-an-account-using-device-code-flow"></a>Cihaz kod akışı kullanarak hesap ekleme

Bazı durumlarda, oturum açamaz ve düzenli olarak bir hesap ekleyemezsiniz. Bu durum Internet Explorer bazı nedenlerle engellenmişse veya ağınız bir güvenlik duvarının arkasındaysa oluşabilir. Bu sorunu geçici olarak çözmek için, *cihaz kodu akışını* bir hesap eklemek veya hesabınızı yeniden kimlik doğrulaması yapmak üzere etkinleştirebilirsiniz. Cihaz kod akışı, farklı bir tarayıcı veya fiziksel ya da sanal (VM) &mdash;either farklı bir makine kullanarak oturum açmanıza olanak tanır.

Cihaz kod akışını kullanarak oturum açmak için:

1. **Araçlar**  > **Seçenekler**  > **ortam**altında [**hesaplar**](reference/accounts-environment-options-dialog-box.md) sayfasını açın ve **bir hesabı eklerken veya yeniden doğrularken cihaz kod akışını etkinleştir**' i seçin. Seçenekler sayfalarını kapatmak için **Tamam ' ı** seçin.

1. Hesap Yönetimi sayfasını açmak için **dosya**  > **Hesap ayarları** ' nı seçin.

1. **Tüm hesaplar**altında **Hesap Ekle** ' yi seçin.

   Bir iletişim kutusu, bir Web tarayıcısına yapıştıracağınız URL ve kodu gösterir.

   ![Cihaz kod akışı URL 'SI ve kodu](media/work-with-multiple-user-accounts/device-login-code.png)

1. İletişim kutusunun metnini kopyalamak için **Ctrl** +**C** tuşlarına basın ve ardından Iletişim kutusunu kapatmak için **Tamam** ' ı seçin. Kopyaladığınız metni Not Defteri gibi bir metin düzenleyicisine yapıştırın. Bu, bir sonraki adımda kodu kopyalamayı kolaylaştırır.

1. Visual Studio 'da oturum açmak için kullanmak istediğiniz makinede veya Web tarayıcısında bulunan cihaz oturum açma URL 'sine gidin ve ardından **kodu**yazan kutuya kopyaladığınız kodu yapıştırın veya girin.

   **Visual Studio** uygulamasının adı sayfada daha aşağı görünmelidir.

1. **Visual Studio**altında **devam**' ı seçin.

   ![Device-Login-Page. png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Hesap kimlik bilgilerinizi girmek için istemleri izleyin.

   Cihazınızda Visual Studio 'da oturum açmış olduğunu ve tarayıcı penceresini kapatadığınızı bildiren bir sayfa görüntülenir.

   ![Visual Studio tarayıcı aracılığıyla oturum açma tamam](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Visual Studio 'daki hesap yönetimi sayfasına geri dönün ve yeni eklenen hesabı **tüm hesaplar**altında listelenmiş olarak görürsünüz. **Kapat**' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
- [Mac için Visual Studio oturum açın](/visualstudio/mac/signing-in)
