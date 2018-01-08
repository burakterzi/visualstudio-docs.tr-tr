---
title: "Hızlı Başlangıç: İlk Python web uygulamanızı oluşturmak için Visual Studio'yu kullanın. | Microsoft Docs"
ms.custom: 
ms.date: 12/1/2017"
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: python
author: kraigb
ms.author: kraigb
manager: ghogen
dev_langs: python
ms.workload: python
ms.openlocfilehash: bf0a6e187a98a03d3beed33537fe5244ecd5d35d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Hızlı Başlangıç: İlk Python web uygulamanızı oluşturmak için Visual Studio'yu kullanın.

Bu 5-10 dakikalık bir giriş Visual Studio tümleşik geliştirme ortamı (IDE), basit bir Python web uygulaması oluşturun. Visual Studio henüz yüklemediyseniz, ücretsiz yükleme [burada](http://www.visualstudio.com).

## <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio 2017'ni açın.

1. Üst menü çubuğundan seçin **Dosya > Yeni > Proje...** .

1. İçinde **yeni proje** iletişim kutusunda, sol bölmede, genişletin **diğer diller**seçeneğini belirleyip **Python**. Orta bölmede seçin **Web projesi**, proje "HelloPython" gibi bir ad verin ve ardından **Tamam**.

    İşyeri dışında Python proje şablonları görmüyorsanız, İptal **yeni proje** iletişim kutusuna ve üst menü çubuğundan seçin **Araçlar > alma araçları ve özelliklerinin...**  Visual Studio yükleyicisi açın. Seçin **Python geliştirme** iş yükü, ardından **Değiştir**.

    ![Visual Studio yükleyicisi Python geliştirme iş yükü](../python/media/installation-python-workload.png)

1. Yeni Proje açılır **Çözüm Gezgini** sağ bölmede. Proje, bu noktada, diğer bir dosyaları içerdiği için boştur.

    ![Yeni oluşturulan boş proje gösteren Çözüm Gezgini](media/quickstart-python-01-empty-project.png)

## <a name="install-the-falcon-library"></a>Falcon kitaplığını yükle

Web uygulamalarında Python neredeyse her zaman birçok kullanılabilir Python kitaplıklarından birini yönlendirme web isteklerini ve yanıtlarını şekillendirme gibi alt düzey ayrıntıların işlemek için kullanır. Visual Studio'da Python geliştirme iş yükü sağlar [şablonları web uygulamaları için çeşitli](../python/template-web.md) Bottle, Flask ve Django kitaplıklar oluşturulmuştur.

Bu hızlı başlangıç ancak farklı bir kitaplık kullanmak [Falcon](https://falconframework.org/), bir paketi yükleme ve web uygulaması sıfırdan oluşturma işleminde yaşamaya. Kolaylık olması için aşağıdaki adımları Falcon varsayılan genel ortamına yükleyin.

1. Genişletme **Python ortamları** proje için varsayılan ortamı görmek için proje düğümünde.

    ![Varsayılan ortam gösteren Çözüm Gezgini](media/quickstart-python-02-default-environment.png)

1. Ortam sağ tıklatıp **Python paketini yükle...** . Bu komut açar **Python ortamları** penceresinde **paketleri** sekmesi. Arama alanına "falcon" girin ve **"PIP yükle falcon" Pypı**. Sizden yönetici ayrıcalıkları kabul edin ve gözlemlemek **çıkış** ilerleme için Visual Studio penceresinde.

    ![Falcon kitaplığı yükleme](media/quickstart-python-03-install-package.png)

1. Bir kez yüklendikten sonra ortamında kitaplık görünür **Çözüm Gezgini**, yapabileceğiniz anlamına bunu Python kodu kullanın.

    ![Yüklü falcon kitaplığı](media/quickstart-python-04-package-installed.png)

Belirli bir proje için kitaplıkları yükleneceği kitaplıkları genel ortamında yüklemek yerine, geliştiriciler genellikle "sanal ortam" oluşturduğunuz unutmayın. Visual Studio birçok Python proje şablonlarını içeren bir `requirements.txt` şablonu bağımlı olduğu kitaplıkları listeler dosya. Bu şablonlardan birini proje oluşturma içine kitaplıkların yüklü bir sanal ortamın oluşturulmasını tetikler. Daha fazla bilgi için bkz: [Python ortamları - sanal ortamlar](../python/python-environments.md#virtual-environments).

## <a name="add-a-code-file"></a>Bir kod dosyası ekleme

Artık bir en az bir web uygulaması uygulamak için Python kodu biraz eklemek hazırsınız.

1. ' Nde projeye sağ **Çözüm Gezgini** seçip **Ekle > Yeni öğe...** . Görüntülenen iletişim kutusunda, seçin **boş Python dosyası**, adlandırın `hello.py`ve seçin **Tamam**. Visual Studio dosya Düzenleyicisi penceresinde otomatik olarak açılır. (Genel olarak, **Ekle > Yeni öğe...**  komut dosyaları farklı türde bir projeye eklemek için bir yoldur harika öğe şablonları genellikle yararlı Demirbaş kod sağlayın.)

1. Kopyala-yapıştır veya aşağıdaki kodu girin `hello.py`:

    ```python
    import falcon
    api = falcon.API()

    # In Falcon, define a class for each resource; the on_get 
    # method then handles any GET requests.

    class HelloResource:
        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to the HelloResource
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

Falcon hakkında daha fazla bilgi için bkz: [Falcon Quickstart](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Uygulamayı çalıştırın

1. Sağ `hello.py` içinde **Çözüm Gezgini** seçip **başlangıç dosyası olarak ayarlamak**. Bu komut, uygulama çalışırken Python içinde başlatmak için kod dosyası tanımlar.

1. "Hello Python" projeye sağ **Çözüm Gezgini** seçip **özellikleri**. Ardından **hata ayıklama** sekmesinde ve ayarlama **bağlantı noktası numarası** özelliğine `8080`. Bu adım, Visual Studio bir tarayıcı ile başlatır sağlar `localhost:8080` rastgele bir bağlantı noktası kullanarak yerine.

1. Seçin **hata ayıklama > hata ayıklama olmadan Başlat** (dosyalara değişiklikleri kaydedin ve uygulamayı çalıştırmak için Ctrl + F5).

1. "Başlangıç web uygulaması sunucusu" iletisiyle bir komut penceresi görüntülenir, sonra için bir tarayıcı penceresi açılır `localhost:8080` iletisini görürseniz burada "Hello, Python!" GET isteğini da komut penceresinde görünür. (Yalnızca Python etkileşimli Kabuk komut penceresinde görürseniz, bu pencereyi kısaca ekranda yanıp sönen varsa, ayarladığınız emin olun veya `hello.py` başlangıç dosyası olarak yukarıdaki adım 1.)

1. Uygulama durdurmak için komut penceresini kapatın.

## <a name="next-steps"></a>Sonraki adımlar

İçinde biraz Python ile Visual Studio IDE hakkında öğrendiğinize Bu hızlı başlangıç Tamamlanıyor tebrikler. Visual Studio'da etkileşimli penceresini kullanarak da dahil olmak üzere, veri görselleştirme, hata ayıklama ve Git ile çalışma, Python daha eksiksiz bir öğretici devam etmek için aşağıdaki düğmesini seçin.

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio'da Python ile çalışmaya başlama](../python/vs-tutorial-01-01.md).

- Hakkında bilgi edinin [Python web Visual Studio'da Uygulama Şablonları](../python/template-web.md)
- Daha fazla bilgi edinmek [Visual Studio IDE](../ide/visual-studio-ide.md)
- Nasıl kullanacağınızı öğrenin [Visual Studio hata ayıklayıcısı](../debugger/debugger-feature-tour.md)