---
title: Unity uygulamalarıyla uygulama yaşam döngüsü yönetimi (ALM) | Microsoft Docs
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 8d6cbdee57d2f1edf7d696ad9a4053ddcb08bce3
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777728"
---
# <a name="devops-with-unity-apps"></a>Unity uygulamalarıyla DevOps

Modern platformlar için uygulama geliştirme, yalnızca koddan çok daha fazla etkinlik içerir. DevOps (geliştirme + işlemler) olarak adlandırılan bu etkinlikler, uygulamanın tamamlanma yaşam döngüsünü kapsar ve iş planlama ve izleme, kod tasarlama ve uygulama, bir kaynak kodu deposunu yönetme, yapıları çalıştırma, sürekli tümleştirmeler yönetme ve dağıtımlar, test (birim testleri ve UI testleri dahil), hem geliştirme hem de üretim ortamlarında çeşitli tanılama biçimlerini çalıştırıp uygulama performansını ve kullanıcı davranışlarını telemetri ve analiz aracılığıyla gerçek zamanlı olarak izleyin.

Visual Studio, Azure DevOps Services ve Team Foundation Server ile birlikte çeşitli DevOps özellikleri sunar. Bunların birçoğu, bir komut dosyası dili olarak kullanılırken C# Unity &mdash;especially oluşturulan Oyunlar ve modern grafik uygulamaları da dahil olmak üzere platformlar arası projeler için geçerlidir. Ancak, Unity 'nin kendi geliştirme ortamı ve çalışma zamanı altyapısı bulunduğundan, Visual Studio 'da oluşturulan diğer proje türlerine yaptıkları için bazı DevOps özellikleri uygulanmaz.

Aşağıdaki tablolar, Unity ile çalışırken Visual Studio 'daki DevOps özelliklerinin nasıl uygulanacağını veya uygulanacağını belirler. Özelliklerin kendileri hakkındaki ayrıntılar için bağlantılı belgelere başvurun.

## <a name="agile-tools"></a>Çevik Araçlar

Başvuru bağlantısı: [Çevik Araçlar ve çevik proje yönetimi hakkında](/azure/devops/boards/backlogs/backlogs-overview?view=vsts) (Team Explorer Everywhere dahil Azure BOARDS veya TFS kullanarak)

Genel Açıklama: tüm planlama ve izleme özellikleri proje türü ve kodlama dillerinden bağımsızdır.

|Özellik|Unity ile desteklenir|Ek açıklamalar|
|-------------|--------------------------|-------------------------|
|Biriktirme listeleri ve Sprint 'leri yönetme|Evet||
|Çalışma izleme|Evet||
|Takım odası işbirliği|Evet||
|Kanban panoları|Evet||
|İlerlemeyi raporla ve görselleştirin|Evet||

## <a name="modeling"></a>Modelleme

Başvuru bağlantısı:  **[çözümleme ve model mimarisi](../modeling/analyze-and-model-your-architecture.md)**

Genel Açıklama: Bu tasarım özellikleri kodlama dilinden bağımsız olsa da, gibi C#.NET dilleri ile birlikte çalışarak, nesne hiyerarşileri ve sınıf ilişkileri ile geleneksel bir uygulama paradigması üzerinde çalışır. Unity içinde bir oyun tasarlamak, grafik nesnelerin, seslerin, gölgelendiricilerin, betiklerin vb. ilişkilerini tamamen farklı bir paradigma içerir. Bu nedenle, Visual Studio modelleme diyagramı araçları özellikle bir Unity projesinin tamamına uygun değildir. Bunlar, C# betiklerdeki ilişkileri yönetmek için kullanılabilir, ancak bu yalnızca tek bir parçasıdır.

|Özellik|Unity ile desteklenir|Ek açıklamalar|
|-------------|--------------------------|-------------------------|
|Sıralı diyagramlar|Hayır||
|Bağımlılık grafikleri|Hayır||
|Çağrı hiyerarşisi|Hayır||
|Sınıf Tasarımcısı|Hayır||
|Mimari Gezgini|Hayır||
|UML diyagramları (kullanım örneği, etkinlik, sınıf, bileşen, dizi ve DSL)|Hayır||
|Katman diyagramları|Hayır||
|Katman doğrulama|Hayır||

## <a name="code"></a>Kod

|Özellik|Unity ile desteklenir|Ek açıklamalar|
|-------------|--------------------------|-------------------------|
|[Team Foundation sürüm denetimi (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) veya Azure Repos kullanın|Evet|Unity projeleri yalnızca diğer projeler gibi sürüm denetim sistemlerine yerleştirilebilecek bir dosya koleksiyonudur, ancak bu tablodan sonra açıklanan bazı özel noktalar vardır.|
|[Azure Repos git ile çalışmaya başlama](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Evet|Tablodan sonraki notlara bakın.|
|[Kod Kalitesini Geliştirme](../test/improve-code-quality.md)|Evet||
|[Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)|Evet||
|[Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)|Evet||

Unity ile sürüm denetimi için özel hususlar:

1. Unity, oyun varlıkları hakkındaki meta verileri, varsayılan olarak gizlenen tek ve donuk bir kitaplıkta izler. Dosyaları ve meta verileri eşitlenmiş halde tutmak için meta verilerin görünür olması ve daha yönetilebilir parçalara depolanması gerekir. Ayrıntılar için [Unity Ile dış sürüm denetim sistemleri](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity belgeleri) kullanma konusuna bakın.

2. Bir Unity projesindeki tüm dosyalar ve klasörler, yukarıdaki bağlantıda da açıklandığı gibi, kaynak denetimi için uygun değildir. Varlıklar ve ProjectSettings klasörleri eklenmelidir, ancak kitaplık ve geçici klasörlerin olmaması gerekir. Kaynak denetimine gitmeyecek oluşturulan dosyaların ek bir listesi için, StackOverflow 'de [unity3d kaynak denetimi Için git kullanma](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) konusuna bakın. Birçok geliştirici bu konuya bağımsız olarak da BDE oturum açtı.

3. Unity projesindeki (dokular veya ses dosyaları gibi) ikili varlıklar, büyük miktarda depolama alanı alabilir. Git deposu gibi çeşitli kaynak denetim sistemleri, değişiklik yalnızca dosyanın küçük bir kısmını etkilese bile, yapılan her değişiklik için dosyanın benzersiz bir kopyasını saklar. Bu, git deposunun blok haline gelmesine neden olabilir. Unity geliştiricileri bu şekilde ele almak için genellikle depolarına yalnızca son varlıkları eklemeyi ve OneDrive, DropBox veya git-ek gibi varlıklarının çalışma geçmişini tutmanın farklı bir araçlarını kullanır. Bu yaklaşım, bu tür varlıkların genellikle kaynak kodu değişiklikleriyle birlikte sürüm oluşturulması gerekmediği için geçerlidir. Geliştiriciler ayrıca, genellikle proje düzenleyicisinin varlık serileştirme modunu, metni, sahne dosyalarını, kaynak denetiminde birleştirme yapılmasına izin veren ikili biçim yerine metin halinde depolamaya zorlamak üzere ayarlar. Ayrıntılar için bkz. [Düzenleyici ayarları](https://docs.unity3d.com/Manual/class-EditorManager.html) (Unity belgeleri).

## <a name="build"></a>Yapı

Başvuru bağlantısı:  **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts)**

|Özellik|Unity ile desteklenir|Ek açıklamalar|
|-------------|--------------------------|-------------------------|
|Şirket içi Team Foundation Server (TFS)|Üç|Unity projeleri, Visual Studio derleme sistemi aracılığıyla değil Unity ortamı aracılığıyla oluşturulur (Unity için Visual Studio Araçları içinde derleme betikleri derler ancak yürütülebilir bir işlem oluşturmaz). Unity [projelerini komut satırından](https://docs.unity3d.com/Manual/CommandLineArguments.html) (Unity belgeleri) derlemek mümkündür. bu nedenle, Unity 'nin kendisi bu bilgisayarda yüklü olması şartıyla uygun Unity komutlarını yürütmek IÇIN bir TFS sunucusunda MSBuild işlemini yapılandırmak mümkündür.<br /><br /> Unity Ayrıca, bir git veya SVN deposunu izleyen ve düzenli derlemeler çalıştıran [Unity bulut derlemesini](https://build.cloud.unity3d.com/landing/)de sunmaktadır. Şu anda TFVC veya Azure DevOps Services ile çalışmaz.|
|Azure DevOps Services bağlı şirket içi derleme sunucusu|Üç|Yukarıdaki koşulların aynısını göz önüne alarak, Azure DevOps Services aracılığıyla tetiklenen derlemelerin şirket içi TFS bilgisayarı kullanması daha da olasıdır. Yönergeler için bkz. [Yapı ve sürüm aracıları](/azure/devops/pipelines/agents/agents?view=vsts) .|
|Azure DevOps Services barındırılan denetleyici hizmeti|Hayır|Unity derlemeleri Şu anda desteklenmiyor.|
|Ön ve son betiklerle derleme tanımları|Evet|Bir derlemeyi çalıştırmak için Unity komut satırını kullanan özel bir derleme tanımı, ön ve derleme sonrası betikler için de yapılandırılabilir.|
|Geçitli iadeler dahil sürekli tümleştirme|Evet|TFVC için geçitli iadeler, yalnızca git, iadeler yerine bir çekme isteği modelinde çalışmaktadır.|

## <a name="test"></a>Test

|Özellik|Unity ile desteklenir|Ek açıklamalar|
|-------------|--------------------------|-------------------------|
|Testleri planlama, test çalışmaları oluşturma ve test paketlerini düzenleme|Evet||
|El ile test|Evet||
|Test Yöneticisi (kaydı ve kayıttan yürütme testleri)|Yalnızca Windows cihazları ve Android öykünücüleri||
|Kod kapsamı|yok|Birim testi, Unity içinde, Visual Studio değil, için geçerli değildir, aşağıya bakın.|
|[Kodunuzun birim testi](../test/unit-test-your-code.md)|Unity içinde, ancak Visual Studio 'Ya değil|Unity, [Unity test araçlarının](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity varlık deposu) bir parçası olarak kendi birim test çerçevesini sağlar. Birim testi sonuçları Unity içinde raporlanır ve Visual Studio içinde kullanıma sunulacaktır.|
|[UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)|Hayır|Kodlanmış UI testleri, uygulamanın kullanıcı arabirimindeki okunabilir denetimlere dayanır; Unity uygulamaları doğası halinde grafik olduğundan, içerik kodlanmış UI test araçları tarafından okunamaz.|

## <a name="improve-code-quality"></a>Kod kalitesini geliştirme

Başvuru bağlantısı:  **[kod kalitesini geliştirme](../test/improve-code-quality.md)**

|Özellik|Unity ile desteklenir|Ek açıklamalar|
|-------------|--------------------------|-------------------------|
|[Yönetilen kod kalitesini analiz etme](../code-quality/code-analysis-for-managed-code-overview.md)|Evet|, C# Visual Studio içinde betik kodunu çözümleyebilir.|
|[Kod kopyası algılamayı kullanarak yinelenen kod bulma](https://msdn.microsoft.com/library/hh205279.aspx)|Evet|, C# Visual Studio içinde betik kodunu çözümleyebilir.|
|[Yönetilen kodun ölçüm karmaşıklığı ve bakımma](../code-quality/code-metrics-values.md)|Evet|, C# Visual Studio içinde betik kodunu çözümleyebilir.|
|[Performans Gezgini](../profiling/performance-explorer.md)|Hayır|[Unity profil oluşturucuyu](https://docs.unity3d.com/Manual/Profiler.html) (Unity Web sitesi) kullanın.|
|[.NET Framework bellek sorunlarını analiz etme](https://msdn.microsoft.com/library/dn342825.aspx)|Hayır|Visual Studio Araçları, profil oluşturma için mono Framework 'te (Unity tarafından kullanılan) kancalar içermez. [Unity profil oluşturucuyu](http://docs.unity3d.com/Manual/Profiler.html) (Unity belgeleri) kullanın.|

## <a name="release-management"></a>Yayın yönetimi

Başvuru bağlantısı: [Azure Pipelines ve TFS 'de derleme ve yayınlama](/azure/devops/pipelines/overview?view=vsts)

|Özellik|Unity ile desteklenir|Ek açıklamalar|
|-------------|--------------------------|-------------------------|
|Yayın süreçlerini yönetme|Evet||
|Betikler aracılığıyla dışarıdan yükleme için sunuculara dağıtım|Evet||
|App Store 'a yükle|Kısmi|Bazı uygulama mağazalarında bu işlemi otomatik hale getirebilen uzantılar vardır. [Azure DevOps Services Için uzantılara](https://marketplace.visualstudio.com/VSTS)bakın; Örneğin, [Google Play için uzantı](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>HockeyApp ile izleme

Başvuru bağlantısı:  **[HockeyApp ile izleme](https://www.hockeyapp.net/features/)**

|Özellik|Unity ile desteklenir|Ek açıklamalar|
|-------------|--------------------------|-------------------------|
|Kilitlenme Analizi, telemetri ve Beta dağıtımı|Evet|HockeyApp, Beta dağıtımını işlemek ve kilitlenme raporları almak için öncelikli olarak faydalıdır.<br /><br /> Betiklerden C# telemetri Için, Unity tarafından kullanılan .NET sürümünde çalışan herhangi bir analiz çerçevesini kullanmak mümkündür. Ancak bu, yalnızca oyun betikleri içinde analizler ve Unity altyapısının içinde daha derin değildir. Mevcut olan Application Insights için eklenti yoktur, ancak [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) ve [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity)gibi diğer analiz çözümleri için eklentiler mevcuttur. Bir Unity projesinin doğasını anlayan, Unity Analytics gibi hizmetler, genel çerçevelerden çok daha anlamlı analizler sunacaktır.|
