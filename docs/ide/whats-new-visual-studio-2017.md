---
title: Visual Studio 2017’deki yenilikler
titleSuffix: ''
description: Visual Studio 2017 ' deki yeni özellikler hakkında bilgi edinin.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: de26054894783df283d38223a59741c0500d0bc5
ms.sourcegitcommit: 0a8855572c6c88f4b2ece232c04aa124fbd9cec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955042"
---
# <a name="whats-new-in-visual-studio-2017"></a>Visual Studio 2017’deki yenilikler

**İçin güncelleştirilmiş [15,9 sürüm](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Visual Studio 'nun önceki bir sürümünden yükseltme mi arıyorsunuz? Visual Studio 2017 size şunları sunabilir: herhangi bir geliştirme, uygulama ve herhangi bir platform için benzersiz üretkenlik. Android, iOS, Windows, Linux, Web ve bulut uygulamaları geliştirmek için Visual Studio 2017 kullanın. Hızlı kod yazın, kolayca hata ayıklama ve tanılama yapın, sık sık test edin ve güvenle kullanıma sunun. Ayrıca, kendi uzantılarınızı oluşturarak Visual Studio’yu özelleştirebilir ve kapsamını genişletebilirsiniz. Sürüm denetimi kullanın, çevik olun ve bu sürümle verimli bir şekilde işbirliği yapın!

>[!div class="button"]
>[Visual Studio 'Yu indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Aşağıda, önceki sürümden bu yana yapılan değişikliklerin Yüksek düzey bir üst sınırı olan Visual Studio 2015:

* **[Temelleri yeniden tanımlandı](#redefined-fundamentals)** . Yeni bir kurulum deneyimi sayesinde daha hızlı bir şekilde yükleyebilir ve ihtiyacınız olduğunda istediğiniz şeyi yükleyebilirsiniz.
* **[Performans ve üretkenlik](#performance-and-productivity)** . Yeni ve modern mobil, bulut ve masaüstü geliştirme özelliklerine odaklandık. Visual Studio daha hızlı başlar, daha fazla yanıt verir ve öncesinde daha az bellek kullanır.
* **[Azure Ile bulut uygulaması geliştirme](#cloud-app-development-with-azure)** . Yerleşik bir Azure Araçları Paketi, Microsoft Azure tarafından desteklenen bulut öncelikli uygulamaları kolayca oluşturmanıza olanak tanır. Visual Studio, Azure 'da uygulamaları ve hizmetleri yapılandırma, derleme, hata ayıklama, paketleme ve dağıtmayı kolaylaştırır.
* **[Windows uygulama geliştirme](#windows-app-development)** . PC, tablet, Phone, Xbox, HoloLens, Surface Hub ve daha fazlasını &ndash; tüm Windows 10 cihazları için tek bir proje oluşturmak üzere Visual Studio 2017 ' deki UWP şablonlarını kullanın.
* **[Mobil uygulama geliştirme](#mobile-app-development)** . Yenilik yapın ve çok platformlu mobil gereksinimlerinizi bir çekirdek kod temeli ve beceriler kümesiyle birleştiren Xamarin ile sonuçları hızlı bir şekilde alın.
* **[Platformlar arası geliştirme](#cross-platform-development)** . Her türlü hedeflenen platforma sorunsuz bir şekilde yazılım sunun. Redgate veri araçları aracılığıyla SQL Server DevOps süreçlerini genişletin ve Visual Studio 'dan veritabanı dağıtımlarını güvenle otomatik hale getirin. Veya, Windows, Linux ve macOS işletim sistemlerinde değiştirilmemiş olarak çalışan uygulamalar ve kitaplıklar yazmak için .NET Core ' u kullanın.
* **[Oyun geliştirme](#games-development)** . Visual Studio Araçları ile Unity (VSTU), oyun ve düzenleyici betikleri C# dilinde yazın ve ardından, güçlü bir hata ayıklayıcı hataları bulma ve düzeltme için Visual Studio kullanabilirsiniz.
* **[AI geliştirme](#ai-development)** . Visual Studio Tools for AI, Visual Studio 'nun üretkenlik özelliklerini kullanarak AI yeniliklerini hızlandırabilir. Güçlü deneme özellikleri için Azure Machine Learning ile sorunsuz bir şekilde tümleştirilen derin öğrenme/AI çözümleri oluşturun, test edin ve dağıtın.

> [!NOTE]
> Visual Studio 2017 ' deki yeni özellik ve işlevlerin tamamı listesi için bkz. [geçerli sürüm notları](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Ve gelecekteki Özellik tekliflerinden göz atın, bkz. [Önizleme sürüm notları](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Aşağıda, Visual Studio 2017 ' deki en önemli iyileştirmeler ve yeni özelliklerden bazıları hakkında daha ayrıntılı bilgiler verilmiştir.

## <a name="redefined-fundamentals"></a>Temel kavramlar yeniden tanımlandı

### <a name="a-new-setup-experience"></a>Yeni bir kurulum deneyimi

Visual Studio, ihtiyacınız olduğunda yalnızca ihtiyacınız olan özellikleri yüklemeyi kolaylaştırır ve daha hızlı hale getirir. Ayrıca, düzgün bir şekilde kaldırılır.

Visual Studio 'Yu yüklerken en önemli değişiklik, yeni kurulum deneyimidir. **Iş yükleri** sekmesinde, ortak çerçeveleri, dilleri ve platformları temsil edecek şekilde gruplanmış yükleme seçeneklerini görürsünüz. .NET masaüstü geliştirmeden Windows, Linux ve C++ iOS 'ta uygulama geliştirmeye kadar her şeyi ele alır.

İhtiyacınız olan iş yüklerini seçin ve gerektiğinde değiştirin.

![Visual Studio 2017 kurulum iletişim kutusu](../install/media/install-visual-studio-enterprise.png)

Ve yüklemenizi hassas şekilde ayarlama seçenekleriniz da var:

* İş yüklerini kullanmak yerine kendi bileşenlerinizi seçmek mı istiyorsunuz? Yükleyiciden **ayrı bileşenler** sekmesini seçin.
* Dil paketlerini de Windows dil seçeneğini değiştirmek zorunda kalmadan yüklemek istiyor musunuz? Yükleyicinin **dil paketleri** sekmesini seçin.
* **15,7 ' de yeni**: Visual Studio 'nun yüklediği konumu değiştirmek istiyor musunuz? Yükleyicinin **yükleme seçenekleri** sekmesini seçin.

Adım adım yönergeler de dahil olmak üzere yeni yükleme deneyimi hakkında daha fazla bilgi edinmek için [Visual Studio 'Yu yükleme](../install/install-visual-studio.md) sayfasına bakın.

### <a name="a-focus-on-accessibility"></a>Erişilebilirlik üzerinde bir odak

**15,3 ' de yeni**, Visual Studio ile birçok müşterinin kullandığı yardımcı teknolojiler arasındaki uyumluluğun geliştirilmesi için 1.700 hedefli düzeltmelerin üzerinden yaptık. Ekran okuyucular, yüksek karşıtlıklı Temalar ve daha önce hiç olmadığı gibi diğer yardımcı teknolojilerle daha uyumlu olan onlarca senaryo vardır. Hata ayıklayıcı, düzenleyici ve kabuğun hepsi de çok önemli iyileştirmeler içerir.

Daha fazla bilgi için bkz. [Visual Studio 2017 sürüm 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) blog gönderisine yönelik erişilebilirlik geliştirmeleri.

## <a name="performance-and-productivity"></a>Performans ve üretkenlik

### <a name="sign-in-across-multiple-accounts"></a>Birden fazla hesabında oturum açın

Visual Studio 'da, Kullanıcı hesaplarını Takım Gezgini, Azure Araçları, Microsoft Store yayımlama ve daha fazlasını paylaşmanıza olanak sağlayan yeni bir kimlik hizmeti sunuyoruz.

Daha uzun bir süre içinde oturum açabilirsiniz. Visual Studio, her 12 saatte bir oturum açmanızı istemez. Daha fazla bilgi edinmek için, daha [az Visual Studio oturum açma komut istemlerini](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) blog gönderisine bakın.

### <a name="start-visual-studio-faster"></a>Visual Studio 'Yu daha hızlı başlatın

Yeni Visual Studio performans Merkezi, IDE başlangıç zamanını iyileştirmenize yardımcı olabilir. Performans Merkezi, IDE başlangıcını yavaşlatabilecek tüm uzantıları ve araç pencerelerini listeler. Bu uygulamayı, uzantıların ne zaman başlatılacağını belirleyerek veya araç pencerelerinin başlangıçta açık olup olmadığını belirleyerek başlangıç performansını geliştirmek için kullanabilirsiniz.

### <a name="faster-on-demand-loading-of-extensions"></a>Uzantılar için daha hızlı yükleme

Visual Studio, uzantıları (ve üçüncü taraf uzantılarla birlikte çalışarak) IDE başlatma yerine isteğe bağlı olarak yüklenecek şekilde taşıyor. Hangi uzantıların ne kadar etkili olduğunu, çözüm yükünü ve yazma performansını merak ediyor musunuz? Bu bilgileri, **Visual Studio performansını yönetmek** > **Yardım** 'da görebilirsiniz.

  ![Visual Studio 2017 ' de Seçenekler iletişim kutusu](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Uzantılarınızı dolaşım uzantıları Yöneticisi ile yönetme

Visual Studio 'da oturum açtığınızda, her geliştirme ortamını en sevdiğiniz uzantılara göre ayarlamak daha kolay olur. Yeni dolaşım uzantısı Yöneticisi, bulutta eşitlenmiş bir liste oluşturarak en sevdiğiniz uzantıların tamamını izler.

Visual Studio 'daki uzantılarınızın listesini görmek için **araçlar** > **Uzantılar & güncelleştirmeler**' e tıklayın ve ardından **gezici Uzantı Yöneticisi**' ne tıklayın.

![Visual Studio 2017-Uzantılar ve güncelleştirmeler iletişim kutusu](media/vs2017ide-extensions-and-updates.png)

Dolaşım uzantısı Yöneticisi yüklediğiniz tüm uzantıları izler, ancak dolaşım listenize hangi olanları eklemek istediğinizi seçebilirsiniz.

![Visual Studio 2017-Uzantılar ve güncelleştirmeler iletişim kutusu](media/vs2017ide-RoamingExtensionManager.png)

Dolaşım uzantısı yöneticisini kullandığınızda, listenizde üç simge türü vardır:

* ![dolaşıma eklenen simge](media/vs2017ide-roamedicon.png) **_dolaşıma_** açıldı: bu dolaşım listesinin bir parçası olan, ancak makinenizde yüklü olmayan bir uzantı.
  (Bunları, **İndir** düğmesini kullanarak yükleyebilirsiniz.)
* ![& yüklü simge](media/vs2017ide-roamedinstalledicon.png) dolaşıma eklenen **_& yüklendi_** : bu dolaşım listesinin parçası olan ve geliştirme ortamınıza yüklenen tüm uzantılar.
  (Dolaşımda istemediğinize karar verirseniz, bunu **dolaşımı durdur** düğmesini kullanarak kaldırabilirsiniz.)
* ![yüklü simge](media/vs2017ide-installedicon.png) **_yüklü_** : Bu ortamda yüklü olan, ancak dolaşım listenizin bir parçası olmayan tüm uzantılar.
  ( **Dolaşım Başlat** düğmesini kullanarak dolaşım listesine uzantı ekleyebilirsiniz.)

Oturum açtığınız sırada yüklediğiniz herhangi bir uzantı, **& yüklenirken**listenize eklenir. Daha sonra uzantı, dolaşım listenizin bir parçası haline gelir ve bu, size herhangi bir makineden erişmenizi sağlar.

### <a name="experience-live-unit-testing"></a>Canlı birim testi yaşayın

Visual Studio Enterprise 2017 ' de, canlı birim testi, kodlarken düzenleyicide canlı birim test sonuçları ve kod kapsamı sağlar. Hem .NET Framework hem C# de .NET Core için ve Visual Basic projelerle birlikte çalışarak, MSTest, xUnit ve NUnit 'in üç test çerçevesini destekler.

![Live Unit Testing](media/lut-codewindow.png)

Daha fazla bilgi için bkz. [tanıtma Live Unit Testing](../test/live-unit-testing-intro.md). Visual Studio Enterprise 2017 ' nin her sürümünde eklenen yeni özelliklerin listesi için, bkz. [Live Unit Testing yenilikleri](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>CI/CD işlem hattı ayarlama

#### <a name="automated-testing"></a>Otomatikleştirilmiş test

Otomatikleştirilmiş test, herhangi bir DevOps işlem hattının önemli bir parçasıdır. Çözümünüzü çok daha kısa bir Döngülerde tutarlı ve güvenilir bir şekilde test etmenize ve serbest bırakmanıza olanak tanır. CI/CD (sürekli tümleştirme ve sürekli teslim) akışları, işlemi daha verimli hale getirmenize yardımcı olabilir.

Otomatikleştirilmiş testler hakkında daha fazla bilgi için bkz. [DevOps blog gönderisine yönelik otomatik testler Için CI/CD işlem hattı](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) .

Ayrıca, Visual Studio DevLabs uzantısı [Için sürekli teslim araçlarındaki](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) yenilikler hakkında daha fazla bilgi için bkz. [güvenle Yürüt: kayıt zaman kodu kalitesi](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) blog gönderisi.

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE geliştirmeleri

#### <a name="multi-caret-editing"></a>Çoklu giriş işareti düzenleme

**15,8 ' de yeni**: aynı anda bir dosyadaki birden çok konumu düzenlemeyle artık kolay bir işlemdir. Bir dosyada birden çok konumda ekleme noktaları ve seçimler oluşturarak başlayın. Daha sonra, aynı anda iki veya daha fazla yerde aynı düzenleme yapmak için çoklu giriş işareti düzenleme özelliğini kullanın.

Daha fazla bilgi için [metin bul ve Değiştir](finding-and-replacing-text.md) sayfasının [Çoklu şapka seçimi](finding-and-replacing-text.md#multi-caret-selection) bölümüne bakın.

#### <a name="keep-keybinding-profiles-consistent"></a>Keep keybinding profiles consistent

**New in 15.8**: Now, you can keep your keybindings consistent across tools with two new keyboard profiles: Visual Studio Code and ReSharper (Visual Studio). You can find these schemes under **Tools** > **Options** > **General** > **Keyboard** and the top drop-down menu.

  ![New keybinding profiles for Visual Studio Code and ReSharper](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Use new refactorings

Refactoring is the process of improving your code after it has been written. Refactoring changes the internal structure of the code without changing its behavior. We add new refactorings often; here are just a few:

* Add parameter (from CallSite)
* Generate overrides
* Add named argument
* Add null-check for parameters
* Insert digit-separators into literals
* Change base for numeric literals (for example, hex to binary)
* Convert if-to-switch
* Remove unused variable

For more information, see [Quick Actions](common-quick-actions.md).

#### <a name="interact-with-git"></a>Interact with Git

When you are working with a project in Visual Studio, you can set up and quickly commit and publish your code to a Git service. You can also manage your Git repositories by using menu clicks from buttons in the bottom right-hand corner of the IDE.

![Visual Studio 2017 interacts with the Git dialog](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Experience improved navigation controls

We've refreshed the navigation experience to help you get from A to B with greater confidence and fewer distractions.

* **New in 15.4**: **Go To Definition** (**Ctrl**+**click** or **F12**) &ndash; Mouse users have an easier way to navigate to the definition of a member by pressing **Ctrl** and then clicking the member. Pressing **Ctrl** and hovering over a code symbol will underline it and turn it into a link. See [Go To Definition and Peek Definition](go-to-and-peek-definition.md) for more information.

* **Go To Implementation** (**Ctrl**+**F12**) &ndash; Navigate from any base type or member to its various implementations.

* **Go To All** (**Ctrl**+**T** or **Ctrl**+ **,** ) &ndash; Navigate directly to any file/type/member/symbol declaration. You can filter your result list or use the query syntax (for example, "f searchTerm" for files, "t searchTerm" for types, etc.).

  ![Improved Go To All](media/vs2017ide-navigation-go-to.png)

* **Find All References** (**Shift**+**F12**) &ndash; With syntax colorization, you can group Find All Reference results by a combination of project, definition, and path. You can also "lock" results so that you can continue to find other references without losing your original results.

  ![New Find All References tool](media/vs2017ide-find-all-references.png)

* **Structure Visualizer** &ndash; Dotted, gray vertical lines (indent guides) act as landmarks in code to provide context within your frame of view. You may recognize them from the popular Productivity Power Tools. You can use them to visualize and discover what block of code you're in at any time without having to scroll. Hovering over the lines displays a tooltip that shows you the opening of that block and its parents. It's available for all the languages supported via TextMate grammars, as well as C#, Visual Basic, and XAML.

  ![Visual Studio 2017 structure visualizer](media/vsIDE-StructureVisualizer.png)

For more information about the new productivity features, see the [Visual Studio 2017: Productivity, Performance, and Partners](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) blog post.

### <a name="visual-c"></a>Visual C++

You'll see several improvements in Visual Studio, such as distributing C++ Core Guidelines with Visual Studio, updating the compiler by adding enhanced support for C++11 and C++ features, and adding and updating functionality in the C++ libraries. We've also improved the performance of the C++ IDE, installation workloads, and more.

As well, we've fixed over 250 bugs and reported issues in the compiler and tools, many submitted by customers through the [Developer Community for C++](https://developercommunity.visualstudio.com/spaces/62/index.html "İçin geliştirici topluluğuC++").

Tüm ayrıntılar için bkz. [Visual için visual 2017 C++ 'deki](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) yenilikler sayfası.

### <a name="debugging-and-diagnostics"></a>Hata ayıklama ve tanılama

#### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Şimdi, istediğiniz satırda durmak üzere bir kesme noktası ayarlamadan hata ayıklama sırasında daha kolay bir şekilde atlayabilirsiniz. Hata ayıklayıcıda durdurulduğunda, kod satırının yanında görünen simgeye tıklamanız yeterlidir. Kodunuz, kod yolunuzda bir sonraki isabet edildiğinde çalışır ve bu satırda durdurulur.

![Visual Studio 2017 hata ayıklama-tıklama Için Çalıştır](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Yeni özel durum Yardımcısı

Yeni özel durum Yardımcısı, özel durum bilgilerinizi bir bakışta görüntülemenize yardımcı olur. Bilgiler, iç özel durumlara anında erişimli bir kompakt biçimde sunulur. Bir NullReferenceException 'yi tanılarken, özel durum Yardımcısı içinde neyin null olduğunu hızla görebilirsiniz.

![Visual Studio 'da yeni özel durum Yardımcısı iletişim kutusu](media/vs2017ide-ExceptionHelper.png)

Daha fazla bilgi için bkz. [Visual Studio 'da yeni özel durum yardımcısını kullanma](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) blog gönderisi.

#### <a name="snapshots-and-intellitrace-step-back"></a>Anlık görüntüler ve IntelliTrace adım geri

**15,5 sürümündeki yenilikler**: IntelliTrace adım geri alma, her kesme noktası ve hata ayıklayıcı adım olayında uygulamanızın bir anlık görüntüsünü otomatik olarak alır. Kaydedilen anlık görüntü, önceki kesme noktaları veya adımlara geri dönün ve daha önce olduğu gibi uygulama durumunu görüntülemek etkinleştirin. IntelliTrace geri adım atma önceki uygulama durumu görmek istiyorsanız ancak hata ayıklamayı yeniden başlatın veya istenen uygulama durumu yeniden istemediğiniz durumlarda size zaman kazandırabilir.

**Hata ayıklama** araç çubuğundaki **geri** ve **adım ileri** düğmelerini kullanarak anlık görüntülerle gezinerek görüntüleyebilirsiniz. Bu düğmeler **Tanılama araçları** penceresindeki **Olaylar** sekmesinde görüntülenen olaylara gider. Bir olaya geri veya ileri dönmek, seçili olayda geçmiş hata ayıklamayı otomatik olarak etkinleştirir.

![Visual Studio 'da yeni özel durum Yardımcısı iletişim kutusu](../debugger/media/intellitrace-step-back-icons-description.png  "Geri adımla ve Ilet düğmeleri")

Daha fazla bilgi için [IntelliTrace adım geri 'yi kullanarak anlık görüntüleri görüntüleme](../debugger/view-historical-application-state.md) sayfasına bakın.

### <a name="containerization"></a>Kapsayıcıyla taşıma

Kapsayıcılar, geliştirilmiş üretkenlik ve DevOps çevikleriyle birlikte daha fazla uygulama yoğunluğu ve daha düşük dağıtım maliyeti sağlar.

#### <a name="docker-container-tooling"></a>Docker kapsayıcı araçları

**15,5 sürümündeki yenilikler**:

* Visual Studio artık çok aşamalı Dockerfiles 'ı destekleyen, iyileştirilmiş kapsayıcı görüntüleri oluşturmayı kolaylaştıran Docker kapsayıcıları için araçlar içerir.
* Varsayılan olarak Visual Studio, Docker desteği olan bir projeyi açtığınızda gerekli kapsayıcı görüntülerini otomatik olarak çeker, derler ve arka planda çalıştırır. Bunu, Visual Studio'da **Kapsayıcıları arka planda otomatik olarak başlat** ayarı ile devre dışı bırakabilirsiniz.

## <a name="cloud-app-development-with-azure"></a>Azure ile bulut uygulaması geliştirme

### <a name="azure-functions-tools"></a>Azure Işlevleri araçları

"Azure geliştirme" iş yükünün parçası olarak, önceden derlenmiş C# sınıf kitaplıklarını kullanarak Azure işlevleri geliştirmenize yardımcı olacak araçlar sunuyoruz. Artık yerel geliştirme makinenizde derleme, çalıştırma ve hata ayıklama yapabilir ve sonra Visual Studio 'dan doğrudan Azure 'a yayımlayabilirsiniz.

Daha fazla bilgi için bkz. [Visual Studio Için Azure işlevleri araçları](/azure/azure-functions/functions-develop-vs) sayfası.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Canlı Azure uygulamalarında anlık görüntü noktalarını ve günlüğe kaydetme noktaları 'i kullanarak canlı ASP.NET uygulamalarında hata ayıklayın

**15,5 ' de yeni**: Snapshot Debugger, çalıştırırken ilgilendiğiniz kod olduğunda üretim içi uygulamalarınızın anlık görüntüsünü alır. Bir anlık görüntüsünü almak için hata ayıklayıcı açmasını sağlamak için anlık görüntü noktaları ve günlüğe kaydetme noktaları kodunuzda ayarlayın. Hata ayıklayıcı, tam olarak üretim uygulamanızın trafiğini etkilemeden, çıktığına görmenizi sağlar. Snapshot Debugger, üretim ortamlarında ortaya çıkan sorunları çözmek için gereken süreyi ciddi ölçüde azaltmaya yardımcı olabilir.

Anlık görüntü koleksiyonunu, Azure App Service'te çalışan aşağıdaki web uygulamaları için kullanılabilir:

* .NET Framework 4.6.1 üzerinde çalışan ASP.NET uygulamalarından veya üzeri.
* .NET Core 2.0 veya daha sonra Windows üzerinde çalışan ASP.NET Core uygulamaları.

Daha fazla bilgi için bkz. anlık görüntü [noktalarını ve günlüğe kaydetme noktaları kullanarak canlı ASP.NET uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Windows uygulaması geliştirme

### <a name="universal-windows-platform"></a>Evrensel Windows Platformu

Evrensel Windows Platformu (UWP), Windows 10 için uygulama platformudur. PC, tablet, Phone, Xbox, HoloLens, Surface Hub ve daha fazlasını &ndash; tüm Windows 10 cihazlarına ulaşmak için tek bir API kümesi, bir uygulama paketi ve tek bir mağaza ile UWP için uygulama geliştirebilirsiniz. UWP, dokunmatik, fare ve klavye, oyun denetleyicisi veya kalem gibi farklı ekran boyutlarını ve çeşitli etkileşim modellerini destekler. UWP uygulamalarının temel tarafında, kullanıcıların deneyimlerinin tüm cihazlarında mobil olmasını istediği ve her zaman en uygun veya üretken olan her türlü görev için hangi cihazdan yararlandıkları konusunda fikir sahibi olduğu düşüncedir.

![Evrensel Windows Platformu](../cross-platform/media/uwp_coreextensions.png)

Windows 10 cihazları için bir Evrensel Windows Platformu uygulaması C#oluşturmak üzere, C++Visual Basic, veya JavaScript&mdash;tercih ettiğiniz geliştirme dilini&mdash;seçin. Visual Studio 2017, tüm cihazlar için tek bir proje oluşturmanıza olanak sağlayan her dil için UWP uygulama şablonu sağlar. İşiniz bittiğinde, uygulamanızı herhangi bir Windows 10 cihazında müşterilere almak için bir uygulama paketi oluşturabilir ve bunu Visual Studio içinden Microsoft Store gönderebilirsiniz.

**15,5 ' de yeni**: Visual Studio 2017 sürüm 15,5, Windows 10 Fall CREATORS Update SDK (10.0.16299.0) için en iyi desteği sağlar. Windows 10 Fall Creators Update ayrıca UWP geliştiricileri için pek çok geliştirme sunar. En büyük değişikliklerden bazıları şunlardır: 

* **.NET Standard 2,0 desteği**<br/>Kolaylaştırılmış uygulama dağıtımına ek olarak Windows 10 Fall Creators Update, .NET Standard 2,0 desteği sağlamak için Windows 10 ' un ilk sürümüdür. Etkin olarak, [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) herhangi bir .NET platformunun uygulayabildikleri temel sınıf kitaplığının başvuru uygulamasıdır. .NET Standard amacı, .NET geliştiricilerin üzerinde çalışmak üzere seçtikleri herhangi bir .NET platformunda kod paylaşması mümkün olduğunca kolay hale gelidir.
* **Hem UWP hem de Win32 için en iyi**<br/>Windows 10 platformunu [Masaüstü Köprüsü](/windows/uwp/porting/desktop-to-uwp-root) ile geliştirdik. Bu, GEÇERLI odağın UWP, WPF, Windows Forms veya Xamarin üzerinde olmasına bakılmaksızın, tüm .NET geliştiricileri için Windows 10 ' u daha iyi hale getirir. Visual Studio 2017 sürüm 15,5 ' de yeni uygulama paketleme proje türü ile, tıpkı UWP projeleri için yaptığınız gibi WPF veya Windows Forms projeleriniz için Windows uygulama paketleri oluşturabilirsiniz. Uygulamanızı paketledikten sonra, tüm Windows 10 uygulama dağıtımı avantajlarına sahip olursunuz ve Microsoft Store (tüketici uygulamaları için) veya Iş ve eğitim için Microsoft Store aracılığıyla dağıtım seçeneği vardır. Paketlenmiş uygulamaların hem tam UWP API yüzeyine hem de masaüstündeki Win32 API 'Lerine erişimi olduğundan, artık WPF ve Windows Forms uygulamalarınızı UWP API 'Leri ve Windows 10 özellikleriyle birlikte yavaş şekilde modernleştirin edebilirsiniz. Üstelik, Win32 bileşenlerinizi, tüm Win32 özellikleri ile masaüstüne açık olan UWP uygulamalarınıza ekleyebilirsiniz.

UWP hakkında daha fazla bilgi için bkz. [Evrensel Windows platformu uygulamalar geliştirme (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) sayfası.

## <a name="mobile-app-development"></a>Mobil uygulama geliştirme

### <a name="xamarin"></a>Xamarin

".NET ile mobil geliştirme" iş yükü kapsamında, .net ve Visual Studio tanıdık C#geliştiriciler Xamarin kullanarak yerel Android, IOS ve Windows uygulamaları sunabilir. Geliştiriciler, Android, iOS ve Windows cihazlarında uzaktan hata ayıklama da dahil olmak üzere, hedef-C veya Java gibi yerel kodlama dillerini öğrenmeden&mdash;, mobil uygulamalar için Xamarin ile çalışırken aynı güç ve verimliliğin avantajlarından yararlanabilir.

Daha fazla bilgi için bkz. [Visual Studio ve Xamarin](/xamarin/) sayfası.

### <a name="entitlements-editor"></a>Yetkilendirmeler Düzenleyicisi

**15,3 sürümündeki yenilikler**: iOS geliştirme gereksinimleriniz için tek başına yetkilendirmeler Düzenleyicisi ekledik. Kolayca gözatılabilir, Kullanıcı dostu bir kullanıcı ARABIRIMI içerir. Başlatmak için *yetkilendirmeler. plist* dosyasına çift tıklayın.

![Xamarin için yetkilendirme Düzenleyicisi](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Xamarin için Visual Studio Araçları

**15,4 sürümündeki yenilikler**: Xamarin Live, geliştiricilerin uygulamalarını doğrudan IOS ve Android cihazlarında sürekli olarak dağıtmalarını, test etmesini ve hatalarını ayıklamasını sağlar. Uygulama mağazasındaki veya&mdash;Google Play Xamarin Live Player&mdash;indirdikten sonra, cihazınızı Visual Studio ile eşleştirmenizi ve mobil uygulamalar oluşturma şeklini eşleyebilir. Bu işlevsellik artık Visual Studio’ya eklenmiştir ve **Araçlar** > **Seçenekler** > **Xamarin** > **Diğer** > **Xamarin Live Player’ı Etkinleştir** seçeneği kullanılarak etkinleştirilebilir.

![Xamarin Live Player çiftinin, dağıtımın ve canlı düzenleme modlarının animasyonu](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Google Android Emulator desteği

**15,8 ' de yeni**: Hyper-v kullandığınızda, artık Google 'ın Android Emulator Hyper-v sanal makineleri, Docker Araçları, Hololens öykünücüsü ve daha fazlası gibi Hyper-v ' d i temel alan diğer teknolojilerle yan yana kullanabilirsiniz. (Bu özellik Windows 10 Nisan 2018 güncelleştirmesi veya sonraki bir sürümünü gerektirir.)

![Hyper-V teknolojilerinde Google Android öykünücüsü](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin. Android Designer bölünmüş görünüm Düzenleyicisi

**15,8 ' de de yenidir**: Xamarin. Android için tasarımcı deneyiminde önemli geliştirmeler yaptık. Bir vurgulama, düzenlerinizi aynı anda oluşturmanıza, düzenlemenize ve önizlemenize olanak tanıyan yeni bölünmüş görünüm düzenleyicidir.

![Xamarin. Adroıd tasarımcı bölünmüş görünüm Düzenleyicisi](media/android-designer-split-view.png)

Daha fazla bilgi için bkz. [öykünücü performansı Için donanım hızlandırma](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**15,5 ' de yeni**eklendi: Android, IOS, MacOS ve Windows&mdash;uygulamaları için genel kullanıma açık olan Visual Studio App Center&mdash;, otomatik derlemeler, buluttaki gerçek cihazlara test etme, Beta Sınayıcılar ve uygulama mağazalarına dağıtım ve kilitlenme ve analiz verileri aracılığıyla gerçek dünyanın kullanımını izleme dahil olmak üzere uygulamalarınızın yaşam döngüsünü yönetmeniz için gereken her şeyi içerir. Amaç-C, Swift, Java, C#, Xamarin ve yerel olarak yanıt verme bölümünde yazılan uygulamalar tüm özellikler genelinde desteklenir.

  ![Test ortamı Visual Studio App Center](media/app-center-test-env.png)

Daha fazla bilgi için bkz. [tanıtma App Center: bulut blog gönderisinde uygulama oluşturma, test etme, dağıtma ve izleme](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) .

## <a name="cross-platform-development"></a>Platformlar arası geliştirme

### <a name="redgate-data-tools"></a>Redgate Veri Araçları

DevOps yeteneklerini SQL Server veritabanı geliştirmeye genişletmek için, Redgate veri araçları artık Visual Studio 'da kullanılabilir.

Visual Studio 2017 Enterprise ile birlikte:

* [Redgate ReadyRoll Core](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) , geçiş betikleri geliştirmenize, kaynak denetimini kullanarak veritabanı değişikliklerini yönetmenize ve uygulamalar değiştikçe SQL Server veritabanı değişikliklerinin dağıtımlarını güvenle otomatikleştirmenize yardımcı olur.
* [Redgate SQL Prompt Core](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) , akıllı kod tamamlama yardımıyla SQL 'i daha hızlı ve doğru bir şekilde yazmanıza yardımcı olur. SQL Prompt, veritabanı ve sistem nesnelerinin yanı sıra anahtar sözcükleri de otomatik olarak tamamlar ve yazdığınız sırada sütun önerileri sunar. Bu, tüm sütun adlarını veya diğer adları hatırlamanız gerekmiyorsa Temizleyici kod ve daha az hata oluşmasına neden olur.

Tüm Visual Studio 2017 sürümlerinde bulunur:

* [Redgate SQL arama](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) , birden çok veritabanında SQL parçalarını ve nesneleri hızlı bir şekilde bulmanıza yardımcı olarak üretkenliğinizi artırır.

Daha fazla bilgi edinmek için bkz. [Visual Studio 2017 blog postasında Redgate veri araçları](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/) .

### <a name="net-core"></a>.NET Core

.NET Core, .NET Standard genel amaçlı, modüler, platformlar arası ve açık kaynaklı bir uygulamadır ve .NET Framework aynı API 'lerin çoğunu içerir.

.NET Core platformu, yönetilen derleyiciler, çalışma zamanı, temel sınıf kitaplıkları ve ASP.NET Core gibi çok sayıda uygulama modeli dahil olmak üzere birkaç bileşenden oluşur. .NET Core üç ana işletim sistemini destekler: Windows, Linux ve macOS. .NET Core 'u cihaz, bulut ve katıştırılmış/IoT senaryolarında kullanabilirsiniz.

Artık Docker desteği de içerir.

**15,3 ' de yeni**: Visual Studio 2017 sürüm 15,3, .net Core 2,0 geliştirmesini destekler. .NET Core 2,0 kullanılması için .NET Core 2,0 SDK 'sını ayrı olarak indirip yüklemeniz gerekir.

Daha fazla bilgi için bkz. [.NET Core Guide](/dotnet/core/index) sayfası.

## <a name="games-development"></a>Oyun geliştirme

### <a name="visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları

"Unity için oyun geliştirme" iş yükü kapsamında, 2B ve 3B oyunlar ve etkileşimli içerik oluşturmak için platformlar arası geliştirme yapmanıza yardımcı olacak araçlar sunuyoruz. Visual Studio 2017 ve Unity 5,6 kullanarak tüm mobil platformlar, WebGL, Mac, PC ve Linux masaüstü, Web veya konsolları dahil olmak üzere bir kez oluşturun ve 21 platformda yayımlayın.

Daha fazla bilgi için [Unity için Visual Studio Araçları](../cross-platform/visual-studio-tools-for-unity.md) sayfasına bakın.

## <a name="ai-development"></a>AI geliştirme

### <a name="visual-studio-tools-for-ai"></a>AI için Visual Studio Araçları

**15,5 ' deki yenilikler**: AI yeniliklerini bugün hızlandırmak Için Visual Studio 'nun üretkenlik özelliklerini kullanın. Sözdizimi vurgulama, IntelliSense ve metin otomatik biçimlendirme gibi yerleşik kod düzenleyici özelliklerini kullanın. Yerel değişkenlerde ve modellerde adım adım hata ayıklamayı kullanarak derin öğrenme uygulamanızı yerel ortamınızda etkileşimli bir şekilde test edebilirsiniz.

  ![Derin öğrenme IDE](../ai/media/about/ide.png)

Daha fazla bilgi için [Visual Studio Tools for AI](../ai/about-ai-tools.md) sayfasına bakın.

## <a name="whats-next"></a>Sırada ne var?

Visual Studio 2017 ' i genellikle geliştirme deneyiminizi daha da iyi hale getirebileceğiniz yeni özelliklerle güncelleştiririz. Deneysel Önizlemedeki en önemli güncelleştirmelerimizden bazıları aşağıda verilmiştir:

* **[Live share](https://visualstudio.microsoft.com/services/live-share/)** , bir kod temeli ve bağlamını bir ekiple paylaşmanıza ve doğrudan Visual Studio içinden çift yönlü işbirliği yapmanıza olanak tanıyan yeni bir araç. Live Share, bir ekip Mate kendileriyle paylaştığınız bir projeyi okuyabilir, gezinmiş, düzenleyebilir ve hata ayıklamanızı ve sorunsuz ve güvenli bir şekilde yapabilmesini sağlayabilir.<br><br>Daha fazla bilgi için [LIVE Share SSS](/visualstudio/liveshare/faq)bölümüne bakın.<br><br>
* **[Intellicode](https://visualstudio.microsoft.com/services/intellicode/)** , daha iyi bağlama duyarlı kod tamamlama sağlamak IÇIN geliştiricilere AI kullanarak yazılım geliştirmeyi geliştiren yeni bir özelliktir, geliştiricilerin takımlarının desenlerine ve stillerine kod oluşturmasını, daha fazla catch kodu sorunlarını bulmasını ve gerçekten de önem verdiği alanlara kod incelemelerini odaklamasını sağlar. <br><br>Daha fazla bilgi için bkz. [ıntellicode SSS](/visualstudio/intellicode/faq).

Visual Studio 2017 için çalışmadaki diğer özellikler hakkında daha fazla bilgi edinmek istiyor musunuz? Bkz. [Visual Studio yol haritası](/visualstudio/productinfo/vs2018-roadmap) sayfası.

[Visual Studio 2019](whats-new-visual-studio-2019.md), en yeni sürümü kullanıma almayı unutmayın.

## <a name="contact-us"></a>Bizimle iletişim kurun

Neden Visual Studio ekibine geri bildirim gönderilsin mi? Size müşteri geri bildirimi ciddiye olduğundan. Yaptığımız kadar çok şey vardır.

Visual Studio 'Yu nasıl geliştirebileceğimizi ve ürün desteği seçenekleri hakkında daha fazla bilgi edinmek istiyorsanız lütfen [bize geri bildirim gönder](feedback-options.md) sayfasına bakın.

### <a name="report-a-problem"></a>Sorun bildirin

Bazen, karşılaştığınız bir sorunun tam etkisini iletmek için bir ileti yeterli değildir. Bir askıda kalma, kilitlenme veya başka bir performans sorunuyla karşılaşırsanız **sorun bildir** aracını kullanarak, yeniden üretme adımlarını ve destekleyici dosyaları (ekran görüntüleri ve izleme ve yığın dökümü dosyaları) bizimle paylaşabilirsiniz. Bu aracın nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [sorun bildirme](how-to-report-a-problem-with-visual-studio.md) sayfası.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 sürüm notları](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio 2017 SDK’daki Yenilikler](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Görseldeki yeniliklerC++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# Yenilikleri](/dotnet/csharp/whats-new)
* [Team Foundation Server yenilikler](/azure/devops/server/whats-new)
* [Mac için Visual Studio yenilikleri](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Visual Studio 2019 ' deki yenilikler](whats-new-visual-studio-2019.md)
