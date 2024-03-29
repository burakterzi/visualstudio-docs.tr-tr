---
title: Visual Studio adım 2, görünümler ve şablonlar 'daki Flask öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask temel bilgileri, özellikle bir uygulama oluşturma ve görünümleri ve şablonları kullanma adımları.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1786c8c57c841744ed27b03e4969fe2bd21ce2c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985188"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>2\. Adım: görünümler ve sayfa şablonlarıyla bir Flask uygulaması oluşturma

**Önceki adım: [Visual Studio projesi ve çözümü oluşturma](learn-flask-visual-studio-step-01-project-solution.md)**

Bu öğreticinin 1. adımında sahip olduğunuz şey, tek bir sayfadaki ve tüm kodun tek bir dosyada yer aldığı Flask uygulamasıdır. Gelecekte geliştirmeye izin vermek için, kodu yeniden düzenleme ve sayfa şablonları için bir yapı oluşturma en iyisidir. Özellikle, uygulamanın görünümleri için kodu başlangıç kodu gibi diğer yollardan ayırmak istersiniz.

Bu adımda şu adımları öğrenebilirsiniz:

> [!div class="checklist"]
> - Başlangıç kodundan görünümleri ayırmak için uygulamanın kodunu yeniden düzenleyin (adım 2-1)
> - Sayfa şablonu kullanarak bir görünüm işleme (adım 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Adım 2-1: daha fazla geliştirmeyi desteklemek için projeyi yeniden düzenleme

"Boş Flask Web projesi" şablonu tarafından oluşturulan kodda, tek bir görünümle birlikte başlangıç kodu içeren tek bir *app.py* dosyanız vardır. Birden çok görünüm ve şablon içeren bir uygulamanın daha fazla geliştirmesinde izin vermek için, bu kaygıları ayırmak en iyisidir.

1. Proje klasörünüzde `HelloFlask` adlı bir uygulama klasörü oluşturun ( **Çözüm Gezgini** projeye sağ tıklayın ve **Yeni > klasör** **Ekle** ' yi seçin.)

2. *Helloflask* klasöründe, `Flask` örneğini oluşturan ve uygulamanın görünümlerini yükleyen (bir sonraki adımda oluşturulan) *\_\_init\_\_. Kopyala* adlı bir dosya oluşturun:

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. *Helloflask* klasöründe, aşağıdaki içeriklerle *views.py* adlı bir dosya oluşturun. *\_\_init\_\_. Kopyala*; `import HelloFlask.views` kullandığınız için ad *views.py* . adlar eşleşmezse çalışma zamanında bir hata görürsünüz.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    İşlevi ve `home`yolunu yeniden adlandırmanın yanı sıra, bu kod *app.py* adresinden sayfa işleme kodunu içerir ve *\_\_init\_\_. kopyala*içinde belirtilen `app` nesnesini içeri aktarır.

4. *Helloflask* adlı *şablonlarda*, şimdilik boş kalan bir alt klasör oluşturun.

5. Projenin kök klasöründe *app.py* *olarak yeniden*adlandırın ve içeriğin aşağıdaki kodla eşleştiğinden emin olun:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```

6. Proje yapınız aşağıdaki görüntüye benzer şekilde görünmelidir:

    ![Kodu yeniden düzenlemeye başladıktan sonra proje yapısı](media/flask/step02-project-structure.png)

7. Uygulamayı başlatmak ve bir tarayıcı açmak için, hata **ayıklamayı Başlat** (**F5**) > **Hata Ayıkla** ' yı seçin veya araç çubuğundaki **Web sunucusu** düğmesini (değişiklik gösterebilir) kullanın. Hem/hem de/Home URL 'SI yollarını deneyin.

8. Ayrıca, kodun çeşitli bölümlerinde kesme noktaları ayarlayabilir ve başlangıç sırasını izlemek için uygulamayı yeniden başlatabilirsiniz. Örneğin, *runserver.py* ve *Helloflask\_* init_ *. Kopyala*' nın ilk satırlarında ve *views.py*içindeki `return "Hello Flask!"` satırında bir kesme noktası ayarlayın. Ardından uygulamayı yeniden başlatın (**hata ayıkla** > **yeniden başlat**, **CTRL**+**F5**veya araç çubuğu düğmesi aşağıda**gösterilmiştir) ve** **F5**kullanarak her bir kesme noktasından çalıştırın.

    ![Visual Studio 'da hata ayıklama araç çubuğunda yeniden Başlat düğmesi](media/debugging-restart-toolbar-button.png)

9. İşiniz bittiğinde uygulamayı durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine Kaydet

Kodunuzda değişiklik yaptığınız ve bunları başarıyla test ettiğiniz için, değişiklikleri gözden geçirmek ve kaynak denetimine uygulamak harika bir süredir. Bu öğreticideki sonraki adımlar, kaynak denetimine yeniden kaydolmasını ve bu bölüme geri dönebilmeniz için uygun zamanları hatırlatır.

1. **Takım Gezgini**gittiği, Visual Studio 'nun alt kısmındaki (aşağıda daire içinde) bulunan değişiklikler düğmesini seçin.

    ![Visual Studio durum çubuğunda kaynak denetimi değişiklikleri düğmesi](media/flask/step02-source-control-changes-button.png)

1. **Takım Gezgini**' de, "kodu yeniden Düzenle" gibi bir teslim iletisi girin ve **Tümünü Kaydet**' i seçin. Kayıt tamamlandığında, **karma > yerel olarak oluşturulan bir Ileti tamamlama \<görürsünüz. Değişikliklerinizi sunucuyla paylaşmak için eşitleyin.** Değişiklikleri uzak deponuza göndermek istiyorsanız **Eşitle**' yi ve ardından **giden işlemeler**altında **Gönder** ' i seçin. Ayrıca, uzaktan göndermeden önce birden çok yerel işleme de birikmeniz gerekir.

    ![Takım Gezgini 'da yürütmeleri uzak 'a gönderme](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Soru: kaynak denetimine ne sıklıkla bir kayıt yapılmalıdır?

Cevap: kaynak denetimine değişiklikler uygulamak, değişiklik günlüğünde bir kayıt oluşturur ve gerekirse depoyu döndüremezsiniz. Her bir kayıt, belirli değişiklikler için de incelenebilir. Git 'teki işlemeler pahalı olduğundan, çok sayıda değişikliği tek bir işlemede biriktirmek yerine sık yapılan işlemeler yapmak daha iyidir. Açık olarak, tek tek dosyalarda her küçük değişikliği yürütmeniz gerekmez. Genellikle bir özellik eklerken, bu adımda yaptığınız gibi bir yapıyı değiştirirken veya kod yeniden düzenlemesi yaptığınızda bir işlem yaparsınız. Ayrıca herkes için en iyi şekilde çalışan yürütmelerin ayrıntı düzeyi için ekibinizdeki diğer kullanıcılarla görüşün.

Ne sıklıkla işlemeniz ve bir uzak depoya yürütmelerin ne sıklıkta gönderirsiniz iki farklı kaygılardır. Yerel deponuzda, uzak depoya göndermeden önce birden fazla yürütme birikmesini sağlayabilirsiniz. Ne sıklıkta yaptığınız, takımınızın depoyu nasıl yönetmek istediğini bağlıdır.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Adım 2-2: bir sayfayı işlemek için şablon kullanma

Şimdiye kadar *views.py* sahip olduğunuz `home` işlevi, sayfa için düz metın bir HTTP yanıtından daha fazla şey oluşturuyor. Ancak, çoğu gerçek dünya Web sayfası, genellikle canlı verileri birleştiren zengin HTML sayfalarıyla yanıt verir. Aslında, bir işlevi kullanarak bir görünüm tanımlamanın birincil nedeni içeriği dinamik olarak oluşturmak.

Görünümün dönüş değeri yalnızca bir dize olduğundan, dinamik içerik kullanarak bir dize içinde istediğiniz herhangi bir HTML oluşturabilirsiniz. Ancak, biçimlendirmeyi verilerden ayırmak en iyi şekilde, biçimlendirmeyi bir şablona yerleştirmek ve verileri kodda tutmak çok daha iyidir.

1. Başlangıçlarda, *views.py* öğesini düzenleyerek, sayfa için bazı dinamik içeriğe sahip satır içi HTML kullanan aşağıdaki kodu içeren bir düzenleme:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Tarihi/saati güncelleştirildiğini görmek için uygulamayı çalıştırın ve sayfayı birkaç kez yenileyin. İşiniz bittiğinde uygulamayı durdurun.

1. Sayfa işlemesini bir şablon kullanacak şekilde dönüştürmek için, aşağıdaki içeriğe sahip *Şablonlar* klasöründe *index. html* adlı bir dosya oluşturun; burada `{{ content }}`, sizin için bir yer tutucu veya değiştirme belirteci ( *şablon değişkeni*olarak da bilinir) kodda bir değer girin:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Şablonu yüklemek için `render_template` kullanmak üzere `home` işlevini değiştirin ve "içerik" için bir değer sağlayın. Bu işlem, yer tutucunun adıyla eşleşen adlandırılmış bir bağımsız değişken kullanılarak yapılır. Flask *Şablonlar* klasöründeki şablonları otomatik olarak arar, bu nedenle şablonun yolu bu klasöre göre belirlenir:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Uygulamayı çalıştırın, sonuçları görün ve şablon altyapısı (Jınja) otomatik olarak HTML içeriğini iptal ettiğinden `content` değerindeki satır içi HTML 'nin HTML *olarak* işlenmediğini gözlemleyin. Otomatik kaçış, yanlışlıkla güvenlik açıklarına ekleme saldırılarına engel olur: geliştiriciler genellikle bir sayfadan giriş toplar ve şablonu bir şablon yer tutucusu aracılığıyla bir değer olarak kullanır. Kaçış Ayrıca, HTML 'nin koddan en iyi şekilde tutulmasını sağlayan bir anımsatıcı işlevi görür.

    Buna uygun olarak, her bir veri parçası için biçimlendirme içindeki farklı yer tutucuları içerecek şekilde *templates\ındex.html dosyasını* gözden geçirin:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Ardından `home` işlevini, tüm yer tutucular için değer sağlayacak şekilde güncelleştirin:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Düzgün şekilde işlenmiş çıktıyı görmek için uygulamayı yeniden çalıştırın.

    ![Şablonu kullanarak uygulamayı çalıştırma](media/flask/step02-result.png)

1. Değişikliklerinizi kaynak denetimine kaydedin ve isterseniz, uzak deponuzu [adım 2-1](#commit-to-source-control)' de açıklandığı gibi güncelleştirin.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: sayfa şablonlarının ayrı bir dosyada olması gerekir mi?

Cevap: Şablonlar genellikle ayrı HTML dosyalarında tutulabilse de, bir satır içi şablonu da kullanabilirsiniz. Ancak, biçimlendirme ve kod arasında temiz ayrımı sürdürmek için, ayrı bir dosya kullanılması önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: şablonlar. html dosya uzantısını kullanmalıdır mi?

Cevap: `render_template` işlevine ilk bağımsız değişkende dosyanın tam yolunu her zaman tanımlayacağından, sayfa şablonu dosyaları için *. html* uzantısı tamamen isteğe bağlıdır. Ancak, Visual Studio (ve diğer düzenleyiciler), genellikle, sayfa şablonlarının tamamen HTML olmaması durumunda kod tamamlama ve *. html* dosyalarıyla söz dizimi renklendirme gibi özellikler sağlar.

Aslında, bir Flask projesiyle çalışırken, Visual Studio, düzenlemekte olduğunuz HTML dosyasının aslında bir Flask şablonu olduğu zaman otomatik olarak algılar ve belirli otomatik tamamlanmış özellikleri sağlar. Örneğin, bir Flask sayfa şablonu açıklaması yazmaya başladığınızda `{#`, Visual Studio otomatik olarak kapatma `#}` karakterleri verir. **Açıklama seçimi** ve **seçim komutlarının açıklamasını kaldırın** ( **düzenleme** > **GELIŞMIŞ** menüsünde ve araç çubuğunda), HTML açıklamaları yerine şablon açıklamalarını de kullanır.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Soru: projeyi çalıştırdığımda, şablonun bulunamadığını belirten bir hata görüyorum. Ne oldu?

Cevap: şablonun bulunamadığını belirten hatalar görürseniz, uygulamayı `INSTALLED_APPS` listesinde Flask projesinin *Settings.py* eklediğinizden emin olun. Bu giriş olmadan Flask, uygulamanın *Şablonlar* klasörüne bakmayacak şekilde bilmez.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Soru: Şablonlar, daha fazla alt klasör halinde düzenlenebilir mi?

Cevap: Evet, alt klasörleri kullanabilir ve sonra `render_template`çağrılarında *Şablonlar* altındaki göreli yola başvurabilirsiniz. Bunun yapılması, şablonlarınız için etkin ad alanları oluşturmanın harika bir yoludur.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Daha derin git

- [Flask hızlı başlangıç-şablonları işleme](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (Flask.pocoo.org)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-Flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
