---
title: Kodlanmış UI Testleri için En İyi Yöntemler
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 174059a3b5053602c7f5d21f7b663d0a48bbe709
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665285"
---
# <a name="best-practices-for-coded-ui-tests"></a>Kodlanmış UI testleri için en iyi uygulamalar

Bu konuda, kodlanmış UI testleri geliştirmeye yönelik bazı öneriler açıklanmaktadır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Önerilen uygulamalar

Esnek kodlanmış bir UI testi oluşturmak için aşağıdaki yönergeleri kullanın.

- Mümkün olduğunda **KODLANMıŞ UI test oluşturucusunu** kullanın.

- *UIMap.Designer.cs* dosyasını doğrudan değiştirmeyin. Dosyayı değiştirirseniz, dosyadaki değişikliklerin üzerine yazılır.

- Testinizi kayıtlı yöntemlerin bir dizisi olarak oluşturun. Bir yöntemi kaydetme hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md).

- Her kaydedilen yöntemin tek bir sayfa, form veya iletişim kutusu üzerinde işlem yapması gerekir. Her yeni sayfa, form veya iletişim kutusu için yeni bir test yöntemi oluşturun.

- Bir yöntem oluşturduğunuzda, varsayılan ad yerine anlamlı bir yöntem adı kullanın. Anlamlı bir ad yöntemin amacını belirlemenize yardımcı olur.

- Mümkün olduğunda, her bir kaydedilen yöntemi 10 ' dan az eylemden sınırlayın. Bu modüler yaklaşım, UI değişirse bir yöntemin değiştirilmesini kolaylaştırır.

- *UIMap.Designer.cs* dosyasına otomatik olarak bir onaylama yöntemi ekleyen **kodlanmış UI test oluşturucusunu**kullanarak her bir onaylama işlemi oluşturun.

- Kullanıcı arabirimi (UI) değişirse, test yöntemlerini veya onaylama yöntemlerini yeniden kaydedin veya var olan bir test yönteminin etkilenen bölümlerini yeniden kaydedin.

- Test edilen uygulamanızdaki her bir modül için ayrı bir [UIMap](/previous-versions/dd580454(v=vs.140)) dosyası oluşturun. Daha fazla bilgi için bkz. [birden çok UI haritası ile büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md).

- Test edilen uygulamada, UI denetimlerini oluştururken anlamlı adlar kullanın. Anlamlı adların kullanılması, otomatik olarak oluşturulan denetim adlarına daha fazla açıklık ve kullanılabilirlik sağlar.

- API ile kodlamaya göre onay oluşturuyorsanız, *UIMap.cs* dosyasındaki [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının bölümünde her onaylama için bir yöntem oluşturun. Onaylama işlemi yürütmek için, test yönteinizden bu yöntemi çağırın.

- Doğrudan API ile kodladıysanız, kodunuzda *UIMap.Designer.cs* dosyasında oluşturulan sınıflarda özellikleri ve yöntemleri kullanabilirsiniz. Bu sınıflar işinizi daha kolay, daha güvenilir hale getirir ve daha üretken olmanıza yardımcı olur.

Kodlanmış UI testleri Kullanıcı arabirimindeki birçok değişikliğe otomatik olarak uyum sağlar. Örneğin, bir kullanıcı arabirimi öğesi konum veya renge değiştiyse, çoğu zaman kodlanmış UI testi doğru öğeyi bulmaya devam eder.

Bir test çalıştırması sırasında, Kullanıcı arabirimi denetimleri, bir arama özellikleri kümesi kullanılarak test çerçevesi tarafından bulunur. Arama özellikleri, *UIMap.Designer.cs* dosyasında **kodlanmış UI Test Oluşturucusu** tarafından oluşturulan tanımlarda her bir denetim sınıfına uygulanır. Arama özellikleri, denetimin <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> ve <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> özellikleri gibi, denetimi tanımlamak için kullanılabilen özellik adlarının ad-değer çiftlerini ve özellik değerlerini içerir. Arama özellikleri değişmezse, kodlanmış UI testi Kullanıcı arabirimindeki denetimi başarıyla bulur. Arama özellikleri değiştirilirse, kodlanmış UI testlerinde Kullanıcı arabirimindeki denetimleri ve pencereleri bulmak için buluşsal yöntemler uygulayan bir akıllı eşleşme algoritması vardır. Kullanıcı arabirimi değiştirildiğinde, daha önce tanımlanan öğelerin arama özelliklerini değiştirerek bunların bulundıklarından emin olun.

## <a name="if-your-user-interface-changes"></a>Kullanıcı arabiriminiz değişirse

Kullanıcı arabirimleri genellikle geliştirme sırasında değişir. Bu değişikliklerin etkilerini azaltmak için bazı yollar şunlardır:

- Bu denetime başvuran kayıtlı yöntemi bulun ve bu yöntemin eylemlerini yeniden kaydetmek için **KODLANMıŞ UI test oluşturucusunu** kullanın. Mevcut eylemlerin üzerine yazmak için yöntemi için aynı adı kullanabilirsiniz.

- Bir denetimde artık geçerli olmayan bir onaylama işlemi varsa:

  - Onaylama içeren yöntemi silin.

  - Bu yöntemin çağrısını test yönteminden kaldırın.

  - İnce artı düğmesini UI denetimine sürükleyerek yeni bir onaylama ekleyin, UI haritasını açın ve yeni onay ekleyin.

Kodlanmış UI testlerini kaydetme hakkında daha fazla bilgi için bkz. [kodunuzu test etmek IÇIN UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Teste devam etmeden önce bir arka plan işleminin tamamlanmasını gerekiyorsa

Sonraki UI eylemine devam edebilmeniz için bir işlem bitene kadar beklemeniz gerekebilir. Bunu yapmak için, aşağıdaki örnekte olduğu gibi, testi devam etmeden önce beklemek için <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> kullanabilirsiniz:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Ayrıca bkz.

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Birden çok UI haritası ile büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
