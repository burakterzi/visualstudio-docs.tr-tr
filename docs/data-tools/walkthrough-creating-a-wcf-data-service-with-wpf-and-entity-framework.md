---
title: WPF & Entity Framework WCF veri hizmeti oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c17872b7fcfd0ecfa7c927880980fce79f432451
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648085"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>İzlenecek yol: WPF ve Entity Framework bir WCF veri hizmeti oluşturma
Bu kılavuzda, bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasında barındırılan basit bir [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] oluşturma ve ardından Windows Forms uygulamasından erişme gösterilmektedir.

Bu kılavuzda şunları yapabilirsiniz:

- @No__t_0 barındırmak için bir Web uygulaması oluşturun.

- Northwind veritabanındaki `Customers` tablosunu temsil eden bir [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] oluşturun.

- @No__t_0 oluşturun.

- Bir istemci uygulaması oluşturun ve [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] bir başvuru ekleyin.

- Hizmete veri bağlamayı etkinleştirin ve kullanıcı arabirimini oluşturun.

- İsteğe bağlı olarak, uygulamaya filtreleme yetenekleri ekleyin.

## <a name="prerequisites"></a>Prerequisites
Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi**aracılığıyla yükleyin. **Visual Studio yükleyicisi**, SQL Server Express LocalDB 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (**SQL Server Nesne Gezgini** , Visual Studio yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="creating-the-service"></a>Hizmeti Oluşturma
@No__t_0 oluşturmak için bir Web projesi ekleyin, bir [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] oluşturun ve sonra modelden hizmeti oluşturun.

İlk adımda, hizmeti barındırmak için bir Web projesi eklersiniz.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Web projesi oluşturmak için

1. Menü çubuğunda **dosya**  > **Yeni**  > **Proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#**  ve **Web** düğümlerini genişletin ve **ASP.NET Web uygulaması** şablonunu seçin.

3. **Ad** metin kutusuna **NorthwindWeb**yazın ve sonra **Tamam** düğmesini seçin.

4. **Yeni ASP.NET projesi** iletişim kutusunda, **bir şablon seçin** listesinde **boş**' ı seçin ve ardından **Tamam** düğmesini seçin.

Sonraki adımda, Northwind veritabanındaki `Customers` tablosunu temsil eden bir [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] oluşturursunuz.

### <a name="to-create-the-entity-data-model"></a>Varlık Veri Modeli'ni oluşturmak için

1. Menü çubuğunda, **proje**  > **Yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **veri** düğümünü seçin ve ardından **ADO.net varlık veri modeli** öğesini seçin.

3. **Ad** metin kutusuna `NorthwindModel` girin ve sonra **Ekle** düğmesini seçin.

     Varlık Veri Modeli Sihirbazı görüntülenir.

4. Varlık Veri Modeli sihirbazında, **model Içeriğini seçin** sayfasında, **veritabanı öğesinden EF Designer** ' ı seçin ve sonra **İleri** düğmesini seçin.

5. **Veri bağlantınızı seçin** sayfasında, aşağıdaki adımlardan birini gerçekleştirin:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         veya

    - Yeni bir veri bağlantısı yapılandırmak için **Yeni bağlantı** düğmesini seçin. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

6. Veritabanı parola gerektiriyorsa, **Evet ' i seçin, hassas verileri bağlantı dizesi** seçenek düğmesine ekleyin ve sonra **İleri** düğmesini seçin.

    > [!NOTE]
    > Bir iletişim kutusu görüntülenirse, dosyayı projenize kaydetmek için **Evet** ' i seçin.

7. **Sürümünüzü seçin** sayfasında **Entity Framework 5,0** seçenek düğmesini ve ardından **İleri** düğmesini seçin.

    > [!NOTE]
    > Entity Framework 6 ' nın en son sürümünü WCF hizmetleriyle kullanabilmek için, WCF Veri Hizmetleri Entity Framework sağlayıcısı NuGet paketini yüklemeniz gerekir. Bkz. [Entity Framework 6 + ile WCF veri Hizmetleri 5.6.0 kullanma](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin, **müşteriler** onay kutusunu seçin ve ardından **son** düğmesini seçin.

     Varlık modeli diyagramı görüntülenir ve projenize bir *NorthwindModel. edmx* dosyası eklenir.

Sonraki adımda, veri hizmetini oluşturup test edersiniz.

### <a name="to-create-the-data-service"></a>Veri hizmetini oluşturmak için

1. Menü çubuğunda, **proje**  > **Yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle** Iletişim kutusunda **Web** düğümünü seçin ve ardından **WCF veri hizmeti 5,6** öğesini seçin.

3. **Ad** metin kutusuna `NorthwindCustomers` girin ve sonra **Ekle** düğmesini seçin.

     **NorthwindCustomers. svc** dosyası **kod düzenleyicisinde**görüntülenir.

4. **Kod Düzenleyicisi**'nde, ilk `TODO:` açıklamasını bulun ve kodu aşağıdaki kodla değiştirin:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5. @No__t_0 olay işleyicisindeki açıklamaları aşağıdaki kodla değiştirin:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6. Hizmeti çalıştırmak için, menü çubuğunda **hata ayıkla**  >  hata ayıklama**olmadan Başlat** ' ı seçin. Bir tarayıcı penceresi açılır ve hizmet için XML şeması görüntülenir.

7. **Adres** çubuğunda, **NorthwindCustomers. svc**URL 'sinin sonuna `Customers` girin ve **ENTER** tuşunu seçin.

     @No__t_0 tablosundaki verilerin XML temsili görüntülenir.

    > [!NOTE]
    > Bazı durumlarda, Internet Explorer verileri yanlışlıkla RSS akışı olarak yorumlar. RSS akışlarını görüntüleme seçeneğinin devre dışı bırakıldığından emin olmalısınız. Daha fazla bilgi için bkz. [hizmet başvurularına sorun giderme](../data-tools/troubleshooting-service-references.md).

8. Tarayıcı penceresini kapatın.

Sonraki adımlarda, hizmeti kullanmak için bir Windows Forms istemci uygulaması oluşturacaksınız.

## <a name="creating-the-client-application"></a>İstemci Uygulamasını Oluşturma
İstemci uygulamasını oluşturmak için ikinci bir proje ekleyin, projeye bir hizmet başvurusu ekleyin, bir veri kaynağı yapılandırın ve hizmetten verileri göstermek için bir kullanıcı arabirimi oluşturun.

İlk adımda, çözüme bir Windows Forms projesi ekler ve bunu başlangıç projesi olarak ayarlarsınız.

### <a name="to-create-the-client-application"></a>İstemci uygulamasını oluşturmak için

1. Menü çubuğunda dosya,  > **Yeni proje** **Ekle** ' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual Basic** veya **görsel C#**  düğümünü genişletin, **Windows** düğümünü seçin ve sonra **Windows Forms uygulama**' yı seçin.

3. **Ad** metin kutusuna `NorthwindClient` girin ve sonra **Tamam** düğmesini seçin.

4. **Çözüm Gezgini**, **NorthwindClient** proje düğümünü seçin.

5. Menü çubuğunda **Proje**, **Başlangıç projesi olarak ayarla**' yı seçin.

Bir sonraki adımda, Web projesindeki [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] bir hizmet başvurusu eklersiniz.

### <a name="to-add-a-service-reference"></a>Hizmet başvurusu eklemek için

1. Menü çubuğunda, **proje**  > **hizmet başvurusu Ekle**' ni seçin.

2. **Hizmet başvurusu Ekle** Iletişim kutusunda **bul** düğmesini seçin.

     NorthwindCustomers hizmeti URL 'SI, **Adres** alanında görüntülenir.

3. Hizmet başvurusunu eklemek için **Tamam** düğmesini seçin.

Bir sonraki adımda, hizmete veri bağlamayı etkinleştirmek için bir veri kaynağı yapılandırırsınız.

### <a name="to-enable-data-binding-to-the-service"></a>Hizmete veri bağlamayı etkinleştirmek için

1. Menü çubuğunda  > **diğer Windows**  > **veri kaynaklarını** **görüntüle** ' yi seçin.

   **Veri kaynakları** penceresi açılır.

2. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle** düğmesini seçin.

3. **Veri kaynağı Yapılandırma Sihirbazı**' nın **veri kaynağı türünü seçin** sayfasında, **nesne**' yi seçin ve ardından **İleri** düğmesini seçin.

4. **Veri nesnelerini seçin** sayfasında, **NorthwindClient** düğümünü genişletin ve ardından **NorthwindClient. ServiceReference1** düğümünü genişletin.

5. **Müşteri** onay kutusunu seçin ve ardından **son** düğmesini seçin.

Sonraki adımda, hizmetten gelen verileri görüntüleyen Kullanıcı arabirimini oluşturursunuz.

### <a name="to-create-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için

1. **Veri kaynakları** penceresinde, **müşteriler** düğümünün kısayol menüsünü açın ve **Kopyala**' yı seçin.

2. **Form1. vb** veya **Form1.cs** form tasarımcısında, kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    @No__t_0 denetim, bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeni forma eklenir.

3. **CustomersDataGridView** denetimini seçin ve ardından **Özellikler** penceresinde **Dock** özelliğini **Fill**olarak ayarlayın.

4. **Çözüm Gezgini**, **Form1** düğümünün kısayol menüsünü açın ve kod düzenleyicisini açmak için **kodu görüntüle** ' yi seçin ve aşağıdaki `Imports` veya `Using` ifadesini dosyanın en üstüne ekleyin:

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. @No__t_0 olay işleyicisine aşağıdaki kodu ekleyin:

   ```vb
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
           Dim proxy As New NorthwindEntities _
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
           Me.CustomersBindingSource.DataSource = proxy.Customers
       End Sub
   ```

   ```csharp
   private void Form1_Load(object sender, EventArgs e)
   {
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
   this.CustomersBindingSource.DataSource = proxy.Customers;
   }
   ```

6. **Çözüm Gezgini**, **NorthwindCustomers. svc** dosyasının kısayol menüsünü açın ve **Tarayıcıda görüntüle '** yi seçin. Internet Explorer açılır ve hizmet için XML şeması görüntülenir.

7. Internet Explorer adres çubuğundan URL'yi kopyalayın.

8. Adım 4 ' te eklediğiniz kodda `http://localhost:53161/NorthwindCustomers.svc/` ' yi seçin ve yeni kopyaladığınız URL ile değiştirin.

9. Uygulamayı çalıştırmak için, menü çubuğunda **hata ayıkla**  >  hata**ayıklamayı Başlat** ' ı seçin. Müşteri bilgileri gösterilir.

   Artık, NorthwindCustomers hizmetinden müşterilerin listesini görüntüleyen çalışır bir uygulamanız var. Hizmet aracılığıyla ek verileri kullanıma sunmak istiyorsanız, [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Northwind veritabanından ek tablolar içerecek şekilde değiştirebilirsiniz.

Sonraki isteğe bağlı adımda, hizmet tarafından döndürülen verileri nasıl filtreleyeceğinizi öğrenirsiniz.

## <a name="adding-filtering-capabilities"></a>Filtreleme Yetenekleri Ekleme
Bu adımda, verileri müşterinin şehre göre filtrelemek için uygulamayı özelleştirirsiniz.

### <a name="to-add-filtering-by-city"></a>Şehir bilgisine göre filtreleme eklemek için

1. **Çözüm Gezgini**, **Form1. vb** veya **Form1.cs** düğümünün kısayol menüsünü açın ve **Aç**' ı seçin.

2. **Araç kutusundan** forma bir <xref:System.Windows.Forms.TextBox> denetimi ve bir <xref:System.Windows.Forms.Button> denetimi ekleyin.

3. @No__t_0 denetiminin kısayol menüsünü açın, **kodu görüntüle**' yi seçin ve ardından aşağıdaki kodu `Button1_Click` olay işleyicisine ekleyin:

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4. Önceki kodda, `http://localhost:53161/NorthwindCustomers.svc` `Form1_Load` olay işleyicisindeki URL ile değiştirin.

5. Uygulamayı çalıştırmak için, menü çubuğunda **hata ayıkla**  >  hata**ayıklamayı Başlat** ' ı seçin.

6. Metin kutusuna **Londra**yazın ve ardından düğmeyi seçin. Yalnızca Londralı müşteriler görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Nasıl yapılır: WCF veri hizmeti başvurusu ekleme, güncelleştirme veya kaldırma](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)