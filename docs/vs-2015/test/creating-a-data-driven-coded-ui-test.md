---
title: Veri odaklı kodlanmış UI testi oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
ms.assetid: 5838f02d-001f-49ce-adce-c9ea1afaec2f
caps.latest.revision: 58
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3aec055c0fb0253f0b233f51e50485ccb4ee3382
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302604"
---
# <a name="creating-a-data-driven-coded-ui-test"></a>Verilerle Çalışan Kodlanmış UI Testi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı koşulları test etmeye yönelik farklı parametre değerleriniz ile birden çok kez testleri çalıştırabilirsiniz. Verilerle çalışan kodlanmış UI testleri bunu yapmak için uygun bir yoldur. Veri kaynağındaki her satır bir kodlanmış UI test yinelemesini olduğunu ve parametre değerlerini bir veri kaynağı tanımlayın. Genel sonuç testi sonucu yineleme için hesaplanır. Örneğin, bir test yineleme başarısız olursa, genel test sonucu başarısız olur.

 **Requirements**

- Visual Studio Enterprise

## <a name="create-a-data-driven-coded-ui-test"></a>Verilerle çalışan kodlanmış UI testi oluşturma
 Bu örnek, Windows hesaplayıcısı uygulaması üzerinde çalışan kodlanmış UI testi oluşturur. İki sayıyı toplar ve toplamı doğru olduğunu doğrulamak için bir onay kullanır. Ardından, iki sayının onaylama ve parametre değerleri, veri odaklı ve virgülle ayrılmış değer (. csv) dosyasında depolanacak şekilde kodlanır.

#### <a name="step-1---create-a-coded-ui-test"></a>1\. adım - kodlanmış UI testi oluşturma

1. Bir proje oluşturun.

     ![Kodlanmış UI test projesi oluşturma](../test/media/cuit-datadriven.png "CUIT_dataDriven_")

2. Eylemleri kaydetmeyi seçin.

     ![Eylemleri kaydetmeyi seçin](../test/media/cuit-datadriven-generatecodedialog.png "CUIT_dataDriven_GenerateCodeDialog")

3. Hesaplayıcı uygulamasını açın ve testi kaydetmeyi başlatın.

     ![Kayıt eylemleri](../test/media/cuit-datadriven-cuitbuilder.png "CUIT_dataDriven_CUITBuilder")

4. 1 ve 2 ekleme, kaydedicisini durdurur ve test yöntemi oluşturun. Daha sonra bu kullanıcı girişinin değerlerini bir veri dosyasındaki değerlerle değiştirecek.

     ![Test yöntemi oluştur](../test/media/cuit-datadriven-cuitbuildergencode.png "CUIT_dataDriven_CUITBuilderGenCode")

     Test Oluşturucusu'nu kapatın. Yöntemi, teste eklenir:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();

    }
    ```

5. Testin çalıştığını doğrulamak için `AddNumbers()` yöntemini kullanın. İmleci yukarıda gösterilen test yöntemine yerleştirin, bağlam menüsünü açın ve **Testleri Çalıştır**' ı seçin. (Klavye kısayolu: CTRL + R, T).

     Test Gezgini penceresinde başarılı veya başarısız olan testin görüntülendiğini gösteren test sonucu. Test Gezgini penceresini açmak için, **Test** menüsünde **Windows** ' u ve ardından **Test Gezgini**' ni seçin.

6. Bir veri kaynağı, beklenen değerleri doğrulamak için test tarafından kullanılan onaylama parametre değerleri için de kullanılabilir —, iki sayının toplamının doğru olduğunu doğrulamak için bir onaylama ekleyelim. İmleci yukarıda gösterilen test yöntemine yerleştirin, bağlam menüsünü açın ve **KODLANMıŞ UI testi Için kod oluştur**' u seçin ve **kodlanmış UI Test Oluşturucusu**' nu kullanın.

     Toplamı görüntüleyen hesaplayıcı metin denetiminde eşleyin.

     ![UI metin denetimini eşleme](../test/media/cuit-datadriven-addassertion.png "CUIT_dataDriven_AddAssertion")

7. Toplam değeri doğru olduğunu doğrulayan bir onay ekleyin. **3** değerine sahip **Görüntümetni** özelliğini seçin ve ardından **onay Ekle**' yi seçin. **Areeşitse** karşılaştırıcısı ' nı kullanın ve karşılaştırma değerinin **3**olduğunu doğrulayın.

     ![Onaylama işlemi yapılandırma](../test/media/cuit-datadriven-builderaddassertion2.png "CUIT_dataDriven_BuilderAddAssertion2")

8. Onaylama yapılandırdıktan sonra kodu yeniden Oluşturucu oluşturur. Bu, doğrulama için yeni bir yöntem oluşturur.

     ![Onaylama yöntemini oluşturma](../test/media/cuit-datadriven-assertiongencode.png "CUIT_dataDriven_AssertionGenCode")

     `ValidateSum` yöntemi `AddNumbers` yönteminin sonuçlarını doğruladığından, kodu kod bloğunun en altına taşıyın.

    ```csharp
    public void CodedUITestMethod1()
    {

        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();

    }
    ```

9. Testin `ValidateSum()` yöntemini kullanarak çalıştığını doğrulayın. İmleci yukarıda gösterilen test yöntemine yerleştirin, bağlam menüsünü açın ve **Testleri Çalıştır**' ı seçin. (Klavye kısayolu: CTRL + R, T).

     Bu noktada, tüm parametre değerlerini kendi yöntemlerini sabiti olarak tanımlanır. Ardından, test veri odaklı bir veri kümesi oluşturalım.

#### <a name="step-2---create-a-data-set"></a>2\. adım - veri kümesi oluşturma

1. `data.csv`adlı dataDrivenSample projesine bir metin dosyası ekleyin.

     ![Projeye virgülle ayrılmış bir değer dosyası ekleyin](../test/media/cuit-datadriven-addcsvfile.png "CUIT_dataDriven_AddCSVFile")

2. . Csv dosyasını aşağıdaki verilerle doldurun:

    |Num1|Num2|TOPLA|
    |----------|----------|---------|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Veri ekledikten sonra dosyanın aşağıdaki gibi görünmelidir:

     ![Öğesini doldurun. Verilerle CSV dosyası](../test/media/cuit-datadriven-adddatatocsvfile.png "CUIT_dataDriven_AddDataToCSVFile")

3. Doğru kodlamayı kullanarak. csv dosyasını kaydetmeniz önemlidir. **Dosya** menüsünde **Gelişmiş Kaydet seçeneklerini** belirleyin ve kodlama olarak **Unicode (imzasız UTF-8 65001)** seçeneğini belirleyin.

4. . Csv dosyası, çıkış dizinine kopyalanmalıdır veya test çalıştırılamıyor. Kopyalamak için Özellikler penceresi kullanın.

     ![Dağıtımını yapın. CSV dosyası](../test/media/cuit-datadriven-deploycsvfile.png "CUIT_dataDriven_DeployCSVFile")

     Veri kümesi oluşturulduğuna göre, artık verileri teste bağlayalim.

#### <a name="step-3--add-data-source-binding"></a>3\. adım – veri kaynağı bağlamayı ekleme

1. Veri kaynağını bağlamak için, test yönteminin hemen üzerinde yer alan var olan `[TestMethod]` özniteliği içine bir `DataSource` özniteliği ekleyin.

    ```
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {

        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();

    }

    ```

     Veri kaynağı artık bu test yöntemi, kullanabilmeniz için kullanılabilir.

    > [!TIP]
    > XML, SQL Express ve Excel gibi diğer veri kaynağı türlerini kullanma örnekleri için bkz. soru-& cevap bölümünde [veri kaynağı öznitelik örnekleri](#CreateDataDrivenCUIT_QA_DataSourceAttributes) .

2. Testi çalıştırın.

     Üç yineleme ile test çalışmaları dikkat edin. Veri kaynağına bağlanan üç veri satırı içerdiğinden budur. Ancak, test yine de sabit parametre değerlerini kullanıyor ve her zaman 1 + 2 3 toplamı ile ekliyor de görürsünüz.

     Daha sonra, veri kaynağı dosyasındaki değerleri kullanmak için testi yapılandıracağız.

#### <a name="step-4--use-the-data-in-the-coded-ui-test"></a>4\. adım – kodlanmış UI testinde verileri kullanma

1. CodedUITest.cs dosyasının en üstüne `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` ekleyin:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text.RegularExpressions;
    using System.Windows.Input;
    using System.Windows.Forms;
    using System.Drawing;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UnitTesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    ```

2. `CodedUITestMethod1()` yöntemine, veri kaynağından değerleri uygulayacak `TestContext.DataRow[]` ekleyin. Veri kaynağı değerleri, `SearchProperties`denetimleri kullanılarak UIMap denetimlerine atanan sabitleri geçersiz kılar:

    ```
    public void CodedUITestMethod1()
    {

        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();this.UIMap.UICalculatorWindow.UIItemWindow21.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSumExpectedValues.UIItem2TextDisplayText = TestContext.DataRow["Sum"].ToString();
        this.UIMap.ValidateSum();

    }
    ```

     Verileri kodlamak için hangi arama özelliklerinin ekleyeceğimi için kodlanmış UI Test Düzenleyicisi'ni kullanın.

    - UIMap. UITest dosyasını açın.

         ![Kodlanmış UI test düzenleyicisini açın](../test/media/cuit-datadriven-opentesteditor.png "CUIT_dataDriven_OpenTestEditor")

    - UI eylemi seçin ve karşılık gelen UI denetim eşlemesi gözlemleyin. Eşlemenin koda nasıl karşılık geldiğini (örneğin, `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`) unutmayın.

         ![Koda yardımcı olması için kodlanmış UI test düzenleyicisini kullanın](../test/media/cuit-datadriven-testeditor.png "CUIT_dataDriven_TestEditor")

    - Özellikler penceresinde **arama özellikleri**' ni açın. Arama özellikleri **adı** değeri, veri kaynağı kullanılarak kodda ne tür bir şekilde işlenemekte. Örneğin, `SearchProperties` her bir veri satırının ilk sütunundaki değerler atanmaktadır: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. Bu test, üç yineleme için arama özelliğinin **ad** değerini 3, sonra 5 ve son 6 olarak değiştirir.

         ![Kodlamaya yardımcı olması için arama özelliklerini kullanın](../test/media/cuit-datadriven-searchproperties.png "CUIT_dataDriven_SearchProperties")

3. Çözümünüzü kaydedin.

#### <a name="step-5--run-the-data-driven-test"></a>5\. adım – veri temelli testi çalıştırma

1. Test şimdi testi yeniden çalıştırarak veri odaklı olduğunu doğrulayın.

    Test çalıştırmasını,. csv dosyasındaki değerleri kullanarak üç yineleme aracılığıyla görmeniz gerekir. Doğrulama de çalışması gerekir ve test, Test Gezgini'nde geçti olarak görüntülenmelidir.

   **Kılavuz**

   Daha fazla bilgi için bkz [. Visual Studio Ile sürekli teslim Için test etme 2012 – Bölüm 2: birim testi:](https://go.microsoft.com/fwlink/?LinkID=255188) [Visual Studio 2012 ile sürekli teslim için, içeri ve test etmeyi test etme – Bölüm 5: Sistem testlerini otomatikleştirme](https://go.microsoft.com/fwlink/?LinkID=255196)

## <a name="q--a"></a>Soru - Yanıt

### <a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a>SQL Express veya XML gibi diğer veri kaynağı türleri için veri kaynağı öznitelikleri nelerdir?
 Kodunuza kopyalayarak ve gereken özelleştirmeleri yaparak, aşağıdaki tabloda örnek veri kaynağı dizeleri kullanabilirsiniz.

 **Veri kaynağı türleri ve öznitelikleri**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Team Foundation Server test çalışmasında

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-can-i-use-data-driven-tests-on-my-windows-phone-app"></a>S: Windows Phone uygulamamda veri tabanlı testleri kullanabilir miyim?
 Y **:** Yes. Windows Phone için veri odaklı kodlanmış UI testleri, bir test yönteminde DataRow özniteliği kullanılarak tanımlanır. Aşağıdaki örnekte x ve y, ilk yineleme için 1 ve 2 değerlerini ve testin ikinci yinelemesi için-1 ve-2 değerlerini kullanır.

```
[DataRow(1, 2, DisplayName = "Add positive numbers")]
[DataRow(-1, -2, DisplayName = "Add negative numbers")]
[TestMethod]
public void DataDrivingDemo_MyTestMethod(int x, int y)

```

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: UIMap. Designer dosyasındaki kodu neden değiştiremiyorum?
 Y **:** UIMapDesigner.cs dosyasında yaptığınız herhangi bir kod değişikliği, UIMap kodlu UI test oluşturucusunu kullanarak kod oluşturduğunuzda üzerine yazılır. Bu örnekte ve çoğu durumda, bir testin bir veri kaynağını kullanmak için gereken kod değişiklikleri testin kaynak kodu dosyasına (yani, CodedUITest1.cs) yapılabilir.

 Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Kodlanmış UI Testleri için En İyi Yöntemler](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
