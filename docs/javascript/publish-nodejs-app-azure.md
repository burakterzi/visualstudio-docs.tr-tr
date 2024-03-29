---
title: Linux App Service’e bir Node.js uygulaması yayımlama
description: Azure 'da Visual Studio 'da oluşturulan Node. js uygulamalarını Linux App Service yayımlayabilirsiniz
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c304aca5171e1addab9a941105f11fb534eaa5ff
ms.sourcegitcommit: e825d1223579b44ee2deb62baf4de0153f99242a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474021"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Bir Node. js uygulamasını Azure 'da yayımlama (Linux App Service)

Bu öğreticide, basit bir Node. js uygulaması oluşturma ve Azure 'da yayımlama görevi gösterilmektedir.

Bir Node. js uygulamasını Azure 'a yayımlarken birkaç seçenek vardır. Bunlar arasında Azure App Service, Kubernetes ile yönetim için Azure Container Service (AKS) bir VM çalıştıran bir VM, Docker kullanan bir kapsayıcı örneği ve daha fazlası bulunur. Bu seçeneklerin her biri hakkında daha fazla bilgi için bkz. [COMPUTE](https://azure.microsoft.com/product-categories/compute/).

Bu öğretici için, uygulamayı [Linux App Service](/azure/app-service/containers/app-service-linux-intro)'ye dağıtırsınız.
Linux App Service, Node. js uygulamasını çalıştırmak için bir Linux Docker kapsayıcısı dağıtır (Windows üzerinde IIS 'nin arkasındaki Node. js uygulamalarını çalıştıran Windows App Service aksine).

Bu öğreticide, Visual Studio için Node.js Araçları yüklenen bir şablondan başlayan bir Node. js uygulaması oluşturma, kodu GitHub 'daki bir depoya gönderme ve sonra Azure Web portalı aracılığıyla bir Azure App Service sağlama GitHub deposu. Azure App Service sağlamak ve kodu yerel bir git deposundan göndermek için komut satırını kullanmak için bkz. [Node. js uygulaması oluşturma](/azure/app-service/containers/quickstart-nodejs).

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kod için bir GitHub deposu oluşturun
> * Azure 'da Linux App Service oluşturma
> * Linux 'a dağıtma

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node. js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. **Node. js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![Node.js iş yükü VS yükleyicisi](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanı yüklü olması gerekir.

    Yüklü değilse, [Node. js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz. Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayıp **Özellikler**' i seçin).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Azure 'da çalıştırmak için bir Node. js projesi oluşturma

1. Visual Studio'yu açın.

1. Yeni bir TypeScript Express uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node. js**yazın ve ardından **Yeni temel Azure Node. js Express 4 uygulaması** (TypeScript) öğesini seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde **TypeScript**' i genişletin ve **Node. js**' yi seçin. Orta bölmede, **temel Azure Node. js Express 4 uygulaması**' nı seçin ve ardından **Tamam**' ı seçin.

    ![Yeni bir TypeScript Express uygulaması oluşturun](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    **Temel Azure Node. js Express 4 uygulama** projesi şablonunu görmüyorsanız **Node. js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio projeyi oluşturur ve Çözüm Gezgini (sağ bölme) içinde açar.

1. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın ve her şeyin beklendiği gibi çalıştığından emin olun.

1. Proje için yerel bir git deposu oluşturmak üzere **dosya** > **kaynak denetimine Ekle** ' yi seçin.

    Bu noktada, Express çerçevesini kullanan ve TypeScript 'te yazılan bir Node. js uygulaması çalışıyor ve yerel kaynak denetimine iade edildi.

1. Sonraki adımlara geçmeden önce projeyi istediğiniz gibi düzenleyin.

## <a name="push-code-from-visual-studio-to-github"></a>Visual Studio 'dan GitHub 'a kod gönderme

Visual Studio için GitHub 'ı ayarlamak için:

1. [Visual Studio Için GitHub uzantısının](https://visualstudio.github.com/) , **uzantılar ve güncelleştirmeler** > menü öğesi **araçları** kullanılarak yüklendiğinden ve etkinleştirildiğinden emin olun.

2. Menüden **görünüm** > **diğer pencereler** > **GitHub**' ı seçin.

    GitHub penceresi açılır.

3. GitHub penceresinde **Başlarken** düğmesini görmüyorsanız **Dosya** > **kaynak denetimine Ekle** ' ye tıklayın ve Kullanıcı arabiriminin güncelleştirilmesini bekleyin.

    ![GitHub penceresini açın](../javascript/media/azure-github-get-started.png)

4. **Başlarken**' e tıklayın.

    Zaten GitHub 'a bağlıysanız, araç kutusu aşağıdaki çizime benzer şekilde görünür.

    ![GitHub depo ayarları](../javascript/media/azure-github-publish.png)

5. Yayımlanacak yeni deponun alanlarını tamamlayıp **Yayımla**' ya tıklayın.

    Birkaç dakika sonra, "depo başarıyla oluşturuldu" belirten bir başlık görüntülenir.

    Sonraki bölümde, bu depodan Linux üzerinde bir Azure App Service nasıl yayımlayacağınızı öğreneceksiniz.

## <a name="create-a-linux-app-service-in-azure"></a>Azure 'da Linux App Service oluşturma

1. [Azure Portal](https://portal.azure.com)oturum açın.

2. Sol taraftaki hizmetler listesinden **uygulama hizmetleri** ' ni seçin ve ardından **Ekle**' ye tıklayın.

3. Gerekirse, yeni bir kaynak grubu oluşturun ve yeni uygulamayı barındırmak için plan App Service.

4. **Işletim sistemini** **Linux**'a ayarladığınızdan emin olun ve **çalışma zamanı yığınını** çizimde gösterildiği gibi gerekli Node. js sürümüne ayarlayın.

    ![Linux App Service oluşturma](../javascript/media/azure-create-appservice-annotated.png)

5. App Service oluşturmak için **Oluştur** ' a tıklayın.

    Dağıtım birkaç dakika sürebilir.

6. Dağıtıldıktan sonra, **uygulama ayarları** bölümüne gidin ve `SCM_SCRIPT_GENERATOR_ARGS` adı ve `--node`değeri olan bir ayar ekleyin.

    ![Uygulama ayarları](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > App Service dağıtım işlemi, deneyebileceğiniz ve çalıştırılacak uygulama türünü belirleyen bir buluşsal yöntem kümesi kullanır. Bir. dağıtılan içerikte *bir dosya dosyası* algılanırsa, MSBuild tabanlı bir projenin dağıtılmakta olduğunu varsayacaktır. Yukarıda eklenen ayar bu mantığı geçersiz kılar ve açıkça bunun bir Node. js uygulaması olduğunu belirtir. Bu ayar olmadan, Node. js uygulaması,. *sln* dosyası, App Service dağıtılan deponun bir parçasıdır.

7. **Uygulama ayarları**' nın altında, adı `WEBSITE_NODE_DEFAULT_VERSION` ve `8.9.0`değeri olan başka bir ayar ekleyin.

8. Dağıtıldıktan sonra, App Service açın ve **dağıtım seçenekleri**' ni seçin.

    ![Dağıtım seçenekleri](../javascript/media/azure-deployment-options.png)

9. **Kaynak Seç**' e tıklayın ve ardından **GitHub**' ı seçin ve ardından gerekli izinleri yapılandırın.

    ![GitHub izinleri](../javascript/media/azure-choose-source.png)

10. Yayımlanacak depoyu ve dalı seçin ve ardından **Tamam**' ı seçin.

    ![Linux App Service’e yayımlama](../javascript/media/azure-repo-and-branch.png)

    **Dağıtım seçenekleri** sayfası eşitleme sırasında görüntülenir.

    ![GitHub ile dağıtma ve eşitleme](../javascript/media/azure-deployment-options-sync.png)

    Eşitleme tamamlandıktan sonra bir onay işareti görünür.

    Site artık GitHub deposundan Node. js uygulamasını çalıştırıyor ve Azure App Service için oluşturulan URL 'den (varsayılan olarak, ". azurewebsites.net" tarafından izlenen Azure App Service verilen ad) erişilebilir.

## <a name="modify-your-app-and-push-changes"></a>Uygulamanızı değiştirin ve değişiklikleri gönderin

1. Burada gösterilen kodu, satır `app.use('/users', users);`sonra *app. TS* ' de ekleyin. Bu, */API*URL 'sinde bir REST API ekler.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Kodu derleyin ve yerel olarak test edin, sonra iade edin ve GitHub 'a gönderin.

    Azure portal, GitHub deposunda yapılan değişiklikleri algılamak birkaç dakika sürer ve ardından dağıtımın yeni bir eşitlemesi başlar. Bu, aşağıdaki resme benzer şekilde görünür.

    ![Değiştir ve Eşitle](../javascript/media/azure-changes-detected.png)

3. Dağıtım tamamlandıktan sonra ortak siteye gidin ve URL 'ye */API* ekleyin. JSON yanıtı döndürülür.

## <a name="troubleshooting"></a>Sorun giderme

* Node. exe işlemi (yani, işlenmeyen bir özel durum oluşursa), kapsayıcı yeniden başlatılır.
* Kapsayıcı başladığında, Node. js işlemini nasıl başlatacağınızı anlamak için çeşitli buluşsal yöntemler aracılığıyla çalışır. Uygulamanın ayrıntıları [Generatestartupcommand. js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js)' de görülebilir.
* Araştırmalar için SSH aracılığıyla çalışan kapsayıcıya bağlanabilirsiniz. Bu, Azure portal kullanılarak kolayca yapılır. App Service seçin ve **geliştirme araçları** bölümü altında **SSH** 'ye ulaşıncaya kadar araç listesini aşağı kaydırın.
* Sorun gidermeye yardımcı olmak için, App Service için **tanılama günlükleri** ayarlarına gidin ve **Docker kapsayıcı günlüğü** ayarını **dosya sistemine**çevirin. Günlükler */Home/LogFiles/* _docker. log * altındaki kapsayıcıda oluşturulur ve SSH veya FTP kullanılarak kutudan erişilebilir.
* Varsayılan olarak atanmış *. azurewebsites.net URL 'SI yerine siteye özel bir etki alanı adı atanabilir. Daha ayrıntılı bilgi için bkz. [özel etki alanı eşleme](/azure/app-service/app-service-web-tutorial-custom-domain)konusu.
* Üretime geçmeden önce daha fazla test için bir hazırlama sitesine dağıtım en iyi uygulamadır. Bunun nasıl yapılandırılacağı hakkında ayrıntılı bilgi için, [hazırlama ortamları oluşturma](/azure/app-service/web-sites-staged-publishing)konusuna bakın.
* Daha sık sorulan sorular için [Linux 'ta App Service](/azure/app-service/containers/app-service-linux-faq) bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir Linux App Service oluşturmayı ve bir Node. js uygulamasını hizmete dağıtmayı öğrendiniz. Linux App Service hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
