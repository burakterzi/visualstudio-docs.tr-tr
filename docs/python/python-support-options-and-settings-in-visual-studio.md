---
title: Python için seçenekler ve ayarlar
description: Visual Studio 'da Python kodu ve projelerle ilgili çeşitli ayarlara yönelik bir başvuru.
ms.date: 03/13/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 08501d71400a0df139022f04e68573d0dd1449d1
ms.sourcegitcommit: 77ef1dcc71057cd5fdc4733ff0cb6085bd6113e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73661917"
---
# <a name="options-for-python-in-visual-studio"></a>Visual Studio 'da Python seçenekleri

Python seçeneklerini görüntülemek için **araçlar** > **Seçenekler** menü komutunu kullanın, **tüm ayarları göster** ' in seçili olduğundan emin olun ve ardından **Python**' a gidin:

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general-2019.png)
::: moniker-end

Ayrıca **metin düzenleyicisi** > **Python** > **Gelişmiş** sekmesinde ve **metin düzenleyici** grubundaki **ortam** > **yazı tipleri ve renkler** sekmesinde ek Python 'a özgü seçenekler de vardır.

> [!Note]
> **Deneysel** Grup, hala geliştirme aşamasında olan ve burada açıklanmayan özellikler için seçenekler içerir. Bunlar genellikle [Microsoft blogu 'Ndaki Python mühendisliğinde](https://devblogs.microsoft.com/python/)gönderilerde ele alınmıştır.

## <a name="general-options"></a>Genel Seçenekler

(**Araçlar** > **Seçenekler** > **Python** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Sanal ortamlar oluştururken Çıkış Penceresi göster**| Açık | **Çıkış** penceresinin görünmesini engellemek için işaretini kaldırın. |
| **Paketleri yüklerken veya kaldırırken Çıkış Penceresi göster** | Açık | **Çıkış** penceresinin görünmesini engellemek için işaretini kaldırın. |
| **Ortam oluşturmak için bildirim çubuğunu göster** | Açık | *Yalnızca Visual Studio 2019.* Bu seçenek ayarlandığında ve Kullanıcı *requirements. txt* veya *Environment. yıml* dosyası içeren bir proje açtığında, Visual Studio sırasıyla sanal ortam veya Conda ortamı oluşturma önerilerini içeren bir bilgi çubuğu görüntüler. Varsayılan genel ortamı kullanmak yerine. |
| **Paketleri yüklemek için bildirim çubuğunu göster** | Açık | *Yalnızca Visual Studio 2019.* Bu seçenek ayarlandığında ve Kullanıcı *requirements. txt* dosyasını içeren bir proje açtığında (ve varsayılan genel ortamı kullanmıyorsanız), Visual Studio bu gereksinimleri geçerli ortamda yüklü paketlerle karşılaştırır. Herhangi bir paket eksikse, Visual Studio bu bağımlılıkları yüklemek için bir istem görüntüler. |
| **Paket yöneticilerini her zaman yönetici olarak çalıştır** | Kapalı | Tüm ortamlarda `pip install` ve benzer Paket Yöneticisi işlemlerini her zaman yükseltir. Paketler yüklenirken, ortam dosya sisteminin *C:\Program Files*gibi korumalı bir alanında yer alıyorsa, Visual Studio yönetici ayrıcalıkları ister. Bu istem içinde, yalnızca bir ortam için install komutunu her zaman yükseltmeyi seçebilirsiniz. Bkz. [Paketler sekmesi](python-environments-window-tab-reference.md#packages-tab). |
| **İlk kullanımda tamamlanma DB 'yi otomatik olarak oluştur** | Açık | *Bir IntelliSense veritabanı kullanılırken Visual Studio 2017 sürüm 15,5 ve önceki sürümleri ve sonraki sürümler için geçerlidir.* Onu kullanan kodu yazdığınızda, bir kitaplık için veritabanının tamamlanmasını önceliklendirir. Daha fazla bilgi için bkz. [IntelliSense sekmesi](python-environments-window-tab-reference.md?view=vs-2017#intellisense-tab). |
| **Sistem genelinde PYTHONPATH değişkenlerini yoksay** | Açık | PYTHONPATH varsayılan olarak yok sayılır, çünkü Visual Studio ortamlar ve projelerde arama yolları belirtmek için daha doğrudan bir yol sağlar. Ayrıntılar için bkz. [arama yolları](search-paths.md) . |
| **Bağlı dosyalar eklenirken arama yollarını Güncelleştir** | Açık | Ayarlandığında, bir projeye [bağlı dosya](managing-python-projects-in-visual-studio.md#linked-files) eklemek, IntelliSense 'in bağlantılı dosyanın klasörünün içeriğini tamamlanma veritabanına dahil edebilmesi için [arama yollarına](search-paths.md) ekler. Bu tür içerikleri tamamlama veritabanından dışlamak için bu seçeneği temizleyin. |
| **İçeri aktarılan modül bulunamadığında uyar** | Açık | İçeri aktarılan bir modülün Şu anda kullanılabilir olmadığını bildiğiniz halde kod işlemini etkilemediği durumlarda uyarıları bastırmak için bu seçeneği temizleyin. |
| **Tutarsız Girintiyi şöyle raporla** | **Uyarılarına** | Python yorumlayıcı kapsamı belirlemek için uygun girintide büyük ölçüde bağlı olduğundan, Visual Studio varsayılan olarak, kodlama hatalarını gösterebilen tutarsız girintili girintiler algıladığında uyarılar verir. Bu tür durumlarda programın çıkmasına neden olan, daha sıkı olması için **hatalara** ayarlanır. Bu davranışı tamamen devre dışı bırakmak için **değil**' i seçin. |
| **Anketi/haberleri denetle** | **Haftada bir kez** | *Visual Studio 2017 ve öncesi.* Visual Studio 'Nun, varsa Python ile ilgili anketler ve haber öğeleriyle Web sayfası içeren bir pencere açmasına izin verilen sıklığı ayarlar. Seçenekler **hiçbir**şekilde, **günde bir**kez, **haftada**bir ve **ayda bir**kez. |
| **Kalıcı olarak gizli iletişim kutularını Sıfırla** düğmesi | yok | Farklı iletişim kutuları **bunu bir daha gösterme**gibi seçenekler sağlar. Bu seçenekleri temizlemek ve iletişim kutularının yeniden görüntülenmesine neden olmak için bu düğmeyi kullanın. |

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Conda seçenekleri

(**Araçlar** > **seçenekler** > **Python** > **Conda** Tab.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Conda çalıştırılabilir yolu** | adet | Python iş yüküne dahil olan varsayılan Miniconda yüklemesine güvenmek yerine *Conda. exe* yürütülebilir dosyasının tam yolunu belirtir. Burada başka bir yol verilirse, bu, kayıt defterinde belirtilen varsayılan yüklemeden ve diğer tüm Conda. exe yürütülebilir dosyalarının önüne geçer. Anaconda veya Miniconda 'ın daha yeni bir sürümünü el ile yüklüyorsanız veya varsayılan 64-bit dışında bir 32-bit ayırıcı kullanmak istiyorsanız bu ayarı değiştirebilirsiniz. |

![Python seçenekleri iletişim kutusu, dil sunucusu sekmesi](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Hata ayıklama seçenekleri

(**Araçlar** > **seçenekler** > **Python** > **hata ayıklama** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Hata olduğunda çalıştırmadan önce sor** | Açık | Ayarlandığında, hata içeren kodu çalıştırmak istediğinizi onaylamanızı ister. Uyarıyı devre dışı bırakmak için bu seçeneği temizleyin. |
| **İşlem anormal bir şekilde çıkıldığında girişi bekle**<br/><br/>**İşlem normal şekilde çıkıldığında girişi bekle** | Açık (her ikisi için) | Visual Studio 'dan başlatılan bir Python programı kendi konsol penceresinde çalışır. Varsayılan olarak, pencere, programın nasıl çıkdığına bakmaksızın kapatmadan önce bir tuşa basmanız için bekler. Bu istemi kaldırmak ve pencereyi otomatik olarak kapatmak için bu seçeneklerden birini veya her ikisini temizleyin. |
| **Hata ayıklama çıkışı penceresinde t program çıktısı** | Açık | Program çıkışını ayrı bir konsol penceresinde ve Visual Studio **çıktı** penceresinde görüntüler. Çıktıyı yalnızca ayrı konsol penceresinde göstermek için bu seçeneği temizleyin. |
| **Sıfırın çıkış kodu ile SystemExit özel durumuyla kes** | Kapalı | Ayarlanırsa, bu özel durum üzerinde hata ayıklayıcıyı sonlandırır. Açık olduğunda, hata ayıklayıcı koparmadan çıkar. |
| **Python Standart Kitaplığı 'nda hata ayıklamayı etkinleştir** | Kapalı | Hata ayıklama sırasında standart kitaplık kaynak koduna geçmek mümkün olsa da, hata ayıklayıcının başlaması için gereken süreyi artırır.|
| **İşlev dönüş değerini göster** | Açık | *Yalnızca Visual Studio 2019.* **Locals** penceresinde işlev dönüş değerlerini görüntüler ve sonra hata ayıklayıcıdaki bir işlev çağrısının üzerine adımlanıyor (F10) |
| **Eski hata ayıklayıcıyı kullan** | Kapalı | *Yalnızca Visual Studio 2019.* Visual Studio 'ya, varsayılan olarak eski hata ayıklayıcıyı kullanmasını söyler. Daha fazla bilgi için bkz. [hata ayıklama-eski hata ayıklayıcıyı kullanın](debugging-python-in-visual-studio.md#use-the-legacy-debugger). |

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, hata ayıklama sekmesi](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, hata ayıklama sekmesi](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Tanılama seçenekleri

(**Araçlar** > **seçenekler** > **Python** > **Tanılama** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Analiz günlüklerini dahil et** | Açık | , Tanılamayı bir dosyaya kaydederken veya düğmeleri kullanarak panoya kopyalarken, yüklü Python ortamlarının analizine ilişkin ayrıntılı günlükleri içerir. Bu seçenek, oluşturulan dosyanın boyutunu önemli ölçüde artırabilir, ancak genellikle IntelliSense sorunlarını tanılamak için gereklidir. |
| **Tanılamayı dosyaya kaydet** düğmesi | yok | Bir dosya adı ister ve günlüğü bir metin dosyasına kaydeder. |
| **Tanılamayı panoya kopyala** düğmesi | yok | Günlüğün tamamını Pano 'ya yerleştirir; Bu işlem, günlüğün boyutuna bağlı olarak biraz zaman alabilir. |

![Python seçenekleri iletişim kutusu, Tanılama sekmesi](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Etkileşimli Windows seçenekleri

(**Araçlar** > **Seçenekler** >  **etkileşimli Windows** sekmesi > .)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Betikleri** | yok | Tüm ortamlarda **etkileşimli** Windows için uygulanacak başlangıç betikleri için genel bir klasör belirtir. Bkz. [Başlangıç betikleri](python-environments-window-tab-reference.md#startup-scripts). Ancak, bu özelliğin şu anda çalışmadığına not edin. |
| **Yukarı/aşağı okları geçmişe gider** | Açık | **Etkileşimli** penceredeki geçmiş arasında gezinmek için ok tuşlarını kullanır. Bunun yerine **etkileşimli** pencerenin çıktısı içinde gezinmek için ok tuşlarını kullanmak üzere bu ayarı temizleyin. |
| **Tamamlama modu** | **Yalnızca işlev çağrıları olmayan ifadeleri değerlendir** | **Etkileşimli** penceredeki bir ifadede kullanılabilir üyeleri belirleme işlemi, geçerli tamamlanmamış ifadenin değerlendirilmesi gerektirebilir, bu da yan etkiler veya işlevlerin birden çok kez çağrılmasına neden olabilir. Varsayılan ayar, **yalnızca işlev çağrıları olmadan ifadeleri değerlendir** işlevi çağıran ifadeleri hariç tutar, ancak diğer ifadeleri değerlendirir. Örneğin, `a.b` değerlendirir ancak `a().b`vermez.  **Ifadeleri hiçbir şekilde değerlendirme** , öneriler için yalnızca normal IntelliSense altyapısı kullanılarak tüm yan etkileri engeller. **Tüm Ifadeleri değerlendir** , yan etkilerden bağımsız olarak öneriler almak için tüm ifadeyi değerlendirir. |
| **Statik analiz önerilerini gizle** | Kapalı | Ayarlandığında, yalnızca ifade hesaplanarak elde edilen önerileri görüntüler. **Tamamlama modu** değeri ile birleştirildiğinde **ifadeleri hiçbir şekilde değerlendirirse** **etkileşimli** pencerede hiçbir yararlı tamamlama görünmez. |

![Python seçenekleri iletişim kutusu, etkileşimli pencereler sekmesi](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Dil sunucusu seçenekleri

(**Araçlar** > **seçenekler** > **Python** > **dil sunucusu** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Türden tamamlanmış işlemleri devre dışı bırak** | Kapalı | Visual Studio IntelliSense normalde, her ikisi de Python 2 ve Python 3 için standart kitaplık ve üçüncü taraf kitaplıklar için tür ipuçları bulmak üzere yazı tipinde (bir *. Pyi* dosyaları kümesi) paketlenmiş bir sürümünü kullanır. Bu seçeneğin ayarlanması, paketlenmiş yazı davranışını devre dışı bırakır. |
| **Özel Türleştirilmiş yol** | adet | Ayarlanırsa, Visual Studio paketlenmiş sürümü yerine bu yoldaki yazı dosyalarını kullanır. **Türden tamamlanmayı devre dışı bırak** ayarlandıysa yoksay. |

![Python seçenekleri iletişim kutusu, dil sunucusu sekmesi](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Gelişmiş Python Düzenleyicisi seçenekleri

(**Araçlar** > **Seçenekler** > **metin düzenleyici** > **Python** > **Gelişmiş** sekmesi.)

### <a name="completion-results"></a>Tamamlanma sonuçları

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Üye tamamlama üyelerin kesişimini görüntüler** | Kapalı | Ayarlandığında, yalnızca tüm olası türler tarafından desteklenen bitirmaları gösterir. |
| **Arama dizesine göre filtre listesi** | Açık | Yazarken tamamlama önerilerinin filtrelenmesini uygular (varsayılan olarak işaretlidir). |
| **Tüm tanımlayıcılar için bitirmaları otomatik olarak göster** | Açık | Hem düzenleyicide hem de **etkileşimli** pencerede bitirmaları devre dışı bırakmak için bu seçeneği temizleyin. |

### <a name="selection-in-completion-list"></a>Tamamlanma listesinde seçim

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Aşağıdaki karakterler yazılarak işlendi** | **{}\[\]().,:; +-*/% &&#124;^ ~ = < > # @\\** | Bu karakterler tipik olarak bir tamamlanma listesinden seçim yaptığı bir tanımlayıcıyı izler, bu nedenle tamamlama işleminin yalnızca bir karakter yazarak yürütülmesi uygun olabilir. İstediğiniz gibi listeye belirli karakterleri kaldırabilir veya ekleyebilirsiniz.  |
| **İşlemeleri geçerli tamamlamayı girin** | Açık | Ayarlandığında, **ENTER** tuşu yukarıdaki karakterlerle birlikte seçili olan tamamlamayı seçer ve uygular (ancak elbette, bu listeye doğrudan gidememesi **için bir** karakter yok). |
| **Tam yazılmış kelimenin sonunda ENTER 'a yeni satır ekle** | Kapalı | Varsayılan olarak, tamamlama açılır penceresinde görüntülenen tüm sözcüğü yazarsanız ve **ENTER**tuşuna basarsanız, bu tamamlamayı işleyin. Bu seçeneği ayarlayarak, tanımlayıcıyı yazmayı tamamladığınızda, yeni bir **satır ekler gibi** tamamlama işlemleri etkili bir şekilde tamamlanır. |

### <a name="miscellaneous-options"></a>Çeşitli seçenekler

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Dosyalar açıkken anahat oluşturma moduna gir** | Açık | Python kod dosyası açılırken otomatik olarak düzenleyicide Visual Studio 'nun ana hat özelliğini etkinleştirin. |
| **Kaldırılan REPL istemlerini Yapıştır** | Açık | Yapıştırılan metinden **>>>** ve **...** ' ı kaldırarak kodun **etkileşimli** pencereden düzenleyiciye kolayca aktarılmasını sağlar. Diğer kaynaklardan yapıştırırken bu karakterleri saklamanız gerekiyorsa bu seçeneği temizleyin. |
| **Türlere göre renk adları** | Açık | Python kodunda sözdizimi renklendirmesini sunar. |

![Python düzenleyici seçenekleri iletişim kutusu, Gelişmiş sekmesi](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Yazı tipleri ve renkler seçenekleri

(**Ortam** > **yazı tipi ve renkler** sekmesi **metin Düzenleyicisi** grubu içinde.)

Python seçeneklerinin adları **Python** ile önek olarak eklenir ve kendine açıklayıcı bir şekilde yapılır. Tüm Visual Studio renk temaları için varsayılan yazı tipi 10pt Consolas Regular (kalın değildir). Varsayılan renkler temaya göre farklılık gösterir. Genellikle, varsayılan ayarlarla metin okumayı zorlaştırdıysanız bir yazı tipi veya rengi değiştirirsiniz.

![Python yazı tipi ve renk seçenekleri](media/options-fonts-and-colors.png)
