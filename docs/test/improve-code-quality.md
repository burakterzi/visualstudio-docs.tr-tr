---
title: Test araçları
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: e57feede5963b9efc04f98f4c7ba3adfb1eb49b1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984641"
---
# <a name="testing-tools-in-visual-studio"></a>Visual Studio'daki test etme araçları

Visual Studio test araçları, sizin ve ekibinizin yüksek standartlara sahip kod mükemmelliği geliştirmelerine ve bu konuda yardımcı olabilir.

> [!NOTE]
> Birim testi, Visual Studio 'nun tüm sürümlerinde kullanılabilir. Live Unit Testing, IntelliTest ve kodlanmış UI testi gibi diğer test araçları yalnızca Visual Studio Enterprise sürümünde kullanılabilir. Sürümler hakkında daha fazla bilgi için bkz. [Visual Studio Ides 'ı karşılaştırın](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini** penceresi, geliştiricilerin birim testlerini oluşturmalarına, yönetmesine ve çalıştırmasına yardımcı olur. Microsoft birim testi çerçevesini veya çeşitli üçüncü taraf ve açık kaynak çerçevelerinden birini kullanabilirsiniz.

::: moniker range="vs-2017"
![Visual Studio Test Gezgini](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Visual Studio Test Gezgini 16,2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Birim testini kullanmaya başlama](unit-test-your-code.md)
* [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md)
* [Test Gezgini Hakkında SSS](test-explorer-faq.md)
* [Üçüncü taraf birim testi çerçevelerini yükleme](install-third-party-unit-test-frameworks.md)

Visual Studio da genişletilebilir ve NUnit ve xUnit.net gibi üçüncü taraf birim testi bağdaştırıcılarının kapısını açar. Ayrıca, kod kopyalama özelliği, yaygın hata düzeltmeleri veya yeniden düzenleme için aday olabilecek anlamsal benzer kod bloklarını tanımlamanızı sağlayarak yüksek kaliteli yazılım sunmaya yardımcı olur.

![Üçüncü taraf test tümleştirmesi](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) arka planda birim testlerini otomatik olarak çalıştırır ve Visual Studio kod düzenleyicisinde kod kapsamını ve test sonuçlarını grafiksel olarak görüntüler.

## <a name="intellitest"></a>IntelliTest

IntelliTest, yönetilen kodunuz için birim testlerini ve test verilerini otomatik olarak oluşturur. IntelliTest kapsamı geliştirir ve yeni veya mevcut kod için birim testleri oluşturma ve sürdürme çabaları önemli ölçüde azaltır.

![IntelliTest eylemde](media/devtest-intellitest.png)

* [Intellitest ile kodunuz için birim testleri oluşturma](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – tümünü kurala göre bir test](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Intellitest başvuru kılavuzu](intellitest-manual/index.md)

## <a name="code-coverage"></a>Kod kapsamı

[Kod kapsamı](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) , proje kodunuzun birim testleri gibi kodlanmış testler tarafından ne oranda test edildiğini belirler. Hatalara karşı etkili bir şekilde koruma sağlamak için, testleriniz kodunuzun büyük bir oranını "ele almalıdır" veya "kapsamalıdır".

Kod kapsamı analizi, hem yönetilen hem de yönetilmeyen (yerel) koda uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

* [Ne kadar kodun test edildiğini öğrenmek için kod kapsamını kullanın](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Visual Studio (Lab) ile birim testi, kod kapsamı ve kod kopyası Analizi](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [Kod kapsamı analizini özelleştirme](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) , uygulamanın diğer bölümlerini saplamalar veya parçalar ile değiştirerek test ettiğiniz kodu yalıtmanıza yardımcı olur.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Kodlanmış UI ve Selenium ile Kullanıcı Arabirimi testi

Kodlanmış UI testleri, uygulamanızın kullanıcı arabiriminin işlevselliğini ve davranışını doğrulamak için tam otomatikleştirilmiş testlerin oluşturulması için bir yol sağlar. XAML tabanlı UWP uygulamaları, tarayıcı uygulamaları ve SharePoint uygulamaları da dahil olmak üzere çeşitli teknolojiler genelinde UI testini otomatik hale getirebilir.

Selenium ile, en iyi kodlanmış UI testlerini veya genel tarayıcı tabanlı UI testini tercih etmeksizin, Visual Studio ihtiyacınız olan tüm araçları sağlar.

![Kodlanmış UI ile UI testi](media/devtest-codeduitest.png)

* [UI otomasyonunu kullanarak kodunuzu test etme](use-ui-automation-to-test-your-code.md)
* [Kodlanmış UI testi oluşturmaya, düzenlemesine ve sürdürme ile çalışmaya başlama](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Kodlanmış UI Testleriyle UWP uygulamalarını test etme](test-uwp-app-with-coded-ui-test.md)
* [Visual Studio Enterprise (Lab) ile kodlanmış UI testlerine giriş](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="load-testing"></a>Yük testi

[Yük testi](../test/quickstart-create-a-load-test-project.md) , birim testlerini ve Web performans testlerini çalıştırarak bir sunucu uygulamasındaki yükün benzetimini yapar.

## <a name="related-scenarios"></a>İlgili senaryolar

* [Araştırmacı & el ile test (Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [Yük testi (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [Sürekli test (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Kod analizi araçları](../code-quality/code-analysis-for-managed-code-overview.md)
