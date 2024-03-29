---
title: Kodunuzda birim testi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c861099ac5253c9610e8ae75d3c429a5ce88a9d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301430"
---
# <a name="unit-test-your-code"></a>Kodunuza Birim Testi Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birim testleri, geliştiricilere ve test edicilere [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)]ve [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)] projelerindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir yol sağlar.

 Birim testi araçları şunları içerir:

1. **Test Gezgini.** Test Gezgini, birim testleri çalıştırmanıza ve sonuçları görüntülemenize izin verir. Test Gezgini, üçüncü taraf çerçeve dahil, Gezgin için bağdaştırıcısı olan herhangi bir test çerçevesini kullanabilir.

2. **Yönetilen kod için Microsoft birim testi çerçevesi.** Yönetilen kod için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve .NET kodunu test etmek için bir çerçeve sağlar.

3. **İçin C++Microsoft birim testi çerçevesi.** C++ için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve yerel kodu test etmek için bir çerçeve sağlar.

4. **Kod kapsamı araçları.** Test Gezgini'nde bir tek komuttan birim testlerinizin çalıştıracağı ürün kodu miktarını belirleyebilirsiniz.

5. **Microsoft Fakes yalıtım çerçevesi.** Microsoft Fakes yalıtım çerçevesi, test edilen kodda bağımlılıklar oluşturan üretim ve sistem kodunun yerine geçecek sınıflar ve yöntemler oluşturabilir. Bir işlev için sahte temsilciler uygulayarak, bağımlılık nesnesinin davranışını ve çıkışını denetlersiniz.

   Ayrıca, test verileri ve birim testleri paketi oluşturmak üzere .NET kodunuzu araştırmak için [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) ' i de kullanabilirsiniz. Koddaki her ifade için bir test girişi oluşturulur o ifadeyi yürütecek. Koddaki her koşullu şube için bir vaka analizi yapılır.

## <a name="key-tasks"></a>Ana görevler
 Birim testlerini anlamaya ve oluşturmaya yardımcı olmaları için aşağıdaki konuları kullanın:

|Görevler|İlişkili Konular|
|-----------|-----------------------|
|**Hızlı başlar ve izlenecek yollar:** Kod örneklerinden Visual Studio 'da birim testini öğrenmek için aşağıdaki konuları kullanın.|-   [Izlenecek yol: yönetilen kod Için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [hızlı başlangıç: Test Gezgini Ile test temelli geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)<br />[var olan C++ uygulamalara birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) -   <br />[Test Gezgini ile yerel kod -   birim testi](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|
|**Test Gezgini Ile birim testi:** Test Gezgini 'nin daha üretken ve verimli birim testleri oluşturmaya nasıl yardımcı olabileceğini öğrenin.|-   [birim testi temelleri](../test/unit-test-basics.md)<br />-   [birim testi projesi oluşturma](../test/create-a-unit-test-project.md)<br />[Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md) -   <br />[üçüncü taraf birim testi](../test/install-third-party-unit-test-frameworks.md) çerçevelerini -   yüklemesi<br />[Visual Studio 2010 ' den birim testlerini yükseltme](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172) -   |
|**Birim testi yönetilen kodu:**|[yönetilen kod Için Microsoft birim testi çerçevesi ile .NET Framework Için birim testleri yazma](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md) -   |
|**Birim test C++ kodu**|[Için C++ Microsoft birim testi çerçevesi ile CC++ /için birim testleri yazma](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md) -   |
|**Birim testlerini yalıtma**|[Microsoft Fakes Ile test edilen kodu yalıtmak](../test/isolating-code-under-test-with-microsoft-fakes.md) -   |
|**Proje kodunuzun birim testleri kullanılarak ne oranda test edildiğini belirlemek için kod kapsamını kullanın:** [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] test araçlarının kod kapsamı özelliği hakkında bilgi edinin.|[ne kadar kodun test edildiğini öğrenmek Için kod kapsamını kullanarak](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) -   |
|**Birim testleriniz için yük testlerini kullanarak stres ve performans analizini gerçekleştirin:** Uygulamanızdaki performans ve stres sorunlarını yalıtmaya yardımcı olmak için bir yük testi oluşturabilir ve birim testlerinizi buna ekleyebilirsiniz. **Note:**  Yük testlerinin oluşturulması ve kullanılması Visual Studio Enterprise gerekir.|[Yük testleri oluşturma ve düzenlemeyle](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337) -   <br />-   [nasıl yapılır: yük testi senaryosuna Web performans testleri ve birim testleri ekleme](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [nasıl yapılır: yük testi senaryosundan Web testlerini ve birim testlerini kaldırma](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|
|**Kalite kapıları ayarlama ve zorlama:** Kodun kalitesini sağlamaya yardımcı olmak için testlerin kod iade etmeden önce çalıştırılmasını zorlamak için kalite kapıları oluşturabilirsiniz.|-   [kalite kapıları ayarlama ve zorlama](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Birim test türünü genişletin:** Testlerinizi, birim testi çerçevesinde bulunmayabilir, testleriniz için işlevler ekleyebilirsiniz. Örneğin, bir testin normal kullanıcı olarak çalışıp çalışmayacağını belirten bir test özelliği ekleyebilirsiniz. Veya çerçeveyi, bir yönteme satır öznitelikleri eklemek ve bu satırda bulunan verileri testin içinde kullanmak üzere genişletebilirsiniz.|Birim testi çerçevesinin nasıl genişletileceği hakkında örnek kod için aşağıdaki [Microsoft Web sitesine](https://go.microsoft.com/fwlink/?LinkId=185591)bakın.|
|**Test seçeneklerini ayarla:** Örneğin, test sonuçlarının nerede depolandığını belirtebilirsiniz.|[.runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="related-tasks"></a>İlişkili görevler
 [Microsoft Test Yöneticisi Test Sonuçları gözden geçirme](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)

 Test sonuçları ve nasıl görüntülendiği, kaydedildiği ve silindiği de dahil bunlarla çalışma yollarını açıklar.

 [Microsoft Visual Studio kullanarak sistem testlerini çalıştırma](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)

 Otomatikleştirilmiş testleri çalıştırmak için [!INCLUDE[TCMext](../includes/tcmext-md.md)] kullanmanın aksine Visual Studio 'Yu kullanma hakkında bilgi için bağlantılar sağlar.

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>, öznitelikleri, özel durumları, onayları ve birim testini destekleyen diğer sınıfları sağlayan UnitTesting Ad alanını açıklar.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ve Web hizmeti birim testleri için destek sağlayarak UnitTesting Ad alanını genişleten UnitTesting. Web ad alanını açıklar.

## <a name="external-resources"></a>Dış kaynaklar

### <a name="videos"></a>Videolar
 [Channel 9: XAML kullanılarak oluşturulan Windows Mağazası uygulamalarınızı birim testi yapma](https://go.microsoft.com/fwlink/?LinkId=226285)

### <a name="forums"></a>Forumlar
 [Visual Studio birim testi](https://go.microsoft.com/fwlink/?LinkId=224477)

### <a name="guidance"></a>Rehber
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](https://go.microsoft.com/fwlink/?LinkID=255188)

### <a name="reference"></a>Başvuru
 [Birim testleri için içerik dizini](https://go.microsoft.com/fwlink/?LinkID=254719)

## <a name="see-also"></a>Ayrıca Bkz.
 Uygulamanın [kod kalitesi](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945) [sınamasını](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) geliştirme
