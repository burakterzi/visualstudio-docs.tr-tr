---
title: T4 Şablon Yönergesi
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 410bc879ff4822f19436794d3cb99732be9d413e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983698"
---
# <a name="t4-template-directive"></a>T4 Şablon Yönergesi

Visual Studio T4 metin şablonu genellikle şablonun nasıl işleneceğini belirten bir `template` yönergesiyle başlar. Bir metin şablonu ve içerdiği herhangi bir dosya içinde birden fazla şablon yönergesi bulunmamalıdır.

Metin şablonları yazma hakkında genel bir bakış için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template-directive"></a>Şablon Yönergesini Kullanma

```
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>
```

`template` yönergesinin, dönüşümün farklı yönlerini belirtmenizi sağlayan birkaç özniteliği vardır. Tüm öznitelikler isteğe bağlıdır.

## <a name="compileroptions-attribute"></a>compilerOptions özniteliği

Örnek:

`compilerOptions="optimize+"`

Geçerli değerler:

Tüm geçerli derleyici seçenekleri.

Çalışma zamanı (önceden işlenmiş) şablonları için yok sayılır.

Bu seçenekler, şablon [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]dönüştürüldüğünde uygulanır ve sonuçta elde edilen kod derlenir.

## <a name="culture-attribute"></a>culture özniteliği

Örnek:

`culture="de-CH"`

Geçerli değerler:

Sabit kültür olan "" varsayılan değerdir.

xx-XX biçiminde bir dize olarak ifade edilen bir kültür. Örneğin, en-US, ja-JP, de-CH, de-DE. Daha fazla bilgi için bkz. <xref:System.Globalization.CultureInfo?displayProperty=fullName>.

Culture özniteliği, bir ifade bloğu metne dönüştürüldüğünde kullanılacak kültürü belirtir.

## <a name="debug-attribute"></a>debug özniteliği

Örnek:

```
debug="true"
```

Geçerli değerler:

`true`

`false` (varsayılan)

`debug` özniteliği `true`ise, ara kod dosyası, hata ayıklayıcının, şablonunuzda bir kesmenin veya özel durumun gerçekleştiği konumu daha doğru belirlemesine olanak tanıyan bilgiler içerir.

Tasarım zamanı şablonlarında, ara kod dosyası **% Temp%** dizininize yazılır.

Hata ayıklayıcıda bir tasarım zamanı şablonu çalıştırmak için, metin şablonunu kaydedin, sonra Çözüm Gezgini metin şablonunun kısayol menüsünü açın ve **T4 şablonunda hata ayıkla**' yı seçin.

## <a name="hostspecific-attribute"></a>hostspecific özniteliği

Örnek:

```
hostspecific="true"
```

Geçerli değerler:

`true`

`false` (varsayılan)

`trueFromBase`

Bu özniteliğin değerini `true` olarak ayarlarsanız, metin şablonunuz tarafından oluşturulan sınıfa `Host` adlı bir özellik eklenir. Özelliği, dönüşüm altyapısının ana bilgisayarına bir başvurudur ve [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))olarak bildirilmiştir. Özel bir sunucu tanımladıysanız, bunu özel ana bilgisayar türüne atayabilirsiniz.

Bu özelliğin türü ana bilgisayarın türüne bağlı olduğundan, yalnızca belirli bir ana bilgisayar ile çalışan bir metin şablonu yazıyorsanız faydalıdır. [Tasarım zamanı şablonları](../modeling/design-time-code-generation-by-using-t4-text-templates.md), ancak [çalışma zamanı şablonları](../modeling/run-time-text-generation-with-t4-text-templates.md)için geçerlidir.

`hostspecific` `true` ve Visual Studio kullanıyorsanız, Visual Studio özelliklerine erişmek için `this.Host` IServiceProvider 'a çevirebilirsiniz. Projedeki bir dosyanın mutlak yolunu almak için `Host.ResolvePath(filename)` de kullanabilirsiniz. Örneğin:

```csharp
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System.IO" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<# // Get the Visual Studio API as a service:
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

<#
 // Find a path within the current project:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

`inherits` ve `hostspecific` özniteliklerini birlikte kullanırsanız, türetilmiş sınıfta Host = "trueFromBase" ve taban sınıfta Host = "true" değerini belirtin. Bu, oluşturulan koddaki `Host` özelliğinin çift tanımını önler.

## <a name="language-attribute"></a>language özniteliği

Örnek:

`language="VB"`

Geçerli değerler:

`C#` (varsayılan)

`VB`

`language` özniteliği, deyim ve ifade blokları içindeki kaynak kodu için kullanılacak dili ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] veya [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]) belirtir. Çıktının oluşturulmasında kullanılan ara kod dosyası bu dili kullanır. Bu dil, şablonunuzun oluşturduğu ve herhangi bir türdeki bir metin olabilecek dille ilişkili değildir.

Örneğin:

```vb
<#@ template language="VB" #>
<#@ output extension=".txt" #>
Squares of numbers:
<#
  Dim number As Integer
  For number = 1 To 4
#>
  Square of <#= number #> is <#= number * number #>
<#
  Next number
#>
```

## <a name="inherits-attribute"></a>inherits özniteliği

Şablonunuzun program kodunun, bir metin şablonundan oluşturulabilen başka bir sınıftan devralma işlemi yapabileceğini belirtebilirsiniz.

### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Çalışma zamanı (önceden işlenmiş) metin şablonunda devralma

Türetilmiş birkaç varyanta sahip bir temel şablon oluşturmak için çalışma zamanı metin şablonları arasında devralmayı kullanabilirsiniz. Çalışma zamanı şablonları, **özel araç** özelliği **Texttemplatingfileönişlemci**olarak ayarlanmış olanlardır. Çalışma zamanı şablonu, şablonda tanımlanan metin oluşturmak için uygulamanızda çağırabildiğiniz bir kod oluşturur. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

Bir `inherits` özniteliği belirtmezseniz, metin şablonınızdan bir temel sınıf ve türetilmiş sınıf oluşturulur. Bir `inherits` özniteliği belirttiğinizde yalnızca türetilmiş sınıf oluşturulur. Bir taban sınıfı elle yazabilirsiniz, ancak türetilmiş sınıf tarafından kullanılan yöntemleri sağlaması gerekir.

Daha genel bir durum, önceden işlenmiş başka bir şablonu taban sınıf olarak belirtmenizdir. Temel şablon, türetilmiş şablonlara ait metinle ayrılabilen ortak metin blokları sağlar. Metin parçaları içeren yöntemleri tanımlamak için sınıf özelliği bloklarını `<#+ ... #>` kullanabilirsiniz. Örneğin, türetilmiş şablonlarda geçersiz kılınabilen sanal yöntemler sağlayacak şekilde, çıktı metninin çerçevesini temel şablona yerleştirebilirsiniz:

Çalışma zamanı (önceden işlenmiş) metin şablonu BaseTemplate.tt:

```scr
This is the common header.
<#
  SpecificFragment1();
#>
A common central text.
<#
  SpecificFragment2();
#>
This is the common footer.
<#+
  // Declare abstract methods
  protected virtual void SpecificFragment1() { }
  protected virtual void SpecificFragment2() { }
#>
```

Çalışma zamanı (önceden işlenmiş) metin şablonu DerivedTemplate1.tt:

```csharp
<#@ template language="C#" inherits="BaseTemplate" #>
<#
  // Run the base template:
  base.TransformText();
#>
<#+
// Provide fragments specific to this derived template:
protected override void SpecificFragment1()
{
#>
   Fragment 1 for DerivedTemplate1
<#+
}
protected override void SpecificFragment2()
{
#>
   Fragment 2 for DerivedTemplate1
<#+
}
#>
```

DerivedTemplate1 olanağını çağırmak için uygulama kodu:

```csharp
Console.WriteLine(new DerivedTemplate().TransformText());
```

Sonuç çıktısı:

```
This is the common header.
   Fragment 1 for DerivedTemplate1
A common central text.
   Fragment 2 for DerivedTemplate1
This is the common footer.
```

Temel ve türetilmiş sınıfları farklı projelerde oluşturabilirsiniz. Temel projeyi veya derlemeyi türetilen projenin başvurularına eklemeyi unutmayın.

Ayrıca sıradan bir elle yazılmış sınıfı taban sınıf olarak kullanabilirsiniz. Taban sınıfın, türetilmiş sınıf tarafından kullanılan yöntemleri sağlaması gerekir.

> [!WARNING]
> `inherits` ve `hostspecific` özniteliklerini birlikte kullanıyorsanız, ana sınıfta hostspecific = "trueFromBase" değerini türetilmiş sınıfta ve Host = "true" olarak belirtin. Bu, oluşturulan koddaki `Host` özelliğinin çift tanımını önler.

### <a name="inheritance-in-a-design-time-text-template"></a>Tasarım zamanı metin şablonunda devralma

Tasarım zamanı metin şablonu, **özel aracın** **TextTemplatingFileGenerator**olarak ayarlandığı bir dosyadır. Şablon, Visual Studio projenizin bir kısmını oluşturan kod veya metin çıkış dosyası oluşturur. Çıktı dosyasını oluşturmak için, şablon ilk olarak genellikle görmediğiniz bir ara program kod dosyasına çevrilir. `inherits` özniteliği bu ara kodun temel sınıfını belirtir.

Tasarım zamanı metin şablonu için <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> türetilen herhangi bir temel sınıfı belirtebilirsiniz. Temel sınıfı içeren derlemeyi veya projeyi yüklemek için `<#@assembly#>` yönergesini kullanın.

Daha fazla bilgi için, [Gareth Jones ' bloguna "metin şablonlarına devralma"](https://blogs.msdn.microsoft.com/garethj/2011/01/03/vs2010-sp1-t4-template-inheritance-part-i-sample-metadata/)konusuna bakın.

## <a name="linepragmas-attribute"></a>linePragmas özniteliği

Örnek:

`linePragmas="false"`

Geçerli değerler:

`true` (varsayılan)

`false`

Bu özniteliğin false olarak ayarlanması, oluşturulan kod içinde satır numaralarınızı tanımlayan etiketleri kaldırır. Bu, derleyicinin tüm hataları oluşturulan kodun satır numaralarını kullanarak bildireceği anlamına gelir. Metin şablonunun veya oluşturulan kodun hatalarını ayıklamayı seçebileceğiniz için bu size daha fazla hata ayıklama seçeneği sunar.

Bu öznitelik, pragmalar içindeki mutlak dosya adlarını buluyorsanız, kaynak kodu denetimi altında dikkat dağıtıcı birleştirmelere neden olduğundan da yardımcı olabilir.

## <a name="visibility-attribute"></a>görünürlük özniteliği

Örnek:

`visibility="internal"`

Geçerli değerler:

`public` (varsayılan)

`internal`

Bir çalışma zamanı şablonunda, bu, oluşturulan sınıfın görünürlük özniteliğini ayarlar. Varsayılan olarak, sınıfı, kodunuzun ortak API 'sinin bir parçasıdır, ancak `visibility="internal"` ayarlanarak yalnızca kodunuzun metin oluşturma sınıfını kullanabilmesini sağlayabilirsiniz.
