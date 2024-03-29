---
title: Etki Alanına Özgü Dillerle Çalışmaya Başlama
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c86383ddc833a6b76affa451f21180ed4941ad14
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985045"
---
# <a name="get-started-with-domain-specific-languages"></a>Alana Özgü Dilleri Kullanmaya Başlama

Bu konu başlığı altında, Visual Studio için modelleme SDK 'Sı ile oluşturulmuş bir etki alanına özgü dili (DSL) tanımlama ve kullanma konusundaki temel kavramlar açıklanmaktadır.

> [!NOTE]
> Metin şablonu dönüştürme SDK 'Sı ve Visual Studio modelleme SDK 'Sı, Visual Studio 'nun belirli özelliklerini yüklediğinizde otomatik olarak yüklenir. Daha ayrıntılı bilgi için [Bu blog gönderisine](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)bakın.

DSLs 'yi yeni Deneyiyorsanız, bu sitede bulabileceğiniz **dsl araçları Laboratuvarı**aracılığıyla çalışmanızı öneririz: [görselleştirme ve modelleme SDK 'sı](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Etki alanına özgü dille ne yapabilirsiniz?

Etki alanına özgü dil, genellikle grafik olan ve belirli bir amaç için kullanılmak üzere tasarlanan bir gösterimidir. Bunun aksine, UML gibi dillerin genel amaçlı olması gerekir. Bir DSL 'de model öğesi türlerini ve bunların ilişkilerini ve bunların ekranda nasıl sunulduğunu tanımlayabilirsiniz.

Bir DSL tasarladıktan sonra, bir Visual Studio Tümleştirme Uzantısı (VSıX) paketinin parçası olarak dağıtabilirsiniz. Kullanıcılar, Visual Studio 'da DSL ile çalışır:

![Aile ağacı diyagramı, araç kutusu ve gezgin](../modeling/media/familyt_instance.png)

Gösterim yalnızca DSL 'nin bir parçasıdır. Gösterimle birlikte, VSıX paketiniz kullanıcıların, modellerinden malzemeleri düzenlemeye ve oluşturmaya yardımcı olmak için uygulayabileceğiniz araçları içerir.

DSLs 'nin asıl uygulamalarından biri program kodu, yapılandırma dosyaları ve diğer yapıtları oluşturmak için kullanılır. Özellikle büyük projelerde ve ürün satırlarında, bir ürünün çeşitli varyantlarının oluşturulması durumunda, DSLs 'deki değişken yönlerinin birçoğu, güvenilirlikte büyük bir artış ve gereksinimler değişikliklerine çok hızlı yanıt verebilir.

Bu genel bakışın geri kalanında, Visual Studio 'da alana özgü dil oluşturma ve kullanma ile ilgili temel işlemleri tanıtan bir anlatım sunulmaktadır.

## <a name="prerequisites"></a>Prerequisites

Bir DSL tanımlamak için aşağıdaki bileşenleri yüklemiş olmanız gerekir:

| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Visual Studio için modelleme SDK 'Sı | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>DSL çözümü oluşturma

Yeni bir etki alanına özgü dil oluşturmak için, etki alanına özgü dil proje şablonunu kullanarak yeni bir Visual Studio çözümü oluşturun.

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Proje türleri**altında **diğer proje türleri** düğümünü genişletin ve **genişletilebilirlik**' e tıklayın.

3. **Alana özgü dil Tasarımcısı**' ye tıklayın.

     ![DSL oluştur iletişim kutusu](../modeling/media/create_dsldialog.png)

4. **Ad** kutusuna **FamilyTree**yazın. **Tamam**'a tıklayın.

     **Etki alanına özgü dil Sihirbazı** açılır ve şablon DSL çözümlerinin listesini görüntüler.

     Açıklamaları görmek için her şablona tıklayın,

     Şablonlar, yararlı başlangıç noktalarıdır. Bunların her biri, gereksinimlerinize uyacak şekilde düzenleyebileceğiniz, tamamlanmış bir çalışan DSL sağlar. Normalde, oluşturmak istediğiniz en yakın şablonu seçersiniz.

5. Bu izlenecek yol için **en az dil** şablonunu seçin.

6. Uygun sihirbaz sayfasında DSL 'niz için bir dosya adı uzantısı girin. Bu, DSL 'nin örneklerini içeren dosyaların kullanacağı uzantıdır.

    - Bilgisayarınızdaki herhangi bir uygulamayla veya DSL 'yi yüklemek istediğiniz herhangi bir bilgisayarda ilişkilendirilmemiş bir uzantı seçin. Örneğin, **docx** ve **htm** kabul edilemez dosya adı uzantıları olacaktır.

    - Girdiğiniz uzantı DSL olarak kullanılıyorsa, sihirbaz sizi uyarır. Farklı bir dosya adı uzantısı kullanmayı düşünün. Ayrıca, eski deneysel tasarımcıları temizlemek için Visual Studio SDK Deneysel örneğini de sıfırlayabilirsiniz. **Başlat**' a tıklayın, **tüm programlar**, **Microsoft Visual Studio 2010 SDK**ve **araçlar**' a tıklayın ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın**.

7. Diğer sayfaları inceleyin ve ardından **son**' a tıklayın.

     İki proje içeren bir çözüm oluşturulur. Bunlar DSL ve DslPackage olarak adlandırılır. DslDefinition. dsl adlı bir diyagram dosyası açılır.

    > [!NOTE]
    > İki projedeki klasörlerde görebileceğiniz kodun çoğu DslDefinition. dsl ' den oluşturulmuştur. Bu nedenle, bu dosyada DSL 'niz üzerinde yapılan çoğu değişiklik yapılır.

Kullanıcı arabirimi artık aşağıdaki resme benzer.

![DSL Tasarımcısı](../modeling/media/dsl_designer.png)

Bu çözüm, etki alanına özgü bir dili tanımlar. Daha fazla bilgi için bkz. [alana özgü dil Araçları Kullanıcı arabirimine genel bakış](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>DSL çözümünün önemli bölümleri

Yeni çözümün aşağıdaki yönlerini görürsünüz:

- **Dsl\dsldefinition.exe** Bu, bir DSL çözümü oluştururken gördüğünüz dosyadır. Çözümdeki kodun neredeyse tamamı bu dosyadan oluşturulmuştur ve DSL tanımında yaptığınız değişikliklerin çoğu burada yapılır. Daha fazla bilgi için bkz. [DSL tanımı diyagramı Ile çalışma](../modeling/working-with-the-dsl-definition-diagram.md)ile çalışma.

- **DSL projesi** Bu proje, etki alanına özgü dili tanımlayan kodu içerir.

- **DslPackage projesi** Bu proje, Visual Studio 'da DSL örneklerinin açılmasına ve düzenlenmesine izin veren kodu içerir.

## <a name="Debugging"></a>DSL 'yi çalıştırma

DSL çözümünü, oluşturduktan hemen sonra çalıştırabilirsiniz. Daha sonra, her değişiklikten sonra çözümü yeniden çalıştırarak DSL tanımını kademeli olarak değiştirebilirsiniz.

### <a name="to-experiment-with-the-dsl"></a>DSL 'yi denemek için

1. **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın. Bu, kaynak kodun büyük bölümünü DslDefinition. dsl 'den yeniden oluşturur.

    > [!NOTE]
    > *DslDefinition. dsl*'yi her değiştirdiğinizde, çözümü yeniden oluşturmadan önce **Tüm Şablonları Dönüştür** ' e tıklamanız gerekir. Bu adımı otomatik hale getirebilirsiniz. Daha fazla bilgi için bkz. [tüm şablonları dönüştürmeyi otomatikleştirme](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. **F5**tuşuna basın veya **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın.

     DSL derlemeleri ve Visual Studio 'nun deneysel örneğine yüklenir.

     Visual Studio 'nun deneysel bir örneği başlar. Deneysel örnek, Visual Studio uzantılarının hata ayıklama amacıyla kaydedildiği, kayıt defterinin farklı bir alt ağacında bulunan ayarlarını alır. Visual Studio 'nun normal örnekleri orada kayıtlı uzantılara erişemez.

3. Visual Studio 'nun deneysel örneğinde, **Çözüm Gezgini** **Test** adlı model dosyasını açın.

     \- veya-

     Hata ayıklama projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **öğe**' ye tıklayın. **Öğe Ekle** iletişim kutusunda, DSL 'nizin dosya türünü seçin.

     Model dosyası boş bir diyagram olarak açılır.

     Araç kutusu açılır ve diyagram türüne uygun araçları görüntüler.

4. Diyagram üzerinde şekiller ve bağlayıcılar oluşturmak için araçları kullanın.

    1. Şekil oluşturmak için örnek Şekil aracı diyagramda sürükleyin.

    2. İki şekli bağlamak için, örnek bağlayıcı aracına tıklayın, ilk şekle tıklayın ve ardından ikinci şekle tıklayın.

5. Bunları değiştirmek için şekillerin etiketlerine tıklayın.

Deneysel Visual Studio, aşağıdaki örneğe benzeyecektir:

![Visual Studio 'da etki alanına özgü dil örnek ağacı](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Bir modelin Içeriği

Bir DSL örneği olan bir dosyanın içeriğine *model*denir. *Model* <em>öğeleri</em> ve öğeler arasındaki *bağlantıları* içerir. DSL tanımı, modelde model öğesi ve bağlantı türlerinin ne tür bir bulunabilir olduğunu belirtir. Örneğin, minimum dil şablonundan oluşturulan bir DSL 'de, bir tür model öğesi ve bir bağlantı türü vardır.

DSL tanımı, modelin diyagram üzerinde nasıl göründüğünü belirtebilir. Birçok şekil ve bağlayıcı stili arasından seçim yapabilirsiniz. Bazı şekillerin diğer şekillerin içinde görünmesini sağlayabilirsiniz.

Bir modeli düzenlediğinizde, bir modeli **Gezgin** görünümünde ağaç olarak görüntüleyebilirsiniz. Diyagrama şekil eklerken, model öğeleri de gezgin 'de görüntülenir. Diyagram olmasa bile gezgin kullanılabilir.

Visual Studio 'nun hata ayıklama örneğinde gezgin 'i göremiyorsanız, **Görünüm** menüsünde **diğer pencereler**' in üzerine gelin ve *\<Your dil >* **Gezgini**' ne tıklayın.

### <a name="the-api-of-your-dsl"></a>DSL API 'SI

DSL 'niz, DSL örnekleri olan modelleri okumanızı ve güncelleştirmenizi sağlayan bir API oluşturur. API 'nin bir uygulaması, bir modelden metin dosyaları üretmesidir. Daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Hata ayıklama çözümünde ". tt" uzantılı şablon dosyalarını açın. Bu örneklerde modellerden nasıl metin oluşturabileceğiniz ve DSL 'nizin API 'sini test etmeniz için nasıl izin oluşturabileceğiniz gösterilmektedir. Örneklerden biri, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]diğer [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]yazılır.

Her şablon dosyası altında oluşturduğu dosyadır. Çözüm Gezgini şablon dosyasını genişletin ve oluşturulan dosyayı açın.

Şablon dosyası, modeldeki tüm öğeleri listeleyen kısa bir kod segmenti içerir.

Oluşturulan dosya sonucu içerir.

Bir model dosyasını değiştirdiğinizde, dosyaları yeniden oluşturduktan sonra oluşturulan dosyalarda ilgili değişiklikleri görürsünüz.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Model dosyasını değiştirdikten sonra metin dosyalarını yeniden oluşturmak için

1. Visual Studio 'nun deneysel örneğinde model dosyasını kaydedin.

2. Her. tt dosyasındaki dosya adı parametresinin, denemeleri için kullandığınız model dosyasına başvurduğundan emin olun. . Tt dosyasını kaydedin.

3. **Çözüm Gezgini**araç çubuğundan **Tüm Şablonları Dönüştür** ' e tıklayın.

     \- veya-

     Yeniden oluşturmak istediğiniz şablonlara sağ tıklayın ve ardından **özel araç Çalıştır**' a tıklayın.

Bir projeye istediğiniz sayıda metin şablonu dosyası ekleyebilirsiniz. Her şablon bir sonuç dosyası üretir.

> [!NOTE]
> DSL tanımını değiştirdiğinizde örnek metin şablonu kodu, güncelleştirmediğiniz takdirde çalışmaz.

Daha fazla bilgi için, bkz. [etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md) ve [etki alanına özgü bir dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>DSL 'yi özelleştirme

DSL tanımını değiştirmek istediğinizde, deneysel örneği kapatın ve ana Visual Studio örneğindeki tanımı güncelleştirin.

> [!NOTE]
> DSL tanımını değiştirdikten sonra, önceki sürümleri kullanarak oluşturduğunuz test modellerinde bilgileri kaybedebilirsiniz.  Örneğin, hata ayıklama çözümü, bazı şekiller ve bağlayıcılar içeren örnek adlı bir dosya içerir. DSL tanımınızı geliştirmeye başladıktan sonra, bunlar görünür olmayacaktır ve dosyayı kaydettiğinizde kaybedilir.

DSL 'niz için çok çeşitli uzantılar yapabilirsiniz. Aşağıdaki örnekler size olasılıklardan oluşan bir izlenim verecektir.

Her değişiklikten sonra DSL tanımını kaydedin, **Çözüm Gezgini** **Tüm Şablonları Dönüştür** ' e tıklayın ve ardından değiştirilen DSL 'yi denemek için **F5** tuşuna basın.

### <a name="rename-the-types-and-tools"></a>Türleri ve araçları yeniden adlandırma

Var olan etki alanı sınıflarını ve ilişkileri yeniden adlandırın. Örneğin, minimum dil şablonundan oluşturulan bir DSL tanımından başlayarak, DSL 'nin aile ağaçlarını göstermesini sağlamak için aşağıdaki yeniden adlandırma işlemlerini gerçekleştirebilirsiniz.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Etki alanı sınıflarını, ilişkileri ve araçları yeniden adlandırmak için

1. DslDefinition diyagramında, **ExampleModel** ' i **FamilyTreeModel**, **ExampleElement** öğesini **kişiye**, **Ebeveynler**için **hedefler** ve **alt öğeleri**olan **kaynaklara** yeniden adlandırın. Her etikete tıklayarak bunu değiştirebilirsiniz.

     ![DSL tanımı diyagramı &#45; aile ağacı modeli](../modeling/media/familyt_person.png)

2. Öğe ve bağlayıcı araçlarını yeniden adlandırın.

    1. Çözüm Gezgini altındaki sekmeye tıklayarak DSL Gezgini penceresini açın. Bunu göremiyorsanız, **Görünüm** menüsünde **diğer pencereler** ' i Işaret edin ve ardından **DSL Gezgini**' ne tıklayın. DSL Gezgini yalnızca DSL tanımı diyagramı etkin pencere olduğunda görülebilir.

    2. Özellikler penceresi açın ve aynı anda DSL Gezginini ve özelliklerini görebilmek için konumlandırın.

    3. DSL Gezgini ' nde **Düzenleyici**, **araç kutusu SEKMELERI**, *\<your DSL >* ve ardından **Araçlar**' ı genişletin.

    4. **ExampleElement öğesine**tıklayın. Bu, öğeleri oluşturmak için kullanılan araç kutusu öğesidir.

    5. Özellikler penceresi, **ad** özelliğini **Person**olarak değiştirin.

         **Caption** özelliğinin de değişdiğine dikkat edin.

    6. Aynı şekilde, **ExampleConnector** aracının adını **parentlınk**olarak değiştirin. **Caption** özelliğini, Name özelliğinin bir kopyası olmaması için değiştirin. Örneğin, **üst bağlantıyı**girin.

3. DSL 'yi yeniden derleyin.

    1. DSL tanım dosyasını kaydedin.

    2. Çözüm Gezgini araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın

    3. F5 tuşuna basın. Visual Studio 'nun deneysel örneği görünene kadar bekleyin.

4. Visual Studio 'nun Deneysel örneğindeki hata ayıklama çözümünde bir test modeli dosyası açın. Öğeleri araç kutusu 'ndan üzerine sürükleyin. DSL Gezgini 'ndeki araç başlıklarının ve tür adlarının değiştiğini unutmayın.

5. Model dosyasını kaydedin.

6. Bir. tt dosyası açın ve eski tür ve özellik adlarının oluşumlarını yeni adlarla değiştirin.

7. . Tt dosyasında belirtilen dosya adının test modelinizi belirttiğinden emin olun.

8. . Tt dosyasını kaydedin. Kodu. tt dosyasında çalıştırmanın sonucunu görmek için oluşturulan dosyayı açın. Doğru olduğunu doğrulayın.

### <a name="add-domain-properties-to-classes"></a>Sınıflara etki alanı özellikleri ekleyin
 Bir etki alanı sınıfına özellikler ekleyin, örneğin, bir kişinin Doğum ve ölül yılını temsil edin.

 Yeni özellikleri diyagramda görünür hale getirmek için model öğesini görüntüleyen şekle *dekoratörler* eklemeniz gerekir. Ayrıca özellikleri dekoratörler ile de eşlemeniz gerekir.

##### <a name="to-add-properties-and-display-them"></a>Özellikleri eklemek ve bunları göstermek için

1. Özellikleri ekleyin.

   1. DSL tanımı diyagramında **kişi** etki alanı sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **etki alanı özelliği**' ne tıklayın.

   2. **Doğum** ve **ölüm**gibi yeni özellik adlarının bir listesini yazın. Her birinin ardından **ENTER** tuşuna basın.

2. Şekildeki özellikleri görüntüleyecek dekoratörler ekleyin.

   1. Kişi etki alanı sınıfından diyagramın diğer tarafına genişleyen gri çizgiyi izleyin. Bu bir diyagram öğe eşlemedir. Alan sınıfını bir şekil sınıfına bağlar.

   2. Bu şekil sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **metin dekoratörü**' ne tıklayın.

   3. **Ikdekoratör** ve **DeathDecorator**gibi adlara sahip iki dekoratörü ekleyin.

   4. Her yeni dekoratör ' ı seçin ve Özellikler penceresi **konum** alanını ayarlayın. Bu, şekil üzerinde etki alanı özelliği değerinin nerede gösterileceğini belirler. Örneğin, **InnerBottomLeft** ve **InnerBottomRight**'yi ayarlayın.

        ![Bölme şekli tanımı](../modeling/media/familyt_compartment.png)

3. Dekoratlarını özelliklerle eşleyin.

   1. DSL ayrıntıları penceresini açın. Genellikle çıkış penceresinin yanındaki bir sekmeden oluşur. Bunu göremiyorsanız, **Görünüm** menüsünde **diğer pencereler**' ın üzerine gelin ve **DSL ayrıntıları**' na tıklayın.

   2. DSL tanımı diyagramında, **kişi** etki alanı sınıfını şekil sınıfına bağlayan satıra tıklayın.

   3. **DSL ayrıntıları** **dekoratör haritaları** sekmesinde, eşlenmemiş dekoratörün onay kutusuna tıklayın. **Görüntü özelliği**' nde, eşleştirilmesini istediğiniz etki alanı özelliğini seçin. Örneğin, **Doğıcı dolabı** **Doğum**olarak eşleyin.

4. DSL 'yi kaydedin, tüm Şablonları Dönüştür ' e tıklayın ve F5 tuşuna basın.

5. Örnek model diyagramında, artık seçtiğiniz konumlara tıklabildiğinizi ve bunlara değer yazdığınıza emin olun. Ayrıca, bir **kişi** şekli seçtiğinizde Özellikler penceresi, yeni özellikleri Doğum ve ölüm olarak görüntüler.

6. Bir. tt dosyasında, her birinin özelliklerini elde eden kodu ekleyebilirsiniz.

   ![Aile ağacı diyagramı, araç kutusu ve gezgin](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Yeni sınıfları tanımlama
 Bir modele etki alanı sınıfları ve ilişkiler ekleyebilirsiniz. Örneğin, kasaları temsil eden yeni bir sınıf ve kasadaki bir kişinin süreli olduğunu temsil eden yeni bir ilişki oluşturabilirsiniz.

 Farklı türleri bir model diyagramında farklı hale getirmek için, etki alanı sınıflarını farklı şekil türlerine veya farklı geometri ve renklere sahip şekillere eşleyebilirsiniz.

##### <a name="to-add-and-display-a-new-domain-class"></a>Yeni bir etki alanı sınıfı ekleme ve görüntüleme

1. Bir etki alanı sınıfı ekleyin ve model kökünün alt öğesi yapın.

    1. DSL tanımı diyagramında, **katıştırma ilişkisi** aracına tıklayın, **FamilyTreeModel**kök sınıfına tıklayın ve ardından diyagramın boş bir kısmına tıklayın.

         Yeni bir etki alanı sınıfı görünür, bu, bir katıştırma ilişkisi ile FamilyTreeModel 'e bağlanır.

         Adını (örneğin, **Town**) ayarlayın.

        > [!NOTE]
        > Modelin kökü hariç her etki alanı sınıfı, en az bir katıştırma ilişkisinin hedefi olmalıdır veya bir gömmenin hedefi olan bir sınıftan devralması gerekir. Bu nedenle, ekleme Ilişkisi aracı 'nı kullanarak bir etki alanı sınıfı oluşturmak sıklıkla kullanışlıdır.

    2. Yeni sınıfa bir etki alanı özelliği ekleyin, örneğin **adı**.

2. Kişi ve şehir arasında bir başvuru ilişkisi ekleyin.

    1. **Başvuru ilişkisi** aracına tıklayın, kişi ' ye ve ardından şehir ' e tıklayın.

         ![DSL tanım parçası: aile ağacı kökü](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Başvuru ilişkileri, model ağacının bir bölümünden diğerine çapraz başvuruları temsil eder.

3. Model diyagramlarında kasabalarında şubeleri 'yi temsil edecek bir şekil ekleyin.

    1. Araç kutusundan bir **geometri şeklini** diyagrama sürükleyin ve örneğin, **TownShape**gibi yeniden adlandırın.

    2. Özellikler penceresi, yeni şeklin, Fill Color ve Geometry gibi görünüm alanlarını ayarlayın.

    3. Town adını göstermek için bir dekoratörü ekleyin ve ad dekoratörü 'nı yeniden adlandırın. Position özelliğini ayarlayın.

4. Town etki alanı sınıfını Kasanşekle eşleyin.

    1. **Diyagram öğesi eşleme** aracına tıklayın, ardından Town etki alanı sınıfına ve ardından TownShape şekil sınıfına tıklayın.

    2. Harita Bağlayıcısı seçiliyken **DSL ayrıntıları** penceresinin **dekoratör haritaları** sekmesinde, namedekoratör ' ı Işaretleyin ve **Display özelliğini** Name olarak ayarlayın.

5. Kişi ve Kasans arasındaki ilişkiyi göstermek için bir bağlayıcı oluşturun.

    1. Araç kutusundan bir bağlayıcıyı diyagrama sürükleyin. Yeniden adlandırıp görünüm özelliklerini ayarlayın.

    2. Yeni bağlayıcıyı kişi ve şehir arasındaki ilişkiye bağlamak için **diyagram öğesi eşleme** aracını kullanın.

         ![Eklenmiş Şekil haritası ile aile ağacı tanımı](../modeling/media/familyt_shapemap.png)

6. Yeni bir şehir oluşturmak için bir öğe aracı oluşturun.

    1. **DSL Gezgini**' nde **Düzenleyici** ve **araç kutusu sekmeleri**' ni genişletin.

    2. *DSL >\<* sağ tıklayın ve sonra **Yeni öğe Ekle aracı**' na tıklayın.

    3. Yeni aracının **Name** özelliğini ayarlayın ve **sınıf** özelliğini Town olarak ayarlayın.

    4. **Araç kutusu simgesi** özelliğini ayarlayın. **[...]** Simgesine tıklayın ve **dosya adı** alanında bir simge dosyası seçin.

7. Kasabalarında şubeleri ve kişiler arasında bağlantı oluşturmak için bir bağlayıcı aracı oluşturun.

    1. *DSL >\<* sağ tıklayın ve sonra **yeni bağlayıcı aracı ekle**' ye tıklayın.

    2. Yeni aracın ad özelliğini ayarlayın.

    3. **ConnectionBuilder** özelliğinde, kişi-Town ilişkisinin adını içeren oluşturucuyu seçin.

    4. **Araç kutusu simgesini**ayarlayın.

8. DSL tanımını kaydedin, **Tüm Şablonları Dönüştür**' e tıklayın ve **F5**tuşuna basın.

9. Visual Studio 'nun deneysel örneğinde bir test modeli dosyası açın. Kasabalarında şubeleri ve kişiler arasında kasalar ve bağlantılar oluşturmak için yeni araçları kullanın. Yalnızca doğru öğe türleri arasında bağlantı oluştururıbildiğinize dikkat edin.

10. Her birinin yaşadığı kasayı listeleyen kodu oluşturun. Metin şablonları, bu tür kodları çalıştırabileceğiniz yerlerden biridir. Örneğin, hata ayıklama çözümünde varolan Sample.tt dosyasını aşağıdaki kodu içerecek şekilde değiştirebilirsiniz:

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     *. Tt dosyasını kaydettiğinizde, kişilerin listesini ve bunların onların listesini içeren bir yan kuruluş dosyası oluşturacaktır. Daha fazla bilgi için bkz. [etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Doğrulama ve komutlar
 Doğrulama kısıtlamaları ekleyerek bu DSL 'yi daha da geliştirebilirsiniz. Bu kısıtlamalar, modelin doğru bir durumda olduğundan emin olmak için tanımlayabileceğiniz yöntemlerdir. Örneğin, bir alt öğenin Doğum tarihinin üst öğelerinden daha sonra olduğundan emin olmak için bir kısıtlama tanımlayabilirsiniz. DSL kullanıcısı kısıtlamaların herhangi birini kesen bir model kaydetmeye çalışırsa doğrulama özelliği bir uyarı görüntüler. Daha fazla bilgi için bkz. [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 Kullanıcının çağırabileceği menü komutlarını da tanımlayabilirsiniz. Komutları modeli değiştirebilir. Ayrıca, Visual Studio ve dış kaynaklarla diğer modellerle etkileşime girebilirler. Daha fazla bilgi için bkz. [nasıl yapılır: standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>DSL dağıtma
 Diğer kullanıcıların, etki alanına özgü dili kullanmasına izin vermek için bir Visual Studio uzantısı (VSıX) dosyası dağıtırsınız. Bu, DSL çözümünü yapılandırdığınızda oluşturulur.

 Çözümünüzün bin klasöründe. vsix dosyasını bulun. Onu yüklemek istediğiniz bilgisayara kopyalayın. Bu bilgisayarda VSıX dosyasına çift tıklayın. DSL, bu bilgisayardaki tüm Visual Studio örneklerinde kullanılabilir.

 Aynı yordamı kullanarak DSL 'yi kendi bilgisayarınıza yükleyebilirsiniz. böylece, Visual Studio 'nun Deneysel örneğini kullanmanız gerekmez.

 Daha fazla bilgi için bkz. [etki alanına özgü dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="Reset"></a>Eski deneysel DSLs 'ler kaldırılıyor
 Artık istemediğiniz deneysel DSLs 'Leri oluşturduysanız, Visual Studio Deneysel örneğini sıfırlayarak bunları bilgisayarınızdan kaldırabilirsiniz.

 Bu, bilgisayarınızdan tüm deneysel DSLs ve diğer deneysel Visual Studio uzantılarını kaldırır. Bunlar hata ayıklama modunda yürütülen uzantılardır.

 Bu yordam, VSıX dosyası çalıştırılarak tamamen yüklenmiş olan DSLs 'leri veya diğer Visual Studio uzantılarını kaldırmaz.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Visual Studio Deneysel örneğini sıfırlamak için

1. **Başlat**' a tıklayın, **tüm programlar**, **Microsoft Visual Studio 2010 SDK**ve **araçlar**' a tıklayın ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın**.

2. Hala kullanmak istediğiniz deneysel DSLs 'leri veya diğer deneysel Visual Studio uzantılarını yeniden derleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
