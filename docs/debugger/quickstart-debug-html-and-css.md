---
title: UWP uygulamalarında HTML ve CSS hatalarını ayıklama | Microsoft Docs
ms.date: 07/17/2018
ms.topic: conceptual
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- JavaScript
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [UWP apps]
- DOM Explorer [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 75bdfe55d516deb34872007a9461a286b4d742e0
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568910"
---
# <a name="debug-html-and-css-in-uwp-apps-in-visual-studio"></a>Visual Studio 'da UWP uygulamalarında HTML ve CSS hatalarını ayıklama

JavaScript uygulamaları için, Visual Studio, Internet Explorer ve Visual Studio geliştiricilerine tanıdık olan özellikleri içeren kapsamlı bir hata ayıklama deneyimi sunar. Bu özellikler, UWP uygulamaları ve Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan uygulamalar için desteklenir.

DOM inceleme araçları tarafından sunulan etkileşimli hata ayıklama modelini kullanarak, işlenmiş HTML ve CSS kodunu görüntüleyebilir ve değiştirebilirsiniz. Bunu, hata ayıklayıcıyı durdurup yeniden başlatmadan yapabilirsiniz.

JavaScript Konsol penceresini kullanma ve kesme noktaları ayarlama gibi diğer JavaScript hata ayıklama özellikleri hakkında bilgi için bkz. [hızlı başlangıç:](../debugger/quickstart-debug-javascript-using-the-console.md) [Visual Studio 'Da](debugging-windows-store-and-windows-universal-apps.md)JavaScript ve hata ayıklama uygulamaları.

## <a name="InspectingDOM"></a>Canlı DOM inceleniyor
DOM Gezgini, işlenmiş sayfanın bir görünümünü gösterir ve DOM Gezgini 'ni kullanarak değerleri değiştirebilir ve sonuçları hemen görebilirsiniz. Bu, hata ayıklayıcıyı durdurup yeniden başlatmadan değişiklikleri test etmenizi sağlar. Bu yöntemi kullanarak sayfayla etkileşim kurarken, projenizdeki kaynak kodu değişmez, bu nedenle istenen kod düzeltmelerini bulduğunuzda, kaynak kodunuzda değişiklikler yaparsınız.

> [!TIP]
> Kaynak kodunuzda değişiklikler yaptığınızda hata ayıklayıcıyı durdurup yeniden başlatmadan kaçınmak için, hata ayıklama araç çubuğundaki **Windows uygulamasını Yenile** düğmesini kullanarak uygulamanızı yenileyebilirsiniz (veya F4 tuşuna basarak). Daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).

DOM Gezgini 'ni kullanarak şunları yapabilirsiniz:

- DOM öğesi alt ağacı ' na gidin ve işlenmiş HTML, CSS ve JavaScript kodunu inceleyin.

- Oluşturulan öğelerin özniteliklerini ve CSS stillerini dinamik olarak düzenleyin ve sonuçları hemen görüntüleyin.

- CSS stillerinin sayfa öğelerine nasıl uygulandığını inceleyin ve uygulanan kuralları izleyin.

  Uygulamalarda hata ayıklarken, genellikle DOM Gezgini 'nde öğe seçmeniz gerekir. Bir öğe seçtiğinizde, DOM Gezgini 'nin sağ tarafındaki sekmelerde görüntülenen değerler, DOM Gezgini 'nde seçilen öğeyi yansıtacak şekilde otomatik olarak güncelleşilir. Sekmeler şunlardır: **Stiller**, **hesaplanan**, **Düzen**. UWP uygulamaları ayrıca **olayları** ve **değişiklik** sekmelerini destekler. Öğe seçme hakkında daha fazla bilgi için bkz. [öğeleri seçme](#SelectingElements).

> [!TIP]
> DOM Gezgini penceresi kapalıysa, yeniden açmak için **Windows** > **DOM Gezgini**>**Hata Ayıkla** ' yı seçin. Pencere yalnızca bir betik hata ayıklama oturumu sırasında görüntülenir.

Aşağıdaki yordamda, DOM Gezgini 'ni kullanarak bir uygulamada etkileşimli olarak hata ayıklama işlemini öğreneceksiniz. `FlipView` denetimi kullanan ve sonra hata ayıkladığımız bir uygulama oluşturacağız. Uygulama birkaç hata içeriyor.

> [!WARNING]
> Aşağıdaki örnek uygulama bir UWP uygulamasıdır. Cordova için aynı özellikler desteklenir, ancak uygulama farklı olabilir.

#### <a name="to-debug-by-inspecting-the-live-dom"></a>Canlı DOM 'ı inceleyerek hata ayıklamak için

1. **Yeni proje** > **Dosya** ' yı seçerek Visual Studio 'da yeni bir çözüm oluşturun.

2. **Windows evrensel** > **JavaScript** ' i seçin ve ardından **WinJS uygulaması**' nı seçin.

3. Proje için `FlipViewApp`gibi bir ad yazın ve uygulamayı oluşturmak için **Tamam** ' ı seçin.

4. İndex. html ' nin BODY öğesinde şu kodu ekleyin:

    ```html
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"
            style="display:none">
        <div class="fixedItem" >
            <img src="#" data-win-bind="src: flipImg" />
        </div>
    </div>
    <div id="fView" style="width:100px;height:100px"
        data-win-control="WinJS.UI.FlipView" data-win-options="{
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
    </div>
    ```

5. Default. css ' yi açın ve aşağıdaki CSS 'yi ekleyin:

    ```css
    #fView {
        background-color:#0094ff;
        height: 100%;
        width: 100%;
        margin: 25%;
    }
    ```

6. Default. js ' deki kodu şu kodla değiştirin:

    ```javascript
    (function () {
        "use strict";

        var app = WinJS.Application;
        var activation = Windows.ApplicationModel.Activation;

        var myData = [];
        for (var x = 0; x < 4; x++) {
            myData[x] = { flipImg: "/images/logo.png" }
        };

        var pages = new WinJS.Binding.List(myData, { proxy: true });

        app.onactivated = function (args) {
            if (args.detail.kind === activation.ActivationKind.launch) {
                if (args.detail.previousExecutionState !==
                activation.ApplicationExecutionState.terminated) {
                    // TODO: . . .
                } else {
                    // TODO: . . .
                }
                args.setPromise(WinJS.UI.processAll());

                updateImages();
            }
        };

        function updateImages() {

            pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
            pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
            pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
        };

        app.oncheckpoint = function (args) {
        };

        app.start();

        var publicMembers = {
            items: pages
        };

        WinJS.Namespace.define("Data", publicMembers);

    })();
    ```

    Aşağıdaki çizimde, bu uygulamayı çalıştırıp çalıştırdığımızda neleri görmek istiyoruz gösterilmektedir. Ancak, uygulamayı bu duruma getirmek için öncelikle bir dizi hatayı düzeltmemiz gerekecektir.

    ![Beklenen sonuçları gösteren FlipView uygulaması](../debugger/media/js_dom_appfixed.png "JS_DOM_AppFixed")

7. **Hata ayıklama** araç çubuğundaki **hata ayıklamayı Başlat** düğmesinin yanındaki açılan listeden **yerel makine** ' yi seçin:

    ![Hata ayıklama hedef listesini seçin](../debugger/media/js_select_target.png "JS_Select_Target")

8. Hata **ayıklamayı başlatmak** > **Hata Ayıkla** ' yı seçin veya F5 ' e basarak uygulamanızı hata ayıklama modunda çalıştırın.

    Bu, uygulamayı çalıştırır, ancak stil içinde birkaç hata olduğu için çoğunlukla boş bir ekran görürsünüz. İlk `FlipView` görüntüsü, ekranın ortasında küçük bir karede görünür.

9. Visual Studio 'ya geçin ve **DOM Gezgini** sekmesini seçin.

    > [!TIP]
    > Visual Studio ile çalışan uygulama arasında geçiş yapmak için Alt + Tab veya F12 tuşlarına basabilirsiniz.

10. DOM Gezgini penceresinde, KIMLIĞI `"fView"`olan bölüm için DIV öğesini seçin. Doğru DIV öğesini görüntülemek ve seçmek için ok tuşlarını kullanın. (Sağ ok tuşu, bir öğenin alt öğelerini görüntülemenize olanak sağlar.)

    ![DOM Gezgini](../debugger/media/js_dom_explorer.png "JS_DOM_Explorer")

    > [!TIP]
    > Ayrıca, > > giriş isteminde `select(fView)` yazarak ve ardından ENTER tuşuna basarak JavaScript Konsol penceresinin sol alt köşesindeki DIV öğesini de seçebilirsiniz.

    DOM Gezgini penceresinin sağ tarafındaki sekmelerde görüntülenen değerler, DOM Gezgini 'nde geçerli öğeyi yansıtacak şekilde otomatik olarak günceldir.

11. Sağ tarafta **hesaplanan** sekmesini seçin.

    Bu sekme, seçilen DOM öğesinin her bir özelliği için hesaplanan veya son değeri gösterir.

12. Yükseklik CSS kuralını açın. 100 piksel olarak ayarlanmış bir satır içi stil olduğuna dikkat edin. Bu, `#fView` CSS Seçicisi için ayarlanan %100 ' lik yükseklik değeriyle tutarsız bir şekilde görünür. `#fView` seçicinin üstü çizili metni, satır içi stilin bu stille öncelikli olduğunu gösterir.

    Aşağıdaki çizimde, **hesaplanan** sekmesi gösterilmektedir.

    ![DOM Gezgini hesaplanan sekmesi](../debugger/media/js_dom_explorer_computed.png "JS_DOM_Explorer_Computed")

13. Ana DOM Gezgini penceresinde, `fView` DIV öğesinin yükseklik ve genişlik için satır içi stile çift tıklayın. Artık değerleri burada düzenleyebilirsiniz. Bu senaryoda, bunları tamamen kaldırmak istiyoruz.

14. Ana pencerede `width: 100px;height: 100px;`' a çift tıklayın, **Delete** tuşuna basın ve ardından **ENTER**tuşuna basın. ENTER tuşuna bastıktan sonra, hata ayıklama oturumunuzu durdurmadığınız halde yeni değerler uygulamaya hemen yansıtılır.

    > [!IMPORTANT]
    > DOM Gezgini penceresinde öznitelikleri güncelleştirebilmeniz için, **Stiller**, **hesaplanan**ve **Düzen** sekmelerinde görüntülenen değerleri de güncelleştirebilirsiniz.

15. Uygulamayı seçerek veya alt + TAB tuşlarını kullanarak uygulamaya geçiş yapın.

    Artık `FlipView` denetimi Benzeticisinin veya telefon öykünücüsünün ekran boyutundan daha büyük görünüyor. Bu, amaçlanan sonuç değildir. Araştırmak için, Visual Studio 'ya geri dönün.

16. DOM Gezgini 'nde, **hesaplanmış** sekmesini yeniden seçin ve yükseklik kuralını açın. FView öğesi, CSS 'den beklenen %100 değerini hala gösterir, ancak hesaplanan değer uygulamanın ekran yüksekliğine (örneğin, 800px, 667.67 px veya başka bir değer) eşittir, bu da bu uygulama için istiyoruz. Araştırmak için, sonraki adımlarda `fView` DIV öğesinin yüksekliğini ve genişliğini kaldırdık.

17. **Stiller** SEKMESINDE `#fView` CSS seçicisinin yükseklik ve genişlik özelliklerinin işaretini kaldırın.

    **Hesaplanan** sekmede artık 400px bir yükseklik gösterilmektedir. Bilgiler, bu değerin platform CSS dosyası olan ui-Dark. css dosyasında belirtilen. win-flipview seçicisine geldiğini gösterir.

18. Uygulamaya geri dönün.

    Şeyler geliştirilmiştir. Ancak düzeltilmeye devam eden bir sorun var: kenar boşlukları çok büyük görünüyor.

19. Araştırmak için, Visual Studio 'ya geçin ve öğenin kutu modeline bakmak için **Düzen** sekmesini seçin.

    **Düzen** sekmesinde, aşağıdakileri görürsünüz:

    - cihaz ayarlarınıza bağlı olarak 255px (konum) ve 255px (Margin) veya benzer değerler.

      Aşağıdaki çizimde, 100px fark ve kenar boşluğu ile bir öykünücü kullanıyorsanız **Düzen** sekmesinin nasıl göründüğü gösterilmektedir.

      ![DOM Gezgini Düzen sekmesi](../debugger/media/js_dom_explorer_layout.png "JS_DOM_Explorer_Layout")

      Bu doğru görünmüyor. **Hesaplanan** sekme aynı kenar boşluğu değerlerini de gösterir.

20. **Stiller** sekmesini SEÇIN ve CSS seçicisini `#fView` bulun. Burada, **Margin** özelliği için %25 değerini görürsünüz.

21. %25 ' i seçin ve 25px olarak değiştirin ve ENTER tuşuna basın.

22. Ayrıca, **Stiller** sekmesinde. win-flipview seçicisinin yükseklik kuralını seçin ve 400px ' i 500 piksel olarak değiştirin ve ENTER tuşuna basın.

23. Uygulamaya geri dönün ve öğelerin yerleşiminin doğru göründüğünü görürsünüz. Kaynak üzerinde düzeltmeler yapmak ve hata ayıklayıcıyı durdurup yeniden başlatmadan uygulamayı yenilemek için aşağıdaki yordama bakın.

#### <a name="to-refresh-your-app-while-debugging"></a>Hata ayıklama sırasında uygulamanızı yenilemek için

1. Uygulama çalışmaya devam ederken Visual Studio 'ya geçin.

2. Default. html dosyasını açın ve `"fView"` DIV öğesinin yüksekliğini ve genişliğini %100 olarak değiştirerek kaynak kodunuzu değiştirin.

3. Hata ayıklama araç çubuğunda **Windows uygulamasını Yenile** düğmesini seçin (veya F4 tuşuna basın). Düğme şu şekilde görünür: ![Windows uygulamasını Yenile düğmesi](../debugger/media/js_refresh.png "JS_Refresh").

    Uygulama sayfaları yeniden yükleme ve simülatör veya telefon öykünücüsü ön plana geri döner.

    Yenileme özelliği hakkında daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).

## <a name="SelectingElements"></a>Öğe seçme
Bir uygulamada hata ayıklarken DOM öğelerini üç şekilde seçebilirsiniz:

- Doğrudan DOM Gezgini penceresinde (veya ok tuşlarını kullanarak) öğelere tıklayarak.

- **Öğe seç** düğmesini (Ctrl + B) kullanarak.

- [JavaScript Konsolu komutlarından](../debugger/javascript-console-commands.md?view=vs-2017)biri olan `select` komutunu kullanarak.

  Öğeleri seçmek için DOM Gezgini penceresini kullandığınızda ve fare işaretçisini bir öğe üzerine getirdiğinizde, ilgili öğe çalışan uygulamada vurgulanır. Bunu seçmek için DOM Gezgini 'nde öğeye tıklamalısınız veya öğeleri vurgulamak ve seçmek için ok tuşlarını kullanabilirsiniz. DOM Gezgini 'nde **öğe seç** düğmesini kullanarak da öğeleri seçebilirsiniz. Aşağıdaki çizimde **öğe seç** düğmesi gösterilmektedir.

  ![DOM Gezgini 'nde öğe seç düğmesi](../debugger/media/js_dom_select_element_button.png "JS_DOM_Select_Element_Button")

  **Öğe seç** ' e tıkladığınızda (veya CTRL + B tuşlarına basın), bu seçim modu, çalışan uygulamada tıklayarak DOM Gezgini 'nde bir öğe seçebilmeniz için değiştirilir. Tek bir tıklama sonrasında mod normal seçim moduna geri değişir. **Öğe seç**' e tıkladığınızda, uygulama ön plana gelir ve imleç yeni seçim modunu yansıtacak şekilde değişir. Seviyelendirilmiş öğeye tıkladığınızda, DOM Gezgini belirtilen öğe seçili olan ön plana geri döner.

  **Öğe seç**' i seçmeden önce, **Web sayfası vurgulamaları göster** düğmesini değiştirerek çalışan uygulamadaki öğelerin vurgulanmasını belirtebilirsiniz. Aşağıdaki çizimde bu düğme gösterilmektedir. Vurgular varsayılan olarak görüntülenir.

  ![Web sayfası vurgulamaları göster düğmesi](../debugger/media/js_dom_display_highlights_button.png "JS_DOM_Display_Highlights_Button")

  Öğeleri vurgulamanızı seçtiğinizde benzeticide üzerine geldiğinizde bulunan öğeler vurgulanır. Vurgulanan öğelerin renkleri, DOM Gezgini 'nin **Düzen** sekmesinde görüntülenen kutu modeliyle eşleşir.

> [!NOTE]
> Öğelerin üzerine gelindiğinde vurgulanması yalnızca Windows Phone öykünücüsünde kısmen desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da uygulamaların hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
- [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)
- [Klavye kısayolları](../debugger/keyboard-shortcuts-html-and-javascript.md?view=vs-2017)
- [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md?view=vs-2017)
- [HTML, CSS ve JavaScript'te hata ayıklama örnek kodu](../debugger/debug-html-css-and-javascript-sample-code.md)
- [Ürün desteği ve erişilebilirlik](https://msdn.microsoft.com/library/tzbxw1af(VS.120).aspx)
