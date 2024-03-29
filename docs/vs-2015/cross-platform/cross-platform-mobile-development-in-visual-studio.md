---
title: Platformlar arası Mobil Geliştirme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 27f6ee12d7404c77e4994a4e89cf23c9b3cdef0f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297894"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio’da Platformlar Arası Mobil Geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio kullanarak Android, iOS ve Windows cihazlar için uygulamalar oluşturabilirsiniz.  Uygulamanızı tasarlarken, araçları Visual Studio'da bağlı hizmetler Application ınsights'ı Office 365 ve Azure App Service gibi kolayca eklemek için kullanın.

 C# ve .NET Framework, HTML ve JavaScript veya C++ kullanarak uygulamalarınızı oluşturun. Kod, dizeler, resimleri paylaşın ve kullanıcı arabiriminin bazı durumlarda bile.

 Oyun veya derinlikli bir grafik uygulaması oluşturmak istiyorsanız, Unity için Visual Studio Araçları'nı yükleyin ve tüm Visual Studio ile Unity uygulamaları için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı, güçlü üretkenlik özellikleri keyfini çıkarın, iOS, Android, Windows ve diğer platformlarda çalıştırın.

 **Bu makalede:**

- [Android, iOS ve Windows için uygulama oluşturma (.NET Framework)](#NET)

  - [Tek bir kod tabanında Android, iOS ve Windows 'u hedefleyin](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Hedef Windows 10 cihazları](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Android, iOS ve Windows için uygulama oluşturma (HTML/JavaScript)](#HTML)

- [Android ve Windows için uygulama oluşturma (C++)](#CPP)

- [Unity için Visual Studio Araçları 'nı kullanarak Android, iOS ve Windows için platformlar arası bir oyun oluşturun](#Unity)

## <a name="NET"></a>Android, iOS ve Windows için uygulama oluşturma (.NET Framework)
 ![Cihazlarınız](../cross-platform/media/homedevices.png "HomeDevices")

 Xamarin ile kod ve hatta kullanıcı Arabirimi paylaşımı aynı çözüm içinde Android, iOS ve Windows hedefleyebilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com) yükler|
|[Visual Studio 'Da Xamarin hakkında bilgi edinin](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio ve Xamarin](../cross-platform/visual-studio-and-xamarin.md) (MSDN Kitaplığı)|
|[Xamarin uygulamalarıyla uygulama yaşam döngüsü yönetimi (ALM)](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (MSDN Kitaplığı)|
|[Visual Studio 'da Evrensel Windows uygulamaları hakkında bilgi edinin](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift ve C# (download.Microsoft.com) arasındaki benzerlikler hakkında bilgi edinin](https://aka.ms/scposter)|
|[Android Için Visual Studio öykünücüsü (VisualStudio.com) hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/msft-android-emulator/)|

### <a name="AndroidHTML"></a>Tek bir kod tabanında Android, iOS ve Windows 'u hedefleyin
 Kullanarak Android, iOS ve Windows için yerel uygulamalar oluşturabilirsiniz C# veya F# (Visual Basic şu anda desteklenmiyor).  Başlamak için Visual Studio 2015 ' i yükledikten sonra yükleyicideki **özel** seçeneğini belirleyin ve **platformlar arası mobil geliştirme > C#/.net (Xamarin)** altındaki kutuyu işaretleyin. Ayrıca, Visual Studio 2013 için Xamarin 'i yüklemek için gereken [Xamarin yükleyicisi](https://www.xamarin.com/download)ile de başlayabilirsiniz.

 Visual Studio 2015 zaten yüklüyse, yükleyici 'yi **Denetim Masası 'ndan çalıştırın > programlar ve Özellikler** ' den çalıştırın ve yukarıdaki Xamarin Için aynı **özel** seçeneği belirleyin.

 İşiniz bittiğinde, proje şablonları **Yeni proje** iletişim kutusunda görünür. "Xamarin" üzerinde yalnızca aramak için Xamarin şablonları bulmanın en kolay yolu olan

 Xamarin yerel Android, iOS ve Windows işlevselliğini .NET nesneleri olarak kullanıma sunar. Bu nedenle, uygulamalarınızı yerel API'lere ve yerel kullanıcı denetimleri tam erişime sahiptir ve bunlar yalnızca, yerel platform dillerde yazılan uygulamaları olarak duyarlı.

 Bir proje oluşturduğunuzda, tüm Visual Studio üretkenlik özelliklerinden faydalanabilirsiniz. Örneğin, sayfa oluşturmak için bir tasarımcı kullanır ve yerel API'lere mobil platformlarda keşfetmek için IntelliSense kullanın. Uygulamanızı çalıştırın ve nasıl göründüğüne bakmak hazır olduğunuzda, Android veya Android SDK öykünücüsü için Visual Studio öykünücüsü'nü kullanın, Windows uygulamaları yerel olarak çalıştırma veya Windows uygulamalarını Windows Phone öykünücü üzerinde çalıştırın. Tethered Android ve Windows cihazları doğrudan da kullanabilirsiniz. İOS projeleri için bir mac'e bağlanın ve Visual Studio'dan Mac öykünücüyü başlatın veya tethered bir cihaza bağlayın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Bir Xamarin.Forms kullanarak tüm cihazlarda oluşturan sayfalar kümesini tasarlama
 Uygulama tasarımınızın karmaşıklığına bağlı olarak, proje şablonlarının **Mobile Apps** grubundaki *Xamarin. Forms* şablonlarını kullanarak oluşturmayı düşünebilirsiniz. Xamarin.Forms, Android, iOS ve Windows arasında paylaşabilirsiniz tek bir arabirim oluşturmanıza imkan tanıyan bir UI araç takımıdır.  Xamarin.Forms çözümü derlediğinizde, bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması elde edersiniz. Daha fazla ayrıntı için bkz. [Xamarin ile mobil geliştirme hakkında bilgi edinin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="ShareHTML"></a>Android, iOS ve Windows uygulamaları arasında kod paylaşma
 Xamarin.Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarlamak seçerseniz, çoğu kullanıcı Arabirimi olmayan kodunuzun platformu projelerinde (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, iş mantığı, bulut tümleştirme, veritabanı erişimi veya .NET Framework'ü hedefleyen herhangi bir kod içerir. Paylaşamazsınız yalnızca kodu belirli bir platformu hedefleyen kodudur.

 ![Windows, iOs ve Android kullanıcı arabirimi ile kod paylaşma](../cross-platform/media/sharecode.png "ShareCode")

 Paylaşılan bir proje, taşınabilir sınıf kitaplığı projesi veya her ikisini de kullanarak kodunuzu paylaşabilir. Daha fazla iyi bir paylaşılan projede veya bazı kod yapar bazı kod uygun bir taşınabilir sınıf kitaplığı projesi içinde anlamlıdır bulabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|Paylaşılan projeler, taşınabilir sınıf kitaplığı projeleri veya her ikisini de kullanarak kodunuzu paylaşmak isteyip istemediğinizi seçin.<br /><br /> [Platformlar arasında kod paylaşma](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (blog .NET Framework)<br /><br /> [Kod seçeneklerini paylaşma](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [.NET Framework Ile kod paylaşma seçenekleri](https://msdn.microsoft.com/library/dn720832.aspx) (MSDN Kitaplığı)|

### <a name="WindowsHTML"></a>Hedef Windows 10 cihazları
 ![Windows cihazları](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Windows 10 cihazları olan tüm tekliflerden hedefleyen tek bir uygulama oluşturmak istiyorsanız, bir evrensel Windows uygulaması oluşturun. Tek bir proje kullanarak uygulama tasarlayın ve hangi cihaz ne olursa olsun, bunları görüntülemek için kullanılır, sayfalar düzgün bir şekilde işlenir.

 Evrensel Windows uygulaması proje şablonu ile başlayın. Sayfalarınızı görsel olarak tasarlamanıza ve bunları çeşitli cihaz türleri için görünme görmek için bir önizleme penceresini açın. Nasıl bir cihazda bir sayfa görünür kullanmak istemiyorsanız, sayfanın ekran boyutu, çözüm ya da yatay veya dikey modu gibi çeşitli yönleriyle daha iyi uyacak şekilde en iyi duruma getirebilirsiniz. Tüm bu, Visual Studio'da sezgisel araç pencereleri ve kolayca erişilebilen menü seçeneklerini kullanarak yapabilirsiniz. Uygulamanızı çalıştırmaya ve kodunuzda ilerlemenize hazırsanız, **Standart** araç çubuğunda bulunan bir açılan listede farklı cihaz türleri için cihaz öykünücülerini ve simülatörleri tümünü bulacaksınız.

 Windows 10 oldukça yeni olduğundan Windows 8.1 hedefleyen proje şablonları da bulabilirsiniz. İstediğiniz ve uygulamanızı Windows 10 telefonlar, tabletler ve bilgisayarlar üzerinde çalışır, bu proje şablonları kullanabilirsiniz. Ancak, Windows 8.1 çalıştıran tüm cihazlara otomatik alırsınız Windows 10 yükseltme, bu nedenle özel nedenlerin neden yerine hedef Windows 8.1 olmadığı sürece, Windows 10'u hedefleyen proje şablonları kullanmanızı öneririz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Evrensel Windows uygulamaları](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Geliştirme Merkezi) hakkında bilgi edinin|
|[İlk birini oluşturma](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Geliştirme Merkezi)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Uygulamaları Evrensel Windows Platformu geçirme (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="HTML"></a>Android, iOS ve Windows için uygulama oluşturma (HTML/JavaScript)
 ![Cihazlarınız](../cross-platform/media/homedevices.png "HomeDevices")

 Bir web geliştiricisi olduğunuzu ve HTML ve JavaScript ile ilgili bilgi sahibi olduğunuz, Apache Cordova için Visual Studio araçları kullanarak Windows, Android ve iOS hedefleyebilirsiniz. Bu uygulamalar, tüm üç platformlar hedefleyebilir ve bunları en alışık olduğunuz işlemleri ve becerileri kullanarak oluşturun.

 Apache Cordova eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, tüm üç platformları (Android, iOS ve Windows), yerel cihaz özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API'si sağlar.

 Bu API'ler, platformlar arası olduğundan, tüm üç platformlar arasında yazma çoğu paylaşabilirsiniz. Bu, geliştirme ve Bakım maliyetlerinizi azaltır. Ayrıca, baştan başlatmaya gerek yoktur. Web uygulamalarının diğer türleri oluşturduysanız, herhangi bir şekilde yeniden tasarlayıp tasarlayamayacağınızı veya değiştirmek zorunda kalmadan, bu dosyaları ile Cordova uygulamanızı paylaşabilirsiniz.

 ![Çok&#45;cihazlı karma uygulamalar](../cross-platform/media/multidevicehybridapps.png "Multidevicehybridaps")

 Başlamak için Visual Studio 2015 ' yi yükleyip kurulum sırasında **HTML/JavaScript (Apache Cordova)** özelliğini seçin. Visual Studio 2013 kullanıyorsanız, Apache Cordova uzantısı için Visual Studio Araçları yükleyin. Her iki durumda da, Cordova araçları, çok platformlu uygulamanızı oluşturmak için gerekli tüm üçüncü taraf yazılımlarını otomatik olarak yükler.

 Uzantıyı yükledikten sonra, Visual Studio 'Yu açın ve **boş bir uygulama (Apache Cordova)** projesi oluşturun. Ardından, JavaScript veya Typescript kullanarak uygulamanızı geliştirebilirsiniz. Uygulamanızı genişletmek için eklentilerini da ekleyebilir ve kod yazarken IntelliSense içinde eklentiler API'lerinden görünür.

 Kodunuz uygulama ve adım çalıştırmaya hazır olduğunuzda, Apache Ripple öykünücü, Visual Studio öykünücü (Android veya Windows Phone), bir tarayıcı veya bilgisayarınıza doğrudan bağlı bir cihaz gibi bir öykünücü seçin. Ardından, uygulamanızı başlatın. Bir Windows bilgisayarda uygulama geliştiriyorsanız, hatta üzerinde çalıştırabilirsiniz. Bu seçeneklerin tümü Visual Studio Araçları'nın bir parçası olarak Visual Studio ile Apache Cordova için oluşturulur.

 Evrensel Windows uygulamaları oluşturma Visual Studio'da hala kullanılabilir proje şablonları bu nedenle yalnızca Windows cihazları hedefleyen planlıyorsanız, bunları kullanan çekinmeyin. Daha sonra Android ve iOS platformlarını karar verirseniz, her zaman bir Cordova projesi için kod bağlantı noktası. Bu API kullanan herhangi bir kod yeniden kullanabilmesi WinJS API'leri, açık kaynak sürümü vardır. Bu, gelecekte diğer platformları hedefleyen planlıyorsanız, Apache Cordova için Visual Studio Araçları ile başlamanızı öneririz belirtti.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com) yükler|
|[Apache Cordova için Visual Studio araçları kullanmaya başlama](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (Taco.VisualStudio.com)|
|[Android Için Visual Studio öykünücüsü (VisualStudio.com) hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/msft-android-emulator/)|

## <a name="CPP"></a>Android ve Windows için uygulama oluşturma (C++)
 ![Android,&#43; &#43; iOS ve Windows için derlemek için C kullanın](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak Visual Studio 2015 ve Visual C++ platformlar arası mobil geliştirme araçlarını yükleyin. Ardından, Android veya Windows hedefleyen bir uygulama için bir yerel etkinlik uygulaması oluşturabilirsiniz. İOS hedefleyen C++ şablonları henüz kullanıma sunulmamıştır. Ve ardından bunları bir platformlar arası statik veya dinamik paylaşılan kitaplık kullanarak arasında kod paylaşma, Android ve Windows aynı çözüm içinde hedefleyebilirsiniz.

 Gelişmiş grafik işleme, oyun gibi her türlü gerektiren Android için bir uygulama oluşturmak ihtiyacınız varsa yapmak için C++ kullanabilirsiniz. **Yerel etkinlik uygulaması (Android)** projesi ile başlayın. Bu proje, Clang araç zinciri için tam destek sunar.

 ![Yerel etkinlik proje şablonu](../cross-platform/media/cross-plat-cpp-native.png "Çapraz Plat_CPP_Native")

 Uygulamanızı çalıştırın ve nasıl göründüğüne bakmak hazır olduğunuzda, Android için Visual Studio öykünücüsü'nü kullanın. Bu hızlı, güvenilir ve kolay yükleme ve yapılandırma.

 Ayrıca, C++ ve evrensel Windows uygulaması proje şablonunu kullanarak Windows 10 cihazları olan tüm tekliflerden hedefleyen bir uygulama oluşturabilirsiniz. Bu konuda daha önce görünen [hedef Windows 10 cihazları](#WindowsHTML) bölümünde bunun hakkında daha fazla bilgi edinin.

 Bir statik veya dinamik paylaşılan kitaplık oluşturarak, Android ve Windows arasında C++ kod paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Bir Windows veya Android projesi, daha önce bu bölümde açıklanan olanlar gibi bu kitaplığı kullanabilir. Ayrıca, bir uygulamada, Xamarin, Java veya yönetilmeyen DLL işlevlerini çağırma olanak sağlayan herhangi bir dil kullanarak yapı raporlarını kullanabilirsiniz.

 Bu kitaplıklara kod yazarken, Android ve Windows platformlarını yerel API'leri keşfetmek için IntelliSense'i kullanabilirsiniz. Kesme noktaları, kodu adımlama ve bulabilir ve tüm hata ayıklayıcı'nın Gelişmiş özelliklerine kullanarak sorunları düzeltmek için bu kitaplık projeleri, Visual Studio hata ayıklayıcıyla tamamen tümleştirilmiştir.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'Yu indirin.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Platformlar arası mobil C++ geliştirme araçları için görseli yükler.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Kitaplığı)|
|[Birden çok platformu hedeflemek C++ için kullanımı hakkında daha fazla bilgi edinin.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[İhtiyaç duyduğunuz şeyi yükleyip Android için yerel bir etkinlik uygulaması oluşturun](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Kitaplığı)|
|[Android Için Visual Studio öykünücüsü (VisualStudio.com) hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/msft-android-emulator/)|
|[Android ve Windows uygulamalarıyla C++ kod paylaşma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Platformlar arası mobil geliştirme örnekleri C++ ](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Kitaplığı)|
|[İçin C++ ek platformlar arası mobil geliştirme örnekleri](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (Code. MSDN)|

## <a name="Unity"></a>Unity için Visual Studio Araçları 'nı kullanarak Android, iOS ve Windows için platformlar arası bir oyun oluşturun
 Unity için Visual Studio Araçları, Visual Studio 'nun, Web dahil olmak üzere Windows, iOS, Android ve diğer platformları hedefleyen çok yönlü uygulamalar için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı olan *Unity*ile Visual Studio 'nun güçlü kod düzenlemesini, üretkenliğini ve hata ayıklama araçlarını tümleştiren ücretsiz bir uzantıdır.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Visual Studio Araçları ile Unity (VSTU), oyun ve düzenleyici betikleri C# dilinde yazın ve ardından, güçlü bir hata ayıklayıcı hataları bulma ve düzeltme için Visual Studio kullanabilirsiniz. VSTU en son sürümünü Unity 5 için destek getirir ve Unity'nın ShaderLab gölgelendirici dili için söz dizimi renklendirme, daha iyi eşitlemesi Unity, daha zengin hata ayıklama ve geliştirilmiş kod oluşturma için MonoBehavior Sihirbazı'nı içerir. VSTU, Unity proje dosyalarınızı, konsol iletileri ve daha az zaman için ve Unity Düzenleyicisi'nden kod yazarken geçiş ayırmasına oyununuzu Visual Studio'ya başlatma özelliğini de getirir.

 Oyununuzu Unity ve Unity için Visual Studio Araçları ile oluşturmaya hemen başlayın.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio ile Unity oyunları oluşturma hakkında daha fazla bilgi edinin](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Unity için Visual Studio Araçları hakkında daha fazla bilgi edinin](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Kitaplığı)|
|[Unity için Visual Studio araçları kullanmaya başlama](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Kitaplığı)|
|[Unity için Visual Studio Araçları 2,0 önizlemesine yönelik en son geliştirmeler hakkında bilgi edinin](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blogu)|
|[Unity için Visual Studio Araçları 2,0 önizlemesine bir video tanıtımı izleyin](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (video)|
|[Unity hakkında bilgi edinin](https://unity.com/) (Unity Web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio projesine Office 365 API 'leri ekleme](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Services](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
