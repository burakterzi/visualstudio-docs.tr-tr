---
title: 'İzlenecek yol: kod parçacıklarını uygulama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: madskristensen
ms.author: madsk
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 84674a12165a3c5cd47c9004274669d377d330c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632503"
---
# <a name="walkthrough-implement-code-snippets"></a>İzlenecek yol: kod parçacıklarını uygulama
Kod parçacıkları oluşturabilir ve bunları bir düzenleyici uzantısına ekleyerek uzantı kullanıcılarının bunları kendi koduna ekleyebilmesini sağlayabilirsiniz.

 Kod parçacığı, bir kod parçası veya bir dosyaya dahil edilebilir başka bir metindir. Belirli programlama dilleri için kaydedilmiş tüm kod parçacıklarını görüntülemek için, **Araçlar** menüsünde **kod parçacığı Yöneticisi**' ne tıklayın. Bir dosyaya kod parçacığı eklemek için, kod parçacığını istediğiniz yere sağ tıklayın, kod parçacığı Ekle ' ye tıklayın veya **Ile çevreleyin**, istediğiniz kod parçacığını bulun ve ardından çift tıklayın. Kod parçacığının ilgili bölümlerini **değiştirmek Için** **tab** veya **SHIFT** +**Tab** tuşlarına basın ve ardından **ENTER** tuşuna basın ve kabul edin. Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

 Kod parçacığı,. parçacığının * dosya adı uzantısına sahip bir XML dosyasında bulunur. Bir kod parçacığı, kullanıcının onları bulabileceği ve değiştirebilmeleri için kod parçacığı eklendikten sonra vurgulanan alanları içerebilir. Kod parçacığı oluşturma dosyası aynı zamanda **kod parçacığı Yöneticisi** için bilgi sağlar, böylece kod parçacığı adı doğru kategoride de görüntülenebilir. Kod parçacığı şeması hakkında daha fazla bilgi için bkz. [kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md).

 Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:

1. Belirli bir dil için kod parçacıkları oluşturun ve kaydedin.

2. Bir kısayol menüsüne **kod parçacığı Ekle** komutunu ekleyin.

3. Kod parçacığı genişletmeyi Uygula.

   Bu izlenecek yol, [Izlenecek yol: görüntüleme ifadesinin tamamlanmasını](../extensibility/walkthrough-displaying-statement-completion.md)temel alır.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Kod parçacıkları oluşturma ve kaydetme
 Genellikle, kod parçacıkları kayıtlı bir dil hizmeti ile ilişkilendirilir. Ancak, kod parçacıklarını kaydetmek için bir <xref:Microsoft.VisualStudio.Package.LanguageService> uygulamanız gerekmez. Bunun yerine, kod parçacığı dizini dosyasında bir GUID belirtmeniz ve ardından projenize eklediğiniz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> aynı GUID 'yi kullanmanız yeterlidir.

 Aşağıdaki adımlarda, kod parçacıklarının nasıl oluşturulacağı ve belirli bir GUID ile nasıl ilişkilendirileceğini gösterilmektedir.

1. Aşağıdaki dizin yapısını oluşturun:

    **%InstallDir%\TestSnippets\Snippets\1033 \\**

    Burada *% InstallDir%* , Visual Studio yükleme klasörüdür. (Bu yol genellikle kod parçacıklarını yüklemek için kullanılsa da, herhangi bir yol belirtebilirsiniz.)

2. \ 1033 \ klasöründe bir *. xml* dosyası oluşturun ve **testparçacıklar. xml**olarak adlandırın. (Bu ad genellikle bir kod parçacığı Dizin dosyası için kullanılsa da, bir *. xml* dosya adı uzantısına sahip olduğu sürece herhangi bir ad belirtebilirsiniz.) Aşağıdaki metni ekleyin ve ardından yer tutucu GUID 'INI silin ve kendinizinkini ekleyin.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. Kod parçacığı klasöründe bir dosya oluşturun, **test** `.snippet` adlandırın ve ardından aşağıdaki metni ekleyin:

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   Aşağıdaki adımlarda kod parçacıklarının nasıl kaydedileceği gösterilmektedir.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Belirli bir GUID için kod parçacıklarını kaydetmek için

1. **CompletionTest** projesini açın. Bu projenin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [Izlenecek yol: görüntüleme ifadesinin tamamlanması](../extensibility/walkthrough-displaying-statement-completion.md).

2. Projede, aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. TextManager. Interop. 8.0

    - Microsoft. MSXML

3. Projesinde, **kaynak. Extension. valtmanifest** dosyasını açın.

4. **Varlıklar** sekmesinin **VSPackage** içerik türünü içerdiğinden ve bu **projenin** projenin adına ayarlandığından emin olun.

5. CompletionTest projesini seçin Özellikler penceresi set **Generate pkgdef dosyasını** **true**olarak ayarlayın. Projeyi kaydedin.

6. Projeye statik bir `SnippetUtilities` sınıfı ekleyin.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. SnippetUtilities sınıfında bir GUID tanımlayın ve *SnippetsIndex. xml* dosyasında kullandığınız değeri verin.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. @No__t_0 `TestCompletionHandler` sınıfına ekleyin. Bu öznitelik, projedeki herhangi bir genel veya iç (statik olmayan) sınıfa eklenebilir. (Microsoft. VisualStudio. Shell ad alanı için bir `using` yönergesi eklemeniz gerekebilir.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Projeyi derleyin ve çalıştırın. Projeyi çalıştırdığınızda, Visual Studio 'nun deneysel örneğinde, yeni kaydettiğiniz kod parçacığı, **Test parçacıkları** dili altındaki **kod parçacıkları yöneticisinde** görüntülenmelidir.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne kod parçacığı Ekle komutunu ekleyin
 **Kod parçacığı Ekle** komutu, bir metin dosyasının kısayol menüsüne dahil değildir. Bu nedenle, komutunu etkinleştirmeniz gerekir.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne kod parçacığı Ekle komutu eklemek için

1. @No__t_0 sınıf dosyasını açın.

     Bu sınıf <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> uyguladığından, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yönteminde **kod parçacığı Ekle** komutunu etkinleştirebilirsiniz. Komutu etkinleştirmeden önce, **kod parçacığı Ekle** komutuna tıklandığında bu yöntemin bir Otomasyon işlevi içinde çağrılmadığından emin olun, kod parçacığı seçici Kullanıcı ARABIRIMINI (UI) görüntüler.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Projeyi derleyin ve çalıştırın. Deneysel örnekte, *. zzz* dosya adı uzantısına sahip bir dosya açın ve ardından içinde herhangi bir yere sağ tıklayın. **Kod parçacığı Ekle** komutu, kısayol menüsünde görünmelidir.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Kod parçacığı seçici Kullanıcı arabiriminde kod parçacığı genişletmeyi Uygula
 Bu bölümde, kısayol menüsünde kod **parçacığı Ekle** tıklandığında Parçacık Seçici Kullanıcı arabiriminin görüntülenmesi için kod parçacığı genişletmesinin nasıl uygulanacağı gösterilmektedir. Bir Kullanıcı kod parçacığı kısayolunu yazdığında ve sonra **sekme**tuşuna bastığında bir kod parçacığı de genişletilir.

 Kod parçacığı seçici Kullanıcı arabirimini göstermek ve gezinti ve ekleme sonrası kod parçacığı kabulünü etkinleştirmek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemini kullanın. Ekleme işlemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> yöntemi tarafından işlenir.

 Kod parçacığı genişletmesinin uygulanması eski <xref:Microsoft.VisualStudio.TextManager.Interop> arabirimlerini kullanır. Geçerli düzenleyici sınıflarından eski koda çevirinizde, eski arabirimlerin bir metin arabelleğindeki konumları belirtmek için satır numaralarının ve sütun sayılarının bir bileşimini kullanmasını unutmayın, ancak geçerli sınıflar bir dizin kullanır. Bu nedenle, bir arabellekte her biri 10 karakter (artı bir karakter olarak sayan bir yeni satır) varsa, üçüncü satırdaki dördüncü karakter geçerli uygulamada 27 konumunda, ancak 2. satır, eski uygulamada 3. konumda yer alır.

#### <a name="to-implement-snippet-expansion"></a>Kod parçacığı genişletmeyi uygulamak için

1. @No__t_0 sınıfını içeren dosyaya aşağıdaki `using` yönergelerini ekleyin.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. @No__t_0 sınıfının <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> arabirimini uygulamasını sağlayın.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. @No__t_0 sınıfında <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> içeri aktarın.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Kod genişletme arabirimleri ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için bazı özel alanlar ekleyin.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. @No__t_0 sınıfının oluşturucusunda aşağıdaki alanları ayarlayın.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Kullanıcı **kod parçacığı Ekle** komutuna tıkladığında kod parçacığı seçiciyi göstermek için, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemine aşağıdaki kodu ekleyin. (Bu açıklamayı daha okunabilir hale getirmek için, deyimin tamamlanması için kullanılan `Exec()`code gösterilmez; bunun yerine, kod blokları var olan yönteme eklenir.) Bir karakteri denetleyen koddan sonra aşağıdaki kod bloğunu ekleyin.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Bir kod parçacığında gezinilebilirler alanları varsa, genişletme açık olarak kabul edilene kadar genişletme oturumu açık tutulur; kod parçacığında alan yoksa, oturum kapatılır ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> yöntemi tarafından `null` olarak döndürülür. @No__t_0 yönteminde, önceki adımda eklediğiniz kod parçacığı seçicisinin kullanıcı ARABIRIMI kodundan sonra, kod parçacığı gezintisini işlemek için aşağıdaki kodu ekleyin (Kullanıcı, kod parçacığı eklendikten sonra **sekme** veya **SHIFT** +**sekmesine** bastığında).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Kullanıcı ilgili kısayolu yazdığında ve sonra **sekme**tuşuna bastığında kod parçacığını eklemek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemine kod ekleyin. Parçacığı ekleyen özel yöntem sonraki bir adımda gösterilir. Önceki adımda eklediğiniz gezinti kodundan sonra aşağıdaki kodu ekleyin.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. @No__t_0 arabiriminin yöntemlerini uygulayın. Bu uygulamada, yalnızca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> ilgilendiğiniz yöntemler vardır. Diğer yöntemler yalnızca <xref:Microsoft.VisualStudio.VSConstants.S_OK> döndürmelidir.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. @No__t_0 yöntemini uygulayın. Aslında genişletmeleri ekleyen yardımcı yöntemi sonraki bir adımda ele alınmıştır. @No__t_0, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> alabileceğiniz satır ve sütun bilgilerini sağlar.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Aşağıdaki özel yöntem, kısayolu ya da başlık ve yol üzerine bağlı olarak bir kod parçacığı ekler. Ardından, kod parçacığında <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> yöntemini çağırır.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Kod parçacığı genişletmeyi derleme ve test etme
 Kod parçacığının genişletmesinin projenizde çalışıp çalışmadığını test edebilirsiniz.

1. Çözümü oluşturun. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

2. Bir metin dosyası açın ve metin yazın.

3. Metinde bir yere sağ tıklayın ve **kod parçacığı Ekle**' ye tıklayın.

4. Kod parçacığı seçici Kullanıcı arabirimi, **Test değiştirme alanlarını**belirten bir açılır pencere ile görüntülenmelidir. Açılır pencerede çift tıklayın.

     Aşağıdaki kod parçacığı eklenmelidir.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     **ENTER** veya **ESC**tuşuna basmayın.

5. "First" ve "Second" arasında geçiş yapmak için **Tab** ve **SHIFT** +**Tab** tuşlarına basın.

6. **ENTER** veya **ESC**tuşuna basarak ekleme işlemini kabul edin.

7. Metnin farklı bir bölümünde "test" yazın ve ardından **sekme**tuşuna basın. "Test" kod parçacığı kısayolu olduğundan, kod parçacığı yeniden eklenmelidir.

## <a name="next-steps"></a>Sonraki adımlar
