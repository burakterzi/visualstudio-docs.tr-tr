---
title: Kodlanmış UI testiyle UWP uygulamasını test etme
ms.date: 05/31/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 7000cb64a14510e972222d2d4dae30ceee593c43
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659973"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>UWP uygulamasını test etmek için kodlanmış UI testi oluşturma

Bu makalede, bir Evrensel Windows Platformu (UWP) uygulaması için kodlanmış UI testinin nasıl oluşturulduğu açıklanmaktadır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Test etmek için bir UWP uygulaması oluşturma

İlk adım, testi çalıştırmak için basit bir UWP uygulaması oluşturmaktır.

1. Visual Studio 'da, Visual C# veya Visual Basic Için **boş uygulama (Evrensel Windows)** şablonunu kullanarak yeni bir proje oluşturun.

   ::: moniker range="vs-2017"

   ![Boş uygulama Evrensel Windows şablonu](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. **Yeni Evrensel Windows platformu projesi** iletişim kutusunda, varsayılan platform sürümlerini kabul etmek için **Tamam** ' ı seçin.

1. **Çözüm Gezgini**, *MainPage. xaml*' yi açın.

   Dosya **XAML Tasarımcısı**açılır.

1. **Araç kutusu** ' ndan bir düğme denetimi ve TextBox denetimini tasarım yüzeyine sürükleyin.

     ![UWP uygulamasını tasarlama](../test/media/toolbox-controls.png)

1. Denetimlere adlar verin. TextBox denetimini seçin ve ardından **Özellikler** penceresinde, **ad** alanına **TextBox** yazın. Düğme denetimini seçin ve ardından **Özellikler** penceresinde, **ad** alanına **düğme** girin.

1. Düğme denetimine çift tıklayın ve `Button_Click` yönteminin gövdesine aşağıdaki kodu ekleyin. Bu kod, daha sonra oluşturacağımız kodlanmış UI testi ile bir şeyler sağlamak için metin kutusundaki metni yalnızca düğme denetiminin adına ayarlar.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Uygulamayı çalıştırmak için **Ctrl** +**F5** tuşuna basın. Aşağıdakine benzer bir şey görmeniz gerekir:

   ![Düğme ve metin kutusuyla UWP uygulaması](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Kodlanmış UI testi oluşturma

1. Çözüme bir test projesi eklemek için **Çözüm Gezgini** çözüme sağ tıklayın ve  > **Yeni proje** **Ekle** ' yi seçin.

1. **KODLANMıŞ UI test projesi (Evrensel Windows)** şablonunu arayın ve seçin.

   ::: moniker range="vs-2017"

   ![Yeni kodlanmış UI test projesi](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > **KODLANMıŞ UI testi projesi (Evrensel Windows)** şablonunu görmüyorsanız, [kodlanmış UI test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

1. **KODLANMıŞ UI testi Için kod üret** iletişim kutusunda **testi el ile Düzenle**' yi seçin.

   ![Kodlanmış UI testi iletişim kutusu için kod oluştur](../test/media/manually-edit-the-test.png)

1. UWP uygulamanız zaten çalışmıyorsa, **Ctrl** +**F5**tuşuna basarak bunu başlatın.

1. İmleci `CodedUITestMethod1` yöntemine yerleştirip **Test**  > **kodlanmış UI testi için kod üret** ' i **seçerek kodlanmış UI testi Oluşturucu ILETIŞIM kutusunu** açın  > **kodlanmış UI test oluşturucusunu kullanın**.

1. Denetimleri UI denetim haritasına ekleyin. UWP uygulamasındaki düğme denetimini seçmek için **KODLANMıŞ UI Test Oluşturucusu** çapraz artı aracını kullanın. **Onaylama Ekle** iletişim kutusunda, gerekirse **UI denetim Haritası** BÖLMESINI genişletin ve ardından **UI Denetim Haritasına denetim Ekle**' yi seçin.

     ![Kullanıcı arabirimi eşlemesine denetim ekleme](../test/media/add-control-to-ui-control-map.png)

1. TextBox denetimini UI denetim haritasına eklemek için önceki adımı tekrarlayın.

1. **KODLANMıŞ UI Test Oluşturucusu** Iletişim kutusunda **kod oluştur** ' u seçin veya **CTRL** +**G**tuşuna basın. Ardından, UI denetim haritasında değişiklikler için kod oluşturmak üzere **Oluştur** ' u seçin.

     ![UI eşlemesi için kod oluştur](../test/media/generate-code-dialog.png)

1. Düğme tıklandığında metin kutusundaki metnin **düğme düğmesine** değişdiğini doğrulamak için düğmesine tıklayın.

     ![TextBox değerini ayarlamak için düğme denetimi ' ne tıklayın](../test/media/uwp-app-button-textbox.png)

1. TextBox denetimindeki metni doğrulamak için onay ekleyin. TextBox denetimini seçmek için ince artı aracını kullanın ve ardından onay **Ekle** Iletişim kutusunda **metin** özelliğini seçin. Ardından, **onaylama Ekle** ' yi veya **alt** +**A**' yı seçin. **Onaylama hatasında ileti** kutusuna **metin kutusu değeri beklenmiyor yazın.** ardından **Tamam**' ı seçin.

     ![Çapraz artı ve onaylama Ekle metin kutusunu seçin](../test/media/add-assertion-for-text.png)

1. Onaylama için test kodu oluşturun. **KODLANMıŞ UI Test Oluşturucusu** Iletişim kutusunda **kod oluştur**' u seçin. **Kod oluştur** Iletişim kutusunda **Ekle ve oluştur**' u seçin.

     ![TextBox onaylama için kod oluştur](../test/media/add-and-generate-assert-method.png)

   **Çözüm Gezgini**' de, onay yöntemi ve denetimleri için eklenen kodu görüntülemek üzere *UIMap.Designer.cs* öğesini açın.

   > [!TIP]
   > Visual Basic kullanıyorsanız, *CodedUITest1. vb*dosyasını açın. Ardından, `CodedUITestMethod1()` test yöntemi kodunda, onaylama yöntemine `Me.UIMap.AssertMethod1()` çağrıya sağ tıklayın ve **Tanıma Git**' i seçin. *UIMap. Designer. vb* kod düzenleyicisinde açılır ve onaylama yöntemi ve denetimler için eklenen kodu görüntüleyebilirsiniz.

    > [!WARNING]
    > *UIMap.Designer.cs* veya *UIMap. Designer. vb* dosyalarını doğrudan değiştirmeyin. Bunu yaparsanız, test oluşturulduğunda değişikliklerinizin üzerine yazılacak.

    Onaylama yöntemi şöyle görünür:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. Ardından, test etmek istediğimiz UWP uygulamasının **AutomationId** 'sini edinmemiz [](#create-a-uwp-app-to-test) gerekiyor. Uygulamanın kutucuğunu görmek için Windows **Başlat** menüsünü açın. Daha sonra, **KODLANMıŞ UI Test Oluşturucusu** iletişim kutusundan ](media/target-icon.png) ince artı aracı ![Target simgesini uygulamanızın kutucuğuna sürükleyin. Bir mavi kutu kutucuğu çevreleyecek şekilde farenizi serbest bırakın.

   ![Çapraz saç aracı](media/cross-hair-tool.png)

   **Onaylama Ekle** iletişim kutusu açılır ve uygulamanız Için **AutomationId** görüntülenir. **AutomationId** öğesine sağ tıklayın ve **değeri panoya kopyala**' yı seçin.

   ![Onaylama Ekle iletişim kutusunda AutomationId](../test/media/automation-id.png)

1. UWP uygulamasını başlatmak için test yöntemine kod ekleyin. **Çözüm Gezgini**' de, *CodedUITest1.cs* veya *CodedUITest1. vb*dosyasını açın. @No__t_0 çağrısının üzerinde, UWP uygulamasını başlatmak için kod ekleyin:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Örnek kodundaki Otomasyon KIMLIĞINI, önceki adımda Pano 'ya kopyaladığınız değerle değiştirin.

   > [!IMPORTANT]
   > **P ~** gibi karakterleri kaldırmak IÇIN Otomasyon kimliği başlangıcını kırpın. Bu karakterleri kırpmıyorsanız, test uygulamayı başlatmaya çalıştığında bir `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` oluşturur.

1. Sonra, düğmeye tıklayarak test yöntemine kod ekleyin. @No__t_0 sonra satırdaki düğme denetimine dokunarak bir hareket ekleyin:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Kodu ekledikten sonra, `CodedUITestMethod1` test yönteminin tamamı aşağıdaki gibi görünmelidir:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Test projesi oluşturun ve **ardından test** **gezgini** 'ni açın  > **Windows**  > **Test Gezgini**' ni seçin.

1. Testi çalıştırmak için **Tümünü Çalıştır** ' ı seçin.

   Uygulama açılır, düğme dokunmuş ve TextBox 'ın **Text** özelliği doldurulur. Onaylama yöntemi TextBox 'ın **Text** özelliğini doğrular.

   Test tamamlandıktan sonra test **Gezgini** testin geçtiğini görüntüler.

   ![Test Gezgini 'nde geçilen test ekranları](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>soru-cevap &

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>S: kodlanmış UI testi iletişim kutusu için kod üret içinde, kodlanmış UI testimi kaydetme seçeneğini neden görmüyorum?

Y **: kayıt**SEÇENEĞI, UWP uygulamaları için desteklenmez.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>S: WinJS tabanlı UWP Uygulamalarım için kodlanmış UI testi oluşturabilir miyim?

Y **: Hayır**, yalnızca XAML tabanlı uygulamalar desteklenir.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: UIMap. Designer dosyasındaki kodu neden değiştiremiyorum?

Y: *UIMapDesigner.cs* dosyasında yaptığınız tüm kod değişikliklerinin, **kodlanmış UI Test Oluşturucusu**'nu kullanarak kod oluşturduğunuzda üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, *UIMap.cs* dosyasına kopyalayın ve yeniden adlandırın. *UIMap.cs* dosyası, *UIMapDesigner.cs* dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. *CodedUITest.cs* dosyasındaki özgün yönteme başvuruyu kaldırın ve yeniden adlandırılmış yöntem adıyla değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [UWP denetimleri için benzersiz Otomasyon özellikleri ayarlama](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)