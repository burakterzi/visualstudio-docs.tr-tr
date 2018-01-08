---
title: "Kodlanmış UI testleriyle Windows UWP uygulamaları test | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: "23"
ms.author: douge
manager: douge
ms.workload: uwp
ms.openlocfilehash: f5df259efedd50e67ee6e8f94203eb4e0ac56c71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="test-windows-uwp-apps-with-coded-ui-tests"></a>Kodlanmış UI testleriyle Windows UWP uygulamaları sınama

UWP uygulamaları ve XAML tabanlı 8.1 için UI testleri oluşturmak için bu kılavuzu kullanın uygulamalar. 
  
## <a name="create-a-simple-uwp-app"></a>Basit bir UWP uygulaması oluşturma  
  
1.  XAML tabanlı UWP uygulamanız için kodlanmış UI testleri çalıştırmak istiyorsanız, şunları yapmalısınız [her denetim tanımlayan benzersiz Otomasyon özelliği ayarlama](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).  
  
     Üzerinde **Araçları** menüsündeki **seçenekleri** ve ardından **metin düzenleyici**, ardından **XAML**ve son olarak **çeşitli** .  
  
     Otomatik olarak etkileşimli öğelerde oluşturma adı için bu onay kutusunu seçin.  
  
     ![XAML çeşitli seçenekleri](../test/media/cuit_windowsstoreapp_b.png "CUIT_WindowsStoreApp_B")  
  
2.  UWP uygulamasını Visual C# veya Visual Basic şablonu kullanarak boş bir XAML tabanlı için yeni bir proje oluşturun.  
  
     ![Bir uygulamanın &#40;oluşturun; XAML &#41; ] (../test/media/cuit_windowsstoreapp_newproject_blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")  
  
3.  Çözüm Gezgini'nde MainPage.xaml açın. Araç Kutusu'ndan bir düğmeyi ve textbox denetimi tasarım yüzeyine sürükleyin.  
  
     ![UWP uygulamasında tasarım](../test/media/cuit_windowsstoreapp_design.png "CUIT_WindowsStoreApp_Design")  
  
4.  Düğme denetimi çift tıklayın ve aşağıdaki kodu ekleyin:  
  
    ```csharp  
    private void button_Click_1(object sender, RoutedEventArgs e)  
    {  
        this.textBox.Text = this.button.Name;  
    }  
  
    ```  
  
    ```vb  
    Public NotInheritable Class MainPage  
        Inherits Page  
  
        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click  
            Me.textBox.Text = Me.button.Name  
        End Sub  
    End Class  
    ```  
  
5.  UWP uygulamanızı çalıştırmak için F5 tuşuna basın.  
  
## <a name="create-and-run-a-coded-ui-test-for-the-uwp-app"></a>Oluşturma ve UWP uygulaması için kodlanmış UI testi çalıştırma  

[Kodlanmış UI testleri Evrensel Windows Platformu (UWP) uygulamaları için nasıl oluşturulur?](#uwpapps)
  
1.  UWP uygulaması için yeni kodlanmış UI test projesi oluşturun.  
  
     ![Yeni kodlanmış UI tet proje &#40; UWP uygulamaları &#41; ] (../test/media/cuit_windowsstore_newproject.png "CUIT_WindowsStore_NewProject")  
  
2.  Çapraz hedef aracını kullanarak UI eşlemesini düzenlemek bu seçeneği seçin.  
  
     ![Düzenleme UI eşlemesi seçin veya onaylar eklemek](../test/media/cuit_windowsstoreapp_createproject_gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")  
  
3.  Kodlanmış UI Test derleyicisini artı şeklindeki aracını uygulama kutucuğunu seçin, sağ tıklatın **Automationıd** ve **Panoya Kopyala değeri**. Pano değer daha sonra eylem yazmak için test etmek için uygulamayı başlatmak için kullanılır.  
  
     ![Automationıd Panoya Kopyala](../test/media/cuit_windows_store_tileautomationid.png "CUIT_Windows_Store_TileAutomationID")  
  
4.  Çalışan UWP uygulamasında artı şeklindeki aracı düğmesi ve textbox denetimi seçmek için kullanın. Her denetim eklendikten sonra Seç **UI denetim eşlemesine denetim eklemek** kodlanmış UI Test derleyicisini araç çubuğu düğmesi.  
  
     ![UI eşlemesine denetim eklemek](../test/media/cuit_windowsstoreapp_uimap.png "CUIT_WindowsStoreApp_UIMap")  
  
5.  Seçin **kodu oluştur** kodlanmış UI Test derleyicisini araç çubuğu düğmesini tıklatın ve ardından seçin **Generate** değişiklikler UI denetim eşlemesi için kod oluşturmak için.  
  
     ![UI eşlemesi için kod oluşturma](../test/media/cuit_windowsstoreapp_generate.png "CUIT_WindowsStoreApp_Generate")  
  
6.  Metin kutusuna bir değer ayarlamak için düğmesini seçin.  
  
     ![Düğme denetimi TextBox değeri ayarlamak için tıklayın](../test/media/cuit_windowsstoreapp_clickbutton.png "CUIT_WindowsStoreApp_ClickButton")  
  
7.  Textbox denetimi seçin ve ardından artı şeklindeki aracını kullanın **metin** özelliği.  
  
     ![Metin özelliği seçin](../test/media/cuit_windowsstoreapp_selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")  
  
8.  Bir onaylama ekleyin. Bu testte değerin doğru olduğunu doğrulamak için kullanılır.  
  
     ![Çapraz ile testbox &#45; seçin artı ve onay eklemek](../test/media/cuit_windowsstoreapp_textbox_addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")  
  
9. Ekleyin ve onaylama için kod oluşturur.  
  
     ![Textbox onaylama kodunu oluşturmak](../test/media/cuit_windowsstoreapp_textbox_generate_assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")  
  
10. **Visual C#**  
  
     Çözüm Gezgini'nde assert yöntemini ve denetimler için eklenen kod görüntülemek için UIMap.Designer.cs dosyasını açın.  
  
     **Visual Basic**  
  
     Çözüm Gezgini'nde CodedUITest1.vb dosyasını açın ve otomatik olarak eklenen onay yöntemi çağrısı Codeduıtestmethod1() test yöntemi kodda sağ tıklatın `Me.UIMap.AssertMethod1()` ve **Tanıma Git**. Assert yöntemini ve denetimler için eklenen kod görünümü görüntüleyebilmeniz Bu kod düzenleyicisinde UIMap.Designer.vb dosyasını açar.  
  
    > [!WARNING]
    >  UIMap.Designer.cs veya UIMap.Designer.vb dosyasını doğrudan değiştirmeyin. Bunu yaparsanız, değişiklikleri dosyaya test üretilen her zaman üzerine yazılır.  
  
     **Assert yöntemi**  
  
    ```csharp  
    public void AssertMethod1()  
    {  
        #region Variable Declarations  
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;  
        #endregion  
  
        // Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(this.AssertMethod3ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Denetimler**  
  
    ```csharp  
    #region Properties  
    public XamlButton UIButtonButton  
    {  
        get  
        {  
            if ((this.mUIButtonButton == null))  
            {  
                this.mUIButtonButton = new XamlButton(this);  
                #region Search Criteria  
                this.mUIButtonButton.SearchProperties[XamlButton.PropertyNames.AutomationId] = "button";  
                this.mUIButtonButton.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUIButtonButton;  
        }  
    }  
  
    public XamlEdit UITextBoxEdit  
    {  
        get  
        {  
            if ((this.mUITextBoxEdit == null))  
            {  
                this.mUITextBoxEdit = new XamlEdit(this);  
                #region Search Criteria  
                this.mUITextBoxEdit.SearchProperties[XamlEdit.PropertyNames.AutomationId] = "textBox";  
                this.mUITextBoxEdit.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUITextBoxEdit;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private XamlButton mUIButtonButton;  
  
    private XamlEdit mUITextBoxEdit;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
                Me.mUIButtonButton.WindowTitles.Add("App2")  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
                Me.mUITextBoxEdit.WindowTitles.Add("App2")  
            End If  
            Return Me.mUITextBoxEdit  
        End Get  
    End Property  
    #End Region  
  
    #Region "Fields"  
    Private mUIButtonButton As XamlButton  
  
    Private mUITextBoxEdit As XamlEdit  
    #End Region  
    ```  
  
11. Çözüm Gezgini'nde Codeduıtest1.cs veya CodedUITest1.vb dosyasını açın. Şimdi de CodedUTTestMethod1 yöntemi Uımap'a eklenen denetimleri kullanarak testini çalıştırmak için Eylemler gereken için kod ekleyebilirsiniz:  
  
    1.  Daha önce kopyaladığınız panoya Otomasyon kimliği özelliğini kullanarak UWP uygulamasını başlatın:  
  
        ```csharp  
        XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
        ```  
  
        ```vb  
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
        ```  
  
    2.  Düğme denetimi dokunmak hareketi ekleyin:  
  
        ```csharp  
        Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);  
        ```  
  
        ```vb  
        Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)  
        ```  
  
    3.  Uygulama başlatıldıktan sonra otomatik olarak oluşturulan assert yöntemi çağrısı geldiğini doğrulamak ve hareketi düğmesine dokunun:  
  
        ```csharp  
        this.UIMap.AssertMethod1();  
        ```  
  
        ```vb  
        Me.UIMap.AssertMethod1()  
        ```  
  
     Kod ekledikten sonra Codeduıtestmethod1 test yöntemi aşağıdaki gibi görünmelidir:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
  
        // Launch the app.  
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest(CodedUITestType.WindowsStore)>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
  
            ' Launch the app.  
            XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp2Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
12. Test yapı ve test Gezgini kullanarak testi çalıştırın.  
  
     ![Çalıştırma kodlanmış UI testi Test Gezgini'nden](../test/media/cuit_windowsstoreapp_runtest.png "CUIT_WindowsStoreApp_RunTest")  
  
     Eylem düğmesi tamamlandı dokunun ve özellik doldurulur ve assert yöntemi kullanılarak doğrulandı textbox's metin UWP uygulamasını başlatır.  
  
     ![Çalışan Kodlanmış UI testi](../test/media/cuit_windowsstoreapp_running.png "CUIT_WindowsStoreApp_Running")  
  
     Test tamamlandıktan sonra test Gezgini testini geçtiğini görüntüler.  
  
     ![Test Gezgini içinde test görüntüler geçirilen](../test/media/cuit_windowsstorapp_passedtest.png "CUIT_WindowsStorApp_PassedTest")  
  
## <a name="q--a"></a>Soru - Yanıt  
  
#### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>S: yok görmemin nedeni kodlanmış UI testi iletişim oluşturmak kodunda my kodlanmış UI testini kaydetme seçeneği? **  
  
**A**: kaydetme seçeneği UWP uygulamaları için desteklenmiyor.  
  
#### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>S: kodlanmış UI testi için UWP uygulamalarım üzerinde WinJS oluşturabiliyorum? **  

**A**: Hayır, yalnızca temel XAML uygulamaları desteklenmez.  
  
#### <a name="q-can-i-create-coded-ui-tests-for-my-uwp-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>S: kodlanmış UI testleri Windows 8.1 veya Windows 10 çalıştırmayan bir sistemde my UWP uygulamalar için oluşturabiliyorum? **  
  
**A**: Hayır, kodlanmış UI Test proje şablonları yalnızca Windows 8.1 ve Windows 10 kullanılabilir. Otomasyon için evrensel Windows Platformu (UWP) uygulamaları oluşturmak için Windows 10 gerekir.  

<a name="uwpapps"></a>  
#### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>S: Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri nasıl oluşturabilirim? **  
  
**A**: Burada test UWP uygulamanızı platformuna bağlı olarak kodlanmış UI test projesi şu yollardan biriyle oluşturun:  
  
- Yerel makine üzerinde çalışan bir UWP uygulaması bir UWP uygulaması gibi çalışır. Bu test için kullanmanız gerekir **kodlanmış UI Test projesine (Windows)** şablonu. Yeni bir proje oluşturduğunuzda, bu şablonu bulmak için Git **Windows**, **Evrensel** düğümü. Veya gitmek **Windows**, **Windows 8**, **Windows** düğümü.  
  
- Mobil cihaz veya öykünücü üzerinde çalışan bir UWP uygulaması bir telefon uygulaması gibi çalışır. Bu test için kullanmanız gerekir **kodlanmış UI Test projesine (Windows Phone)** şablonu. Yeni bir proje oluşturduğunuzda, bu şablonu bulmak için Git **Windows**, **Evrensel** düğümü. Veya gitmek **Windows**, **Windows 8**, **Windows Phone** düğümü.  
  
Projesi oluşturduktan sonra bir test yazma önceki ile aynı kalır.  
  
#### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: neden ı değiştiremiyor UIMap.Designer dosyasındaki kodu? **  
  
**A**: UIMap - Kodlanmış UI Test derleyicisini kullanarak kod oluşturma her zaman UIMapDesigner.cs dosyasında yaptığınız herhangi bir kod değişikliğinin üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Test Etme Amacıyla UWP Denetimleri için Benzersiz Otomasyon Özelliği Ayarlama](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)