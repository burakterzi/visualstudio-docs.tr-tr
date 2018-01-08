---
title: "Birden çok UI eşlemesi bulunan büyük uygulamaları sınama | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: "22"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 2ecea317b60e100b282428d953694238b5c63f21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Birden Çok UI Eşlemesi Bulunan Büyük Uygulamaları Sınama
Bu konuda, birden çok UI eşlemesi kullanarak büyük bir uygulamayı test ederken kodlanmış UI testleri kullanma açıklanmaktadır.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
 Bir yeni kodlanmış UI testi oluşturduğunuzda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] test çerçevesi varsayılan olarak test için kod oluşturur bir <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> sınıfı. Kodlanmış UI testlerini nasıl kaydedileceği hakkında daha fazla bilgi için bkz: [kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) ve [kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md).  
  
 UI eşlemesi için oluşturulan kod testin etkileşimde her nesne için bir sınıf içerir. Oluşturulan her yöntemi için Yöntem parametreleri için bir yardımcı sınıf özellikle bu yöntem için oluşturulur. Çok sayıda nesneleri, sayfalar ve formlar ve denetimler, uygulamanızda varsa, UI eşlemesi çok fazla büyüyebilir. Ayrıca, birkaç kişiye testleri üzerinde çalışıyorsanız, uygulama, tek bir büyük UI eşleme dosyası ile yönetilmeleri haline gelir.  
  
 Birden çok UI haritası dosyalarını kullanarak aşağıdaki faydaları sağlayabilir:  
  
-   Her eşleme mantıksal bir alt uygulama ile ilişkili olabilir. Bu değişiklikleri yönetmeyi kolaylaştırır.  
  
-   Her tester uygulamanın bir bölüm çalışma ve diğer uygulama bölümleri üzerinde çalışan diğer sınayıcılar müdahale olmaksızın kendi kodunda denetleyin.  
  
-   Uygulama kullanıcı Arabirimi eklemeler, artımlı olarak UI diğer bölümleri için en az düzeyde etkisi testleri ile genişletilebilir.  
  
## <a name="do-you-need-multiple-ui-maps"></a>Birden çok UI eşlemesi gerekiyor mu?  
 Birden çok UI eşlemesi her durumlarda bu tür oluşturun:  
  
-   Birlikte bir Web sitesinde bir kayıt sayfası veya satın alma sayfası alışveriş sepeti gibi mantıksal bir işlemi gerçekleştirme bileşik UI denetimlerinin birkaç karmaşık ayarlar.  
  
-   Uygulama birkaç sayfa işlem sihirbazla gibi çeşitli noktalarından erişilen denetimlerinin bağımsız ayarlayın. Sihirbazın her sayfasını özellikle karmaşık ise, her bir sayfa için ayrı UI haritaları oluşturabilirsiniz.  
  
## <a name="adding-multiple-ui-maps"></a>Birden çok UI eşlemesi ekleme  
  
#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Kodlanmış UI test projenize UI eşlemesi eklemek için  
  
1.  İçinde **Çözüm Gezgini**, tüm UI eşlemesi depolamak için kodlanmış UI test projesi dosyasını sağ tıklatın, işaret kodlanmış UI test projenizdeki bir klasör oluşturmak için **Ekle** ve ardından **yeni klasör**. Örneğin, adlandırabilirsiniz `UIMaps`.  
  
     Yeni klasör kodlanmış UI test projesi altında görüntülenir.  
  
2.  Sağ `UIMaps` klasörünü **Ekle**ve ardından **yeni öğe**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
    > [!NOTE]
    >  Yeni bir kodlanmış UI test eşlemesi eklemek için kodlanmış UI test projede olmalıdır.  
  
3.  Seçin **kodlanmış UI Test eşlemesi** listeden.  
  
     İçinde **adı** kutusuna, yeni UI eşlemesi için bir ad girin. Bileşen veya harita, örneğin, temsil edecek sayfa adını kullanmak `HomePageMap`.  
  
4.  Seçin **eklemek**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Penceresini simge durumuna küçültür ve **kodlanmış UI Test derleyicisini** iletişim kutusu görüntülenir.  
  
5.  İlk yöntem için eylemleri kaydedin ve seçin **kodu oluştur**.  
  
6.  Kaydedilen tüm eylemler ve ilk bileşen veya sayfa için onaylar ve yöntemler halinde gruplandırdıktan sonra kapatın **kodlanmış UI Test derleyicisini** iletişim kutusu.  
  
7.  UI eşlemesi oluşturmaya devam edin. Eylemleri ve onaylamaları kaydedin, her bileşen için yöntemlerde gruplandırın ve kod oluşturma.  
  
 Çoğu durumda, tüm sihirbazlar, formlar ve sayfalar için uygulamanızın en üst düzey penceresi sabit kalır. Her UI eşlemesi üst düzey penceresi için bir sınıf olsa da, tüm eşlemeler büyük olasılıkla çalıştırmak, uygulamanızın hangi tüm bileşenleri aynı üst düzey pencereye başvuruyordur. En üst düzey penceresinden başlangıç kodlanmış UI testleri için arama denetimleri hiyerarşik olarak yukarıdan aşağıya doğru karmaşık bir uygulamada gerçek üst düzey pencere her UI eşlemesi yinelenen şekilde. Gerçek üst düzey pencere yineleniyorsa Bu pencere değiştiğinde birden fazla değişiklik neden olur. UI eşlemesi arasında geçiş yaptığınızda bu performans sorunlarına neden olabilir.  
  
 Bu etkiyi en aza indirmek için kullanabileceğiniz `CopyFrom()` UI eşlemesi ana en üst düzey pencere ile aynıdır, yeni bir üst düzey penceresi emin olmak için yöntem.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, her bileşen ve çeşitli UI haritaları'nda oluşturulan sınıflar tarafından temsil edilen kendi alt denetimleri için erişim sağlayan bir yardımcı sınıfı bir parçasıdır.  
  
 Bu örnekte, bir Web uygulaması adlı `Contoso` bir giriş sayfası, bir ürün sayfası ve bir alışveriş sepeti sayfası vardır. Bu sayfaların her biri bir tarayıcı penceresi olan ortak bir üst düzey penceresini paylaşır. Her bir sayfa için bir kullanıcı Arabirimi eşleme yoktur ve yardımcı program sınıfı aşağıdakine benzer bir kod içerir:  
  
```  
using ContosoProject.UIMaps;  
using ContosoProject.UIMaps.HomePageClasses;  
using ContosoProject.UIMaps.ProductPageClasses;  
using ContosoProject.UIMaps.ShoppingCartClasses;  
  
namespace ContosoProject  
{  
    public class TestRunUtility  
    {  
        // Private fields for the properties  
        private HomePage homePage = null;  
        private ProductPage productPage = null;  
        private ShoppingCart shoppingCart = null;  
  
        public TestRunUtility()  
        {  
            homePage = new HomePage();  
        }  
  
        // Properties that get each UI Map  
        public HomePage HomePage  
        {  
            get { return homePage; }  
            set { homePage = value; }  
        }  
  
        // Gets the ProductPage from the ProductPageMap.  
        public ProductPage ProductPageObject  
        {  
            get  
            {  
                if (productPage == null)  
                {  
                    // Instantiate a new page from the UI Map classes  
                    productPage = new ProductPage();  
  
                    // Since the Product Page and Home Page both use  
                    // the same browser page as the top level window,  
                    // get the top level window properties from the  
                    // Home Page.  
                    productPage.UIContosoFinalizeWindow.CopyFrom(  
                        HomePage.UIContosoWindowsIWindow);  
                }  
                return productPage;  
            }  
        }  
  
    // Continue to create properties for each page, getting the   
    // page object from the corresponding UI Map and copying the   
    // top level window properties from the Home Page.  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Kodlanmış UI Testinin Anatomisi](../test/anatomy-of-a-coded-ui-test.md)