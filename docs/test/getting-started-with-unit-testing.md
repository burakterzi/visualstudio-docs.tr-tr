---
title: Birim testini kullanmaya başlama
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ecddad721547fdb5689a26a192cf0580ddb44cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664912"
---
# <a name="get-started-with-unit-testing"></a>Birim testini kullanmaya başlama

Kod durumunu korumak, kod kapsamını sağlamak ve müşterilerinizin yapabilmesi için hata ve hataları bulmak üzere birim testlerini tanımlamak ve çalıştırmak için Visual Studio 'Yu kullanın. Kodunuzun düzgün çalıştığından emin olmak için birim testlerinizi sıklıkla çalıştırın.

## <a name="create-unit-tests"></a>Birim testleri oluşturma

Bu bölümde, bir birim testi projesinin nasıl oluşturulacağı yüksek düzeyde açıklanmaktadır.

1. Visual Studio 'da sınamak istediğiniz projeyi açın.

   Örnek birim testi gösterimi amacıyla, bu makale basit bir "Merhaba Dünya" projesini sınar. Bu tür bir projenin örnek kodu aşağıdaki gibidir:

   ```csharp
   public class Program
   {
       public static void Main()
       {
           Console.WriteLine("Hello World!");
       }
   }
   ```

1. **Çözüm Gezgini**, çözüm düğümünü seçin. Ardından, üst menü çubuğundan **dosya**  >   > **Yeni proje** **Ekle** ' yi seçin.

1. Yeni proje iletişim kutusunda, kullanmak istediğiniz test çerçevesi için bir birim testi proje şablonu bulun ve seçin.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de birim testi proje şablonu](media/vs-2019/add-new-test-project.png)

   **İleri**' ye tıklayın, test projesi için bir ad seçin ve ardından **Oluştur**' a tıklayın.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Visual Studio 2019 ' de birim testi proje şablonu](media/mstest-test-project-template.png)

   Test projesi için bir ad seçin ve ardından **Tamam**' a tıklayın.

   ::: moniker-end

   Proje çözümünüze eklenir.

   ![Çözüm Gezgini birim testi projesi](media/vs-2019/solution-explorer.png)

1. Birim testi projesinde, **Başvurular** veya **Bağımlılıklar** ' a sağ tıklayıp **Başvuru Ekle**' yi seçerek test etmek istediğiniz projeye bir başvuru ekleyin.

1. Test etmek istediğiniz kodu içeren projeyi seçin ve **Tamam**' a tıklayın.

   ![Visual Studio 'Ya proje başvurusu ekleme](media/vs-2019/reference-manager.png)

1. Birim testi yöntemine kod ekleyin.

   ![Visual Studio 'da birim testi yöntemine kod ekleme](media/vs-2019/unit-test-method.png)

> [!TIP]
> Birim testlerini oluşturma hakkında daha ayrıntılı yönergeler için bkz. [yönetilen kod için birim testleri oluşturma ve çalıştırma](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

1. Üst menü çubuğundan **test  > ** **Windows**  > **Test Gezgini** ' ni seçerek [Test Gezgini](../test/run-unit-tests-with-test-explorer.md) 'ni açın.

1. **Tümünü Çalıştır**' a tıklayarak birim testlerinizi çalıştırın.

   ![Test Gezgini ile birim testleri çalıştırma](media/vs-2019/test-explorer-run-all.png)

   Testler tamamlandıktan sonra yeşil onay işareti bir testin geçtiğini gösterir. Kırmızı bir "x" simgesi testin başarısız olduğunu gösterir.

   ![Test Gezgini 'nde birim test sonuçlarını gözden geçirme](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [Test Gezgini](../test/run-unit-tests-with-test-explorer.md) 'ni, yerleşik test çerçevesinden (MSTest) veya üçüncü taraf test çerçevelerinden birim testlerini çalıştırmak için kullanabilirsiniz. Testleri kategoriler halinde gruplandırabilir, test listesine filtre uygulayabilir ve testlerin çalma listelerini oluşturabilir, kaydedebilir ve çalıştırabilirsiniz. Ayrıca, testlerin hatalarını ayıklayabilir ve test performansını ve kod kapsamını çözümleyebilirsiniz.

## <a name="view-live-unit-test-results"></a>Canlı birim testi sonuçlarını görüntüle

Visual Studio 2017 veya sonraki sürümlerde MSTest, xUnit veya NUnit test çerçevesini kullanıyorsanız, birim testlerinizin canlı sonuçlarını görebilirsiniz.

> [!NOTE]
> Canlı birim testi yalnızca Enterprise sürümünde kullanılabilir.

1. **Test  > ** **Live Unit Testing**  > **Başlat**' a tıklayarak **Test** menüsündeki canlı birim testini açın.

   ::: moniker range="vs-2017"

   ![Canlı birim testini aç](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de canlı birim testi başlatma](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Kodu yazarken ve düzenlerken testlerin sonuçlarını kod Düzenleyicisi penceresi içinde görüntüleyin.

   ![Testlerin sonuçlarını görüntüleme](media/vs-2019/live-unit-testing-results.png)

1. Bu yöntemi kapsayan testlerin adları gibi daha fazla bilgi görüntülemek için bir test sonucu göstergesine tıklayın.

   ![Test sonucu göstergelerini seçin](media/vs-2019/live-unit-testing-details.png)

Canlı birim testi hakkında daha fazla bilgi için bkz. [canlı birim testi](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>IntelliTest ile birim testleri oluşturma

IntelliTest çalıştırdığınızda hangi testlerin başarısız olduğunu görebilir ve bunları onarmak için gerekli kodu ekleyebilirsiniz. Bir gerileme paketi sağlamak için test projesine kaydetmek üzere oluşturulan testlerin hangisi olduğunu seçebilirsiniz. Kodunuzu değiştirirken, oluşturulan testleri kod değişiklikleriyle eşitlenmiş halde tutmak için IntelliTest 'i yeniden çalıştırın. Nasıl yapılacağını öğrenmek için bkz. [IntelliTest ile kodunuz için birim testleri oluşturma](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest yalnızca .NET Framework hedefleyen yönetilen kod için kullanılabilir.

![IntelliTest ile birim testleri oluşturma](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Kod kapsamını analiz et

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından test edilen belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Hatalara karşı etkili bir şekilde koruma sağlamak için, testleriniz kodunuzun büyük bir oranını uygulamalıdır. Nasıl yapılacağını öğrenmek için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-third-party-test-framework"></a>Üçüncü taraf bir test çerçevesi kullanma

Visual Studio 'da Boost, Google ve NUnit gibi üçüncü taraf test çerçeveleri kullanarak birim testlerini çalıştırabilirsiniz. Seçtiğiniz çerçeveye yönelik NuGet paketini yüklemek için **NuGet Paket Yöneticisi 'ni** kullanın. Ya da NUnit ve xUnit test çerçeveleri için, Visual Studio gerekli NuGet paketlerini içeren önceden yapılandırılmış test projesi şablonlarını içerir.

[NUnit](https://nunit.org/)kullanan birim testleri oluşturmak için:

1. Test etmek istediğiniz kodu içeren çözümü açın.

2. **Çözüm Gezgini** çözüme sağ tıklayın ve  > **Yeni proje** **Ekle** ' yi seçin.

3. **NUnit test projesi** proje şablonunu seçin.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 'de NUnit test proje şablonu](media/vs-2019/nunit-test-project-template.png)

   **İleri**' ye tıklayın, projeyi adlandırın ve ardından **Oluştur**' a tıklayın.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Projeyi adlandırın ve ardından oluşturmak için **Tamam** ' ı tıklatın.

   ::: moniker-end

   Proje şablonu NUnit ve NUnit3TestAdapter için NuGet başvuruları içerir.

   ![Çözüm Gezgini NUnit NuGet bağımlılıkları](media/vs-2019/nunit-nuget-dependencies.png)

4. Test projesinden test etmek istediğiniz kodu içeren projeye bir başvuru ekleyin.

   **Çözüm Gezgini**' de projeye sağ tıklayın ve ardından  > **başvuru** **Ekle** ' yi seçin. ( **Başvurular** veya **Bağımlılıklar** düğümünün sağ tıklama menüsünde de bir başvuru ekleyebilirsiniz.)

5. Test yönteminiz için kod ekleyin.

   ![Birim test kodu dosyanıza kod ekleme](media/vs-2019/unit-test-method.png)

6. Test **Gezgini** 'nden veya test kodu ' na sağ tıklayıp **Test Çalıştır**' ı seçerek testi çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

* [İzlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Birim Testleri Oluştur komutu](create-unit-tests-menu.md)
* [IntelliTest ile testler oluşturma](generate-unit-tests-for-your-code-with-intellitest.md)
* [Test Gezgini ile testleri çalıştırma](run-unit-tests-with-test-explorer.md)
* [Kod kapsamını analiz et](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
