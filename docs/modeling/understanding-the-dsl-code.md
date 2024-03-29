---
title: DSL Kodunu Anlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44f66ed25ab43db2d08db3cb93263bd61ac3a907
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189452"
---
# <a name="understanding-the-dsl-code"></a>DSL Kodunu Anlama

Etki alanına özgü dil (DSL) çözümü, Visual Studio 'da DSL örneklerini okumak ve güncelleştirmek için kullanabileceğiniz bir API oluşturur. Bu API, DSL tanımından oluşturulan kodda tanımlanmıştır. Bu konuda, oluşturulan API açıklanmaktadır.

## <a name="the-example-solution-component-diagrams"></a>Örnek çözüm: Bileşen diyagramları

Bu konudaki örneklerin çoğunun kaynağı olan çözümü oluşturmak için **bileşen modelleri** çözüm ŞABLONUNDAN bir DSL oluşturun. Bu, yeni bir DSL çözümü oluştururken görüntülenen standart şablonlardan biridir.

> [!NOTE]
> Bileşen diyagramları DSL şablonuna **alana özgü dil Tasarımcısı**denir.

Bu çözüm şablonu hakkında bilginiz yoksa **F5** tuşuna basın ve deneyin. Özellikle bir bağlantı noktası aracını bir bileşene sürükleyerek ve bağlantı noktalarıyla bağlantı kurmak için bağlantı noktaları oluştururuz olduğuna dikkat edin.

![Bileşenler ve birbirine bağlı bağlantı noktaları](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>DSL çözümünün yapısı
 **DSL** projesi DSL için API 'yi tanımlar. **DslPackage** projesi Visual Studio ile nasıl tümleştiğini tanımlar. Ayrıca, modelden oluşturulan kodu da içerebilen kendi projelerinizi ekleyebilirsiniz.

### <a name="the-code-directories"></a>Kod dizinleri
 Bu projelerin her birinde bulunan kodun çoğu **Dsl\dsldefinition.exe**' den oluşturulmuştur. Oluşturulan kod, **oluşturulan kod** klasöründedir. Oluşturulan bir dosyayı görmek için üretilen **. tt** dosyasının yanındaki **[+]** düğmesine tıklayın.

 DSL 'yi anlamanıza yardımcı olması için üretilen kodu incelemenizi öneririz. Oluşturulan dosyaları görmek için Çözüm Gezgini içindeki *. tt dosyalarını genişletin.

 \*. tt dosyaları çok az üretilen kod içerir. Bunun yerine, paylaşılan şablon dosyalarını eklemek için `<#include>` yönergeleri kullanırlar. Paylaşılan dosyalar **\Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates** dizininde bulunabilir

 Kendi program kodunuzu DSL çözümüne eklediğinizde, oluşturulan kod klasörünün dışında ayrı bir dosyaya ekleyin. **Özel bir kod** klasörü oluşturmak isteyebilirsiniz. (Özel bir klasöre yeni bir kod dosyası eklediğinizde, ilk kod isketadaki ad alanını düzeltmeyi unutmayın.)

 Çözümü yeniden oluşturduğunuzda düzenlemeleriniz kaybolacağı için, oluşturulan kodu doğrudan düzenlememenizi önemle tavsiye ederiz. Bunun yerine, DSL 'yi özelleştirmek için:

- DSL tanımındaki birçok parametreyi ayarlayın.

- Oluşturulan sınıflar tarafından tanımlanan veya tarafından devralınan yöntemleri geçersiz kılmak için kısmi sınıfları ayrı kod dosyalarına yazın. Bazı durumlarda, üretilen bir yöntemi geçersiz kılabilmek için DSL tanımındaki bir sınıfın **çift türetilmiş** seçeneğini ayarlamanız gerekir.

- DSL tanımında, üretilen kodun kendi kodunuz için ' kancalar ' sağlamasına neden olan seçenekleri ayarlayın.

     Örneğin, bir etki alanı sınıfına ait **özel Oluşturucu** seçeneğini ayarlarsanız ve sonra çözümü oluşturursanız, hata iletilerini görürsünüz. Bu hata iletilerinden birine çift tıkladığınızda, oluşturulan kodda özel kodunuzun ne sağlaması gerektiğini açıklayan Yorumlar görürsünüz.

- Uygulamanıza özel kod oluşturmak için kendi metin şablonlarınızı yazın. Birçok projede ortak olan şablonların parçalarını paylaşmak için içerme dosyalarını kullanabilir ve kendi dosya yapınız ile başlatılan projeleri ayarlamak için Visual Studio proje şablonları oluşturabilirsiniz.

## <a name="generated-files-in-dsl"></a>DSL 'de oluşturulan dosyalar
 Aşağıdaki oluşturulan dosyalar **DSL** projesinde görüntülenir.

 *Yourdsl* `Schema.xsd`

 DSL örneklerini içeren dosyalar için şema. Bu dosya, derleme (**bin**) dizinine kopyalanır. DSL 'yi yüklediğinizde, model dosyalarının doğrulanması için bu dosyayı **\Program Files\Microsoft Visual Studio 11.0 \ Xml\Schemas dizinine** kopyalayabilirsiniz. Daha fazla bilgi için bkz. [etki alanına özgü dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

 DSL Gezgini 'ndeki seçenekleri ayarlayarak serileştirme 'i özelleştirirseniz, şema buna uygun olarak değişir. Ancak, kendi serileştirme kodunuzu yazarsanız, bu dosya artık gerçek şemayı temsil edemeyebilir. Daha fazla bilgi için bkz. [Dosya depolamayı ve XML Serileştirmeyi özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Bağlantı Oluşturucu, ilişki oluşturan bir sınıftır. Bu, bir bağlantı aracının arkasındaki koddur. Bu dosya, her bağlantı aracı için bir çift sınıf içerir. Adları, etki alanı ilişkisi ve bağlantı aracının adlarından türetilir: *ilişki*Oluşturucu ve *connectortool*ConnectAction.

 (Bileşen çözümü örneğinde, bağlantı oluşturucularının birine ConnectionBuilder denir, bu bir rastlantı, çünkü etki alanı ilişkisi bağlantı olarak adlandırılmaktadır.)

 İlişki, *ilişki* `Builder.Connect()` yönteminde oluşturulur. Varsayılan sürüm, kaynak ve hedef model öğelerinin kabul edilebilir olduğunu doğrular ve ardından ilişkiyi başlatır. Örneğin:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Her Oluşturucu sınıfı, DSL Gezgini 'ndeki **bağlantı oluşturucuları** bölümünde bir düğümden oluşturulur. Bir `Connect` yöntemi, bir veya daha fazla etki alanı sınıfı çifti arasında ilişkiler oluşturabilir. Her bir çift, bir bağlantı bağlama yönergesi tarafından tanımlanır ve bu,, Oluşturucu düğümü altında DSL Gezgini 'nde bulabilirsiniz.

 Örneğin, örnek DSL 'deki üç ilişki türünün her biri için bir bağlantı Oluşturucu bağlantı bağlama yönergeleri ekleyebilirsiniz. Bu, kullanıcıya tek bir bağlantı aracı sağlar. Oluşturulan ilişki türü, Kullanıcı tarafından seçilen kaynak ve hedef öğelerin türlerine bağlıdır.  Bağlantı bağlama yönergeleri eklemek için DSL Gezgininde bir oluşturucuya sağ tıklayın.

 Belirli bir etki alanı ilişkisi türü oluşturulduğunda çalışan özel kod yazmak için, Oluşturucu düğümünün altında uygun bağlantı bağlama yönergesini seçin. Özellikler penceresi, **özel Bağlan kullanır**' ı ayarlayın. Çözümü yeniden derleyin ve ardından ortaya çıkan hataları düzeltmek için kodu sağlayın.

 Kullanıcı bu bağlantı aracını her kullandığında çalışan özel kod yazmak için, bağlantı oluşturucusunun **özel** özelliğini ayarlayın. Kaynak öğeye izin verilip verilmeyeceğini, kaynak ve hedefin belirli bir birleşimine izin verilip verilmeyeceğini ve bir bağlantı yapıldığında modele hangi güncelleştirmelerin yapılması gerektiğine karar veren kodu sağlayabilirsiniz. Örneğin, bir bağlantıya yalnızca diyagramda bir döngü oluşturacaksa izin verebilirsiniz. Tek bir ilişki bağlantısı yerine, kaynak ve hedef arasında birbiriyle ilişkili birkaç öğenin daha karmaşık bir örüntüsünün örneğini oluşturabilirsiniz.

 `Connectors.cs`

 Genellikle başvuru ilişkilerini temsil eden diyagram öğeleri olan bağlayıcıların sınıflarını içerir. Her sınıf DSL tanımındaki bir bağlayıcıdan oluşturulur. Her bağlayıcı sınıfı <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> türetilir

 Çalışma zamanında rengi ve diğer stil özellikleri değişkenlerini yapmak için, DSL tanımı diyagramında sınıfa sağ tıklayın ve **sunulan Ekle**' ye gelin.

 Çalışma zamanında ek stil özellikleri değişkeni yapmak için bkz. Örneğin <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.

 `Diagram.cs`

 Diyagramı tanımlayan sınıfı içerir. <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>türetilir.

 Çalışma zamanında rengi ve diğer stil özellikleri değişkenlerini yapmak için, DSL tanımı diyagramında sınıfa sağ tıklayın ve **sunulan Ekle**' ye gelin.

 Ayrıca, bu dosya modele yeni bir öğe eklendiğinde yanıt veren `FixupDiagram` kuralını içerir. Kural yeni bir şekil ekler ve şekli model öğesine bağlar.

 `DirectiveProcessor.cs`

 Bu yönerge işlemcisi, kullanıcılarınızın DSL örneğini okuyan metin şablonları yazmasına yardımcı olur. Yönerge işlemcisi DSL için derlemeleri (dll 'Ler) yükler ve ad alanınız için etkin bir şekilde `using` deyimlerini ekler. Bu, metin şablonlarındaki kodun DSL 'de tanımladığınız sınıfları ve ilişkileri kullanmasına izin verir.

 Daha fazla bilgi için bkz. [etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md) ve [özel T4 metin şablonu yönerge işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Soyut sınıflar ve model kök sınıfı dahil, tanımladığınız etki alanı sınıflarının uygulamaları. <xref:Microsoft.VisualStudio.Modeling.ModelElement>türetilir.

 Her etki alanı sınıfı şunları içerir:

- Her etki alanı özelliği için bir özellik tanımı ve iç içe geçmiş işleyici sınıfı. OnValueChanging () ve OnValueChanged () öğesini geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [etki alanı özellik değeri değişiklik işleyicileri](../modeling/domain-property-value-change-handlers.md).

   Örnek DSL 'de, `Comment` sınıfı bir özellik `Text` ve bir işleyici sınıfı `TextPropertyHandler` içerir.

- Bu alan sınıfının katıldığı ilişkiler için erişimci özellikleri. (Rol özellikleri için iç içe bir sınıf yoktur.)

   Örnek DSL 'de `Comment` sınıfı, katıştırma ilişkisi `ComponentModelHasComments` aracılığıyla üst modeline erişen erişimcileri içerir.

- Kurucu. Bunları geçersiz kılmak istiyorsanız, set alanı sınıfında **özel Oluşturucusu vardır** .

- Öğe grubu prototipi (EGP) işleyici yöntemleri. Bu, Kullanıcı bu sınıfın örneklerine başka bir öğe *birleştirecan* (eklemek) için gereklidir. Genellikle Kullanıcı bunu bir öğe aracından veya başka bir şekilden sürükleyerek veya yapıştırarak yapar.

   Örnek DSL 'de, bir giriş bağlantı noktası veya çıkış bağlantı noktası bir bileşen üzerinde birleştirilebilir. Ayrıca, bileşenler ve açıklamalar model üzerinde birleştirilebilir. Bu

   Bileşen sınıfındaki EGP işleyici yöntemleri, bir bileşenin bağlantı noktalarını kabul etmesine izin vermez, ancak açıklamaları kabul etmez. Kök model sınıfındaki EGP işleyicisi açıklamaları ve bileşenleri kabul eder, ancak bağlantı noktalarını kabul etmez.

  `DomainModel.cs`

  Etki alanı modelini temsil eden sınıf. <xref:Microsoft.VisualStudio.Modeling.DomainModel>türetilir.

> [!NOTE]
> Bu, modelin kök sınıfıyla aynı değildir.

 Kopyalama ve silme kapanışları, bir öğe kopyalandığında veya silindiğinde diğer öğelerin dahil edileceğini tanımlar. Bu davranışı, her ilişkinin her bir tarafındaki rollerin **Kopyala** ve bu özellik **silme özelliklerini yayar** ayarlayarak denetleyebilirsiniz. Değerlerin dinamik olarak belirlenmesi isterseniz, kapanış sınıflarının yöntemlerini geçersiz kılmak için kod yazabilirsiniz.

 `DomainModelResx.resx`

 Bu, etki alanı sınıfları ve özellikler, özellik adları, araç kutusu etiketleri, standart hata iletileri ve kullanıcıya görüntülenebilecek diğer dizeler gibi dizeler içerir. Ayrıca, görüntü şekilleri için araç simgeleri ve görüntüler içerir.

 Bu dosya, oluşturulan derlemeye bağlanır ve bu kaynakların varsayılan değerlerini sağlar. Kaynakların yerelleştirilmiş bir sürümünü içeren bir uydu derlemesi oluşturarak DSL 'nizi yerelleştirebilirsiniz. Bu sürüm, DSL yerelleştirilmiş kaynaklarla eşleşen bir kültüre yüklendiğinde kullanılacaktır. Daha fazla bilgi için bkz. [etki alanına özgü dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

 `DomainRelationships.cs`

 Bir modeldeki iki öğe arasındaki her bağlantı, bir etki alanı ilişki sınıfının örneğiyle temsil edilir. Tüm ilişki sınıfları <xref:Microsoft.VisualStudio.Modeling.ElementLink> türetilir ve bu, sırasıyla <xref:Microsoft.VisualStudio.Modeling.ModelElement> türetilir. Bir ModelElement olduğundan, ilişkinin bir örneği özelliklere sahip olabilir ve bir ilişkinin kaynağı veya hedefi olabilir.

 `HelpKeywordHelper.cs`

 Kullanıcı F1 tuşuna bastığında kullanılan işlevleri sağlar.

 `MultiplicityValidation.cs`

 1\... 1 veya 1.. * çokluğunu belirttiğiniz ilişki rollerinde, Kullanıcı ilişkinin en az bir örneğinin gerekli olduğu konusunda uyarılmalıdır. Bu dosya, bu uyarıları uygulayan doğrulama kısıtlamalarını sağlar. 1\.. 1 gömme üst öğesine bağlantı doğrulanmadı.

 Bu kısıtlamaların yürütülmesi için DSL Gezgini 'ndeki **Editor\validation** düğümündeki **...** seçeneklerinden birini ayarlamış olmanız gerekir. Daha fazla bilgi için bkz. [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Bu dosya yalnızca bir etki alanı özelliğine özel bir tür tanımlayıcısı eklediyseniz kod içerir. Daha fazla bilgi için bkz. [Özellikler penceresini özelleştirme](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

- Aynı bilinen iki öğeye başvurulmadan emin olmak için bir doğrulama yöntemi. Daha fazla bilgi için bkz. [Dosya depolamayı ve XML Serileştirmeyi özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md).

- Serileştirme sınıfları tarafından yaygın olarak kullanılan işlevleri sağlayan SerializationHelper sınıfı.

  `Serializer.cs`

  Her etki alanı sınıfı, ilişki, şekil, bağlayıcı, Diyagram ve model için seri hale getirici sınıfı.

  Bu sınıfların özelliklerinin birçoğu, **XML serileştirme davranışı**altında DSL Gezgini 'ndeki ayarlar tarafından denetlenebilir.

  `Shapes.cs`

  DSL tanımındaki her şekil sınıfı için bir sınıf. Şekiller <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> türetilir. Daha fazla bilgi için bkz. [Dosya depolamayı ve XML Serileştirmeyi özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md).

  Oluşturulan yöntemleri kısmi bir sınıfta kendi yöntemleriniz ile geçersiz kılmak için, küme, DSL tanımındaki bağlayıcı için **çift türetilmiş oluştur oluşturur** . Bir oluşturucuyu kendi kodunuzla değiştirmek için, kümesinin **özel Oluşturucusu vardır**.

  Çalışma zamanında rengi ve diğer stil özellikleri değişkenlerini yapmak için, DSL tanımı diyagramında sınıfa sağ tıklayın ve **sunulan Ekle**' ye gelin.

  Çalışma zamanında ek stil özellikleri değişkeni yapmak için bkz. Örneğin <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Öğesi grup prototiplerini öğe araçlarına yükleyerek araç kutusunu ayarlar. Bu prototiptürlerin kopyaları, Kullanıcı aracı çalıştırdığında hedef öğelerle birleştirilir.

  Birkaç nesne grubunu oluşturan bir araç kutusu öğesini tanımlamak için `CreateElementPrototype()` geçersiz kılabilirsiniz. Örneğin, alt bileşenlere sahip nesneleri temsil etmek için bir öğe tanımlayabilirsiniz. Kodu değiştirdikten sonra, araç kutusu önbelleğini temizlemek için Visual Studio 'nun Deneysel örneğini sıfırlayın.

## <a name="generated-files-in-the-dslpackage-project"></a>DslPackage projesinde oluşturulan dosyalar
 DslPackage, Windows, araç kutusu ve menü komutlarını yöneten DSL modelini Visual Studio Kabuğu 'na bağar. Sınıfların çoğu çift türetilir, böylece yöntemlerinden herhangi birini geçersiz kılabilirsiniz.

 `CommandSet.cs`

 Diyagramda görünür olan sağ tıklama menü komutları. Bu kümeyi uyarlayabilir veya ekleyebilirsiniz. Bu dosya, komutların kodunu içerir. Menülerde komutların konumu Commands. vsct dosyası tarafından belirlenir. Daha fazla bilgi için bkz. [Kullanıcı komutları ve eylemleri yazma](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `Constants.cs`

 Yapılamıyor.

 `DocData.cs`

 *Yourdsl* `DocData`, bir modeli dosyaya yüklemeyi ve kaydetmeyi yönetir ve mağaza örneğini oluşturur.

 Örneğin, DSL 'yi bir dosya yerine bir veritabanına kaydetmek istiyorsanız `Load` ve `Save` yöntemlerini geçersiz kılabilirsiniz.

 `DocView.cs`

 *Yourdsl* `DocView` diyagramın göründüğü pencereyi yönetir. Örneğin, diyagramı bir Windows formu içine katabilirsiniz:

 DslPackage projesine bir kullanıcı denetim dosyası ekleyin. Diyagramın görüntülenebileceği bir panel ekleyin. Düğmeleri ve diğer denetimleri ekleyin. Formun kod görünümünde, aşağıdaki kodu ekleyerek adı DSL 'nize göre ayarlama:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Data;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Shell;

namespace Company.EmbedInForm
{
  public partial class UserControl1 : UserControl
  {
    public UserControl1()
    {
      InitializeComponent();
    }

    private DiagramDocView docView;

    public UserControl1(DiagramDocView docView, Control content)
      : this()
    {
      this.docView = docView;
      panel1.Controls.Add(content);
    }

    private void button1_Click(object sender, EventArgs e)
    {
      ExampleModel modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      foreach (ExampleElement element in modelRoot.Elements)
      {
       listBox1.Items.Add(element.Name);
      }
    }
  }
  internal partial class EmbedInFormDocView
  {

    private ContainerControl container;

    /// <summary>
    /// Return a User Control instead of the DSL window.
    /// The user control will contain the DSL window.
    /// </summary>

    public override System.Windows.Forms.IWin32Window Window
    {
      get
      {
        if (container == null)
        {
          // Put the normal DSL Window inside our control
          container = new UserControl1(this, (Control)base.Window);
        }
        return container;
      }
    }
  }

}
```

 `EditorFactory.cs`

 `DocData` ve `DocView`örnekleyen. DSL paketiniz başlatıldığında, Visual Studio 'Nun bir düzenleyiciyi açmak için kullandığı standart bir arabirimi karşılar. Package.cs içinde `ProvideEditorFactory` özniteliğinde başvurulur

 `GeneratedVSCT.vsct`

 Menülerde sağ tıklama (bağlam) menüsü, **düzenleme** menüsü gibi menülerde standart menü komutlarını bulur. Komutların kodu CommandSet.cs ' dir. Standart komutları yeniden konumlandıralabilir veya değiştirebilir ve kendi komutlarınızı ekleyebilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı komutları ve eylemleri yazma](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `ModelExplorer.cs`

 DSL için model Gezginini tanımlar. Bu, kullanıcının diyagram ile birlikte gördüğü modelin ağaç görünümüdür.

 Örneğin, öğelerin model Gezgininde görünme sırasını değiştirmek için `InsertTreeView()` geçersiz kılabilirsiniz.

 Model Gezgini 'ndeki seçimin diyagram seçimiyle eşitlenmiş kalmasını istiyorsanız aşağıdaki kodu kullanabilirsiniz:

```csharp
protected override void OnSelectionChanged(global::System.EventArgs e)
{
base.OnSelectionChanged(e);
// get the selected element
DslModeling::ModelElement selectedElement =
this.PrimarySelection as DslModeling::ModelElement;
// Select in the model explorer
SelectInModelExplorer<YOURLANGUAGEExplorerToolWindow>(selectedElement);
}
private void SelectInModelExplorer<T>(DslModeling::ModelElement modelElement)
where T : DslShell.ModelExplorerToolWindow
{
DslShell::ModelingPackage package =
this.GetService(typeof(VSShell.Package)) as DslShell::ModelingPackage;

if (package != null)
{
// find the model explorer window
T explorerWindow = package.GetToolWindow(typeof(T), true) as T;
if (explorerWindow != null)
{
// get the tree container
DslShell.ModelExplorerTreeContainer treeContainer =
explorerWindow.TreeContainer;
// find the tree node
DslShell.ExplorerTreeNode treeNode =
treeContainer.FindNodeForElement(modelElement);
// select the node
explorerWindow.TreeContainer.ObjectModelBrowser.SelectedNode = treeNode;
}
}
}
```

 `ModelExplorerToolWindow.cs`

 Model Gezgini 'nin görüntülendiği pencereyi tanımlar. Gezgin içindeki öğelerin seçimini işler.

 `Package.cs`

 Bu dosya, DSL 'nin Visual Studio ile nasıl tümleştiğini tanımlar. Paket sınıfındaki öznitelikler, dosya uzantınızı içeren dosyalar için bir işleyici olarak DSL 'yi kaydeder, onun araç kutusunu tanımlar ve yeni bir pencerenin nasıl açılacağını tanımlar. Initialize () yöntemi, ilk DSL bir Visual Studio örneğine yüklendiğinde bir kez çağrılır.

 `Source.extension.vsixmanifest`

 Bu dosyayı özelleştirmek için `.tt` dosyasını düzenleyin.

> [!WARNING]
> . Tt dosyasını simgeler veya görüntüler gibi kaynakları içerecek şekilde düzenlerseniz, kaynağın VSıX derlemesinde bulunduğundan emin olun. Çözüm Gezgini, dosyayı seçin ve **VSIX özelliğinde içer** özelliğinin `True` olduğundan emin olun.

 Bu dosya, DSL 'nin bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) nasıl paketlendiğini denetler. Daha fazla bilgi için bkz. [etki alanına özgü dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
