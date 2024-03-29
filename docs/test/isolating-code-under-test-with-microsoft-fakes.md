---
title: Microsoft Fakes ile Test Edilen Kodu Yalıtma
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
dev_langs:
- VB
- CSharp
ms.openlocfilehash: bf00c35868ac5b4df34f2453f046232a91387085
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653111"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Microsoft Fakes ile test edilen kodu yalıtma

Microsoft Fakes, uygulamanın diğer bölümlerini *saplamalar* *veya parçalar*ile değiştirerek test ettiğiniz kodu yalıtmanıza yardımcı olur. Bunlar, testlerinizin denetimi altında olan küçük kod parçalarıdır. Kodunuzu sınama için yalıttığınız zaman, sınama başarısız olduğunda nedeninin başka bir yerde değil, tam da orada olduğunu bileceksiniz. Uygulamanın diğer parçaları çalışmıyor olsa bile, saptamalar ve dolgular kodunuzu test etmenize olanak sağlar.

Fakes iki türde olabilir:

- [Saplama](#get-started-with-stubs) , bir sınıfı aynı arabirimi uygulayan küçük bir değiştirme ile değiştirir.  Saptamalar kullanmak için uygulamanızı her bir bileşenin diğer bileşenlere değil yalnızca arabirimlere bağlı olacak şekilde tasarlamanız gerekir. ("Bileşen" ifadesiyle, birlikte tasarlanan ve güncelleştirilen ve tipik olarak bir derlemede yer alan sınıf veya sınıflardan oluşan grup kastedilmektedir.)

- Bir [Dolgu](#get-started-with-shims) , çalışma zamanında uygulamanızın derlenmiş kodunu değiştirir, böylece belirli bir yöntem çağrısını yapmak yerine, testinizin sağladığı dolgu kodunu çalıştırır. Dolgu, .NET derlemeleri gibi değiştiremeyeceğiniz Derlemelerle değiştirmek için kullanılabilir.

![Fakes diğer bileşenleri değiştirir](../test/media/fakes-2.png)

**Requirements**

- Visual Studio Enterprise
- Bir .NET Framework projesi

> [!NOTE]
> - .NET Standard projeler desteklenmez.
> - Visual Studio ile profil oluşturma, Microsoft Fakes kullanan testler için kullanılamaz.

## <a name="choose-between-stub-and-shim-types"></a>Saplama ve dolgu türleri arasında seçim yapın
Genelde bu sınıfları aynı anda geliştirip güncelleştirdiğinizden bir Visual Studio projesini bileşen olarak kabul edebilirsiniz. Projenin çözümünüzdeki diğer projelere veya diğer derlemelere yaptığı çağrılar için saptama ve dolgu kullanmayı deneyebilirsiniz.

Genel bir kılavuzluk sağlaması için, Visual Studio çözümünüzdeki çağrılar için saptamaları ve diğer başvurulan derlemelerde çağrılar için dolgu verilerini kullanın. Bunun nedeni kendi çözümünüzde bileşenleri, saptamaların gerektirdiği şekilde arabirimleri tanımlayarak ayırmanızın iyi bir uygulama olmasıdır. Ancak *System. dll* gibi dış derlemeler genellikle ayrı arabirim tanımlarıyla sağlanmaz, bu nedenle bunun yerine dolgular kullanmanız gerekir.

Diğer değerlendirmeler şunlardır:

**Mının.** Çalışma zamanında kodunuzu yeniden yazdıkları için dolgular daha yavaş çalışır. Saptamalarda bu performans düşüklüğü yoktur ve sanal yöntemler kadar hızlı ilerleyebilirler.

**Statik yöntemler, korumalı türler.** Arayüzleri uygulamak için yalnızca saptamalar kullanabilirsiniz. Bu nedenle saptama türleri statik yöntemler, sanal olmayan yöntemler, korumalı sanal yöntemler, korumalı türlerdeki yöntemler gibi yöntemlerle kullanılamaz.

**İç türler.** Hem saplamalar hem de parçalar, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> derleme özniteliği kullanılarak erişilebilir hale getirilen iç türlerle birlikte kullanılabilir.

**Özel yöntemler.** Dolgular, bir yöntem imzasındaki tüm türler görünür durumdaysa çağrıları özel yöntemlerle değiştirebilir. Saptamalar yalnızca görünür yöntemlerle değiştirilebilir.

**Arabirimler ve soyut yöntemler.** Saptamalar, test sırasında kullanılabilecek arayüzlerin ve özet yöntemlerin uygulanmalarını sağlar. Kims, metot gövdeleri olmadığından, arabirimleri ve soyut yöntemleri görüntüleyemez.

Genel olarak saptama türlerini kod temelindeki bağımlılıkları ayırmak için kullanmanızı öneririz. Bunu bileşenleri arayüzlerin arkasına gizleyerek yapabilirsiniz. Dolgu türleri, test edilebilir API sağlamayan üçüncü taraf bileşenlerden ayırmak için kullanılabilir.

## <a name="get-started-with-stubs"></a>Saplamalarla çalışmaya başlama
Daha ayrıntılı bir açıklama için, [birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)konusuna bakın.

1. **Arabirim Ekle**

     Saptamalar kullanmak için test etmek istediğiniz kodu, uygulamanızın içindeki diğer bileşende yer alan sınıflara açıkça başvurmayacak şekilde yazmanız gerekir. "Bileşen" ifadesiyle, birlikte geliştirilen ve güncellenen ve tipik olarak tek Visual Studio projesinde yer alan sınıf veya sınıflar kastedilmektedir. Değişkenler ve parametreler, arabirimler kullanılarak bildirilmelidir ve diğer bileşenlerin örnekleri iletilmeli veya fabrika kullanılarak oluşturulmalıdır. Örneğin, StockFeed uygulamadaki farklı bir bileşende bulunan bir sınıfsa bu hatalı olarak değerlendirilir:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Bunun yerine, başka bir bileşen tarafından uygulanabilecek ve bir saptama tarafından test amaçlarıyla uygulanabilecek bir arabirim tanımlayın:

    ```csharp
    public int GetContosoPrice(IStockFeed feed) => feed.GetSharePrice("COOO");
    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Fakes derlemesi Ekle**

    1. **Çözüm Gezgini**, test projesinin başvuru listesini genişletin. Visual Basic ' de çalışıyorsanız, başvuru listesini görmek için **tüm dosyaları göster** ' i seçmeniz gerekir.

    2. Arabirimin (örneğin IStockFeed) tanımlandığı derleme başvurusunu seçin. Bu başvurunun kısayol menüsünde **Fakes derlemesi Ekle**' yi seçin.

    3. Çözümü yeniden derleyin.

3. Testlerinizde saptama örnekleri oluşturun ve yöntemleri için kod sağlayın:

    ```csharp
    [TestClass]
    class TestStockAnalyzer
    {
        [TestMethod]
        public void TestContosoStockPrice()
        {
          // Arrange:

            // Create the fake stockFeed:
            IStockFeed stockFeed =
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                     {
                         // Define each method:
                         // Name is original name + parameter types:
                         GetSharePriceString = (company) => { return 1234; }
                     };

            // In the completed application, stockFeed would be a real one:
            var componentUnderTest = new StockAnalyzer(stockFeed);

          // Act:
            int actualValue = componentUnderTest.GetContosoPrice();

          // Assert:
            Assert.AreEqual(1234, actualValue);
        }
        ...
    }
    ```

    ```vb
    <TestClass()> _
    Class TestStockAnalyzer

        <TestMethod()> _
        Public Sub TestContosoStockPrice()
            ' Arrange:
            ' Create the fake stockFeed:
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
            With stockFeed
                .GetSharePriceString = Function(company)
                                           Return 1234
                                       End Function
            End With
            ' In the completed application, stockFeed would be a real one:
            Dim componentUnderTest As New StockAnalyzer(stockFeed)
            ' Act:
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice
            ' Assert:
            Assert.AreEqual(1234, actualValue)
        End Sub
    End Class

    ```

    Burada Magic 'in özel parçası `StubIStockFeed` sınıftır. Başvurulan derlemedeki her arabirim için saptama sınıfı Microsoft Fakes mekanizması oluşturur. Saplama sınıfının adı, arabirimin adından türetilir, ön ek olarak "`Fakes.Stub`" ve parametre türü adları eklenir.

    Saptamalar ayrıca olaylar ve genel yöntemlerle ilgili olarak özellik okuyucu ve ayarlayıcılar için oluşturulur. Daha fazla bilgi için bkz. [birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Dolgu ile çalışmaya başlama
(Daha ayrıntılı bir açıklama için bkz. [birim testi için uygulamanızı diğer derlemelerden yalıtmak için dolgu kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)

Bileşeninizin `DateTime.Now` çağrıları içerdiğini varsayalım:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Sınama sırasında, gerçek sürüm uygun şekilde her çağrıda farklı bir değer döndürdüğünden `Now` özelliğini dolgu yapmak istersiniz.

Dolgu kullanmak için uygulama kodunu değiştirmeniz veya belirli bir şekilde yazmanız gerekmez.

1. **Fakes derlemesi Ekle**

     **Çözüm Gezgini**, birim testi projenizin başvurularını açın ve taklit etmek istediğiniz yöntemi içeren derlemenin başvurusunu seçin. Bu örnekte, `DateTime` sınıfı *System. dll*' dir.  Visual Basic projesindeki başvuruları görmek için **tüm dosyaları göster**' i seçin.

     **Fakes derlemesi Ekle**' yi seçin.

2. **ShimsContext içine dolgu ekleme**

    ```csharp
    [TestClass]
    public class TestClass1
    {
            [TestMethod]
            public void TestCurrentYear()
            {
                int fixedYear = 2000;

                // Shims can be used only in a ShimsContext:
                using (ShimsContext.Create())
                {
                  // Arrange:
                    // Shim DateTime.Now to return a fixed date:
                    System.Fakes.ShimDateTime.NowGet =
                    () =>
                    { return new DateTime(fixedYear, 1, 1); };

                    // Instantiate the component under test:
                    var componentUnderTest = new MyComponent();

                  // Act:
                    int year = componentUnderTest.GetTheCurrentYear();

                  // Assert:
                    // This will always be true if the component is working:
                    Assert.AreEqual(fixedYear, year);
                }
            }
    }
    ```

    ```vb
    <TestClass()> _
    Public Class TestClass1
        <TestMethod()> _
        Public Sub TestCurrentYear()
            Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
                Dim fixedYear As Integer = 2000
                ' Arrange:
                ' Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet = _
                    Function() As DateTime
                        Return New DateTime(fixedYear, 1, 1)
                    End Function

                ' Instantiate the component under test:
                Dim componentUnderTest = New MyComponent()
                ' Act:
                Dim year As Integer = componentUnderTest.GetTheCurrentYear
                ' Assert:
                ' This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year)
            End Using
        End Sub
    End Class
    ```

    Dolgu sınıfı adları, özgün tür adına `Fakes.Shim` önüne eklenerek yapılır. Parametre adları yöntem adına eklenir. (System. Fakes 'e herhangi bir derleme başvurusu eklemeniz gerekmez.)

Önceki örnek statik yöntem olarak bir dolgu kullanır. Bir örnek yöntemi için dolgu kullanmak üzere tür adı ve Yöntem adı arasında `AllInstances` yazın:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Başvurulacak ' System. ıO. Fakes ' derlemesi yok. Ad alanı dolgu oluşturma işlemi tarafından oluşturulur. , Ancak her zamanki şekilde ' Using ' veya ' Import ' kullanabilirsiniz.)

Ayrıca belirli örnekler, oluşturucular ve özellikler için dolgular oluşturabilirsiniz. Daha fazla bilgi için bkz. [birim testi için uygulamanızı diğer derlemelerden yalıtmak için dolgu kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="in-this-section"></a>Bu bölümde
[Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
